---
title: "ARM7  IDE &amp; ToolChain"
date: 2007-11-04
forum: Programming Talk
---

### Post by bubbalouie on 2007-11-04
Hi all,

Ahead of starting a new project I'd like to investigate my options first. Previously I have always used Analog Devices ADuC702x pocessors and the Rowley Cross Works IDE under wine. I can continue down this path, however, to be honest I'd prefer a native solution if possible.

I intend to start using the Phillips LPC2119 processor, what I'd like to know is whether anyone has experience and might be able to give a few pointers regarding:
 [LIST]
[*] GCC ARM compiler and library packages for ubuntu
[*] A nice IDE to handle the above compiler (manual compiling is fine, however, quickly tweaking options with a GUI is a really nice luxury)
[*] A Firmware Loader for the LPC2000 family (I have found a tool LPC21ISP by Martin Maurer, but have no way yet to verify if it works well)
[/LIST]

I don't care too much for advanced debuggers etc, I find a scope and serial port can usually give me most of what I need to figure out how I have broken something.

Any advice or pointers people can give me would be great, as much as I like the Rowley tools it seems it would make more sense to just use a native solution.

Thanks in advance

Ryan

*EDIT: It looks as though a linux version of CrossWorks exists (huzzah :) ), though I am still inetersted if anyone can suggest something more suitable

---

### Post by abovyan on 2007-11-18
Hi bubbalouie.
As i see, number of answers to You are not so far:))

I`m working on this problem too, I am newbee to Linux at all:) (I was:))
On windows i used Eclipse CDT, and GNUARM toolchainl. It works perfect. Even debuggind thru GDB was working. So i think to do something like it in Linux now.

So answers to Your questions are:
1. [www.gnuarm.org](www.gnuarm.org)
2. [www.eclipse.org](www.eclipse.org) (Eclipse CDT)
3. lpc2000isp (or something like this, it it gnuu tool to program lpc devices)

Best regards

---

### Post by bubbalouie on 2007-11-19
Cheers, I use eclipse for python & perl at work, so keeping everything under the one roof would be nice... I've noticed there is a gnu-arm plugin for eclipse, I will have a play as soon as my development boards arrive.... If I have any success I will post a howto when time permits...

Cheers :)

Edit: Eclipse tool is not so great, it seems to want a rather old tool chain. However the console will cut the mustard and a simple build script isn't that hard to build, the following tool is great fo loading the LPC's with:

[http://www.pjrc.com/arm/lpc2k_pgm/](http://www.pjrc.com/arm/lpc2k_pgm/)

XTerm is needed (sudo apt-get install xterm), I useds the pre built binary and it works well.

---

### Post by adityabankar on 2010-01-30
I use GNU Emacs for this purpose. It highlights syntax of the source code and the linker script too. I have written a Makefile which invokes lpc21isp. Make utility can be invoked from emacs thus compilation and programming the chip happen without quitting emacs. I have made a video and posted it on youtube ([http://www.youtube.com/watch?v=DPfRpCIFaoA](http://www.youtube.com/watch?v=DPfRpCIFaoA))

I saw that even with eclipse Makefile is required and even a linker script. To avoid the mouse clicks I chose to use emacs.

Thanks,
Aditya

---

### Post by ras123 on 2010-05-30
Can you tell me how to install GNU ARM Eclipse plug-gin

[http://gnuarmeclipse.sourceforge.net/index.html](http://gnuarmeclipse.sourceforge.net/index.html)

Thanking You,
Ras

---

