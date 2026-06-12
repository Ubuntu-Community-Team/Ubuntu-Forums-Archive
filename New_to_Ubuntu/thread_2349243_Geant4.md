---
title: "Geant4"
date: 2017-01-12
forum: New to Ubuntu
---

### Post by agelmi on 2017-01-12
Hello all, I'm new user, and I tried to install GEANT4. Before to install GEANT4 I installed CLHEP. During the installation of GEANT4 I didn't received any error messages, after this I tried to run an example, but I have the follow error:```
Make Error at /usr/local/share/cmake3.7/Modules/FindPackageHandleStandardArgs.cmake:138 (message): Could NOT find CLHEP: CLHEP Header Path Not Found CLHEP Library Not Found Incompatible versions, (found) < 2.3.4.3(required) (missing: CLHEP_LIBRARY CLHEP_INCLUDE_DIR) (Required is at least version "2.3.4.3")
```

But during the installation I specified the "include dir" and the "library" with the follow commands:
```
-DGEANT4_USE_SYSTEM_CLHEP=ON -DCLHEP_INCLUDE_DIR=/home/andrea/GEANT4/CLHEP/2.3.4.3/CLHEP-install/include -DCLHEP_LIBRARY=/home/andrea/GEANT4/CLHEP/2.3.4.3/CLHEP-install/lib/libCLHEP.so
```
I tried also to add the follow command found it in web, but doesn't work```
-DCLHEP_CONFIG_EXECUTABLE=/home/andrea/GEANT4/CLHEP/2.3.4.3/CLHEP-install/bin/clhep-config
```
Some one can help me please? thank a lot!!

---

