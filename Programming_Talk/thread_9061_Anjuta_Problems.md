---
title: "Anjuta Problems"
date: 2004-12-23
forum: Programming Talk
---

### Post by soritong on 2004-12-23
Whenever I try to start any type of project within Anjuta, I get this message:

```
configure.in : 80 : './ABOUT.NLS' not found
Makefile.am:6: required directory ./intl does not exist
*error* automake failed
```

It then tells me to run autogen.sh manually, but I'm compeltely lost at why this doesn't work? The projects in Borland BuilderX built just fine.

---

### Post by p!=f on 2004-12-23
[QUOTE=soritong]Whenever I try to start any type of project within Anjuta, I get this message:

```
configure.in : 80 : './ABOUT.NLS' not found
Makefile.am:6: required directory ./intl does not exist
*error* automake failed
```

It then tells me to run autogen.sh manually, but I'm compeltely lost at why this doesn't work? The projects in Borland BuilderX built just fine.[/QUOTE]

Do you have gettext installed?
You may also try to install autotools-dev package.

---

### Post by soritong on 2004-12-23
[QUOTE=p!=f]Do you have gettext installed?
You may also try to install autotools-dev package.[/QUOTE]
 I have both gettext and the autotools-dev package installed.

---

### Post by p!=f on 2004-12-23
Ubuntu Hoary, Anjuta can prepare and build a project. Hmmm... You definitely need some package...
Do you have intltool?

---

### Post by soritong on 2004-12-23
[QUOTE=p!=f]Ubuntu Hoary, Anjuta can prepare and build a project. Hmmm... You definitely need some package...
Do you have intltool?[/QUOTE]
 I have intltool-debian package installed, but not the regular intltool.

---

### Post by GonZo on 2005-02-05
try to install **cvs**

---

### Post by Pierre Maurette on 2005-02-11
Hello newsgroup, this is my first post here,

[QUOTE=GonZo]try to install **cvs**[/QUOTE]

Thanks GonZo, I had the same problem and now, all is fine (Ubuntu 4.10, AMD64).

Pierre

---

### Post by Alain.Menard on 2005-02-16
:grin: Thank you!

I also had this same problem. I was also missing the gnome devs library.
If only somebody would do an anjuta install that also check for all those dependency and install them if needed that would be nice.  :-)

---

### Post by dolson on 2005-03-19
[QUOTE=Alain.Menard]:grin: Thank you!

I also had this same problem. I was also missing the gnome devs library.
If only somebody would do an anjuta install that also check for all those dependency and install them if needed that would be nice.  :-)[/QUOTE]

I agree.

And thanks, this was my problem too!

---

### Post by pierre on 2005-03-21
I had the same problem and did
apt-get install libgnomeui-dev

Everything works fine now.

---

### Post by idn on 2005-03-28
I have hoary AMD64, installed cvs and now everything works fine :) thanks

---

### Post by AndyAWS on 2005-04-19
Has anyone ever put together a comlete list of missing dependancies for Anjuta? I've been searchig around this forum but there are so many people have problems with Anjuta that it's difficult to sort out what all is required to get it working correctly.

---

### Post by babarhaq on 2007-07-16
libglib1.2-dev_1.2.10-17build1_i386.deb
automake_1%3a1.10+nogfdl-1_all.deb
build-essential_11.3_i386.deb
libtool_1.5.22-4_i386.deb
libevent1_1.1a-1_i386.deb
autoconf

Installed all these to make anjuta working.

Babar

---

