---
title: "How to make a cross-platform program to read the serial port?"
date: 2008-08-21
forum: Programming Talk
---

### Post by roccivic on 2008-08-21
Hi everyone,
  I'm an electronics engineer, but I'm not new to software programming, I have previous experiences with bash scripts, assembly, HTML and javascript. And I have recently started learning C and I quite like this language. 
  I'd like to make a program that will read the serial port (RS-232) and that can be compiled for both linux and windoze (maybe even mac?).
  My questions would be:
  Is C a suitable language for making a program to read from the serial port,*say, 32 bits and then displaying them in a shell or DOS prompt every time these 32 bits are transmitted from the external device. And eventually I would like to implement a GUI, too. 

  Many thanks, Rouslan

---

### Post by Game_Ender on 2008-08-21
No C is not really suitable language to do that in.  I would use [PySerial]("http://pyserial.wiki.sourceforge.net/pySerial") for cross platform serial port usage and [wxPython]("http://www.wxpython.org/") for the GUI.  I have used both in the past and they are good solid libraries.

---

### Post by LaRoza on 2008-08-21
> **roccivic said:**
> 
  Is C a suitable language for making a program to read from the serial port,*say, 32 bits and then displaying them in a shell or DOS prompt every time these 32 bits are transmitted from the external device. And eventually I would like to implement a GUI, too. 


Probably not, unless C has cross platform libraries for this (I know of none).

For this, you should use a language that is cross platform and runs on some sort of VM, like Java or Python. I see someone mentioned the libraries you could use, so Python would be an easy choice.

(Python is an easy language, so you should pick it up quickly)

---

### Post by dribeas on 2008-08-21
> **roccivic said:**
> Hi everyone,
  I'm an electronics engineer, but I'm not new to software programming, I have previous experiences with bash scripts, assembly, HTML and javascript. And I have recently started learning C and I quite like this language. 
  I'd like to make a program that will read the serial port (RS-232) and that can be compiled for both linux and windoze (maybe even mac?).
  My questions would be:
  Is C a suitable language for making a program to read from the serial port,*say, 32 bits and then displaying them in a shell or DOS prompt every time these 32 bits are transmitted from the external device. And eventually I would like to implement a GUI, too. 

  Many thanks, Rouslan

I don't know of any library that is cross platform to program serial ports. I have done it manually in windows (a couple of years ago, don't really remember details now) and in linux recently, well, a coworker did it but the code is quite simple.

I think you can use any language you like, if you have no preference, then consider which helps you most with the GUI (what GUI you want to use), as the serial port and/or console printing should be quite simple in all languages.

   David

**EDIT:** As pointed above Python seems to have the cross platform libraries for serial access. Go for it.

---

### Post by roccivic on 2008-08-21
Thanks everyone for the replies.

One thing I'm wondering is if I can make executables from python scripts? As all Python programs I've seen were scripts to be run inside a python shell.

Many thanks,
Rouslan

---

### Post by tinny on 2008-08-21
For Java look at javacomm, ive used it and it worked really well.

[http://java.sun.com/products/javacomm/](http://java.sun.com/products/javacomm/)

---

### Post by LaRoza on 2008-08-21
> **roccivic said:**
> Thanks everyone for the replies.

One thing I'm wondering is if I can make executables from python scripts? As all Python programs I've seen were scripts to be run inside a python shell.

Many thanks,
Rouslan

Yes, you can. If you can't install Python (comes with OS X, most Linux distros, and HP and Compaq computers, and is an easy install, see my wiki for Windows), you can use a script to make standalone executables. But, if you are going to be using a cross platform language like this, you'll have to do the same no matter what language you use (Java requires JRE, etc).

---

### Post by tinny on 2008-08-21
Does the standard Python runtime come with serial coms?

In Java you have to bundle your application with a specific native lib for the platform you are running on (its all done via JNI). So you will need a different distribution of your application for each OS, not hard but it is extra work.

---

### Post by LaRoza on 2008-08-21
> **tinny said:**
> Does the standard Python runtime come with serial coms?


No. see the modules linked to above. It looks simple enough.

If you used it, you'd write standard Python + the modules and it would work everywhere. To distribute, you could set up individual installers for each platform, but you'd just have to install Python and PySerial (which is simple, see link).

---

### Post by mujambee on 2008-08-21
Under Unix, a serial port is a virtual file, names start at /dev/ttys0 and count up. Under Windows is the same, but names start at COM1, so to open a serial port you should use to fopen( "/dev/tty0", "r" ) under ux and fopen( "COM1", "r" ) under win.  Unfortunately fopen cant open COM ports in recent versions of Windows.

Not sure how it works with streams, so you may be able to use C++ streams, you just need to conditionaly compile device names; something like:


#include <iostream>
#include <fstream>

#ifdef WINDOWS
const char pnames[][12]={ "COM1", "COM2", "COM3", "COM4" };
#else
const char pnames[][12]={ "/dev/ttys0", "/dev/ttys1", "/dev/ttys2", "/dev/ttys3" };
#endif
...
...
...

std::ifstream ifs( pnames[port_number] );


Anyway, if you are just learning C, it could be a good exercise to create wrapper functions and conditionaly include calls to fopen, fread, fclose in your unix version and OpenFile, ReadFile and CloseHandle in your Windows version.

---

