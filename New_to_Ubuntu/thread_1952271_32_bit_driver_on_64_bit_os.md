---
title: "32 bit driver on 64 bit os"
date: 2012-04-04
forum: New to Ubuntu
---

### Post by Damuson on 2012-04-04
I have Ubuntu 10.04 64bit os installed on my laptop and am trying to get it to print on the Brother MFC-J435w AiO printer I just bought. I've already installed the 32 bit libs, but every time I try to install the cupswrapper and printer driver, it gives tells me "error: wrong architecture 'i386'". Anyone know why this is still happening or what I may have missed? I appreciate any input.

---

### Post by idoitprone on 2012-04-04
> **Damuson said:**
> I have Ubuntu 10.04 64bit os installed on my laptop and am trying to get it to print on the Brother MFC-J435w AiO printer I just bought. I've already installed the 32 bit libs, but every time I try to install the cupswrapper and printer driver, it gives tells me "error: wrong architecture 'i386'". Anyone know why this is still happening or what I may have missed? I appreciate any input.

it is not really helpful if brother didnt include all the dependencies in th package
```

**$dpkg -i --force-architecture mfcj435wcupswrapper-1.1.2-1.i386.deb **
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
Selecting previously unselected package mfcj435wcupswrapper.
(Reading database ... 271356 files and directories currently installed.)
Unpacking mfcj435wcupswrapper (from mfcj435wcupswrapper-1.1.2-1.i386.deb) ...
dpkg: dependency problems prevent configuration of mfcj435wcupswrapper:
 mfcj435wcupswrapper depends on mfcj435wlpr.
dpkg: error processing mfcj435wcupswrapper (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mfcj435wcupswrapper

``````
**dpkg --info mfcj435wcupswrapper-1.1.2-1.i386.deb**
 new debian package, version 2.0.
 size 13524 bytes: control archive= 475 bytes.
       0 bytes,     0 lines      conffiles            
     302 bytes,     9 lines      control              
     161 bytes,     4 lines   *  postinst             #!/bin/sh
     109 bytes,     3 lines   *  prerm                #!/bin/sh
 Package: mfcj435wcupswrapper
 Version: 1.1.2-1
 Maintainer: Brother Industries, Ltd.
 Architecture: i386
 Description: Brother CUPS Inkjet Printer Definitions
  Copyright: 2004 Brother Industries, Ltd. All Rights Reserved
  Brother Inkjet printer CUPS Driver
 Depends: **mfcj435wlpr**
 Conflicts: CONFLICT_PACKAGE
```

---

### Post by Damuson on 2012-04-04
So I tried to use the code suggested, but didn't get the same response in the terminal.    damuson@ubuntu:~$ $dpkg -i --force-architecture mfcj435wcupswrapper-1.1.2-1.i386.deb   -i: command not found  damuson@ubuntu:~$ dpkg -i --force-architecture mfcj435wcupswrapper-1.1.2-1.i386.deb   dpkg: requested operation requires superuser privilege  damuson@ubuntu:~$ sudo dpkg -i --force-architecture mfcj435wcupswrapper-1.1.2-1.i386.deb   [sudo] password for damuson:   dpkg: error processing mfcj435wcupswrapper-1.1.2-1.i386.deb (--install):  cannot access archive: No such file or directory  Errors were encountered while processing:   mfcj435wcupswrapper-1.1.2-1.i386.deb  damuson@ubuntu:~$ sudo $damuson@ubuntu:~$ $dpkg -i --force-architecture mfcj435wcupswrapper-1.1.2-1.i386.deb   sudo: @ubuntu:~$: command not found  damuson@ubuntu:~$ -i: command not found  -i:: command not found  damuson@ubuntu:~$ damuson@ubuntu:~$ dpkg -i --force-architecture mfcj435wcupswrapper-1.1.2-1.i386.deb   damuson@ubuntu:~$: command not found  damuson@ubuntu:~$ dpkg: requested operation requires superuser privilege No command 'dpkg:' found, did you mean:   Command 'dpkg' from package 'dpkg' (main) dpkg:: command not found  damuson@ubuntu:~$ damuson@ubuntu:~$ sudo dpkg -i --force-architecture mfcj435wcupswrapper-1.1.2-1.i386.deb   damuson@ubuntu:~$: command not found  damuson@ubuntu:~$ [sudo] password for damuson:   [sudo]: command not found  damuson@ubuntu:~$ dpkg: error processing mfcj435wcupswrapper-1.1.2-1.i386.deb (--install):  bash: syntax error near unexpected token `('  damuson@ubuntu:~$  cannot access archive: No such file or directory cannot: command not found  damuson@ubuntu:~$ Errors were encountered while processing: Errors: command not found  damuson@ubuntu:~$  mfcj435wcupswrapper-1.1.2-1.i386.deb mfcj435wcupswrapper-1.1.2-1.i386.deb: command not found  damuson@ubuntu:~$ damuson@ubuntu:~$   damuson@ubuntu:~$: command not found

