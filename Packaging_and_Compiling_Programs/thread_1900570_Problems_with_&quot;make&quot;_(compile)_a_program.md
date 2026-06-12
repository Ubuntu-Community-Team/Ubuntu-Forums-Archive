---
title: "Problems with &quot;make&quot; (compile) a program"
date: 2011-12-26
forum: Packaging and Compiling Programs
---

### Post by sajjad.ir on 2011-12-26
Hi
i'm a new user of ubuntu and this is my firs post in this forum

i tried to install a program from it's source but in compile step (make) i got this error:

make: *** No targets specified and no makefile found.  Stop.

i also google my problem but got nothing :(

also tried step in INSTALL file in the source (./configure -- make -- sudo make install) but not working

and try itried : "cmake.." , and install build-essential , gettext , and somthing that i don't remember :)

i always have this problem :(

PLZ Heeeeeeeeeeeeelp me :'( :confused:

.
this is my configure log (i.e for nautilus-action):

[http://uploadtak.com/images/wmpwdgrgk7k0frhxok4y.zip](http://uploadtak.com/images/wmpwdgrgk7k0frhxok4y.zip)

---

### Post by lisati on 2011-12-26
*Thread moved to **Packaging and Compiling Programs**.*

<aside>
The forum automatcally recognises links, so you don't need to put in [noparse][html] and [/html][/noparse] for them. I've also made a minor edit to your thread title.
<aside ends>

---

### Post by sajjad.ir on 2011-12-30
Is anybody there to help me?!?!?!

---

### Post by Lars Noodén on 2011-12-30
Generally, installing a program not only from source but without the package manager is for advanced users.  

What package are you trying to install?

Is it already in the [Ubuntu package repository](http://packages.ubuntu.com/) so you can get it via the software center or Synaptic?

If you have to have it from source, why not use [apt-get source](http://manpages.ubuntu.com/manpages/oneiric/en/man8/apt-get.8.html) instead to get a known working source package?

---

### Post by sajjad.ir on 2012-01-01
ThanX for reply [thumbs up >> Like ]
.
you are absolutely right but :
i have a not full speed internet connection . :(
somtimes i have to install software from source and i must download them and install, and for download i need to resume them.
i think synaptic or other package manager can't resume downloaded package files because of this i wanted to install them from source file.
.
now what can i do ? HHEEEELLLP

---

### Post by Bachstelze on 2012-01-01
> **sajjad.ir said:**
> 
i think synaptic or other package manager can't resume downloaded package files because of this i wanted to install them from source file.

Actually, yes, it can.

---

