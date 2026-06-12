---
title: "Terminal Not Showing X, H and F"
date: 2015-05-23
forum: New to Ubuntu
---

### Post by miles5 on 2015-05-23
I was trying to install some software via the terminal when I realized that the lowercase characters x, h and f are not displayed and are invisible, they seem to be there because sometimes when I highlight a missing character it will pop into existence.
I used red to signify text that does not appear:
```

shrek@shreks-shrektop:~$ sudo apt-get install transmission[sudo] password for shrek: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libcairo2:i386 libcurl3:i386 libdbus-glib-1-2:i386 libgconf-2-4:i386
  libgraphite2-3:i386 libgtk2.0-0:i386 libharfbuzz0b:i386 libidn11:i386
  libnspr4:i386 libnss3:i386 libpango1.0-0:i386 libpangocairo-1.0-0:i386
  libpangoft2-1.0-0:i386 libpangox-1.0-0:i386 libpangoxft-1.0-0:i386
  libpixman-1-0:i386 librtmp1:i386 libsdl2-image-2.0-0 libsdl2-ttf-2.0-0
  libxcb-shm0:i386 libxft2:i386 libxss1:i386 libxtst6:i386
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  transmission
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
Need to get 1,230 B of archives.
After this operation, 29.7 kB of additional disk space will be used.
Get:1 http://mirror.cc.vt.edu/pub2/ubuntu/ vivid/universe transmission all 2.84-0.2ubuntu1 [1,230 B]
Fetched 1,230 B in 0s (8,000 B/s)         
Selecting previously unselected package transmission.
(Reading database ... 274952 files and directories currently installed.)
Preparing to unpack .../transmission_2.84-0.2ubuntu1_all.deb ...
Unpacking transmission (2.84-0.2ubuntu1) ...
Setting up transmission (2.84-0.2ubuntu1) ...

```

Thanks

---

### Post by cariboo on 2015-05-23
Could you show us a screen shot of the missing letters, as opposed to coloured text?

---

### Post by miles5 on 2015-05-23
After several hours wasting away trying to fix this, I have finally figured out that it was a virus. I have successfully installed a new distro as is customary for me to do, so it is no big deal.

---

### Post by Vladlenin5000 on 2015-05-23
> **miles5 said:**
> After several hours wasting away trying to fix this, I have finally figured out that it was a virus.
How exactly have you found out "it was a virus"?

---

### Post by miles5 on 2015-05-23
I had scanned all my drives with SOPHOS antivirus.

---

### Post by cariboo on 2015-05-23
> **miles5 said:**
> After several hours wasting away trying to fix this, I have finally figured out that it was a virus. I have successfully installed a new distro as is customary for me to do, so it is no big deal.

You could be in for some big time fame, if you found a Linux virus in the wild. you may even have the chance to name it.

Hopefully you created an image of the system, and documented every thing before reinstalling.

---

