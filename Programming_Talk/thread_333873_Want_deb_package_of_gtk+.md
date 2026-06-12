---
title: "Want deb package of gtk+"
date: 2007-01-08
forum: Programming Talk
---

### Post by zenwalker on 2007-01-08
Hello friends,

I have been looking around alot of places to find out GTK+ gui tool kit (package) on google as well as on GTK.org. But none where i find a binary package for ubuntu. I cant download source package of GTK from its home page. Coz i have hardware problem which wont let me do compilation of source packages. Hence i am looking for a binary or .deb package of GTK. Already i have libgtk as well as libgtk-dev package installed. Btw i am using 6.10. 

So can any body give me a link to download .deb package of GTK+ please??

Thanks

---

### Post by po0f on 2007-01-08
zenwalker,

GTK+ *is* libgtk.

---

### Post by zenwalker on 2007-01-08
> **po0f said:**
> zenwalker,

GTK+ *is* libgtk.

Then how to launch GTK application and start off programming or building graphical interfaces??

I dont find any option in the menu to launch GTK or atleast when i say gtk in command line i cant launch it...

---

### Post by po0f on 2007-01-08
zenwalker,

[GTK+ tutorial](http://www.gtk.org/tutorial/)

You'll want to use a text editor with syntax highlighting.  GEdit supports C/C++ syntax highlighting by default, I'd suggest you start with this.

Also, make sure you have [build-essential](http://packages.ubuntu.com/edgy/devel/build-essential) installed as well.

---

### Post by zenwalker on 2007-01-08
> **po0f said:**
> zenwalker,

[GTK+ tutorial](http://www.gtk.org/tutorial/)

You'll want to use a text editor with syntax highlighting.  GEdit supports C/C++ syntax highlighting by default, I'd suggest you start with this.

Also, make sure you have [build-essential](http://packages.ubuntu.com/edgy/devel/build-essential) installed as well.

Oh my bad, i thought GTK+ has some thing graphical interface like Eclipse or Netbeans or anjuta. I read the tutrial of GTK and then i tought it supports an IDE. Oh my bad, i didnt know that. 

Any ways i installed Anjuta and i hope i can work on it...

Thanks poof

---

### Post by po0f on 2007-01-08
zenwalker,

You can use [Glade](http://glade.gnome.org/) to visually create your GUI.  It's [in the repos](http://packages.ubuntu.com/edgy/devel/glade), so you can just install it via Synaptic.

I don't use Anjuta, but there should be something along the lines of "project options" where you can add libraries to link with after creating your source files.

---

### Post by Xealot on 2007-01-10
Glade literally saved my day.

It was a pain trying to design the GTK apps strictly trough code, especially
if you're used to the way windows widgets work..

---

### Post by october1917 on 2007-01-10
Something relative:

I'm trying to compile the Transmission torrent client and there hapends something wrong. Can you help me?

```
g1annis@SovietKong:~/Desktop/Transmission-0.6.1$ ./configure
System:  Linux
OpenSSL: missing, using built-in SHA1 implementation
GTK+:    no

Now use GNU make to build Transmission.
It may be called 'make' or 'gmake' depending on your system.
```I think that this "no" beside "GTK+" isn't right.

What to do? Thanks.

---

### Post by po0f on 2007-01-10
october1917,

Look through the README or INSTALL files to look over the requirements.  You'll need either the [libgtk2.0-dev](http://packages.ubuntu.com/edgy/libdevel/libgtk2.0-dev) or [libgtk1.2-dev](http://packages.ubuntu.com/edgy/libdevel/libgtk1.2-dev) packages, dependent on which version of GTK+ that app requires.

---

### Post by semgok on 2007-04-27
I am using ubuntu 6.10 and using anjuta but i have a problem about gtk+2.0

when i install the libgtk2.0-dev,i have the fallowing message:

The following packages have unmet dependencies:
  libgtk2.0-dev: Depends: libpango1.0-dev (>= 1.10.0-2) but it is not going to be installed
                 Depends: libcairo2-dev but it is not going to be installed
                 Depends: libxcursor-dev but it is not going to be installed
                 Depends: libxfixes-dev but it is not going to be installed
E: Broken packages


and when i install libcairo2-dev,i have the fallowing messeage:

The following packages have unmet dependencies:
  libcairo2-dev: Depends: libcairo2 (= 1.0.4-0ubuntu1) but 1.2.4-1ubuntu~dapper1 is to be installed
E: Broken packages

and libcairo2 have already installed on my machine so If i installed libcairo 1.0.4 packages,would i have a problem ?

thanks all.

---

### Post by WW on 2007-04-27
6.10 is edgy, so why would you have version 1.2.4-1ubuntu~**dapper**1of libcairo2-dev installed? Do you have a mix of edgy and dapper repositories in /etc/apt/sources.list?

---

### Post by semgok on 2007-04-27
oohh I am so sorry.It is big mistake.I am using 6.06.

---

