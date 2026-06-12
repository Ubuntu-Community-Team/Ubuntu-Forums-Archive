---
title: "iostream, related linker error (using g++)"
date: 2010-05-05
forum: Programming Talk
---

### Post by mashaikh on 2010-05-05
Hi all,
 
I need help! 
 
I am getting following linker errors using g++ and ld

***`__static_initialization_and_destruction_0'
***iostream:76: undefined reference to `std::ios_base::Init::Init()'
***iostream:76: undefined reference to `std::ios_base::Init::~Init()'

GNU/Linux using g++ 

.\Objects\main.o: In function `__static_initialization_and_destruction_0':
/cygdrive/c/Hitex/GnuToolPackageArm/bin/../lib/gcc/arm-hitex-elf/4.1.1/../../../../include/c++/4.1.1/iostream:76: undefined reference to `std::ios_base::Init::Init()'
/cygdrive/c/Hitex/GnuToolPackageArm/bin/../lib/gcc/arm-hitex-elf/4.1.1/../../../../include/c++/4.1.1/iostream:76: undefined reference to `std::ios_base::Init::~Init()'

It is a very simple C++ code which is not using any special C++ features.
The code compiles,links and runs fine when <iostream> is "NOT" included in the main.cpp file.

but as soon as <iostream> is included in the main.cpp file, the code compiles, but the above linker error is generated.

Any help is appreciated!!!
Thanks!

---

### Post by Seal Daemon on 2010-05-05
Can you show us the source code of what you are trying to compile ?

---

### Post by snova on 2010-05-05
> **mashaikh said:**
> 
.\Objects\main.o: In function `__static_initialization_and_destruction_0':
/cygdrive/c/Hitex/GnuToolPackageArm/bin/../lib/gcc/arm-hitex-elf/4.1.1/../../../../include/c++/4.1.1/iostream:76: undefined reference to `std::ios_base::Init::Init()'
/cygdrive/c/Hitex/GnuToolPackageArm/bin/../lib/gcc/arm-hitex-elf/4.1.1/../../../../include/c++/4.1.1/iostream:76: undefined reference to `std::ios_base::Init::~Init()'


You aren't linking the C++ standard library, one way or another. Use **g++** to compile, not **gcc**.

Example:

[php]
#include <iostream>
int main() { return 0; }
[/php]

```

$ gcc test.cpp -o /dev/null
/tmp/cc6cu3dg.o: In function `__static_initialization_and_destruction_0(int, int)':
test.cpp:(.text+0x27): undefined reference to `std::ios_base::Init::Init()'
test.cpp:(.text+0x2c): undefined reference to `std::ios_base::Init::~Init()'
/tmp/cc6cu3dg.o:(.eh_frame+0x12): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status
$ g++ test.cpp -o /dev/null
$

```

---

### Post by ibuclaw on 2010-05-05
If you insist on using gcc to compile your C++ application, be sure to link in libstdc++ then.

```
gcc **-lstdc++** helloworld.cc
```

Regards
Iain

PS:
o/ Snova

---

### Post by mashaikh on 2010-05-05
Here is the command line options for g++ and ld 
 
 
arm-hitex-elf-g++ -mcpu=arm7tdmi -c -gdwarf-2 -xc -MD -Wall -O0 -mthumb-interwork -mapcs-frame  -fsigned-char  -mlittle-endian  -marm       
 -I.\Source\  -I.\ -o .\Objects\interrupt.o .\Source\System\interrupt.cpp
 
arm-hitex-elf-as -mcpu=arm7tdmi  -gdwarf2  -mthumb-interwork    
-I.\Source\  -I.\ -o .\Objects\startup.o .\Source\System\startup.s
 
arm-hitex-elf-g++ -mcpu=arm7tdmi  -c -gdwarf-2 -xc++  -Wall -O0 -mthumb-interwork -mapcs-frame  -fsigned-char  -mlittle-endian  -marm   
 -I.\Source\  -I.\ -o .\Objects\main.o .\main.cpp 
 
arm-hitex-elf-ld  -T.\Settings\main.ld.tmp --cref -t -static -nostartfiles -Map=.\DOC\DemoC++.map  -stats -lhcclib -lc -lgcc -lm  
-o .\Objects\DemoC++.elf 

.\Objects\main.o: In function `__static_initialization_and_destruction_0':
/cygdrive/c/Hitex/GnuToolPackageArm/bin/../lib/gcc/arm-hitex-elf/4.1.1/../../../../include/c++/4.1.1/iostream:76: undefined reference to `std::ios_base::Init::Init()'

/cygdrive/c/Hitex/GnuToolPackageArm/bin/../lib/gcc/arm-hitex-elf/4.1.1/../../../../include/c++/4.1.1/iostream:76: undefined reference to `std::ios_base::Init::~Init()'

 
arm-hitex-elf-ld: link errors found, deleting executable `.\Objects\DemoC++.elf'
arm-hitex-elf-ld: mode armelf
.\Objects\interrupt.o (3kb) 
.\Objects\startup.o (6kb)
.\Objects\main.o (35kb)
 
but NO - (DemoC++.elf , DemoC++.SYM  , DemoC++.HTX ) files are generated.

 
 
[COLOR=#ffffff][/COLOR]

---

### Post by kvpnet on 2010-11-25
You can try 2 options.
1. Use g++ itself as the linker instead of ld

arm-hitex-elf-[COLOR="red"]g++[/COLOR] -T.\Settings\main.ld.tmp --cref -t -static -nostartfiles -Map=.\DOC\DemoC++.map -stats -lhcclib -lc -lgcc -lm 
-o .\Objects\DemoC++.elf 

2. As ibuclaw said, insert libstdc++ to the linker command line. 


arm-hitex-elf-ld -T.\Settings\main.ld.tmp --cref -t -static -nostartfiles -Map=.\DOC\DemoC++.map -stats -lhcclib -lc -lgcc -lm -[COLOR="Red"]lstdc++[/COLOR]
-o .\Objects\DemoC++.elf

---

