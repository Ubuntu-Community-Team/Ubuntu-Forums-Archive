---
title: "Executable mistaken for Shared Lib"
date: 2018-03-10
forum: Programming Talk
---

### Post by altaica94 on 2018-03-10
Hello
First, I will say I am quite new to using GNU make and g++ on Ubuntu, and programming in general.  I am trying to learn how to use SDL2 and OpenImageIO together and I have decided to just use makefiles directly (I have had so many headaches with IDE's) I just tried to compile a simple program to display a JPEG on an SDL surface.  I have attached the .cpp file and makefile used (I had to change the extensions to .txt because the uploader would let me send them in their original form).  I compiled the program, but when I tried to use it I got the message: "There is no application installed for 'shared library' files. Do you want to search for an application to open this file?"  I checked the file permissions to see if the "Allow executing file as program" was enabled and it still is.  So my question is how to work around whatever glitch is causing my executable to be mistaken for a shared library.  Any assistance would be greatly appreciated.

Sincerely,
Altaica94.

PS
I love this operating system.

---

### Post by norobro on 2018-03-10
Add -no-pie to your linker flags. [https://stackoverflow.com/questions/45329372/ubuntu-recognizes-executable-as-shared-library-and-wont-run-it-by-clicking?answertab=active#tab-top](https://stackoverflow.com/questions/45329372/ubuntu-recognizes-executable-as-shared-library-and-wont-run-it-by-clicking?answertab=active#tab-top)
Some background: [https://lists.debian.org/debian-gcc/2016/11/msg00005.html](https://lists.debian.org/debian-gcc/2016/11/msg00005.html)

---

### Post by altaica94 on 2018-03-10
Thanks, it compiled.

---

