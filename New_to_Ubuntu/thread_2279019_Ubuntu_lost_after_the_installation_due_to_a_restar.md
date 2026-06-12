---
title: "Ubuntu lost after the installation due to a restart"
date: 2015-05-20
forum: New to Ubuntu
---

### Post by karthik24 on 2015-05-20
Hi Ubuntians,

I was trying to install Ubuntu 14.04 LTS in my Intel i3 4GB DDR3 500GB Desktop. I have done with the installation. After the installation process (Screen showed Successfully installed) it was rebooting, but I forgot to unplug my USB so it again went to the installation. I restarted the computer and unplugged the USB in this time before boot up. Then the computer did not boot up. No error messages on the screen. I had Windows 7 on the same HDD and I reinstalled Windows 7 after this issue. Windows is working fine now.  My question is, I just rebooted the computer once again after the installation, Ubuntu lost. Why does Ubuntu this much unstable and weak or did I make a Fatal error?

---

### Post by leunam12 on 2015-05-20
There was a problem with the installation probably because your motherboard uses UEFI (that is my guess). Read the UEFI installation guide.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by Vladlenin5000 on 2015-05-20
You did a few errors but probably nothing fatal. 
First one was when inadvertently booted again from the USB. That alone wouldn't have started any new installation unless you said so (and you shouldn't have). Letting it go to the usual live session and simply shutdown or reboot wouldn't have changed a bit in what was installed before.
Then you proceeded to reinstall Windows and you probably wouldn't have to. But you did anyway and now are complaining about what should be expected?? And blaming Ubuntu for being "unstable"?
BTW, Ubuntu *probably* isn't lost unless you selected the wrong option when reinstalling Windows (you probably did).

---

### Post by karthik24 on 2015-05-20
Hi Vladlenin5000,
I guess, my words were not clear. Sorry for that. I tried the Ubuntu installation, it ended with failure. The computer was not able to Boot on Ubuntu. I did not have much time to do the installation once again and so I installed Windows 7 back to the computer as I need to do my daily works.

---

### Post by Vladlenin5000 on 2015-05-20
> **karthik24 said:**
> After the installation process (Screen showed Successfully installed) it was rebooting, but I forgot to unplug my USB so it again went to the installation.
This is from your OP, then you say...
> **karthik24 said:**
> I guess, my words were not clear. Sorry for that. I tried the Ubuntu installation, it ended with failure.

Indeed, your word were and are anything but clear. Do you wanna help or just vent out your frustration? If the latter, you already did. Anything else we can help with? If the former then first of all describe how have you tried to install, partitions, etc. and some more information about the hardware itself.

---

### Post by karthik24 on 2015-05-21
> **karthik24 said:**
> Hi Ubuntians,

I was trying to install Ubuntu 14.04 LTS in my Intel i3 4GB DDR3 500GB Desktop.** "I have done with the installation. After the installation process (Screen showed Successfully installed) it was rebooting, but I forgot to unplug my USB so it again went to the installation. I restarted the computer and unplugged the USB in this time before boot up. Then the computer did not boot up." **No error messages on the screen. I had Windows 7 on the same HDD and I reinstalled Windows 7 after this issue. Windows is working fine now.  My question is, **"I just rebooted the computer once again after the installation, Ubuntu lost." **Why does Ubuntu this much unstable and weak or did I make a Fatal error?

Please check quoted text, I hope this means the installation was not successfull on the whole.

---

### Post by buzzingrobot on 2015-05-21
As Vladlenin said, if the original installation was done correctly, it would not have been affected when you rebooted by mistake into the USB. We've all done that. You should have shut down the machine, removed the USB, and rebooted. 

Reinstalling Windows may well have altered the bootloader on the disk, preventing Ubuntu from being shown as an available OS. (Windows installs with the assumption it is the only OS on the machine.) In this case, the Ubuntu system remains in place. You might research a tool called Boot Repair, which may help you fix the bootloader so you can boot Ubuntu. (I don't dual boot with Windows, so I have no experience with Boot Repair.)

---

### Post by karthik24 on 2015-05-21
Thank you so much. I will try the Boot Repair tool and let you know the status.

---

