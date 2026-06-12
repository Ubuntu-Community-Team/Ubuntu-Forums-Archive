---
title: "warning: unused variable Geant4.10.01.p02"
date: 2015-08-05
forum: Programming Talk
---

### Post by medoo2 on 2015-08-05
Hello everybody 

I have faced issue I do not know if someone has experienced such issue

it was ....


/src/PhysicsList.cc: In member function &#8216;void PhysicsList::ConstructEM()&#8217;:
/src/PhysicsList.cc:224:12: warning: unused variable &#8216;EnergyLimit&#8217; [-Wunused-variable]
   G4double EnergyLimit = 9.9*MeV;
            ^
/src/PhysicsList.cc:227:12: warning: unused variable &#8216;massFactor&#8217; [-Wunused-variable]
   G4double massFactor = 1.0079/4.0026;
            ^
/src/PhysicsList.cc:266:1: error: a function-definition is not allowed here before &#8216;{&#8217; token
 { }
 ^
/src/PhysicsList.cc:271:1: error: a function-definition is not allowed here before &#8216;{&#8217; token
 {
 ^
/src/PhysicsList.cc:286:1: error: expected &#8216;}&#8217; at end of input
 }
 ^

any thoughts please .

thanks

---

### Post by medoo2 on 2015-08-05
/src/PhysicsList.cc: In member function &#8216;void PhysicsList::ConstructEM()&#8217;:
/src/PhysicsList.cc:224:12: warning: unused variable &#8216;EnergyLimit&#8217; [-Wunused-variable]
   G4double EnergyLimit = 9.9*MeV;
            ^
/src/PhysicsList.cc:227:12: warning: unused variable &#8216;massFactor&#8217; [-Wunused-variable]
   G4double massFactor = 1.0079/4.0026;
            ^
/src/PhysicsList.cc:266:1: error: a function-definition is not allowed here before &#8216;{&#8217; token
 { }
 ^
/src/PhysicsList.cc:271:1: error: a function-definition is not allowed here before &#8216;{&#8217; token
 {
 ^
/src/PhysicsList.cc:286:1: error: expected &#8216;}&#8217; at end of input

---

