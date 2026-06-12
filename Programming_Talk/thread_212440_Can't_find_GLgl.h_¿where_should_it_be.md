---
title: "Can't find GL/gl.h ¿where should it be?"
date: 2006-07-09
forum: Programming Talk
---

### Post by Román on 2006-07-09
Hi all!

I'm trying to compile a program using OpenGL, but I don have installed the include file GL/gl.h which is needed to compile such aplications.

I don't know wich package (if any) provides this file, and I spent all afternoon triying to find it.  ¿Where should it be??? :confused:

Thanks a lot in advance!

---

### Post by fluffington on 2006-07-10
/usr/include/GL/gl.h is part of the package [mesa-common-dev](mhttp://packages.ubuntu.com/dapper/devel/mesa-common-dev).

---

### Post by Román on 2006-07-10
Thanks a lot!

Now the obvious following question is ¿Is there any way to find a file in a package without downloading every package?

---

### Post by ifokkema on 2006-07-10
> **Román said:**
> Thanks a lot!

Now the obvious following question is ¿Is there any way to find a file in a package without downloading every package?

Use apt-file;
```
sudo apt-get install apt-file
sudo apt-file update
apt-file search GL/gl.h
```

:)

---

### Post by hod139 on 2006-07-10
Another option is to go to [http://packages.ubuntu.com/](http://packages.ubuntu.com/)
and use the "Search the contents of packages" search feature.
****

---

### Post by Román on 2006-07-10
> **ifokkema said:**
> Use apt-file;:)

Great, thanks! I think I should investigate a little more on the many apt-* programs :-k

---

### Post by braddock on 2006-08-01
I had a similar problem, but more complicated.  I think I may have actually encountered a bug in upgrading to dapper?  Here are my notes and a fix; 

I've seen this described on a few forums elsewhere as well, but no fix.

Missing GL/gl.h header file in Ubuntu Dapper Drake 6.06 

In my Ubuntu Dapper Drake installation, distribution-upgraded
from Hoary 5.10, I was missing GL/gl.h.  Note, I was NOT using NVIDIA
drivers on this machine, so that is not a factor for me.

GL/gl.h is provided by the mesa-common-dev package, but strangely that
package was already installed, and dpkg -L mesa-common-dev did not
list GL/gl.h.

apt-file confirmed that GL/gl.h SHOULD be provided by the
mesa-common-dev package.

FIX: apt-get --reinstall install mesa-common-dev

Is Mesa somehow reluctant to add GL/gl.h because it is so often provided by  the nvidia drivers?

     -braddock

---

### Post by hod139 on 2006-08-01
It is a known bug: [https://launchpad.net/distros/ubuntu/+source/mesa/+bug/29435](https://launchpad.net/distros/ubuntu/+source/mesa/+bug/29435)

---

### Post by silver6 on 2007-03-14
Thanks hod139 and ifokkema, i didn't know how to search for files within packages, so that really helps me out big time! ubuntu's ease never ceases to amaze me :D

---

### Post by ifokkema on 2007-03-15
> **silver6 said:**
> Thanks hod139 and ifokkema
Heh heh, you're welcome. Apt rules!

---

