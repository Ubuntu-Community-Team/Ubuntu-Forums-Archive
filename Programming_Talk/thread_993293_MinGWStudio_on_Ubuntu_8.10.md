---
title: "MinGWStudio on Ubuntu 8.10"
date: 2008-11-25
forum: Programming Talk
---

### Post by kjhdaskjlhsdkjgh on 2008-11-25
Hi, not sure if this is the right place to ask about this. Apologies if it isn't. Have also posted to MinGW user list.

I am trying to follow along with a C++ programming book I just took out of the library, but I can't seem to get the supplied MinGWStudio IDE on the CD to work. I've extracted the tar.gz file to my harddrive and it creates a folder MinGWStudio but when I double click on the MinGWStudio file inside the folder nothing happens. Googling 'MinGWStudio' leads to [www.parinyasoft.com/](www.parinyasoft.com/)  but this site is down. So, does anyone know if MinGWStudio actually does work on Ubuntu? Am I missing something really obvious (am a Linux newbie) or does it just not work? 

Thanks in advance for any help.

I realise there are other IDEs btw, but am trying to do it the prescribed way first!...

---

### Post by snova on 2008-11-25
Sounds like a Windows program. Install Wine if you really want to use it. Unless it's a Linux program? Then run it in a terminal and post the output you get, there should be an error message.

Ironically, MinGW is a port of GCC to Windows, which otherwise runs natively on Linux...

My advice is to ditch IDE's entirely. You need nothing more than a text editor and a terminal to invoke GCC from.

---

### Post by kjhdaskjlhsdkjgh on 2008-11-25
Thanks for the reply. You're right. I'd forgotten I'd read that MinGW is a port of GCC to Windows. Seems pretty perverse to port it back, especially with the 'W'! Here's what I did:

**:/usr/local/bin$ ls**

mingw-devstudio_linux-2.06.tar.gz


**tar xvzf mingw-devstudio_linux-2.06.tar.gz** 

MinGWStudio/
MinGWStudio/MinGWStudio.png
MinGWStudio/executer
MinGWStudio/MinGWStudio.xpm
MinGWStudio/Templates/
MinGWStudio/Templates/Linux/
MinGWStudio/Templates/Linux/linuxgtk.tpl
MinGWStudio/Templates/Linux/linuxlib.tpl
MinGWStudio/Templates/Linux/linuxgnome.tpl
MinGWStudio/Templates/Linux/linuxconsole.tpl
MinGWStudio/Templates/Linux/linuxwx.tpl
MinGWStudio/Templates/Linux/linuxdll.tpl
MinGWStudio/Templates/Win32/
MinGWStudio/Templates/Win32/win32console.tpl
MinGWStudio/Templates/Win32/win32gtk.tpl
MinGWStudio/Templates/Win32/win32lib.tpl
MinGWStudio/Templates/Win32/win32gui.tpl
MinGWStudio/Templates/Win32/win32dll.tpl
MinGWStudio/Templates/Win32/win32wx.tpl
MinGWStudio/Calltips/
MinGWStudio/Calltips/win32.ctp
MinGWStudio/Calltips/ansi_c.ctp
MinGWStudio/Readme.txt
MinGWStudio/License.txt
MinGWStudio/MinGWStudio

[B]cd MinGWStudio/
ls -all[/B]

total 4576
drwxr-xr-x 4 usr usr    4096 2005-05-17 06:22 .
drwxr-xr-x 3 usr root       4096 2008-11-25 20:38 ..
drwxr-xr-x 2 usr usr    4096 2005-05-07 02:19 Calltips
-rwxr-xr-x 1 usr usr    4956 2005-04-04 00:44 executer
-rw-r--r-- 1 usr usr    2829 2005-04-03 05:21 License.txt
-rwxr-xr-x 1 usr usr 4629044 2005-07-08 06:10 MinGWStudio
-rw-r--r-- 1 usr usr     324 2005-05-07 02:19 MinGWStudio.png
-rw-r--r-- 1 usr usr    1298 2005-05-07 02:19 MinGWStudio.xpm
-rw-r--r-- 1 usr usr    2872 2005-05-17 06:22 Readme.txt
drwxr-xr-x 4 usr usr    4096 2005-05-14 22:17 Templates

Calltips  License.txt  MinGWStudio.png  Readme.txt
executer  MinGWStudio  MinGWStudio.xpm  Templates

**MinGWStudio**

bash: MInGWStudio: command not found

**executer**

bash: executer: command not found 


Double-clicking MinGWStudio or executer did not work either. As you said, a text editor is all you need and I prefer this way too. Just was trying to be the dutiful student until the book let me down on p1! Are there any clues in this output?

PS. The ReadMe says (excluding Windows portions):

What is MinGW Developer Studio?
-------------------------------
MinGW Developer Studio is a Cross-Platform C/C++ Integrated Development Environment(IDE) 
for GNU GCC compiler system. Currently it supports Windows, Linux and FreeBSD.

System Requirements:

- Linux version

* GTK+ 2.0 or higher.
* GNU gdb 5.21 or higher.(Optional if you don't use its debugging features) (I seem to have gdb 6.8, guessing that's standard)

Installation:

- Linux & FreeBSD version

* Unpack the package mingw-devstudio_OS-yyy.tar.gz in a location that you would like to keep MinGW Studio.

---

### Post by snova on 2008-11-25
It appears to be Linux, then. Try this:

```
./MinGWStudio
```

---

### Post by kjhdaskjlhsdkjgh on 2008-11-25
I tried your suggestion and got:

[I] ./MinGWStudio: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
[/I] 
Nearly posted the above, but decided to google **libstdc++.so.5 ubuntu** first
and these were the top two posts:

[http://ubuntuforums.org/showthread.php?t=72376](http://ubuntuforums.org/showthread.php?t=72376)
[URL="http://ubuntuforums.org/showthread.php?t=77404"]http://ubuntuforums.org/showthread.php?t=77404
[/URL] 
```
 sudo apt-get install libstdc++5
``` seemed like something worth trying. Promising result.

```
 ./MinGWStudio
``` then caused the GUI to pop up. It works! Double-clicking icon now makes the program run. Thanks a lot, snova.

---

