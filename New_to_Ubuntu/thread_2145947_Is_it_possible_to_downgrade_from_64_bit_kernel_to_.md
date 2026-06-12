---
title: "Is it possible to downgrade from 64 bit kernel to 32 bit kernel on ubuntu 10.04"
date: 2013-05-17
forum: New to Ubuntu
---

### Post by shravansofts on 2013-05-17
Hi Ubuntu team,

I am using Ubuntu 10.04 x64bit with 2.6.32-38 Kernel version installed on my laptop. 

In order for one of my installed programs to work, I would like to downgrade the current kernel version to 32bit version of kernel 2.6.32-38 from 64 bit version.


[LIST=1]
[*]Is it possible to downgrade the bit version with out effecting the present OS installation?
[*]Can i switch between 64 bit and 32 bit kernel versions at boot time?
[*]Does the 64bit OS works as 32bit OS after downgrading to 32bit kernel?
[/LIST]

Please, respond for my queries ASAP.

Thanking You,

Regards,
Sravan kumar T.

---

### Post by Paqman on 2013-05-17
No, you can't switch from 64-bit to 32-bit without doing a reinstall as it would require replacing every package on your system.

However, you can install 32-bit applications on a 64-bit system and they'll work fine. You'll need to install a package called ia32-libs. Which program is it that you want to run?

---

### Post by mörgæs on 2013-05-17
10.04 is out of support, so you should switch to a new release. 
If you have the space on the hard drive you could install a 32 and a 64 bit 13.04 side by side, if you want a platform for experimenting.

---

### Post by MoebusNet on 2013-05-17
+1 on recommending switch to 12.04 when feasible.

To install 32-bit libraries:
Ctl-Alt-T to open Terminal
```
sudo apt-get install ia32-libs
```

---

