---
title: "how to dual boot XP &amp; Ubuntu on C drive and install Ubuntu on D drive (2nd harddrive)"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by imgreen on 2008-04-27
hey guys, 

i am still very new to this, so any help would be really appreciated. i have a custom PC that was given to us, it has 2 120gb harddrives, the C drive has microsoft, i'm planning to dual boot it with XP and Ubuntu. also, the 2nd hard drive (D drive) i want to install either Ubuntu or Kubuntu. how can i do the install on the Blank D drive? i have done a dual boot for my laptop before. i just need to learn how to fully install it on the D drive. i really appreciate your time and help in advance. thank you.....

---

### Post by kai60 on 2008-04-27
No worries mate.

So let me get this straight. You have Windows already installed on your first hard drive and you want to dual boot your computer with a Linux distro, which you want to install on the second hard drive. Is that about right?

---

### Post by CloudFX on 2008-04-27
You shouldn't need to worry about which drive letter Ubuntu is installed on.  It won't make a difference, and D:\ is usually taken up by your CD Drive.  

For more information on dual-booting, check out the Documentation here: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Don't be afraid to post for any more assistance!  Installing Ubuntu for the first time is always tricky thing to do!  But it is much easier than you think.

---

### Post by imgreen on 2008-04-28
thanks guys, 

i know how to dual boot with XP and Ubuntu. i did it on my laptop. i just need to know how to install JUST either Kubuntu or Ubuntu on the 2nd drive. Or i even thought of maybe dual booting Kubuntu and other distro. so i would have the 1st drive will have XP & Ubuntu, 2nd drive either JUST kubuntu or dual boot Kubuntu and other distro. so i can kinda try different distros.

---

### Post by schauerlich on 2008-04-28
When you install, make sure that you're installing to /dev/hdb or /dev/sdb (it depends on what type of hard drive you have). This should install it to the second hard disk, but double check the location from your first Ubuntu install. From there, just tell the live installer to use the whole disk. As long as you told it the right disk, you shouldn't have any problems. Back up just in case, though. It's always a good idea.

---

