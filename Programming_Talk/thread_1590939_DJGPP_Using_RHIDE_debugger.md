---
title: "DJGPP: Using RHIDE debugger"
date: 2010-10-08
forum: Programming Talk
---

### Post by xbxb on 2010-10-08
I'm using DJGPP to develop diagnostics for prototype hardware. To debug my code I use the RHIDE debugger. Together DJGPP and RHIDE are a great solution for developing hw diags.

However, RHIDE has an issue which is very annoying: All numbers in Watch windows, Eval/Modify windows, etc, are expressed as decimal numbers. And there seems to be no way to change the radix of these numbers. I want to change the radix to hexadecimal. 

Does anyone know how to get RHIDE to display numbers as hexadecimals? Is there an environment variable or hidden option to do this?

Thanks

---

### Post by gusnan on 2010-10-08
I would seriously recommend updating your toolkit - 
DJGPP is the GNU tools for DOS - not even for windows, and the latest release of RHIDE is from 2003...

If you are looking for a programming toolkit for windows, I would recommend MinGW, which basically what DJGPP is for DOS, but for windows, and for an IDE you could try Code::Blocks.

see:
[www.mingw.org]("http://www.mingw.org")
[www.codeblocks.org]("http://www.codeblocks.org")

Both of those are developed and fully supported today, and there are versions for Linux too. (You can even build your windows programs under Linux using MinGW.)

---

### Post by xbxb on 2010-10-08
Thanks for replying, Gusnan, but I don't think you understand what I'm doing: This type of code is code written specifically for testing and debugging new hardware designs. It must be written quickly in order to debug specific hardware so that hardware can quickly be re-spun. 

The purpose is to exercise unique hardware, not to write applications. I can't run this code from a protected O.S. such as Linux or Windows because I'd have to write drivers to have unlimited access to the hardware. DOS has NO such protections yet still has support for things like files, disks, timers, hooking interrupts, printing messages, etc, so I don't need to re-invent the wheel. 

I use DJGPP because DOS by itself is only 16bit; that means 16bit code and ONLY 16bit addresses, etc. DJGPP provides convenient access to DPMI (DOS Protected Mode Interface) which gives me a quick way to write 32bit code under DOS: I have access to the 32bit address space, and I can call all the DOS functions. And as a nice bonus the code runs MUCH faster, which is important when running several thousand passes to gather statistics.

For embedded, low-cost devices based on inexpensive PC type chipsets (Intel ATOM etc) this is a common approach.

---

