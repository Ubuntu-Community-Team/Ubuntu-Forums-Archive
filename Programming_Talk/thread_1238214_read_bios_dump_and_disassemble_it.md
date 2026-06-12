---
title: "read bios dump and disassemble it"
date: 2009-08-12
forum: Programming Talk
---

### Post by kulkarniniraj on 2009-08-12
Hi
   I actually want to reverse engineer my ROM BIOS.for that i need to collect memory dump at f000:0000 to f000:ffff and then store it in a file and disassemble it.
  So can anyone help me. I tried readinng memory by cat /dev/mem but it gives me whole dump.I need only specific parts.can i try dd? please send me details  of this command.

  My friend told me that i could disassemble using objdump, but i couldn't figure out how to use it for not-object binaries.Please help me here also.
Thanks in advance

---

### Post by NathanB on 2009-08-12
If you are just wanting to examine the embedded strings and other data, then use a FreeDOS boot floppy [ [http://www.fdos.org/bootdisks/](http://www.fdos.org/bootdisks/) ] and, from here [ [http://home.comcast.net/~fbkotler/](http://home.comcast.net/~fbkotler/) ], grab the Seemem (source included) program to view that area of memory.  Seemem can be modified to dump to a binary file that can be disassembled, but that is where I stop participating in this discussion [see this forum's TOS].

F/OSS BIOS code is widely available:

[http://aebios.com/](http://aebios.com/)

[http://www.pcengines.ch/tinybios.htm](http://www.pcengines.ch/tinybios.htm)

[http://www.openfirmware.info/Welcome_to_OpenBIOS](http://www.openfirmware.info/Welcome_to_OpenBIOS)

Hope that helps.

---

### Post by kulkarniniraj on 2009-08-12
Thanx for those links Nathan.
    anyway my first problem is solved. Now I can dump memory into a file using dd. Please help me out in disassembling it using OBJDUMP or maybe any other tool

---

