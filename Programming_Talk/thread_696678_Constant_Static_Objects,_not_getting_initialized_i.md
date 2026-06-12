---
title: "Constant Static Objects, not getting initialized in g++"
date: 2008-02-14
forum: Programming Talk
---

### Post by vnair on 2008-02-14
Hi,
I have a static constant object and have initialized in the corresponding cpp file. This goes in a shared library. 
the declaration and definition of the variable is as below..

------header file -------------
class LCMAspect { 

    protected:
        int e;
        std::string name;
       
        enum {
            unknown_e,
            none_e,
            all_e,
            any_e,
            last_e
        } ;
     
        static const LCMAspect unknown;
      ....
  }

---------cpp file ------------------
const LCMAspect LCMAspect::unknown(LCMAspect::unknown_e, "unknown");

Now from another class in the same module, I am using something like

LCMDelayModeAspect::LCMDelayModeAspect ( ): LCMAspect(LCMAspect::unknown) {}

Now when my application tries to load this library during run time, it gives segmentation fault, where I am trying to access the std::string name field of the static object LCMAspect::unknown.

The same code work fine with the arm compiler. 

On tracking the segmentation fault using GDB, I am getting something like this....


(gdb) bt
#0  0xb7a3dedf in std::basic_string<char, std::char_traits<char>, std::allocator<char> >::basic_string () from /usr/lib/libstdc++.so.6
#1  0xb7c6a0c8 in LCMAspect::str (this=0x815ad70) at ../src/MAspect.cpp:55
#2  0xb7c6a16c in LCMAspect (this=0xb7c8c9d4, _a=@0x815ad70) at ../src/MAspect.cpp:65
#3  0xb7c6bb7f in LCMDelayModeAspect (this=0xb7c8c9d4) at ../src/MDelayModeAspect.cpp:47
#4  0xb7c71445 in LCMVar (this=0xb7c8c980, _parent=0x0, _aspect=@0x815ad70) at ../include/MVar.hpp:94
#5  0xb7c71553 in LCMVarAbsOff (this=0xb7c8c980, _parent=0x0) at ../include/MVarAbsOff.hpp:94
#6  0xb7c7ae9b in __static_initialization_and_destruction_0 (__initialize_p=1, __priority=65535) at ../src/MVarAbsOff.cpp:58
#7  0xb7c7aefb in global constructors keyed to mVarAbsOff_bool () at ../src/MVarAbsOff.cpp:59
#8  0xb7c7e2b6 in __do_global_ctors_aux () from /usr/local/lib/libManagedObjects.so
#9  0xb7c67e61 in _init () from /usr/local/lib/libManagedObjects.so
#10 0xb7f76373 in ?? () from /lib/ld-linux.so.2

the problem i felt is that the static object constructor is not called, 

ny one to help me out.. i m really messed up.. 

I am using g++4.1.2 and GCC version 4.1.2 with Ubuntu..

thanks in advance..

---

