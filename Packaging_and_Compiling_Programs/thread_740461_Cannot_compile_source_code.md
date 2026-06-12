---
title: "Cannot compile source code"
date: 2008-03-30
forum: Packaging and Compiling Programs
---

### Post by arialth on 2008-03-30
System: 
Ubuntu Linux 2.6.20-16-generic (x86 build)
HP dv9420us
Amd 2.2 ghz dualcore
2gb ram
nvidia geforce go 6150 (64mb) 
<more if it is needed>

My problem here is that I am absolutely unable to compile from source any program i want to. Running ./configure executes just fine (or i install the missing libraries and then it works), but when i try to run make i get a whole slew of errors (listed below). I have installed the latest version of gcc, g++, linux-headers, build-essential, libtool...

Errors when attempting to compile ndiswrapper:
```
arialth@valtrion:~/Install files/ndiswrapper/ndiswrapper-1.52.tar.gz_FILES/ndiswrapper-1.52$ make 
make -C driver
make[1]: Entering directory `/home/arialth/Install files/ndiswrapper/ndiswrapper-1.52.tar.gz_FILES/ndiswrapper-1.52/driver'
make -C /usr/src/linux-headers-2.6.20-16-generic SUBDIRS=/home/arialth/Install files/ndiswrapper/ndiswrapper-1.52.tar.gz_FILES/ndiswrapper-1.52/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
make[2]: *** No rule to make target `files/ndiswrapper/ndiswrapper-1.52.tar.gz_FILES/ndiswrapper-1.52/driver'.  Stop.
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/arialth/Install files/ndiswrapper/ndiswrapper-1.52.tar.gz_FILES/ndiswrapper-1.52/driver'
make: *** [all] Error 2

```

Errors when compiling Pidgin: (note this is the END of the process where i saw errors but i can post the rest of the process too)
```
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.2/../../..//libgobject-2.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.2/../../..//libgmodule-2.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.2/../../..//libgthread-2.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.2/../../..//libglib-2.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.2/../../..//libxml2.la' seems to be moved
/bin/sed: can't read files/Pidgin/pidgin-2.4.0.tar.bz2_FILES/pidgin-2.4.0/libpurple/protocols/jabber/libjabber.la: No such file or directory
libtool: link: `files/Pidgin/pidgin-2.4.0.tar.bz2_FILES/pidgin-2.4.0/libpurple/protocols/jabber/libjabber.la' is not a valid libtool archive
make[5]: *** [libxmpp.la] Error 1
make[5]: Leaving directory `/home/arialth/Install files/Pidgin/pidgin-2.4.0.tar.bz2_FILES/pidgin-2.4.0/libpurple/protocols/jabber'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/arialth/Install files/Pidgin/pidgin-2.4.0.tar.bz2_FILES/pidgin-2.4.0/libpurple/protocols'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/arialth/Install files/Pidgin/pidgin-2.4.0.tar.bz2_FILES/pidgin-2.4.0/libpurple'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/arialth/Install files/Pidgin/pidgin-2.4.0.tar.bz2_FILES/pidgin-2.4.0/libpurple'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/arialth/Install files/Pidgin/pidgin-2.4.0.tar.bz2_FILES/pidgin-2.4.0'
make: *** [all] Error 2
arialth@valtrion:~/Install files/Pidgin/pidgin-2.4.0.tar.bz2_FILES/pidgin-2.4.0$ 

```

Errors seen when attempting to compile Xine with mp3 support for Amarok (same case as above):
```
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.2/../../..//libgobject-2.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.2/../../..//libgmodule-2.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.2/../../..//libgthread-2.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.2/../../..//libglib-2.0.la' seems to be moved
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.2/../../..//libxml2.la' seems to be moved
/bin/sed: can't read files/Pidgin/pidgin-2.4.0.tar.bz2_FILES/pidgin-2.4.0/libpurple/protocols/jabber/libjabber.la: No such file or directory
libtool: link: `files/Pidgin/pidgin-2.4.0.tar.bz2_FILES/pidgin-2.4.0/libpurple/protocols/jabber/libjabber.la' is not a valid libtool archive
make[5]: *** [libxmpp.la] Error 1
make[5]: Leaving directory `/home/arialth/Install files/Pidgin/pidgin-2.4.0.tar.bz2_FILES/pidgin-2.4.0/libpurple/protocols/jabber'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/arialth/Install files/Pidgin/pidgin-2.4.0.tar.bz2_FILES/pidgin-2.4.0/libpurple/protocols'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/arialth/Install files/Pidgin/pidgin-2.4.0.tar.bz2_FILES/pidgin-2.4.0/libpurple'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/arialth/Install files/Pidgin/pidgin-2.4.0.tar.bz2_FILES/pidgin-2.4.0/libpurple'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/arialth/Install files/Pidgin/pidgin-2.4.0.tar.bz2_FILES/pidgin-2.4.0'
make: *** [all] Error 2
arialth@valtrion:~/Install files/Pidgin/pidgin-2.4.0.tar.bz2_FILES/pidgin-2.4.0$ 

```

Now i noticed that both the pidgin and xine failures have to do with something called /bin/sed, but i looked it up on google and i have absolutely no clue what to do. I hope someone here can tell me how to fix the /bin/sed error, and also whatever is wrong with the ndiswrapper configuration... I am used to compiling from source, not an expert, but i know how to do it, and i have compiled both ndiswrapper and xine with success on previous installations of linux, so i cannot understand why they would decide to fail this time. Any suggestions are welcomed! Please help me!

---

### Post by mc4man on 2008-03-31
for the heck of just downloaded and built pidgin - extracted to desktop, did a straight ./configure and make - no problem
What seems odd is how you extracted to (similar in all your attempts)
> /Install files/Pidgin/pidgin-2.4.0.tar.bz2_FILES/pidgin-2.4.0$
look at your error lines
```
/bin/sed: can't read files/Pidgin/pidgin-2.4.0.tar.bz2_FILES/pidgin-2.4.0/
*** No rule to make target `files/ndiswrapper/ndiswrapper-1.52.tar.gz_FILES/ndiswrapper-1.52/driver'.
```
no Install  
here's the point you error at on successful make
```
libtool: link: warning: `/usr/lib/gcc/i486-linux-gnu/4.1.3/../../..//libxml2.la' seems to be moved
make[5]: Leaving directory `/home/doug/Desktop/pidgin-2.4.0/libpurple/protocols/jabber'
Making all in msnp9
make[5]: Entering directory `/home/doug/Desktop/pidgin-2.4.0/libpurple/protocols/msnp9'

```
 You should try extracting to a directory name without spaces  in it
ie. get rid of all that stuff in front of pidgin-2.4.0  - so either build directly from extracted folder or use something simple like scr or pidgin  to extract to

---

### Post by arialth on 2008-04-01
Hehe yeah i figured that out after a few hours thinking about it. What i finally did was create a directory /src/ and worked out of that; everything compiled just FINE there. God i feel like such a noob now ^^

I do appreciate that someone actually replied to this, though. Thank you!!

---

