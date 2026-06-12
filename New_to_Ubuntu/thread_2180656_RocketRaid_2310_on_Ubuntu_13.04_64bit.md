---
title: "RocketRaid 2310 on Ubuntu 13.04 64bit"
date: 2013-10-14
forum: New to Ubuntu
---

### Post by neilandmichelle on 2013-10-14
Hi Guys,  I would like to start with how absolutely incompetent I am with Linux in general, as in struggling to use command line so any help is great.  I have a pc that I am trying to turn into a home theater NAS which has a Highpoint RocketRaid 2310 with four 4tb HDD's in Raid 5.

I have been following the thread at:
[http://ubuntuforums.org/showthread.php?t=1856162](http://ubuntuforums.org/showthread.php?t=1856162)

these are just dealing with the generic linux driver but they are working on the 3.0 kernel.  When I compile my dkms I get the following error:
DKMS make.log for rr2310pm-1.0 for kernel 3.8.0-19-generic (x86_64)
Mon Oct 14 17:51:43 EST 2013
make: Entering directory `/var/lib/dkms/rr2310pm/1.0/build/product/rr2310pm/linux'
../../../inc/linux/Makefile.def:86: *** Only kernel 2.4/2.6/3.0 is supported but you use 3.8.  Stop.
make: Leaving directory `/var/lib/dkms/rr2310pm/1.0/build/product/rr2310pm/linux'

Is it just a matter of me redoing all the steps but adding in 3.8 or 
  
would I be better off following this guide?
[http://ubuntuforums.org/showthread.php?t=1899544](http://ubuntuforums.org/showthread.php?t=1899544)

ah trying to get a bit of cheap old kit to work with a modern OS, its my fault really but I do miss an executable :)

---

### Post by foro.carlos on 2014-02-25
I,m struggling with the same problem right know. I think the key is to change the kernel support line in the source file mentioned in this help page
[https://help.ubuntu.com/community/RocketRaid]("https://help.ubuntu.com/community/RocketRaid").
I,ll tell you if I success and how I did it... hopefully.

---

