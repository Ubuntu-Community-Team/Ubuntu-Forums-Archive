---
title: "how exactly does one download and install the source code"
date: 2006-11-16
forum: Programming Talk
---

### Post by brianwarner983 on 2006-11-16
ok, heres my situation:
im trying to install the source code for edgy eft, but i dont have a wireless driver working yet.  my machine has dual boot setup, so i can boot to xp to access the internet.  what exactly do i need to  do in order to install the source code?
bear with me, im a pretty big linx n00b.

---

### Post by sweemeng on 2006-11-16
why you need an ubuntu source code?

---

### Post by hearnden on 2006-11-16
Source-code uses a similar package mechanism to other Ubuntu packages.  The easiest way to get the source-code for a package is to use apt-get, e.g.
to download the source code for wget

```

$ sudo apt-get --download-only source wget

```

However if you don't have internet working in Edgy, then maybe you can find what you're after by manually browsing the repositories:

[http://archive.ubuntu.com/ubuntu/dists/edgy/](http://archive.ubuntu.com/ubuntu/dists/edgy/)

I'm assuming you have a good reason to install the source code, because it is rarely necessary.

---

### Post by igknighted on 2006-11-16
If you do what hearnden suggests you can just find the .deb you are looking for.  Much easier to deal with than the source code (and far less time consuming).

---

### Post by brianwarner983 on 2006-11-16
im trying to use ndiswrapper to get my wireless card working.  in the install guide file it says i need source code installed.  maybe  im looking at it the wrong way?

---

### Post by brianwarner983 on 2006-11-16
oh, and i may be a n00b, but im not afraid to dig deep into stuff, screw it up, and then figure out how to fix it.  thats kinda why i want to get into linux :)

---

### Post by ciscosurfer on 2006-11-16
Have you tried adding a **deb-src** line to your sources.list and updating/ugrading the files you need this way?

---

### Post by shining on 2006-11-16
> **brianwarner983 said:**
> im trying to use ndiswrapper to get my wireless card working.  in the install guide file it says i need source code installed.  maybe  im looking at it the wrong way?

You should post a link to this installing guide, and telling us which particular section causes you trouble. :)

---

### Post by brianwarner983 on 2006-11-16
here is the guide:
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation)

it says at the top "You need a recent kernel at least 2.6.6 or 2.4.26 with source."  

everything was going great with the install, until i checked the system log and it did not display "wlan0: ndiswrapper ethernet device xx:xx:xx:xx:xx:xx"
or anything remotely like that.

---

### Post by hearnden on 2006-11-16
There is a specific package for installing the kernel source:

```

$ sudo aptitude install kernel-source

```

---

### Post by brianwarner983 on 2006-11-16
ok, so i did that, then i did sudo make config in the directory of the driver, and it gave me:

Linux source directory [/usr/src/linux]: 
Linux source tree /usr/src/linux is incomplete or missing!
    See the HOWTO for a list of FTP sites for current kernel sources.

Configuration failed.

make: *** [config] Error 1


is there a different directory that it uses?
i checked, and that folder (/usr/src/linux) isnt in my system

---

### Post by hearnden on 2006-11-16
Actually for ndiswrapper I'm not sure you need the entire kernel source, it appears you only need the headers:

```

sudo apt-get install linux-headers-`uname -r` 

```

and then

```

sudo ln -s /usr/src/linux-<kernel-version> /lib/modules/`uname -r`/build

```

as per the instructions in the link you gave.

---

