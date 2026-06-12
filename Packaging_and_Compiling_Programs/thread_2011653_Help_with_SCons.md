---
title: "Help with SCons"
date: 2012-06-27
forum: Packaging and Compiling Programs
---

### Post by neil_1 on 2012-06-27
i've been trying to compile this program and have been getting errors.
could someone tell me if i'm missing any dependencies ?

[http://www.assembla.com/code/nixcoders/subversion/nodes/qvmkanker/trunk?rev=75]("http://trac.assembla.com/nixcoders/browser/qvmkanker/trunk?rev=8&order=name")

the output i have is
```
neil@crunchbang:~/qvmkanker/qvmkanker/trunk$ scons qvmdump
scons: Reading SConscript files ...

scons: warning: The Options class is deprecated; use the Variables class instead.
File "/home/neil/qvmkanker/qvmkanker/trunk/SConstruct", line 25, in <module>

scons: warning: The BoolOption() function is deprecated; use the BoolVariable() function instead.
File "/home/neil/qvmkanker/qvmkanker/trunk/SConstruct", line 27, in <module>

scons: warning: The build_dir keyword has been deprecated; use the variant_dir keyword instead.
File "/home/neil/qvmkanker/qvmkanker/trunk/SConstruct", line 86, in <module>

scons: warning: The build_dir keyword has been deprecated; use the variant_dir keyword instead.
File "/home/neil/qvmkanker/qvmkanker/trunk/SConstruct", line 93, in <module>
scons: done reading SConscript files.
scons: Building targets ...
scons: building associated VariantDir targets: build/qvmdump
g++ -o build/qvmdump/qvmdump.o -c -Wall -Werror -O2 -Ibuild/libqvm -Ilibqvm qvmdump/qvmdump.cpp
In file included from libqvm/Qvm.h:28,
                 from qvmdump/qvmdump.cpp:27:
libqvm/vm.h:32: error: 'uint32_t' does not name a type
libqvm/vm.h:143: error: 'int32_t' does not name a type
In file included from libqvm/Qvm.h:29,
                 from qvmdump/qvmdump.cpp:27:
libqvm/Opcode.h:33: error: 'qvmOffset' does not name a type
libqvm/Opcode.h:35: error: 'int32_t' does not name a type
In file included from qvmdump/qvmdump.cpp:27:
libqvm/Qvm.h:35: error: 'qvmOffset' was not declared in this scope
libqvm/Qvm.h:35: error: template argument 1 is invalid
libqvm/Qvm.h:35: error: template argument 3 is invalid
libqvm/Qvm.h:35: error: template argument 4 is invalid
libqvm/Qvm.h:35: error: invalid type in declaration before ';' token
qvmdump/qvmdump.cpp: In function 'int main(int, char**)':
qvmdump/qvmdump.cpp:56: error: 'EXIT_FAILURE' was not declared in this scope
qvmdump/qvmdump.cpp:63: error: 'EXIT_FAILURE' was not declared in this scope
qvmdump/qvmdump.cpp:66: error: 'EXIT_FAILURE' was not declared in this scope
qvmdump/qvmdump.cpp:69: error: 'EXIT_FAILURE' was not declared in this scope
qvmdump/qvmdump.cpp:74: error: 'EXIT_SUCCESS' was not declared in this scope
qvmdump/qvmdump.cpp:87: error: 'EXIT_SUCCESS' was not declared in this scope
qvmdump/qvmdump.cpp: In function 'void showDisasm(Qvm&, bool)':
qvmdump/qvmdump.cpp:122: error: 'class Opcode' has no member named 'offset'
qvmdump/qvmdump.cpp:131: error: 'class Opcode' has no member named 'argValue'
qvmdump/qvmdump.cpp:144: error: wrong number of template arguments (1, should be 2)
/usr/include/c++/4.4/bits/stl_pair.h:67: error: provided for 'template<class _T1, class _T2> struct std::pair'
qvmdump/qvmdump.cpp:144: error: invalid type in declaration before ';' token
qvmdump/qvmdump.cpp:146: error: request for member 'equal_range' in 'qvm->Qvm::infos', which is of non-class type 'info_t'
qvmdump/qvmdump.cpp:146: error: 'class Opcode' has no member named 'offset'
qvmdump/qvmdump.cpp:147: error: expected initializer before 'it'
qvmdump/qvmdump.cpp:147: error: request for member 'second' in 'pit', which is of non-class type 'int'
qvmdump/qvmdump.cpp:148: error: 'class Opcode' has no member named 'second'
scons: *** [build/qvmdump/qvmdump.o] Error 1
scons: building terminated because of errors.

```

---

### Post by SevenMachines on 2012-06-28
There was a gcc include file sort out round about version 4.3 (i think), these errors are examples of older code relying on include files being automatically added where they now need to be added manually. If remembered correctly,
uint32_t means you need <stdint.h>
EXIT_FAILURE means you need <cstdlib>
I'll try and find the list of common errors

---

### Post by SevenMachines on 2012-06-28
See [http://gcc.gnu.org/gcc-4.3/porting_to.html](http://gcc.gnu.org/gcc-4.3/porting_to.html) section 'Header Dependency Cleanup' for the most common ones

---

### Post by neil_1 on 2012-06-28
Thanks for that SevenMachines
I've added the headers needed and most of the errors went away apart from one.
i get a 
```

libqvm/Qvm.cpp:54: error: 'strerror' is not a member of 'std'

```when i try to compile.
if i remove the "std::" before the strerror, i get a lot of the same error
```

 libqvm/vm.cpp:215: error: deprecated conversion from string constant to 'char*'

```and at that particular line, there is no conversion at all.

i've uploaded the updated code if you could point me in the right direction.

---

### Post by SevenMachines on 2012-06-28
I think 
#include <cstring>

---

### Post by neil_1 on 2012-06-28
> **SevenMachines said:**
> I think 
#include <cstring>
still have the same error
libqvm/vm.cpp:215: error: deprecated conversion from string constant to 'char*'

the error lies on the last line of this piece of code
```

char *opcodeNames[] = {
    "UNDEF",

    "IGNORE",

    "BREAK",

    "ENTER",
    "LEAVE",
    "CALL",
    "PUSH",
    "POP",

    "CONST",
    "LOCAL",

    "JUMP",

    //-------------------

    "EQ",
    "NE",

    "LTI",
    "LEI",
    "GTI",
    "GEI",

    "LTU",
    "LEU",
    "GTU",
    "GEU",

    "EQF",
    "NEF",

    "LTF",
    "LEF",
    "GTF",
    "GEF",

    //-------------------

    "LOAD1",
    "LOAD2",
    "LOAD4",
    "STORE1",
    "STORE2",
    "STORE4",
    "ARG",

    "BLOCK_COPY",

    //-------------------

    "SEX8",
    "SEX16",

    "NEGI",
    "ADD",
    "SUB",
    "DIVI",
    "DIVU",
    "MODI",
    "MODU",
    "MULI",
    "MULU",

    "BAND",
    "BOR",
    "BXOR",
    "BCOM",

    "LSH",
    "RSHI",
    "RSHU",

    "NEGF",
    "ADDF",
    "SUBF",
    "DIVF",
    "MULF",

    "CVIF",
    "CVFI"
};//error is on this line (though i know it's probably not this)

```i don't understand why though

---

### Post by SevenMachines on 2012-06-28
Thats a slightly different if similarly age related error, the error is more 'newish' gcc stuff.
"something" is a string const, but the array is declared 'char *', which isnt const. You should declare a const char * array here, be warned you may (probably) end up chasing through the code following a ripple of const correct changes though. If you want to fix it properly then thats what to do. 
If you just want to ignore the warning and keep going it'll probably be fine :) then add
'-Wno-write-strings' to your CFLAGS in SConstruct, which hopefully should be in there somewhere. Hopefully thats all fairly accurate :)

---

### Post by neil_1 on 2012-06-28
That did it!
Thanks a bunch SevenMachines!

---

