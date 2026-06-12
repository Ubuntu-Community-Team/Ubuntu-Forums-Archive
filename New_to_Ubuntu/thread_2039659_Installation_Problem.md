---
title: "Installation Problem"
date: 2012-08-09
forum: New to Ubuntu
---

### Post by LionsFan25 on 2012-08-09
All,
 
I am an absolute beginner when it comes to linux in general.  My background is 100% windows based.
 
I am trying to get into using Ubuntu and MythTV since it will allow me to do what I have wanted but couldn't with WMC.  
 
The problem is I am having a hard time getting the OS to install.  I have run the graphical and the alternative versions and both are telling me the same thing.  It failes when trying to install the boot strapper.
 
There are a lot of threads out there that cover this, but either their solutions are not working for me or I just have no idea what I am doing and how to get to where it is I need to be for the solution.  (I am betting on the latter)
 
I have a hardware raid that is run by my mother board on my machine.  There are five 1 TB disks in the array using Raid 1.  This makes my disk size 5.0 TB (approx)
 
Please any help you provide would be greatly appreciated.  Please treat me as someone who doesn't know anything because I don't.  Please don't assume I know the linux commands.
 
Thanks,
 
Keith

---

### Post by Kalanac on 2012-08-09
Have you checked that the install image you downloaded is free of errors?  There is an option in the menu that opens when you boot the live image called "Check disk for defects" or something similar, which will check the install image for you.

You should also check out:

[https://help.ubuntu.com/10.04/serverguide/advanced-installation.html](https://help.ubuntu.com/10.04/serverguide/advanced-installation.html)

for guidance on installing Ubuntu onto a RAID setup

---

### Post by audiomick on 2012-08-09
Hallo.

I haven't done this, just remembered reading about it. Had you seen this information? I know it is an aritcle about fake RAID, and your description indicates you might have hardware RAID, but it think the business of manually telling the installer where to put grub (the boot loader) might still be relevant.

[https://help.ubuntu.com/community/FakeRaidHowto#Installation]("https://help.ubuntu.com/community/FakeRaidHowto#Installation")

---

