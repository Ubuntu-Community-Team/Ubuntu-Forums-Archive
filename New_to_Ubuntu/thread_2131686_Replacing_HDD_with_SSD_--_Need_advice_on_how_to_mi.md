---
title: "Replacing HDD with SSD -- Need advice on how to migrate"
date: 2013-04-02
forum: New to Ubuntu
---

### Post by jimafternoon on 2013-04-02
Hello, 

I'm running Ubuntu 12.10 64 bit alongside Windows 7. The Ubuntu partition is around 150GB. I just ordered a 256GB Samsung SSD, and I plan on installing only Ubuntu on it. 

I'm thinking I could just do a new install, but I don't want to have to redo all of my settings and software installs again if I dont have to. Would it be better to create an image of the current partition?   I'd like to get some opinions on what the best way to go about this would be. Also, this is the first time I'm doing this, so any tips or advice on formatting the drive or anything else would be appreciated. 

I've been reading through some other threads, but a lot of them are a couple years old, some are about SSD/HDD combos, and about different versions of Ubuntu, so I'm hesitant to rely strictly on them. If anyone can link me to confirmed solid instructions I'd appreciate it. 

Thanks.

---

### Post by oldfred on 2013-04-02
I prefer clean installs. All your settings are in /home which you can copy to your new install so you have all your old user configurations. I separate data from /home as I only have a 64GB SSD with two / (root) installs including my /home. But I keep all data on my rotating drive.

       Do SSD need customization?
[http://ubuntuforums.org/showthread.php?t=1981478](http://ubuntuforums.org/showthread.php?t=1981478)
Arch suggests gpt for SSD. Only if installing Windows on older system may you want MBR as Windows only boots from gpt with UEFI. 
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
[http://ubuntuforums.org/showthread.php?t=2003022](http://ubuntuforums.org/showthread.php?t=2003022)
[https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd)

If you have changed hardware settings in /etc and are installing the same version you can probably copy those. If a new version you need to review as they may or may not apply. You can also export a list of installed applications and easily reinstall. Only if you have limited download capability and have not housecleaned old install,  you may be able to copy downloaded .debs but you may get things out of sync. So better to just start fresh.

My backup procedure is to just to a new install but backup what I may need from old install.

 Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

---

