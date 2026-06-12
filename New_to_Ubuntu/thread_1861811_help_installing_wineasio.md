---
title: "help installing wineasio"
date: 2011-10-16
forum: New to Ubuntu
---

### Post by djembeing on 2011-10-16
I need some help installing wineasio.  I'm using ubuntu 10.10.  I've tried 

[COLOR=brown]D/l the last wineasio rpm from the ftp using e.g.
     Code:
     wget [ftp://ftp.gwdg.de/pub/linux/misc/jacklab/SUSE-10.2/RPMS/i586/wineasio-0.7.3-3.1.i586.rpm](ftp://ftp.gwdg.de/pub/linux/misc/jacklab/SUSE-10.2/RPMS/i586/wineasio-0.7.3-3.1.i586.rpm) 
Transform the package using alien :
     Code:
     sudo alien --to-deb wineasio-0.7.3-3.1.i586.rpm 
Then install the package newly created :
     Code:
     dpkg -i wineasio-0.7.3-3.1.i586.deb 
[/COLOR]

it gives me this:

dpkg: error processing wineasio-0.7.3-3.1.i586.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 wineasio-0.7.3-3.1.i586.deb



thanks in advance:)

---

### Post by meatytaco on 2011-10-16
have you tried installing it from the .rpm file as opposed to converting it then installing?

---

### Post by Mark Phelps on 2011-10-17
You can't install from .rpm files -- this is Ubuntu, not Red Hat.

As to using them, that is a very hit-or-miss proposition.  Although alien CAN convert some rpm files to deb files, that's no guarantee they will then work.

You would do better trying to compile from source.

---

### Post by meatytaco on 2011-10-17
> **Mark Phelps said:**
> You can't install from .rpm files -- this is Ubuntu, not Red Hat.

Really? Reading the man page for the "rpm" command, option -i directed toward a .rpm file is to install it?  I admit, I haven't really messed with .rpm files, but is there something I'm missing in that area? Lol.

---

### Post by meatytaco on 2011-10-17
Also, to the OP, this may help ya out...
[http://embraceubuntu.com/2005/09/23/installing-using-an-rpm-file/]("http://embraceubuntu.com/2005/09/23/installing-using-an-rpm-file/")
Cheers!

---

### Post by djembeing on 2011-10-17
i got it working, i think.  Had a path wrong. had to do with capitalization.  forgot we're case sensitive.:oops:  thanks guys.

---

### Post by meatytaco on 2011-10-18
Good deal :D yep. Linux is very case sensitive :P Also, when typing out paths, just type a couple letters of the folder you're going for and hit [TAB]. Is an auto-complete function. (Just in case you weren't aware)

---

### Post by djembeing on 2011-10-18
there's plenty I'm unaware of. Thanks, that'll come in handy

---

