---
title: "dual OS install help"
date: 2012-10-17
forum: New to Ubuntu
---

### Post by deezdrama on 2012-10-17
Decided to give ubuntu a try and installed from the live cd I dl'ed and burned.

I have my desktop and 2 laptops i want to convert over or dualboot with. I installed ubuntu on my older laptop to try it out.
I did the install alongside windows option. My drive was already partitioned so when installing ubuntu I just left the slider at default and continued. After installing it asked to reboot. I clicked continue and it went to a black checksum screen , all said ok,last check said waiting for applications to close or something like that...it hung there and i waited several minutes. 
I hit enter and it imediately rebooted, I got no OS boot option and it went to windows.
I see no ubuntu files on HD when in windows... but noticed the same partition that windows is on is now almost full, so im assuming that ubuntu installed on same partition as windows and the system files cannot be seen from within windows?????

Complete noob to ubuntu and dual OS booting...any suggestions?

Oh- I also went to system> startup and recovery  in windows- went to boot options and windows is only OS listed

---

### Post by deezdrama on 2012-10-17
ok.. just noticed my second partition (not partition windows is installed on)  is nolonger 75gb but 35gb so ubuntu must of installed there, just not getting an option to boot to it

---

### Post by nothingspecial on 2012-10-17
Sounds like you have a problem with grub.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by deezdrama on 2012-10-17
I ran boot manager at startup and ubuntu isnt listed there either :confused:

So do u think i still need to repair grub or did i not install this right?

thanks for the help!

---

### Post by westie457 on 2012-10-17
When you you booted your computer to start the install process did you boot into Windows or did you boot the CD?

Reading through this thread suggests that you installed via Wubi.

In your Windows system do you have a folder called 'Ubuntu'?

---

### Post by audiomick on 2012-10-17
No, I think it was a proper dual boot install. I would suggest following nothingspecial's suggestion to run boot repair on it. That should also supply the option to run the boot info script (that is the "boot info summary" button), which will generate pretty definitive info about the state of things.

---

### Post by cottfcfan on 2012-10-17
A screenshot of your partition table would also be useful.

---

### Post by audiomick on 2012-10-17
> **cottfcfan said:**
> A screenshot of your partition table would also be useful.

That, or the boot info summary....

---

### Post by deezdrama on 2012-10-17
boot repair seemed to do the trick, haven't tried booting into windows again yet but sure i can do that via boot manager.

Ive been computing since the old 486 days and right now running my first non windows based os....ah....liberating, lol

now i get to bug u guys more with some new help me threads.....
like how to get hardware drivers so it doesnt run snail sluggish ;)

---

### Post by audiomick on 2012-10-17
> **deezdrama said:**
> running my first non windows based os....ah....liberating, lol

Yes, isn't it... ;)

> like how to get hardware drivers so it doesnt run snail sluggish ;)

Drivers for stuff that doesn't need proprietary drivers will already be there. Proprietary drivers can be had using the "Additional Drivers" utility. You need to be connected to the internet, of course.

---

