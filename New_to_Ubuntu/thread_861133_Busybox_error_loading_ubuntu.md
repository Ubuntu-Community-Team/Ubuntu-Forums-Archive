---
title: "Busybox error loading ubuntu"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by Mitnick on 2008-07-16
well today i wanted to try ubuntu for my first time, i loaded the live cd.

opened Gparted, made a ext3 partition. and installed ubuntu on it.

after the installation it asked me to restart my computer.

i restarted and booted the installed version of ubuntu, it started to load ( the loading screen).

and then this poped up:

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Build-in shell (ash)
Enter 'help' for a list of built-in commands.

(initframfs) _


what am i suposed to do now? 

my computer:

Intel core 2 quad Q9300 2,50Ghz Procesor
Kindstone 2gb Ram
Nvidia 8800gts Graphic card
Abit IX38 QuadGT Motherboard

---

### Post by kestrel1 on 2008-07-16
What make is your Hard drive? I have seen somewhere about Seagate drives having somesort of problem with the kernel, not sure if this is right though. Also the majority of cases that have this error get it when using the live CD & this is down to the CD drive. Only solution I have seen is to remove the offending drive, but this may not be the case.

---

### Post by Mitnick on 2008-07-16
> **kestrel1 said:**
> What make is your Hard drive? I have seen somewhere about Seagate drives having somesort of problem with the kernel, not sure if this is right though. Also the majority of cases that have this error get it when using the live CD & this is down to the CD drive. Only solution I have seen is to remove the offending drive, but this may not be the case.

how?

---

### Post by avtolle on 2008-07-16
See [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions) for a discussion of boot options. One to try, which is not mentioned in the link, is all_generic_ide which has helped some. It is added to the boot line in the same manner as set out in the link for adding the example that is given. Give this a try and see whether you can boot up.

---

### Post by kestrel1 on 2008-07-16
To remove the offending drive, the only option that seemed to work is to actually unplug it from the motherboard. Only problem with that is if you only have the one CD drive you obviously do not want to do that. Another mentioned making the drive a slave instead of a master, by changing the jumper settings on the device.
You are probably better off trying the link given above by Avtolle before changing hardware settings though.

---

### Post by Mitnick on 2008-07-17
> **avtolle said:**
> See [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions) for a discussion of boot options. One to try, which is not mentioned in the link, is all_generic_ide which has helped some. It is added to the boot line in the same manner as set out in the link for adding the example that is given. Give this a try and see whether you can boot up.



yupp :D all_generic_ide   worked awsuum thanks alot:)))

---

### Post by Francewhoa on 2010-03-11
Same here. **The following worked for me** [http://ubuntuforums.org/showthread.php?p=8952609#post8952609](http://ubuntuforums.org/showthread.php?p=8952609#post8952609)

---

