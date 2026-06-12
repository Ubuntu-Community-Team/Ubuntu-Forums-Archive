---
title: "No Boot device available..."
date: 2008-07-18
forum: New to Ubuntu
---

### Post by JHC130 on 2008-07-18
i just installed ubuntu on my computer, i had windows vista home premimum installed before that but after installation when it told me to take out the disk and press enter it restarted.Now when it boots up it stops at a screen that says No Boot device available then tells me to press f1 to retry boot, f2 fopr setup utility.I press f1 and its tells me the samething.Can someone help me out with this one?......i really want to test out ubuntu.Thanks in advance.

---

### Post by overdrank on 2008-07-18
> **JHC130 said:**
> i just installed ubuntu on my computer, i had windows vista home premimum installed before that but after installation when it told me to take out the disk and press enter it restarted.Now when it boots up it stops at a screen that says No Boot device available then tells me to press f1 to retry boot, f2 fopr setup utility.I press f1 and its tells me the samething.Can someone help me out with this one?......i really want to test out ubuntu.Thanks in advance.

Hi and please do not make multiple threads on the same issue
[http://ubuntuforums.org/showthread.php?t=862986](http://ubuntuforums.org/showthread.php?t=862986)
You could have just bumped your thread ( by posting bump in your other thread) to renew the attention.
Ok could you give us some system specs?
 The system will not boot to Vista or Ubuntu correct? 
You may try and install the grub again.
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by JHC130 on 2008-07-18
> **overdrank said:**
> Hi and pleas do not make multiple threads on the same issue
[http://ubuntuforums.org/showthread.php?t=862986](http://ubuntuforums.org/showthread.php?t=862986)
You could have just bumped your thread ( by posting bump in your other thread) to renew the attention.
Ok could you give us some system specs?
 The system will not boot to Vista or Ubuntu correct? 
You may try and install the grub again.
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

sorry about that.I have a Dell XPS 400 i was running vista but i decided to install ubuntu so i did i followed the instructions then when installation was complete it told me to take out the disk and press enter to restart, so i did.Then durning boot up a screen came up that did when i had vista running.It said press f1 to continue or f2 to run the setup utility.But now when i press f1 it says selected boot device is not available.
I dont know what to do from there.Sorry again for making multiple threads i just really want to get on ubuntu.

---

### Post by overdrank on 2008-07-18
> **JHC130 said:**
> sorry about that.I have a Dell XPS 400 i was running vista but i decided to install ubuntu so i did i followed the instructions then when installation was complete it told me to take out the disk and press enter to restart, so i did.Then durning boot up a screen came up that did when i had vista running.It said press f1 to continue or f2 to run the setup utility.But now when i press f1 it says selected boot device is not available.
I dont know what to do from there.Sorry again for making multiple threads i just really want to get on ubuntu.

Ok you may try as I suggested my first post with installing the grub.

---

### Post by JHC130 on 2008-07-18
ok i will try it but can you tell me what it is and what it does?

---

### Post by overdrank on 2008-07-18
> **JHC130 said:**
> ok i will try it but can you tell me what it is and what it does?

Ok if you are using Ubuntu it uses the Grub to handle the boot order for more that one OS. So the grub is the first thing you see after the bios start. Did you leave Vista intact for a dual booting with Ubuntu?

---

### Post by philinux on 2008-07-18
To boot a hard drive there need to be an MBR . Master Boot Record

This is GRUB. It boots the system. Hence bootable device being your Hard Drive.

Without grub no ubuntu. It must have failed to get installed.

---

### Post by lethalswc on 2009-07-25
Hi I am having the a similar problem. I am running a Dell E510 Pentium D with 2 SATA II drives and factory RAID. I wiped the SATA 0 drive using killdisk and then installed ubuntu. All seemed to go well until i was prompted to restart. Then....no boot device available. When I enter the BIOS it looks like it recognizes both SATA drives but when i check in boot order the sata drive option says "not present". Both SATA drives are turned on in BIOS.

I have tried to installed grub again according to the post

"You may try and install the grub again."
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

and have also tried to restore grub using the SGD.

(from supergrubdisk.org)

I am not sure what the problem is and have run out of options other than posting here and feeling dumb :(.

Please help!!!

---

