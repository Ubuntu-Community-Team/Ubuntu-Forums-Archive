---
title: "Installing Loadrunner in Ubuntu by Converting Unix Installer"
date: 2019-07-31
forum: New to Ubuntu
---

### Post by rajeshv33 on 2019-07-31
Hello Team,

Does anyone know how to convert an unix installer to Ubuntu. 

I am trying install Loadrunner in my machine but its not working.

Thanks,
Rajesh.

---

### Post by Rubi1200 on 2019-07-31
Did you read the documentation?
[https://admhelp.microfocus.com/lr/en/12.60-12.63/help/PDFs/LoadRunner_Installation_Guide.pdf](https://admhelp.microfocus.com/lr/en/12.60-12.63/help/PDFs/LoadRunner_Installation_Guide.pdf)

Linux instructions start on page 27.

And welcome to the forums :-)

---

### Post by rajeshv33 on 2019-07-31
Thanks for the quick reply. is Linux installer will work in Ubuntu? is linux and ubuntu same? I mean All the software that works with Linux will work for Ubuntu too?

Thanks,
Rajesh
[Loadrunner Tutorials]("https://www.softwarehour.com/loadrunner/")

---

### Post by Rubi1200 on 2019-08-01
Yes, Ubuntu is Linux. The same? Well, yes and no.

Why are you installing this? For school, for work?

Were you not given instructions?

From the documentation link I provided I guess the "easiest" way would be to install using Docker (which would need to be installed first).

Will everything work? I have no idea, never heard of let alone used this software.

Hope this somehow helps.

---

### Post by TheFu on 2019-08-01
For software to work on any specific computer, it has to be compiled for that specific OS and the same CPU.
Ubuntu is a Linux variant.  There are many.  Linux is "Unix-Like", in that it follows the same design, the same APIs, the same security model, and has the same interfaces as "Unix" systems.

If you know Unix, then you know 90% of Linux and if you know Linux, then you know 90% of Ubuntu at the OS level.

Depending on how pedantic you want to be, "Linux" really refers do the kernel used by by Android and all Linux variants, not the entire OS.  In normal conversations, Ubuntu == Linux.

Most of the time, Ubuntu would be considered a a "Linux flavor", just like Fedora or SuSE or Arch or Mint or ... any of the 50 others.

So .... whether any specific program will work under Ubuntu or not will depend on how the specific program is created, which languages are used, what dependencies that program requires and how tightly coupled the program is to the dependencies.  A python program will probably work on any Unix system.  It is loosely tied to the OS libraries.  The same for most other scripted languages.  For compiled programs, things are more tightly coupled, so the program is probably tied to the OS version - a compiled program for 16.04 probably won't work under 14.04 or 18.04. The underlying libraries likely changed enough to break things.
Also, if a program is compiled to run on 16.04 on 64-bit Intel CPUs, it absolutely will NOT work on 16.04 ARM CPUs.  Those are not compatible. Period. But a scripted program should work fine, almost always.

You asked, will any program made for any Linux work on any other Linux?  Maybe, possibly. Perhaps not.  It just depends on the dependencies for the libraries and APIs.

I've never used Loadrunner, but I did buy multiple copies for our QA team a long, long, time ago. I don't remember which platforms, but it definitely was not Linux.

A programmer should understand what I've written.

---

