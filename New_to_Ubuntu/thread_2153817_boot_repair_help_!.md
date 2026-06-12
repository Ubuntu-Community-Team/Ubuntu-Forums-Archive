---
title: "boot repair help !"
date: 2013-06-12
forum: New to Ubuntu
---

### Post by Mark Scott on 2013-06-12
Hi there,

I have a really old Mesh P.C. which did sucessfully install and run XP (so it should I hope be capable of running Lubuntu) was Windows 95 before !. I decided to try Lubuntu and burned a live disc. I believe it has installed O.K. but when I boot from HD I get "grub rescue" after "unknown file system". I then tried the boot-repair as suggested and it did a load of stuff. But I still have the same problem. Here is the url for the boot info summary created after boot repair ran. [http://pasteubuntu.com/5758560/](http://pasteubuntu.com/5758560/)
Due to the small HD I got the installer to ditch XP as it was needing to be activated and I lost the code.

I suspect this has fixed the boot part but for some reason I just cannot get it started ! Maybe a BIOS setting which needs to be changed to get the correct file system? Perhaps it is still set for Windows or something? I have no experience of LINUX and very little familiarity of changing BIOS settings. 

Many thanks

Mark

---

### Post by oldfred on 2013-06-12
Welcome to the forums.

What version did you install and what CPU does system have. 
If really old you may need the version without PAE.

 [http://ubuntuforums.org/showthread.php?t=1951653](http://ubuntuforums.org/showthread.php?t=1951653)
Ubuntu, Kubuntu, and probably Edubuntu will ship with the PAE kernel in 12.04, but both Lubuntu and Xubuntu will ship with non-pae
      
 How To Install Ubuntu 12.04 On Non-PAE Capable Hardware.
[http://www.webupd8.org/2012/05/how-to-install-ubuntu-1204-on-non-pae.html#more](http://www.webupd8.org/2012/05/how-to-install-ubuntu-1204-on-non-pae.html#more)
To see processor
lscpu
grep --color=always -i PAE /proc/cpuinfo

 [http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)
PAE is provided by Intel Pentium Pro and above CPUs, including all later Pentium-series processors (except most 400 MHz-bus versions of the Pentium M)

But I am not sure installer would have worked it it was the wrong version.

---

### Post by Mark Scott on 2013-06-12
I just changed a setting in BIOS which has solved it!  It was in the IDE bit and it appeared that no drives were selected so I let it auto select and have now got the sign in screen ! 

Thanks for taking the time to reply. I think I'll be OK now (fingers crossed !)

---

