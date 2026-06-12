---
title: "install deb and rpm files"
date: 2008-07-28
forum: New to Ubuntu
---

### Post by saskatchewan on 2008-07-28
How do I install rpm and deb files.  
I have downloaded Adobe and Skype and I am trying to figure out how to install.

---

### Post by kool_kat_os on 2008-07-28
to install deb files just double click on them.

to install rpm's use alien.

there are alot of good tutorials on alien on google.

---

### Post by Potatoj316 on 2008-07-28
alien is good but it dosent always work and they even tell you that.  If you want a program that you can only find as rpm than by all means, use alien.  I would sugest googling for the programs you want first.  You can also check getdeb.net for .deb packages for many programs.

---

### Post by kool_kat_os on 2008-07-28
> **Potatoj316 said:**
> alien is good but it dosent always work and they even tell you that.  If you want a program that you can only find as rpm than by all means, use alien.  I would sugest googling for the programs you want first.  You can also check getdeb.net for .deb packages for many programs.

i was just answering his question...he asked how to install rpm's and i told him :D

---

### Post by kool_kat_os on 2008-07-28
adobe reader has a deb

---

### Post by OldGrey on 2008-07-28
If you install the Medibuntu repository you can download and install adobe reader and skype through synaptic. Plus other stuff including some useful codecs and Google Earth For Medibuntu see:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by bodhi.zazen on 2008-07-28
First it is best to install from the Ubutu repositories if possible.

Next you should now not all .deb are equal. Some will not install or perhaps cause breakage.

```
sudo dpkg -i package.deb
```

As far as RPM, best advice here is don't. Alien can cause breakage ...

IMO best install from source ;) If you like you can use checkinstall to then make a .deb

---

