---
title: "deborphan"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by AnLGP on 2008-06-10
if I delete the packages that this prints out what's the percentage it won't FUBAR my system?

---

### Post by spiderbatdad on 2008-06-10
What is the question? The packages that what prints out?

---

### Post by brian_p on 2008-06-10
> **AnLGP said:**
> if I delete the packages that this prints out what's the percentage it won't FUBAR my system?

If that happens - file a bug against the package.

---

### Post by AnLGP on 2008-06-10
Thanks :)

I'm trying to take preventative measures so I don't fubar my system.

The package in question is deborphan and it supposedly selects orphaned (no longer needed) packages from your system that way you can remove them.  I just don't want to remove anything important and hope it's right :).  I was asking hoping someone has used it before on here.

---

### Post by cubeist on 2008-06-10
I have never heard of this program, but unless you have been installing a ton of packages in order to do custom compiles of software, I really wouldn't worry too much about older unused packages.  Nevertheless, I can understand you want a clean system...I am the same way.  Have you tried autoremove in synaptic

sudo apt-get autoremove

that will remove packages you installed manually that are no longer needed.

Also, you can open synaptic and manually sort through packages (history in the file menu helps determine old packages).  This takes some time, but if you try to delete a package this way and there are dependencies it will tell you!

---

### Post by schiznik on 2008-06-10
deborphan *should* work without breaking your system. It removes dependincies that were installed when you installed something else, that has now been removed.

If you really want to be sure, please post the list that it gives you, so that someone here can shout if its going to remove anything bad.

(I've used this on ubuntu, as well as debian)

---

### Post by AnLGP on 2008-06-10
libwps-0.1-1
libspeex1
libsamplerate0
libgtk1.2
libthunar-vfs-1-2
libgstreamer-plugins-base0.10-0
libicu38
libjack0
libdb4.4
libcurl3
libsdl-mixer1.2
libresid-builder0c2a
libhyphen0
libarchive1
libsidutils0
libstlport4.6ldbl
libneon27
libast2
libtagc0
libgnutls13

---

### Post by cariboo on 2008-06-10
Deborphan automatically tells you what packages are obsolete and unneeded any more.

In the attached jpg look at **installed (auto removeable)** this is what deborphan does

---

### Post by AnLGP on 2008-06-10
so deborphan is essentially not necessary? also is it safe to say that if it appears there it is deletable?

---

### Post by brian_p on 2008-06-10
> **AnLGP said:**
> so deborphan is essentially not necessary?

Correct. Other package tools (apt-get and aptitude, for example) can help to remove redundant packages.

> also is it safe to say that if it appears there it is deletable? 

If by that you are asking if it is safe to take deborphan's advice then yes. If you do try to remove something necessary to the system the package management will complain and give you time to reconsider.

---

### Post by cariboo on 2008-06-10
I just looked and I don't even have deborphan installed and it really only has libc6 as a depend so uninstall it if you want to. I don't really see the need for uninstalling it, as it is such an obscure command that you will never even see it in day-to-day operation. What made you zero in on this particular file?

Just as aside if you see a program that you have no idea what it is for, in a terminal type:

```
man progname
```

where progname is the program name eg: **man fooz2zjs**

Jim

---

