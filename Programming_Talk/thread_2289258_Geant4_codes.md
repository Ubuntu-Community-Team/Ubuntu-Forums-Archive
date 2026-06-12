---
title: "Geant4 codes"
date: 2015-08-02
forum: Programming Talk
---

### Post by medoo2 on 2015-08-02
dear all

I am trying to see how they wrote example B1 or B3 , to know how they made the codes and to understand how to write the codes .
actually , I have run the examples successfully , but I did not know where is the code files to be able to see how it made .

please help me getting the written codes .

I have Geat4.10.01.p02 installed on  ubuntu 14.04.2 

thanks

---

### Post by steeldriver on 2015-08-02
The source code is in the examples directory - if that's what you're asking

e.g.

```

$ ls geant4.10.01.p02/examples/basic/B1
CMakeLists.txt  **exampleB1.cc**  exampleB1.in  exampleB1.out  GNUmakefile  History  include  init_vis.mac  README  run1.mac  run2.mac  **src  **vis.mac

```

---

### Post by medoo2 on 2015-08-02
thank you dear steeldriver 

I found in src these files
B1ActionInitialization.cc     B1PrimaryGeneratorAction.cc     B1SteppingAction.cc    B1DetectorConstruction.cc     B1RunAction.cc   B1EventAction.cc           B1Run.cc

so , di I can make little changes on them and run to see , just to try understand how to write a code 

I do appreciate your assistance

---

### Post by QIII on 2015-08-19
*Moved to **Programming Talk***

---

