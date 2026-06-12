---
title: "packages from debian sid into ubuntu?"
date: 2009-09-10
forum: Packaging and Compiling Programs
---

### Post by spotspot on 2009-09-10
There are finally packages of the new Electric Sheep for Debian Sid:
[http://packages.debian.org/sid/electricsheep](http://packages.debian.org/sid/electricsheep)

What do we have to do to get this into Ubuntu?

---

### Post by Bachstelze on 2009-09-10
Wait for MOTUs to port it... or do it yourself.

---

### Post by spotspot on 2009-09-10
> **HymnToLife said:**
> Wait for MOTUs to port it... or do it yourself.

thanks.  what or who is MOTU?  i am happy to do stuff myself but i don't believe i have permission to add packages to ubuntu proper.

---

### Post by angryfirelord on 2009-09-18
> **spotspot said:**
> thanks.  what or who is MOTU?  i am happy to do stuff myself but i don't believe i have permission to add packages to ubuntu proper.
MOTU stands for Masters of the Universe. Basically, they're just the package maintainers for Ubuntu.

Oh, and electricsheep is already packaged for ubuntu. Just do a sudo apt-get install electricsheep.

---

### Post by spotspot on 2009-10-08
> **angryfirelord said:**
> 
Oh, and electricsheep is already packaged for ubuntu. Just do a sudo apt-get install electricsheep.

that version is obsolete, it doesn't work anymore.  how does one communicate with the MOTUs to be sure this doesn't slip through the cracks?

---

### Post by komodo on 2009-10-12
Ok. Might be a good time for me to start with packaging ;)
I will have a look on this.

---

### Post by dinxter on 2009-10-12
you might want to look at 
[https://wiki.ubuntu.com/SyncRequestProcess](https://wiki.ubuntu.com/SyncRequestProcess)
There shouldnt be any need to repackage something in debian sid

---

### Post by komodo on 2009-10-12
@dinxter: thanks! We are also during a freeze currently so probably it's best to wait until 9.10 is out.

---

### Post by NoBugs! on 2009-10-27
I remember downloading and installing some packages from Debian once, it seemed to work fine. Are there system stability risks or other risks with installing Debian .deb's in Ubuntu?

---

### Post by Bachstelze on 2009-10-28
> **NoBugs! said:**
> I remember downloading and installing some packages from Debian once, it seemed to work fine. Are there system stability risks or other risks with installing Debian .deb's in Ubuntu?

The only risk is that since you don't have the repository for that package in your sources.list, the package won't be updated automatically, so you could miss an important security update.

---

