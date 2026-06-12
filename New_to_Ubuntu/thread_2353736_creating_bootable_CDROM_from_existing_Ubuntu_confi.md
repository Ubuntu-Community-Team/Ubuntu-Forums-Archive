---
title: "creating bootable CDROM from existing Ubuntu configuration"
date: 2017-02-24
forum: New to Ubuntu
---

### Post by alabamatoy2 on 2017-02-24
I have 16.04 running with specific apps installed, much configuration done they way Im required to have it.

Now I need to create a bootable CDROM (DVD, whatever) based upon my specific running configuration, to deploy this same config to several identical isolated machines.  Can someone point me at a guide as to how to accomplish this, please?

---

### Post by kyknos12 on 2017-02-24
become a little more clear, you want to make bootable dvd rom distribution from of the installed your system as backup solution?

---

### Post by Keith_Helms on 2017-02-24
What does your running configuration consist of?  Is it just a list of installed packages?  Does it also include settings from your home directory?

Building a custom install disc is a pain, but getting a list of installed packages and then installing them on another system is not that hard.  You can get the package names with
```
grep "Package:" /var/lib/dpkg/status | cut -d' ' -f2 | grep -v "^$" | sort > packagelist.txt
```
You could then install them on a different system with something like
```
while read package;do sudo apt-get -y install $package;done < packagelist.txt
```

---

### Post by alabamatoy2 on 2017-02-24
Trying to make my requirement more clear:

I must have a collection of non-networked, standalone boxes that boot from CDROM with no hard disc, no writeable media (except RAM) so that when machine is powered off, it goes to known, totally blank state.

I have a single box (physically identical to the others, except it has n/w and hard drive) with 16.04LTS installed and configured to meet my requirements, necessary apps installed, some simple scripts, user accounts created etc.

Using the configured OS and installed apps and users and such running on the single machine with the hard disc, I need to make several copies on a bootable CDROM or DVD so that I can boot the other machines (which have no NW or hard disc, only a CD/DVD ROM drive) and have them come up and function exactly the same way as the one I have configured.

Does this make sense?

---

### Post by yancek on 2017-02-24
If you want to create an iso image of an installed system, you should be able to use Systemback.  The link below explains how to get and use it and it's limitations.  If you want the Ubiquity installer on the iso, you will need to install it before running Systemback.

[https://www.ostechnix.com/systemback-restore-ubuntu-desktop-and-server-to-previous-state/](https://www.ostechnix.com/systemback-restore-ubuntu-desktop-and-server-to-previous-state/)

---

### Post by kyknos12 on 2017-02-24
Just try this
[https://www.youtube.com/watch?v=1Un0vsw6HKY](https://www.youtube.com/watch?v=1Un0vsw6HKY)
The philosophy that can be applied to any distribution

---

### Post by alabamatoy2 on 2017-02-26
This forum never fails to make this old dog learn new tricks.  Yall have given me two viable courses of action to solve this problem.  Thanks much!!

---

### Post by oldrocker99 on 2017-02-26
If your problem is solved, as it seems to be, please use the Thread Tools to mark this thread as [SOLVED].

---

### Post by alabamatoy2 on 2017-03-07
> **yancek said:**
> If you want to create an iso image of an installed system, you should be able to use Systemback.  The link below explains how to get and use it and it's limitations.  If you want the Ubiquity installer on the iso, you will need to install it before running Systemback.

[https://www.ostechnix.com/systemback-restore-ubuntu-desktop-and-server-to-previous-state/](https://www.ostechnix.com/systemback-restore-ubuntu-desktop-and-server-to-previous-state/)

This is a very capable tool.  Simple, effective, does what it claims.  I was able to produce a bootable DVD of my specially configured OS and deliver what the customer wanted!  Thanks again.

---

