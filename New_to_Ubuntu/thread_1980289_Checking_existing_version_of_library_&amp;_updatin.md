---
title: "Checking existing version of library &amp; updating"
date: 2012-05-15
forum: New to Ubuntu
---

### Post by OccamsChainsaw on 2012-05-15
Hi all,

I'm trying to install FFADO, and I need to update a number of libraries  to do so. From reading around a bit, it looks like pkg_check_modules can  check the existing library versions for me. One of the libraries I need  to update is libiec61883, and in the readme for that, it tells me to  use the following command to check for the installed version's .pc [[COLOR=blue][COLOR=blue !important][FONT=Verdana][COLOR=blue !important][FONT=Verdana]file[/FONT][/FONT][/COLOR][/COLOR][/COLOR]]("http://www.linuxforums.org/forum/#"):
 
PKG_CHECK_MODULES(LIBIEC61883, libiec61883 >= 1.0.0)
 
Except that when I give this command,  I get a syntax error near  'LIBIEC61883'. Can anyone tell me where I've gone wrong? I'm curious to  know how this [[COLOR=blue][COLOR=blue !important][FONT=Verdana][COLOR=blue !important][FONT=Verdana]command[/FONT][/FONT][/COLOR][/COLOR][/COLOR]]("http://www.linuxforums.org/forum/#") will be helpful, since it doesn't specify action_if_found and action_if_not_found as written. 

It also says in the readme that this macro sets the variables LIBIEC61883_CFLAGS and LIBIEC61883_LIBS, and that I have to include this in my build variables so that the build process
correctly links with libraw1394. Can someone explain to me what this means, and how I go about carrying this out during the build?

Thanks in advance. I look forward to pestering all of you with many linux questions in the future.

---

### Post by Lisiano on 2012-05-15
I think it is refering to Python or some other language. To check the version of anything installed on your system, just run this
```
dpkg -l *libsomething*
```
So in your case this is```
dpkg -l libiec61883-0
```

EDIT: FFADO is available in Ubuntu, do you want the tools or the mixer or the dbus server?
[ffado-dbus-server]("apt://ffado-dbus-server")
[ffado-mixer-qt4]("apt://ffado-mixer-qt4")
[ffado-tools]("apt://ffado-tools")
Or just type ```
apt-get install *item*
``` to install using the terminal (Ctrl+Alt+T).

---

### Post by OccamsChainsaw on 2012-05-18
Thanks for your help! I have a small follow up ?. I installed libiec61883, and then tried the dpkg command you suggested. Here's the output:

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-==========================================
ii  libiec61883-0  1.2.0-0.1build an partial implementation of IEC 61883

Can't really decode all of this, but does it mean that I haven't successfully installed libiec after all? Also can you explain the syntax "libiec61883-0" (instead of just "libiec61883")? Thank you again.

---

### Post by Lisiano on 2012-05-18
[LIST]
[*]'ii' means it's installed.
[*]I don't know exactly why, but this is how I understand it[LIST]
[*]-0 means it's a library (Needed to run stuff)
[*]-dev means it's the libraries development files (Needed to compile stuff)
[/LIST] You can also use this to search for stuff```
apt-cache search iec61883
```
[/LIST]

So if you want to compile FFADO, you need to get the -dev libraries in addition to the -0 ones. If you just want to install it, you only need -0 ones.

---

