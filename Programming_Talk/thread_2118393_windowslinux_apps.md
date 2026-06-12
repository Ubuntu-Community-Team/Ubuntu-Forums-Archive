---
title: "windows/linux apps"
date: 2013-02-21
forum: Programming Talk
---

### Post by thedardanius on 2013-02-21
I questioned,
why cant actually apps compiled by compilers targetting windows NT not run on linux (assuming it is all done on the same computer, so same architecture). The assembly/amchine code shouldnt differ too much. I do know that file headers are important for recognition and in linux allowing an app to be an executable, but can anyone explain it more profoundly? What executable does linux use? Why cant it run on windows? Is it becuase linux allocates memory for apps differently, access memory differently and uses different hardware parts?!?
I header linux systems generally use the ELF format. Windows uses the EXE files. Differences?!?

---

### Post by Virtuality314 on 2013-02-21
Ok, here we go...

One of the reasons why Windows apps can't run on Linux is because of the libraries. For example, Rainmeter uses Windows GDI, which cannot run on Linux because...errr...it's **Windows** GDI, which means it has not been compiled for Linux and it cannot communicate with the X-Server, which is used to display the GUI (AFAIK).

Also, I think Linux executables are simply...executable files, as shown in the attachment, while Windows executables are .exe which means it can only run on Windows. I think this is because of the actual structure of the OS - Windows has a different Kernel and a different set of system calls and APIs than Linux does. 

Applications *can* run on both Windows and Linux, i.e. if they have been programmed in a cross-platform language (C, C++, Java, HTML5 etc.) and a cross-platform API/Library (QT, Gtk etc.). However, they still have to be compiled on both operating systems individually.

I hope that helped and I hope I didn't get too much wrong :s

---

### Post by ofnuts on 2013-02-21
> **thedardanius said:**
> I questioned,
why cant actually apps compiled by compilers targetting windows NT not run on linux (assuming it is all done on the same computer, so same architecture). The assembly/amchine code shouldnt differ too much. I do know that file headers are important for recognition and in linux allowing an app to be an executable, but can anyone explain it more profoundly? What executable does linux use? Why cant it run on windows? Is it becuase linux allocates memory for apps differently, access memory differently and uses different hardware parts?!?
I header linux systems generally use the ELF format. Windows uses the EXE files. Differences?!?

Yes the assembly/machine code is the same.

The differences are:
- Available APIs:  displaying a window on Linux or Windows isn't done the same way. You can write your code using libraries like Qt that will handle the differences for you, but the QT for Windows and Qt for Linux will be different.
- There are also some differences at the system level (filesystems, EOL conventions, CLI parameters conventions...)
- And assuming you could use the same C code on both OSes, the format of executable files is different (Windows has its own format, and Linux uses the much more universal ELF format)

Now, if any executable could be run transparently on Linux or Windows, there would not be Linux and Windows... Windows would just be another Linux with a different window manager/desktop...

---

### Post by thedardanius on 2013-02-21
Thank you!

---

### Post by dwhitney67 on 2013-02-21
This info may also be found to be interesting:  [http://en.wikipedia.org/wiki/Linspire](http://en.wikipedia.org/wiki/Linspire)

---

