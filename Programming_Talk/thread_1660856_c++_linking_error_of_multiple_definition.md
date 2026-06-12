---
title: "c++ linking error of multiple definition"
date: 2011-01-05
forum: Programming Talk
---

### Post by jimchen on 2011-01-05
Hi members,
I build up a c++ library of couple hpp files and they define some classes. I have other projects to include this library for inheriting those perdefined classes. In those child-projects, it works well while only one source file includes the hpp file of my library. However, if 2 or more files include the same hpp file of the library, it has linking error of "multiple definition". What is the right way to build up a libray that multiple files of one project can include it at the same time? I don't want to put whole codes in one file because it will become too large and tough to maintain.

I simplified the original code to get people easily understand my program.
Here is my simplified-file-organiztion ,
hpp files of dummy_library:
ShmooUtil.hpp - declare class StepParser and its member function, unsigned int getTotalStep();
ShmooUtil2.hpp - include ShmooUtil.hpp, define unsigned int StepParser::getTotalStep()
AbstractShmoo.hpp - include ShmooUtil.hpp and ShmooUtil2.hpp; declare and define an abstract class AbstractShmoo which declare an object of StepParser inside. 
Shmoo.hpp: include AbstractShmoo.hpp; declare and define class Shmoo which inherits AbstractShmoo. This is the final class which I want other projects to inherits it.

One of my children-project's file-organization:
TX.cpp - includes Shmoo.hpp; all classes of this file will inherit class Shmoo.
RX.cpp - includes Shmoo.hpp; all classes of this file will inherit class Shmoo.


The linking error message is "multiple definition of 'StepParser::getTotalStep()' "

My project is in the trouble of the linking error. I need advices from expertises of c++. I paste my simplified codes below,
ShmooUtil.hpp:
#ifndef INCLUDE_SHMOO_UTIL_HPP
#define INCLUDE_SHMOO_UTIL_HPP

#include <cassert>
#include <string>
#include <map>
#include <utility>
#include <sys/time.h>
using namespace std;


class StepParser
{
public:

  
  unsigned int getTotalStep();
 
 //other decalrations
 
};


#endif

-----------------------------------------------
ShmooUtil2.hpp:
#ifndef SHMOOUTIL2_HPP_
#define SHMOOUTIL2_HPP_

#include "ShmooUtil.hpp"
#include <cmath>
#include <sstream>
using namespace std;


unsigned int StepParser::getTotalStep()
{
    //definitions 
}

 //other definitions

#endif /*SHMOOUTIL2_HPP_*/

----------------------------------------------------------------------------------
AbstractShmoo.hpp:
#ifndef INCLUDE_ABSTRACT_SHMOO_HPP
#define INCLUDE_ABSTRACT_SHMOO_HPP

#include "ShmooUtil.hpp"
#include "ShmooUtil2.hpp"
#include "CommonUtil.hpp"
using namespace std;


class AbstractShmoo: virtual public testmethod::TestMethod
{



protected:
  
  virtual void initialize()
  {
    //definitions

  }
 
 

  virtual void run()
  {
    StepParser stepParserX;
    stepParserX.getTotalStep();
     //other definitions
  }
 
  virtual void saveBeforeShmooRun() = 0;

 //other decalrations
     
};
#endif

--------------------------------------------------------------------------
Shmoo.hpp:
#ifndef SHMOO_HPP_
#define SHMOO_HPP_

#include "AbstractShmoo.hpp"
#include <fstream>
using namespace std;


#ifdef MAINFILE
    #define EXTERN
#else
    #define EXTERN extern
#endif

EXTERN bool pf[100];    //global var which will be utilized by other projects
EXTERN bool pf_rslt;    //global var which will be utilized by other projects



class Shmoo: virtual public AbstractShmoo
{


 
protected:
 
  virtual void initialize()
  {
   
    AbstractShmoo::initialize();
    //other definitions
  }

 
  virtual void saveBeforeShmooRun()
  {
    //definitions
  }

  //other definitions
};

#endif /*SHMOO_HPP_*/


-------------------------------------------------------------------------------------
children-projects, TX.cpp:

#include "Shmoo.hpp"

class TX_SPECTRUM_TEST: public Shmoo
{


virtual void initialize()
{
  Shmoo::initialize();
  //other definitions
}

virtual void run()
{
    //other definitions
}

};

//other definitions


-------------------------------------------------------------------------------------
children-projects, RX.cpp:

#include "Shmoo.hpp"

class RX_SPECTRUM_TEST: public Shmoo
{


virtual void initialize()
{
  Shmoo::initialize();
  //other definitions
}

virtual void run()
{
    //other definitions
}

};

//other definitions




Thanks,
Jim

---

### Post by worksofcraft on 2011-01-05
Well Jim, the problem you are having is that you are mixing definitions and declarations in your header files.

What you need to do is put the definitions in separate .cpp files that you compile into object files that you put in an object library.

The header files are just supposed to tell the compiler that these things exist but not actually define instances of them... otherwise you get multiple definitions.

---

### Post by JakeFrederix on 2011-01-05
Declarations go in the .h file.
The code to make the declarations work goes in a .cpp file with the same name.
Unless it's a template class.

---

### Post by psusi on 2011-01-05
Header files are for declarations, definitions go in a cpp file.

---

### Post by dwhitney67 on 2011-01-06
Two other things should be noted:

1.  Never enter a "using namespace" directive within a header file;

2.  Avoid at all costs the use of global variables when programming in C++; there are better alternatives.

---

### Post by jimchen on 2011-01-06
Hi guys,
Appreciate for your inputs. The "multiple definition" was gone after I push the definitions into a cpp file (replace ShmooUtil2.hpp with ShmooUtil.cpp).


Thanks and Happy New Year,
Jim

---

