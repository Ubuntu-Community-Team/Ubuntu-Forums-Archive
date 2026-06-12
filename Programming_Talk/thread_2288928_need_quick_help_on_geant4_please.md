---
title: "need quick help on geant4 please"
date: 2015-07-30
forum: Programming Talk
---

### Post by medoo2 on 2015-07-30
Dear all

I have installed Geant4.10.01.p02 and every thing went smoothly with no errors , but once I tried to simulate example B3 

when I tried to run source command as following
 medoo@medoo-Inspiron-N4050:~/Desktop/B3-build$ source /home/medoo/Desktop/geant4.10.01.p02-build/InstallTreeFiles/geant4.sh


it gave me this error 

bash: cd: /home/medoo/Desktop/geant4.10.01.p02-build/InstallTreeFiles/../lib: No such file or directory
bash: cd: /home/medoo/Desktop/geant4.10.01.p02-build/InstallTreeFiles/../share/Geant4-10.1.2/data/G4NDL4.5: No such file or directory
bash: cd: /home/medoo/Desktop/geant4.10.01.p02-build/InstallTreeFiles/../share/Geant4-10.1.2/data/G4EMLOW6.41: No such file or directory
bash: cd: /home/medoo/Desktop/geant4.10.01.p02-build/InstallTreeFiles/../share/Geant4-10.1.2/data/PhotonEvaporation3.1: No such file or directory
bash: cd: /home/medoo/Desktop/geant4.10.01.p02-build/InstallTreeFiles/../share/Geant4-10.1.2/data/RadioactiveDecay4.2: No such file or directory
bash: cd: /home/medoo/Desktop/geant4.10.01.p02-build/InstallTreeFiles/../share/Geant4-10.1.2/data/G4NEUTRONXS1.4: No such file or directory
bash: cd: /home/medoo/Desktop/geant4.10.01.p02-build/InstallTreeFiles/../share/Geant4-10.1.2/data/G4PII1.3: No such file or directory
bash: cd: /home/medoo/Desktop/geant4.10.01.p02-build/InstallTreeFiles/../share/Geant4-10.1.2/data/RealSurface1.0: No such file or directory
bash: cd: /home/medoo/Desktop/geant4.10.01.p02-build/InstallTreeFiles/../share/Geant4-10.1.2/data/G4SAIDDATA1.1: No such file or directory
bash: cd: /home/medoo/Desktop/geant4.10.01.p02-build/InstallTreeFiles/../share/Geant4-10.1.2/data/G4ABLA3.0: No such file or directory


any one deal with such issue ?  help me :(

---

### Post by steeldriver on 2015-07-30
Did you add the suggested -DGEANT4_INSTALL_DATA=ON to your cmake command?

---

### Post by medoo2 on 2015-07-30
thank you for replying ...

actually I have run this command
  

[FONT=arial][SIZE=4]  $ cmake -DCMAKE_INSTALL_PREFIX=/usr/local -DGEANT4_INSTALL_DATA=ON -DGEANT4_USE_OPENGL_X11=ON -DGEANT4_INSTALL_EXAMPLES=ON -DBUILD_SHARED_LIBS=ON -DBUILD_STATIC_LIBS=ON /home/medoo/Desktop/geant4.10.01.p02
[/SIZE][/FONT][FONT=arial][SIZE=4]   [/SIZE][/FONT]

---

### Post by steeldriver on 2015-07-30
OK so it looks like the geant.sh file is just plain wrong: there is no ../share/Geant4-10.1.2/data directory, everything goes right in ../data (i.e. a data dir at the same level as the InstallTreeFiles dir)

---

### Post by medoo2 on 2015-07-30
then every thing is ok for installation but when I came to run example B3 

I make a build folder for B3 to be B3-build

then 

B3-build $ source /home/medoo/Desktop/geant4.10.01.p02-build/InstallTreeFileslgeant4.sh
it gave me that error 
bash: cd: /home/medoo/Desktop/geant4.10.01.p02-build/InstallTreeFiles/../lib: No such file or directory
bash: cd:  /home/medoo/Desktop/geant4.10.01.p02-build/InstallTreeFiles/../share/Geant4-10.1.2/data/G4NDL4.5:  No such file or directory
bash: cd:  /home/medoo/Desktop/geant4.10.01.p02-build/InstallTreeFiles/../share/Geant4-10.1.2/data/G4EMLOW6.41:  No such file or directory
bash: cd:  /home/medoo/Desktop/geant4.10.01.p02-build/InstallTreeFiles/../share/Geant4-10.1.2/data/PhotonEvaporation3.1:  No such file or directory
bash: cd:  /home/medoo/Desktop/geant4.10.01.p02-build/InstallTreeFiles/../share/Geant4-10.1.2/data/RadioactiveDecay4.2:  No such file or directory
bash: cd:  /home/medoo/Desktop/geant4.10.01.p02-build/InstallTreeFiles/../share/Geant4-10.1.2/data/G4NEUTRONXS1.4:  No such file or directory
bash: cd:  /home/medoo/Desktop/geant4.10.01.p02-build/InstallTreeFiles/../share/Geant4-10.1.2/data/G4PII1.3:  No such file or directory
bash: cd:  /home/medoo/Desktop/geant4.10.01.p02-build/InstallTreeFiles/../share/Geant4-10.1.2/data/RealSurface1.0:  No such file or directory
bash: cd:  /home/medoo/Desktop/geant4.10.01.p02-build/InstallTreeFiles/../share/Geant4-10.1.2/data/G4SAIDDATA1.1:  No such file or directory
bash: cd:  /home/medoo/Desktop/geant4.10.01.p02-build/InstallTreeFiles/../share/Geant4-10.1.2/data/G4ABLA3.0:  No such file or directory

actually , I think I run in the installation path , since geant4.sh and other libraries are installed in geant4.10.01.p02-build folder 

but I do not how to fix this issue

---

### Post by medoo2 on 2015-07-30
so , what to do know , I am beginner in this software and hope to guide me what to do 

thank you so much

---

### Post by medoo2 on 2015-07-30
Geant4-10.1.2 is in the following path 

/home/medoo/Desktop/geant4.10.01.p02-build/CMakeFiles/Export/lib

---

### Post by steeldriver on 2015-07-31
I think the instructions probably assume that you have actually installed ('sudo make install') the software and are running the geant4.sh script from the installed CMAKE_INSTALL_PREFIX/bin directory (not the version in your build directory's InstallTreeFiles/)

See [http://geant4.web.cern.ch/geant4/UserDocumentation/UsersGuides/InstallationGuide/html/ch03.html](http://geant4.web.cern.ch/geant4/UserDocumentation/UsersGuides/InstallationGuide/html/ch03.html)

---

### Post by medoo2 on 2015-08-02
thank you so much , yes it works with me , I run geant4.sh  from CMAKE_install and it is done

I do appreciate your guidance , many thanks

---

### Post by QIII on 2015-08-19
*Moved to **Programming Talk***

---

