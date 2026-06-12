---
title: "installed ubuntu 14.04 alonside win 7, laptop became too slow"
date: 2015-08-03
forum: New to Ubuntu
---

### Post by riungu on 2015-08-03
hi guys,need some help please;
i installed ubuntu 14.04 alongside win 7 in my hp elitebook 8440p, core i7, 4gb ram but the booting speed became too slow. i also cant load ubuntu directly, i have to go to advanced options and choose recovery mode for ubuntu to load. any help will be appreciated please

---

### Post by yancek on 2015-08-03
To get enough information to make practical suggestions, go to the site below while booted into Ubuntu and download and run the boot repair.  Be sure to select the option to "Create Bootinfo Summary" when you run it and do not make any changes.  Installing a second operating system on another partition should not have a noticeable impact on boot time.

 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

What exactly happens when you select the first boot option for Ubuntu?

---

### Post by oldfred on 2015-08-03
Your specs say you have a nVidia 3400m? Is it just that or switchable graphics between Intel & nVidia?

If you can boot recovery mode, it probably is because it uses nomodeset by default.

Try adding nomodeset to linux line in grub menu.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Then you want to confirm what nVidia driver is best for your system. If it supports the very newest driver, but is not brand new chip/card the most current version in Ubuntu repository should work fine. Go to system settings, Software, and drivers tab.

Updated driver search by nVidia model
[http://www.geforce.com/drivers](http://www.geforce.com/drivers)

Screen shots are from my older system, so you should show newer versions.

---

