---
title: "[SOLVED] Problem resuming from suspend"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by TadeoDiaz on 2008-06-03
I am running 8.04 Hardy on a Lenovo 3000 V100 and every time I suspend my computer freezes upon trying to wake up and I have to forcedly shut down. I did a few searches online but i am completely new to linux and couldn't find a solution to this. Can anyone help?

---

### Post by ZabiGG on 2008-06-04
Hi,

This appears to be a bug ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/226279](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/226279))

On your startup screen, can you launch the .16 version of the kernel and see if your problem is solved by using that previous version?

---

### Post by TadeoDiaz on 2008-06-04
Unfortunately the problem persists with 8.04.16

---

### Post by ZabiGG on 2008-06-04
In the bug report, there are instructions to move on to version 19 as a corrective. But I would not attempt to follow those due to my own lack of technical knowledge... I'm sorry I can't be more help on this. :(

---

### Post by TadeoDiaz on 2008-06-04
It's ok, thanks for your help anyways

---

### Post by TadeoDiaz on 2008-07-01
I stumbled upon instructions on how to upgrade to the 2.6.24-19 generic kernel version online and went through the steps. The upgrade seemed to help with the suspend problem but once I restarted the version was not available to boot up with in the menu so I was back to not being able to suspend. Does anyone know how to make the upgraded kernel version available on the startup menu?

---

### Post by TadeoDiaz on 2008-07-01
Oh and these are my current ACPI settings

ACPI_SLEEP=true
ACPI_HIBERNATE=true
ACPI_SLEEP_MODE=mem
MODULES="ipw4395"
MODULES_WHITELIST=""
SAVE_VBE_STATE=true
VBESTATE=/var/lib/acpi-support/vbestate
POST_VIDEO=false
# SAVE_VIDEO_PCI_STATE=true
USE_DPMS=true
# RADEON_LIGHT=true
# DOUBLE_CONSOLE_SWITCH=true
HIBERNATE_MODE=shutdown
LOCK_SCREEN=true
# DISABLE_DMA=true
# RESET_DRIVE=true
STOP_SERVICES=""
RESTART_IRDA=false
ENABLE_LAPTOP_MODE=true
SPINDOWN_TIME=12

---

### Post by TadeoDiaz on 2008-07-09
Bump

I reinstalled Ubuntu from CD, suspend works in 2.6.24-16 generic but once you upgrade to 2.6.24-19 generic suspend no longer works, even if you chose 2.6.24-16 generic.

---

### Post by ZabiGG on 2008-07-10
That is strange... When you start up your computer, from the GRUB, you should be able to select kernel 16 and run with kernel 16 if you want. Maybe it just booted the first choice, which would be kernel 19, before you had time to change your boot choice to kernel 16?
 
As for your suspend issues, it might be related to your graphics card. If you have an ATI and are not using the latest driver by ATI (which has to be installed from source, so I wouldn't quite suggest it for now), it might explain that.
 
Z.

---

### Post by TadeoDiaz on 2008-07-10
I've tried starting in the 19-generic and the 16-generic in the GRUB and the suspend problem is still present in both. 16-generic only worked before the upgrade to 19-generic.

My laptop is running integrated graphics (Intel 950 I believe). Is there a way to check if that is the problem?

---

### Post by ZabiGG on 2008-07-11
I found [this thread]("http://ubuntuforums.org/showthread.php?t=802232&highlight=intel+suspend"). It appears to be a problem with a lot of laptops, including ones with the Intel card. Unfortunately, there appears to be no way of fixing it at this time. You may want to deactivate hibernating until a solution is found. There are instructions to do so in that thread.

I would advise you not to use the user-contributed patch presented in the last post. Unless you understand code, it is not a good idea yet. Wait until you've studied a while on the subject and compiled (and uninstalled, and purged) a few applications from trusted sources before you use "home-made" programs or scripts.

Cheers,

Z.

---

### Post by TadeoDiaz on 2008-07-11
> **ZabiGG said:**
> I found [this thread]("http://ubuntuforums.org/showthread.php?t=802232&highlight=intel+suspend"). It appears to be a problem with a lot of laptops, including ones with the Intel card. Unfortunately, there appears to be no way of fixing it at this time. You may want to deactivate hibernating until a solution is found. There are instructions to do so in that thread.

I would advise you not to use the user-contributed patch presented in the last post. Unless you understand code, it is not a good idea yet. Wait until you've studied a while on the subject and compiled (and uninstalled, and purged) a few applications from trusted sources before you use "home-made" programs or scripts.

Cheers,

Z.

I've actually had no problems Hibernating (current method used for standby), the only issue with that is that I don't want to have to hibernate and then wait for the computer to start up between classes.

My previous Ubuntu installation was what I considered my "draft" installation. I installed it tried a bunch of things (including fixes to suspend) and once I realized that I've changed too much and the apps that I will actually used I wiped the hard drive and proceeded with a fresh installation. I guess my best option is to wait for a fix in the system update, I've just been a little impatient :) But hopefully it will come out before the summer ends. Thanks for your help ZabiGG

---

### Post by TadeoDiaz on 2008-09-11
Solved with updates! Freakin' SWEET!!

---

### Post by krede21 on 2008-09-24
I'm still having the suspend/hibernate-problem on my Lenovo 300 v100, which kind of upgrade solved the problem?

---

### Post by TadeoDiaz on 2008-09-24
> **krede21 said:**
> I'm still having the suspend/hibernate-problem on my Lenovo 300 v100, which kind of upgrade solved the problem?

Im not exactly sure what update solved it but I noticed this shortly before it resolved:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/243967](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/243967)

(look at the last two posts)

Hope it works

---

### Post by krede21 on 2008-09-25
Success!!

This line did it:

```
echo 'SUSPEND_MODULES="ehci_hcd"' | sudo tee /etc/pm/config.d/lenovo3000v100
```

Thank alot.!

---

