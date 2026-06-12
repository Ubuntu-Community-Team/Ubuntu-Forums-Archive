---
title: "Puzzle: precompiler can't find lib file"
date: 2007-02-21
forum: Programming Talk
---

### Post by brn on 2007-02-21
I'm rying to compile CONE [http://www.courier-mta.org/cone/](http://www.courier-mta.org/cone/) an interesting new email client.  I am not well-grounded in C programming  but the instructions are clear and I have the facilities. The procedure is:
[LIST=1]
[*]run ./configure
[*]run make
[*]run make install
[*]run make install-configure
[/LIST]
This looked simple enough but *configure* ended with this message:
> checking for wgetch in -lncursesw... no
checking for wgetch in -lcursesw... no
checking for wgetch in -lncurses... no
checking for wgetch in -lcurses... no
configure: error: curses library not found.
configure: error: /bin/sh './configure' failed for curses
I tried to proceed but *make* and the rest all crashed reporting "error 2"

i have /lib/libncursesw.so.5.5 and can think of no other library that *configure* might need.  What am I missing:?

---

### Post by duff on 2007-02-21
try installing **libncurses5-dev** (the development files for curses).

---

### Post by brn on 2007-02-22
> try installing libncurses5-dev (the development files for curses).
Thanks! -- This worked and got me past that problem.  Then I ran into this one:
> configure: error: xml-config not found, download libxml from [http://xmlsoft.org](http://xmlsoft.org)
configure: error: /bin/sh './configure' failed for cone
From the link given I learned that both libxml2 and libxml2-devel were required for compiling so I downloaded both.  These came as rpms so I tried installing libxml2 that way.  Here is what I got:
> brn[download]:sudo rpm -i libxml2-2.6.27-1.i386.rpm
warning: libxml2-2.6.27-1.i386.rpm: Header V3 DSA signature: NOKEY, key ID de95bc1f
error: Failed dependencies:
        /bin/sh is needed by libxml2-2.6.27-1.i386
        libc.so.6 is needed by libxml2-2.6.27-1.i386
        libc.so.6(GLIBC_2.0) is needed by libxml2-2.6.27-1.i386
        libc.so.6(GLIBC_2.1) is needed by libxml2-2.6.27-1.i386
        libc.so.6(GLIBC_2.1.3) is needed by libxml2-2.6.27-1.i386
        libc.so.6(GLIBC_2.2) is needed by libxml2-2.6.27-1.i386
        libc.so.6(GLIBC_2.3) is needed by libxml2-2.6.27-1.i386
        libc.so.6(GLIBC_2.3.2) is needed by libxml2-2.6.27-1.i386
        libc.so.6(GLIBC_2.3.4) is needed by libxml2-2.6.27-1.i386
        libc.so.6(GLIBC_2.4) is needed by libxml2-2.6.27-1.i386
        libdl.so.2 is needed by libxml2-2.6.27-1.i386
        libdl.so.2(GLIBC_2.0) is needed by libxml2-2.6.27-1.i386
        libdl.so.2(GLIBC_2.1) is needed by libxml2-2.6.27-1.i386
        libm.so.6 is needed by libxml2-2.6.27-1.i386
        libm.so.6(GLIBC_2.0) is needed by libxml2-2.6.27-1.i386
        libz.so.1 is needed by libxml2-2.6.27-1.i386
        rtld(GNU_HASH) is needed by libxml2-2.6.27-1.i386
I haven't tried libxml2-devel yet but can't help feeling that I might be entering a vortex of interdependent interdependancies.  Where does it end and what can I do?

Thanks again.

---

### Post by duff on 2007-02-22
eerrr...you shouldn't be using rpms. Open Synaptic (System > Administrative > Synaptic Package Manager)  and use that.

---

### Post by public_void on 2007-02-22
Indeed, always look in the repositories first before finding and installing something from the web.

---

### Post by brn on 2007-02-22
OK.  I tried this.  Still getting the failure for libxml-config which I do not have even after refreshing all with synaptic.  RPM isn't going to get me anywhere so i guess I will have to gracefully accept defeat.  :-({|= 

Thanks again.

---

### Post by hod139 on 2007-02-22
What about the package libxml++2.6-dev

---

### Post by brn on 2007-02-22
> hod139  What about the package libxml++2.6-devhod139  What about the package libxml++2.6-dev
Definitely worth a try.  Here is what I got;
> brn[download]:sudo apt-get install libxml++2.6-dev
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

I might be getting in over my head.   :confused:

---

### Post by po0f on 2007-02-22
brn,

Is Synaptic open?  That's usually what gets me.

---

### Post by brn on 2007-02-22
>  Is Synaptic open? That's usually what gets me.

As far as I know, yes.  (Open?)  I have prowled every file in every catagory that Synaptic lists.  All the libraries there are installed.  I think I  will go back to writing Forth apps for nano-processors and leave C for the big kids.  :)

---

