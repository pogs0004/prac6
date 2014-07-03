Practical 6 - Test Plans and Design and Decomposition
---------------------------------------------------------

Nuclear power reactor
------------------------

Background 
------------
In this document I am proposing an overview of what should be considered in an adequate test plan for a nuclear power reactor software system. The specific type of system that I will focus on is the Russian type of reactor that was commonly used pre Chernobyl disaster. 

Decomposition
----------------
The nuclear power reactors used by Russia in the era leading up to the Chernobyl disaster had specific operational constraints that needed to be followed in order to prevent meltdown. While this might seem obvious for any system of this type where the prevention of failures is of critical importance, the Russian rectors at the time where designed with some inherent instabilities and fail points. While this is true, to a point, for all nuclear reactors, the fail safe in the Russian systems were inadequate and in some respects non-existent. 
The critical operational constraint that was not adhered to in the case of the Chernobyl disaster was in regard to the number of fuel rods allowed to be raised (removed) from the reactor core. Should not enough rods be left lowered into the reactor core, the reactor would quickly overheat. To compound the problem, once this unstable overheating state had been reached in these reactors, there was no fail safe in place that could recognise and correct the issue. This was both a missing feature and a design floor in these particular Russian reactors to the point that the design of the system would actually compound the overheating problem.

Test Plans
-----------
Ironically, the Chernobyl disaster occurred as a result of carrying out a badly executed test plan. 
Focusing on the main aspects of testing that will ensure that the reactor never reaches an irreversible critical state; the software system must prevent conditions that are known to generate an unstable reactor core, identify when unstable conditions are present and generate appropriate alerts, take response measures that reverse problems that could lead to meltdown.
As proven at Chernobyl, testing the system directly is risky. While some system features may only be proven this way it should not be the first approach, especially when we think of testing as a way to find faults and not to prove the absence of them. By that token, the Chernobyl meltdown could be considered a successful test that identified a fault and led to the upgrading of existing systems. 
Because testing a nuclear reactor to the point of failure is extremely undesirable a different approach must be taken. 

Important tests
-----------------
System testing
----------------
Ensuring that the system can function correctly as a whole is one of the most important test plans for a power station, it is also the most difficult to carry out in this situation, as mentioned we don’t want to bring a reactor to the point of meltdown to find a fault. 
In this case the system needs to be tested using a dummy platform that fools the software in believing that it is in control of a real power station. This becomes tricky because the dummy platform would actually be another piece of software that behaves as a real reactor, sending messages back the software under test as would be expected from the sensors of a real reactor. A big advantage in this scenario is we can happily send the system the worst possible reactor scenario without any risks.
So what if there’s a fault in the test platform? The sanity check on testing the tests for a nuclear power station should be much broader than any other test regime and perhaps, coming up with new tests and tests of tests could be iterative and never ending in this particular case. 

Unit testing
------------
This would be an important part of a test plan for such a system as it would lend the opportunity for safely testing the system directly (in place). By isolating areas of the power plant to test individually, most areas of the system could be tested with minimal risk. For example, knowing there is an adequate fail safe backup cooling system in place, the unit that controls the raising and lowering of the fuel rods could be effectively tested. 
Constraints on the number of fuel rods raised, resultant alerts and preventative procedures could be tested with unit testing. 

Interference Testing
----------------------
Interference testing would be useful in ensuring that the system reacts correctly to unexpected changes in the normal running of the reactor as would be the case should a genuine physical problem become present in the system. The tests could be simulated either on the dummy platform or the real system by overriding sensors (ensuring there’s a caretaker system in place while the tests are conducted).

Less important tests 
---------------------
Informal code review
-----------------------
While checking code will be important in the early development of the system, by the time code is actually running the system I would consider that faults that can be found through informal code review at the running stage, to highlight a major failing in the development procedures for such a critical system. 

Beta testing
-------------
Beta testing a nuclear reactor sounds like it would be a bad idea as the general premise of this type of testing is to fast track the development of software by deploying it in an unfinished state and testing it in a real environment knowing there is likely to be many faults to be discovered. 

Volume testing
----------------
The volume and type of data that this system has to deal with would be consistent and well defined. Therefore there would be little benefit gained from testing the system far beyond its capacity, assuming sufficient headroom is designed into the system to begin with. Again, should the system not be capable of handling the data volume required it would show major deficiencies in the design and development process. 

While most disasters involving nuclear power stations have been blamed on either human error or natural disasters, developing better systems with the aid of adequate test plans and test driven development will largely reduce the potential for catastrophes. While there are always limitations on development, we would hope that the testing of such systems present an example of the most rigorous regimes that can be employed, with the focus on procedures and safety outweighing the minimisation of costs.
