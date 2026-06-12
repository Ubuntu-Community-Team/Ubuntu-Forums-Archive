---
title: "Difficulty using make"
date: 2008-10-03
forum: New to Ubuntu
---

### Post by lnajt on 2008-10-03
Whenever I try to run 'make' I get a series of unusual error messages (ex. 'stderr' undeclared, or even 'NULL' undeclared (which I think points to a bigger problem)).

I just tried compiling a short piece of c code (using gcc) and it returned the error stdio.h: no such file or directory.  ...

Clearly there is a problem with my computer, or at least the c compiler.(Ubuntu 8 on a Dell Latitude D830, reformatted during installation)

Therefore, what should I do?

(I desperately need to be able to run make so that I can get wl.ko and finish setting up my wireless [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php) )

I am a linx 'noob', but I have basic (above average) computer science knowledge.

- Thanks

---

### Post by cariboo on 2008-10-04
Have you got build-essential installed?

```
sudo apt-get install build-essential
```

That should solve your problems.

Jim

---

### Post by lnajt on 2008-10-04
I ran sudo apt-get install build-essential, but the terminal tells me that it is not available, only refered to by another package.... E: package build-essential has no installation candidate.

I think at this point it would be prudent for me to point out that I do not have a working internet connection on the linux computer (i have to copy the files over from this one.)

---

### Post by adult swim on 2008-10-04
assuming you are using hardy, you can download debs for packages here [http://packages.ubuntu.com/hardy/](http://packages.ubuntu.com/hardy/)

here is build essential [http://packages.ubuntu.com/hardy/devel/build-essential](http://packages.ubuntu.com/hardy/devel/build-essential)

---

### Post by lnajt on 2008-10-04
I am still unable to install these packages (with the exception of make, which changed nothing). They either tell me: Dependancy is not satisfiable or that they could not "download all required files" from [http://security.ubuntu.com/ubuntu/pool/main/l/linux-libc-dev_2.6.24-18.32_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-libc-dev_2.6.24-18.32_i386.deb). 

Thanks anyway.

---

### Post by adult swim on 2008-10-04
it is going to be difficult for you to build anything without a working internet connection.  i see you are trying to build a broadcom driver, do you know what specific card  you have, and is it possible for you to connect this computer to an ethernet cable?

---

### Post by lnajt on 2008-10-04
At the moment I cannot connect through an Ethernet connection, but I can tell you what kind of wireless card I am using:

Broadcom BCM94311MCG wlan mini-PCI (rev 01) the chipset is 14e4:4311 

Using ndiswrapper I have managed to get setup the drivers for my card but for some reason the Network remains disabled (if I run lshw). I have made a post to that effect here: [http://ubuntuforums.org/showthread.php?p=5903726#post5903726](http://ubuntuforums.org/showthread.php?p=5903726#post5903726)

(I am trying to use the drivers from Broadcom's web page (link in first post) as a backup plan since it seems like a more daunting task - especially if I cannot run 'make'.)

Thank you

---

### Post by adult swim on 2008-10-04
if you have successfully installed ndiswrapper, try running these commands one at a time from a terminal and let me know what happens
```
sudo modprobe -r b44

sudo modprobe -r b43

sudo modprobe -r ssb

sudo modprobe ndiswrapper

sudo modprobe b44
```
then run ```
 sudo iwlist scanning
``` and see if any networks come up.

---

### Post by lnajt on 2008-10-04
modprobe -r b44 (nothing printed)
modprobe -r b43 FATAL: error removing b43 (location of b43
modprobe -r ssb FATAL: ssb is in use
modprobe ndiswrapper (nothing printed)
modprobe 44 WARNING: Error inserting mii (location of mii): Operation not permitted   FATAL: Error inserting b44 (location of b44): Operation not permitted

---

### Post by adult swim on 2008-10-04
well im kind of stumped.  here is a guide with your chipset that has alot of positive reviews.  [http://ubuntuforums.org/showthread.php?t=760568](http://ubuntuforums.org/showthread.php?t=760568)  hopefully it will work for you, i know it is terrible to not have internet on a machine.

---

### Post by lnajt on 2008-10-04
Thanks so much. The link you gave me worked perfectly.

---

### Post by adult swim on 2008-10-04
nice!  im glad you got your card in order!

---

