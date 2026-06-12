---
title: "(C++) undefined reference to"
date: 2011-07-12
forum: Programming Talk
---

### Post by 130s on 2011-07-12
Hi all,

I'm relatively to C & C++ and stuck at compiling (or should I say linking). Can anyone give me an idea?
Error message and 3 code files are below. These are what I cut down to minimum from I'm actually working on so that you guys can take a better glimpse at.

Env: Ubuntu 10.10, Eclipse Indigo CDT, g++ (Ubuntu/Linaro 4.4.4-14ubuntu5) 4.4.5

Error message:
[PHP]

**** Build of configuration Debug for project SceneRec2 ****

make all 
Building file: ../src/AdaBoost.cpp
Invoking: GCC C++ Compiler
g++ -I"/home/ubuntuLove/Documents/workspace_eclipse/SceneRec2/Includes" -I/usr/src/linux-headers-2.6.35-30/arch/um/include/shared -O0 -g3 -Wall -c -fmessage-length=0 -MMD -MP -MF"src/AdaBoost.d" -MT"src/AdaBoost.d" -o "src/AdaBoost.o" "../src/AdaBoost.cpp"
Finished building: ../src/AdaBoost.cpp
 
Building file: ../src/AdaMain.cpp
Invoking: GCC C++ Compiler
g++ -I"/home/ubuntuLove/Documents/workspace_eclipse/SceneRec2/Includes" -I/usr/src/linux-headers-2.6.35-30/arch/um/include/shared -O0 -g3 -Wall -c -fmessage-length=0 -MMD -MP -MF"src/AdaMain.d" -MT"src/AdaMain.d" -o "src/AdaMain.o" "../src/AdaMain.cpp"
../src/AdaMain.cpp: In function ‘int main(int, char**)’:
../src/AdaMain.cpp:6: warning: deprecated conversion from string constant to ‘char*’
Finished building: ../src/AdaMain.cpp
 
Building target: SceneRec2
Invoking: GCC C++ Linker
g++  -o "SceneRec2"  ./src/AdaBoost.o ./src/AdaMain.o   
./src/AdaMain.o: In function `main':
/home/ubuntuLove/Documents/workspace_eclipse/SceneRec2/Debug/../src/AdaMain.cpp:5: undefined reference to `AdaBoost<double>::AdaBoost()'
/home/ubuntuLove/Documents/workspace_eclipse/SceneRec2/Debug/../src/AdaMain.cpp:6: undefined reference to `AdaBoost<double>::readFromFile(char*)'
/home/ubuntuLove/Documents/workspace_eclipse/SceneRec2/Debug/../src/AdaMain.cpp:8: undefined reference to `AdaBoost<double>::~AdaBoost()'
/home/ubuntuLove/Documents/workspace_eclipse/SceneRec2/Debug/../src/AdaMain.cpp:8: undefined reference to `AdaBoost<double>::~AdaBoost()'
collect2: ld returned 1 exit status
make: *** [SceneRec2] Error 1

**** Build Finished ****
[/PHP]#1. I receive the same result when I execute g++ on terminal.
#2. The path of .o files in the argument for linker should be correct (./src/###.o).

AdaBoost.h
[PHP]
#ifndef _ADABOOST_H
#define _ADABOOST_H

#include <iostream>

const double eps = 2.2204e-16;

template<class T>
class AdaBoost
{
        int N; //Number of Instances
        int D; //Number of Dimensions
        int nL; //Number of Learners / Classifiers / Rules

        T** fVectors;
        int* labels;

        void learnRule(int t, double* dist);
        double genRule(int t, int* L, double* dist);

    public:

        //Default Constructor
        AdaBoost();

        //Constructor
        AdaBoost(T** data, int* labels, int n, int d, int nL);

        //Train function
        void train();

        //Test function
        void test(double** data, double* pMap);
        void test(double** data, double* pMap, int n);

        int writeToFile(char* fName);
        int readFromFile(char* fName);

        //Destructor
        ~AdaBoost();
};
#endif
[/PHP]AdaBoost.cpp
[PHP]
#include "AdaBoost.h"

#include <fstream>

using namespace std;

template class AdaBoost<double> ;

template<class T>
int AdaBoost<T>::readFromFile(char* fName) {

    ifstream inFile;

    int temp;
    int d, dir;
    float thr, wt;

    inFile.open(fName);
    if (!inFile)
        return 0;

    inFile >> temp;
    this->nL = temp;

    int k = 0;
    while (!inFile.eof() && k < nL) {

        inFile >> d;
        inFile >> thr;
        inFile >> dir;
        inFile >> wt;

        k++;
    }

    inFile.close();

    return 1;
}
[/PHP]AdaMain.cpp
[PHP]
#include "AdaBoost.h"
using namespace std;
int main(int argc, char** argv)
{
    AdaBoost<double> rdClass;
    rdClass.readFromFile("testFileComeOn");

    return 0;
}
[/PHP]Thanks,
Isaac

---

### Post by cgroza on 2011-07-12
Double post.[COLOR=#000000][COLOR=#007700]
[/COLOR][/COLOR]

---

### Post by cgroza on 2011-07-12
You have declared:
```

