---
title: "Question on installing qt"
date: 2007-04-11
forum: Programming Talk
---

### Post by Madley on 2007-04-11
Hi all, 
i'm tring to install qt libraries on my ubuntu edgy eft, but i've got some problems..

I download the source package from trolltech site, and I follow the installing procedure as explained here:

```
http://doc.trolltech.com/4.2/install-x11.html
```

My problem is the 4th point, where are in Ubuntu the .login or .profile files? I can't find them...

Thanks all...


P.S.: Excuse me if this is not the right section, if it is so, please move thanks.

---

### Post by chair on 2007-04-11
.profile goes in you home directory. If you don't have one, create it. There's a system wide one at /etc/profile

.login is only for csh and tcsh so don't worry about that.

Are you building the Qt libs from source? Aren't they avaliable in universe?

---

### Post by Madley on 2007-04-11
Thaks for your quick reply.

I think they're avaliable even in universe repository, but I don't know what I've to install, so I preferr to download the source file... But if you tell me what I must install from Package Manager, i'll install them from universe repository.

I've unpack and install the libraries in /usr/local/qt. Now, i write this:

```
#Qt Options
PATH=/usr/local/qt/bin:$PATH
export PATH
```

in /etc/profile.

Is it right?

Thanks again.

---

### Post by chair on 2007-04-11
Yep that should be right

As for installing the packages just search for "qt4" and install anything you need, most importantly qt4-dev-tools and libqt4

---

### Post by Madley on 2007-04-11
Ok, i added that lines to the files, now all works right. 

Thanks Chain for your help.

:)

---

