---
title: "compiling a source.... errors"
date: 2013-10-22
forum: New to Ubuntu
---

### Post by macstl on 2013-10-22
I am trying to compile the source files for Abiword 3, just for the sake of learning how to do it with some instructions I got from a newsletter . I made a dir and did a wget of the tar file and opened it . Then did a cd to dir it created abiword-3.0.0
When I do a ./configure   it goes through a lot of steps ok but then I get:
checking for png.h... no
configure: error: `png.h' not found, install libpng or specify CPPFLAGS to include custom locations

libpng 12-0 library runtime is already installed on my ubuntu 12.04
Any help would be apprreciated. Just trying to learn how to compile something.

---

### Post by Petro Dawg on 2013-10-22
Its possible the version of libpng you are using isn't the same version as when the Abiword source code was written or you may need to install a development version of libpng (libpng-devel-something).

---

### Post by oldos2er on 2013-10-23
You need libpng*dev and/or libpng++-dev. ```
sudo apt-get build-dep abiword
``` should pull them in.

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

---

### Post by macstl on 2013-10-23
> **oldos2er said:**
> You need libpng*dev and/or libpng++-dev. ```
sudo apt-get build-dep abiword
``` should pull them in.

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

Should I remove the one I got before installing this?
thanks

---

### Post by oldos2er on 2013-10-23
Do you mean the libpng runtime? You can or not, I don't think it will have any effect either way.

---

### Post by macstl on 2013-10-23
> **oldos2er said:**
> Do you mean the libpng runtime? You can or not, I don't think it will have any effect either way.

I installed the build-dep and it compiled without errors. Thank you
I goto /usr/local/bin and abiword is there. I type abiwork in cli and get:
user1@thinkpad61:/usr/local/bin$ sudo abiword
[sudo] password for user1: 
abiword: error while loading shared libraries: libabiword-3.0.so: cannot open shared object file: No such file or directory

should this execute w/o error?

---

### Post by macstl on 2013-10-23
> **macstl said:**
> I installed the build-dep and it compiled without errors. Thank you
I goto /usr/local/bin and abiword is there. I type abiwork in cli and get:
user1@thinkpad61:/usr/local/bin$ sudo abiword
[sudo] password for user1: 
abiword: error while loading shared libraries: libabiword-3.0.so: cannot open shared object file: No such file or directory

should this execute w/o error?

If I type src/abicode in the abicode-3.0.0 dir it works. Should there not be a easier way.

---

### Post by macstl on 2013-10-23
I did a     sudo checkinstall  and then rebooted computer. It show in gui as installed so I moved it to unity launcher. But when I click on it , it does nothing.

---

