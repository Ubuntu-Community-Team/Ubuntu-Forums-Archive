---
title: "Will Fedora RPMs install on other RPM distros?"
date: 2008-12-07
forum: Other OS Talk
---

### Post by shatteredmindofbob on 2008-12-07
Quick question as I consider some distro-hopping. I've noticed a lot of non-repository items are often distributed in only two flavours: Ubuntu or Fedora. 

I'm wondering, will something packaged for Fedora still install on OpenSUSE?

Thanks.

---

### Post by YeOK on 2008-12-07
Depends, some things will work. I have used SUSE rpms on Fedora in the past. Most of them fail though, because required packages have different names.

---

### Post by binbash on 2008-12-07
Some works, i dont suggest it tho.

---

### Post by smartboyathome on 2008-12-07
> **YeOK said:**
> Depends, some things will work. I have used SUSE rpms on Fedora in the past. Most of them fail though, because required packages have different names.

And sometimes the dependancies are in different places even though the names are the same, thus breaking the precompiled program.

---

### Post by jrusso2 on 2008-12-10
As people have mentioned some work and some don't just like how Debian .deb packages sometimes can work on Ubuntu.

---

### Post by cardinals_fan on 2008-12-10
> **jrusso2 said:**
> As people have mentioned some work and some don't just like how Debian .deb packages sometimes can work on Ubuntu.
...except that Ubuntu is directly based off Debian and even imports Debian packages at the start of every release cycle, while a distro like openSUSE is very different from Fedora.

/nit-picking

---

### Post by uljanow on 2008-12-10
You could ask rpmlint which checks for common errors in rpm-packages or check if the disro is LSB-conform. IMHO Fedora and OpenSuSE are very similar.

---

### Post by WaeV on 2008-12-10
> **jrusso2 said:**
> As people have mentioned some work and some don't just like how Debian .deb packages sometimes can work on Ubuntu.

I thought all debian packages could install on ubuntu (because it's based on debian) but not always vice versa.

---

### Post by stinger30au on 2008-12-10
i doubt it will work well

your better of compling from the source code

---

### Post by igknighted on 2008-12-10
> **uljanow said:**
> You could ask rpmlint which checks for common errors in rpm-packages or check if the disro is LSB-conform. IMHO Fedora and OpenSuSE are very similar.

Fedora is based off of Red Hat, while OpenSuse is based (way back when) off of slackware.  Any similarities are due to LSB compliance or fate, and I don't really like trusting my system stability to fate.

[QUOTE=WaeV]I thought all debian packages could install on ubuntu (because it's based on debian) but not always vice versa. [/QUOTE]

No! And not all Ubuntu packages will work either... a package for 8.04 might wreck an 8.10 install, and vice versa.

---

### Post by SunnyRabbiera on 2008-12-10
you might also be better off using Alien or something to convert debian packages too.

---