---

### Post by Damuson on 2012-04-04
Also, I don't seem to know how to get the text from the terminal to translate into the forum without losing the separation in lines.

---

### Post by idoitprone on 2012-04-04
well it is simple. use your mouse and copy paste and put in ```
 tags

to install a package of another architecture. The package have to be in the same directory

[CODE]sudo dpkg -i --force-architecture pkgName.deb
```this is ubuntu, we always need sudo

oh i get the dependency problem, we have to install both lpr and cupswrapper

---

### Post by Damuson on 2012-04-05
Sorry, it seems that you have to talk to me like a five year old. I've put in tags before in other forums, but it doesn't seem to be the same format or something on here. I put in "[CODE]" before and after the thread of code I want to post, right? Because I tried that with no success. Is it case sensitive? Sorry I'm such a noob.

---

### Post by jwbrase on 2012-04-05
> **Damuson said:**
> Sorry, it seems that you have to talk to me like a five year old. I've put in tags before in other forums, but it doesn't seem to be the same format or something on here. I put in "```
" before and after the thread of code I want to post, right? Because I tried that with no success. Is it case sensitive? Sorry I'm such a noob.

You need [noparse][CODE] before and 
``` after.[/noparse] I do not believe it is case sensitive.

---

### Post by Damuson on 2012-04-05
Ok, so here's what I did, and this is what I got:  ```
 damuson@ubuntu:~$ sudo dpkg -i --force-architecture mfcj435wcupswrapper-1.1.2-1.i386.deb  [sudo] password for damuson:  dpkg: error processing mfcj435wcupswrapper-1.1.2-1.i386.deb (--install):  cannot access archive: No such file or directory Errors were encountered while processing:  mfcj435wcupswrapper-1.1.2-1.i386.deb damuson@ubuntu:~$ dpkg --info mfcj435wcupswrapper-1.1.2-1.i386.deb dpkg-deb: failed to read archive `mfcj435wcupswrapper-1.1.2-1.i386.deb': No such file or directory damuson@ubuntu:~$ sudo dpkg install --force-architecture mfcj435wcupswrapper-1.1.2-1.i386.deb dpkg: need an action option  Type dpkg --help for help about installing and deinstalling packages 
[*]; Use `dselect' or `aptitude' for user-friendly package management; Type dpkg -Dhelp for a list of dpkg debug flag values; Type dpkg --force-help for a list of forcing options; Type dpkg-deb --help for help about manipulating *.deb files; Type dpkg --license for copyright license and lack of warranty (GNU GPL) 
[*].  Options marked 
[*] produce a lot of output - pipe it through `less' or `more' ! damuson@ubuntu:~$  
```

---

### Post by Damuson on 2012-04-05
Hmm.. that still didn't seem quite right for the code tags.

---

### Post by idoitprone on 2012-04-06
> **Damuson said:**
> Ok, so here's what I did, and this is what I got:  ```
 damuson@ubuntu:~$ sudo dpkg -i --force-architecture mfcj435wcupswrapper-1.1.2-1.i386.deb  [sudo] password for damuson:  dpkg: error processing mfcj435wcupswrapper-1.1.2-1.i386.deb (--install):  cannot access archive: No such file or directory Errors were encountered while processing:  mfcj435wcupswrapper-1.1.2-1.i386.deb damuson@ubuntu:~$ dpkg --info mfcj435wcupswrapper-1.1.2-1.i386.deb dpkg-deb: failed to read archive `mfcj435wcupswrapper-1.1.2-1.i386.deb': No such file or directory damuson@ubuntu:~$ sudo dpkg install --force-architecture mfcj435wcupswrapper-1.1.2-1.i386.deb dpkg: need an action option  Type dpkg --help for help about installing and deinstalling packages 
[*]; Use `dselect' or `aptitude' for user-friendly package management; Type dpkg -Dhelp for a list of dpkg debug flag values; Type dpkg --force-help for a list of forcing options; Type dpkg-deb --help for help about manipulating *.deb files; Type dpkg --license for copyright license and lack of warranty (GNU GPL) 
[*].  Options marked 
[*] produce a lot of output - pipe it through `less' or `more' ! damuson@ubuntu:~$  
```

whatever, it doent even matter. It is just formatting.
dpkg is complaining that you do not have the package in the same directory as in the path of the shell. Just download the package and it is most likely be located in your Downloads folders
```
cd Downloads
```then install the package

```
sudo dpkg -i --force-architecture pkgName.deb
```

---

