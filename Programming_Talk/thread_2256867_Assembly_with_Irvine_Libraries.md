---
title: "Assembly with Irvine Libraries"
date: 2014-12-15
forum: Programming Talk
---

### Post by Paul_Jewell on 2014-12-15
Hello, 

I have searched for this generally and spent many hours so far with it, without full success so far. I am going to be taking a course in Assembly at college in the spring, and I have so far managed to get away with using ubuntu for all classwork without issue. The problem here is that, not only would it be better if I could use the same syntax as everyone else in the class, but the professor must read programs I make and I dont think he would like to read something with a different syntax than everyone else. We are using the book by Mr. Irvine (seems pretty well written so far). I downloaded this group of supporting libraries: 

[http://kipirvine.com/asm/examples/Irvine_6th_Edition_VS2012.msi](http://kipirvine.com/asm/examples/Irvine_6th_Edition_VS2012.msi)

I have used wine to extract the MSI and I have tried a few methods of assembling and compiling the first example (examples/ch03/AddSub.asm) Note that I have not used assembly before so I could be doing something completely stupid. I am able to create a 'addSub.o' file by using the jwasm freeware binary, but I can not seem to run the linker successfully. Here is what I run, based on some research:

jwlink file AddSub.o format elf l Irvine32.lib 

I have tried putting the various library files 'Kernel32.lib, User32.lib' in addition to the 'Irvine32.lib' but this only generated more errors. Here is what I am getting (with just the irvine lib):

```
JWlink Version 1.9beta 13Portions Copyright (c) 1985-2002 Sybase, Inc. All Rights Reserved.
Source code is available under the Sybase Open Watcom Public License.
loading object files
Error! E2028: _ExitProcess@4 is an undefined reference
Error! E2028: _DumpRegs@0 is an undefined reference
creating an ELF executable
file AddSub.o(AddSub.asm): undefined symbol _DumpRegs@0
file AddSub.o(AddSub.asm): undefined symbol _ExitProcess@4
```

I have also tried MASM in dosdox, which has the same issue, so I guess I am just linking it wrong. Note that I have not modified the files linked above, I an just trying to get the example to work. 

Thanks for reading!

---

