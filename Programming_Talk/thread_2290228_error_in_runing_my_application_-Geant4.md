---
title: "error in runing my application -Geant4"
date: 2015-08-10
forum: Programming Talk
---

### Post by medoo2 on 2015-08-10
Dear all
once I tried to run my application on geant4 it gave me this error


/home/medoo/Desktop/app/basicApplication.cc: In function ‘int main(int, char**)’:
/home/medoo/Desktop/app/basicApplication.cc:15:40: error: expected type-specifier before ‘BasicDetectorConstruction’
  runManager->SetUserInitialization(new BasicDetectorConstruction());
                                        ^
/home/medoo/Desktop/app/basicApplication.cc:19:2: error: ‘G4VModularPhysicsList’ was not declared in this scope
  G4VModularPhysicsList* physicsList = new QBBC;
  ^
/home/medoo/Desktop/app/basicApplication.cc:19:25: error: ‘physicsList’ was not declared in this scope
  G4VModularPhysicsList* physicsList = new QBBC;
                         ^
/home/medoo/Desktop/app/basicApplication.cc:19:43: error: expected type-specifier before ‘QBBC’
  G4VModularPhysicsList* physicsList = new QBBC;
                                           ^
/home/medoo/Desktop/app/basicApplication.cc:19:43: error: expected ‘;’ before ‘QBBC’
/home/medoo/Desktop/app/basicApplication.cc:27:32: error: expected type-specifier before ‘BasicPrimaryGeneratorAction’
  runManager->SetUserAction(new BasicPrimaryGeneratorAction());
                                ^
/home/medoo/Desktop/app/basicApplication.cc: At global scope:
/home/medoo/Desktop/app/basicApplication.cc:7:6: warning: unused parameter ‘argc’ [-Wunused-parameter]
  int main(int argc,char** argv){
      ^
/home/medoo/Desktop/app/basicApplication.cc:7:6: warning: unused parameter ‘argv’ [-Wunused-parameter]
make[2]: *** [CMakeFiles/basicApplication.dir/basicApplication.cc.o] Error 1
make[1]: *** [CMakeFiles/basicApplication.dir/all] Error 2
make: *** [all] Error 2

stepes I used to run the app. is 

1- mkdir app-build
2-  source /usr/local/bin/geant4.sh
3-  cmake -DGeant4_DIR=/usr/local/share/geant4.10.01.p02 /home/medoo/Desktop/app
4- make -j 2

I need your help on this
thanks

---

### Post by steeldriver on 2015-08-10
That looks like an error in compiling - not an error in running

You would need to post your actual source code (i.e. the contents of file `basicApplication.cc`) to be sure, but most likely you have forgotten to include one or more header files.

---

### Post by medoo2 on 2015-08-10
#include "G4RunManager.hh"
#include "G4LogicalVolume.hh"




 int main(int argc , char** argv)
{

  G4RunManager* runManager = new G4RunManager;

    // Detector construction
    runManager->SetUserInitialization(DetectorConstruction);

    // Physics list
  
    G4VModularPhysicsList* physicsList = new QBBC;
        physicsList->SetVerboseLevel(1);
    runManager->SetUserInitialization(physicsList);
    
  

    // Primary generator action
  
    runManager->SetUserAction(new BasicPrimaryGeneratorAction());
   
  

    // Initialize G4 kernel
  
    runManager->Initialize();

      //Cause the run manager to generate a single event using the
    //primary generator action registered above.

    runManager->BeamOn(1);

  
    //After the run is complete, free up the memory used by run 
    //manager and return 

    delete runManager;  
    return 0;

 }

this is the contents of basicApplication.cc file .

thank you

---

### Post by QIII on 2015-08-19
*Moved to **Programming Talk***

---