[COLOR=#000000][COLOR=#0000BB]AdaBoost[/COLOR][COLOR=#007700]()
[/COLOR][COLOR=#0000BB]AdaBoost[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000BB]T[/COLOR][COLOR=#007700]** [/COLOR][COLOR=#0000BB]data[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000BB]int[/COLOR][COLOR=#007700]* [/COLOR][COLOR=#0000BB]labels[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000BB]int n[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000BB]int d[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000BB]int nL[/COLOR][COLOR=#007700]);
[COLOR=Blue]~AdaBoost();[/COLOR]
[/COLOR][/COLOR]
```[COLOR=#000000][COLOR=#007700][COLOR=Black]

but never defined them.
[/COLOR]
[COLOR=Black]And I think the argument of readFromFile should be declared as const char*.
[/COLOR]
[/COLOR][/COLOR]

---

### Post by dwhitney67 on 2011-07-12
The template code implementation MUST be done within the header file.  Otherwise, when the AdaMain.cpp is compiled, the compiler will not have a clue about the data type AdaBoost<double>.

Thus take the code you implemented in AdaBoost.cpp, and copy it into AdaBoost.h.  Then remove AdaBoost.cpp from your project.

For example:
```

#ifndef MY_TEMPLATE_H
#define MY_TEMPLATE_H

template <typename T>
class MyTemplate
{
public:
   // declare constructor and implement here!
   MyTemplate(T& someObj)
      : myObj(someObj)
   {
   }

   ...

private:
   T myObj;
};

#endif

```


P.S.  Remove iostream from AdaBoost.h.  It is not required.  Also finish implementing the other methods of the AdaBoost class.

---

### Post by 130s on 2011-07-12
> **cgroza said:**
> You have declared:
```

[COLOR=#000000][COLOR=#0000bb]AdaBoost[/COLOR][COLOR=#007700]()
[/COLOR][COLOR=#0000bb]AdaBoost[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000bb]T[/COLOR][COLOR=#007700]** [/COLOR][COLOR=#0000bb]data[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000bb]int[/COLOR][COLOR=#007700]* [/COLOR][COLOR=#0000bb]labels[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000bb]int n[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000bb]int d[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000bb]int nL[/COLOR][COLOR=#007700]);
[COLOR=Blue]~AdaBoost();[/COLOR]
[/COLOR][/COLOR]
```[COLOR=#000000][COLOR=#007700][COLOR=Black]
but never defined them.
[/COLOR][/COLOR][/COLOR]

Thanks, it might usually be an issue but this time is not since I just over-removed some codes from original.
[COLOR=#000000][COLOR=#007700]
[/COLOR][/COLOR]> 
[COLOR=#000000][COLOR=#007700] [COLOR=Black]And I think the argument of readFromFile should be declared as const char*.
[/COLOR][/COLOR][/COLOR]

Yeah it sheds warning, not error. I modified that.

---

### Post by 130s on 2011-07-12
> **dwhitney67 said:**
> The template code implementation MUST be done within the header file.  Otherwise, when the AdaMain.cpp is compiled, the compiler will not have a clue about the data type AdaBoost<double>.

Thus take the code you implemented in AdaBoost.cpp, and copy it into AdaBoost.h.  Then remove AdaBoost.cpp from your project.


That seems it! Now finally compile moves forward. Thank you so much.

---

