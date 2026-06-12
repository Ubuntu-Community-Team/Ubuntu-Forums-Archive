---
title: "[SOLVED] Strange installation problem"
date: 2008-08-07
forum: New to Ubuntu
---

### Post by shr2004 on 2008-08-07
Hi,

I have a strange Ubuntu installation problem.
I already installed Ubuntu hardy in a laptop dual boot with Vista and running very nicely. So I know the installation steps.
I have a Dell machine, AMD64 bit and a spare hard disk, 20GB (bit old) where I want to install Ubuntu. 
First I tried to use live 64bit DVD to check and delete that spare hard disk. But the live CD was asking username and password, so I can't use that. For your info, I have unplugged the existing HDD from the dell machine and just plugged in the spare HDD.

Then I want to do some experiments. By using Gparted Live CD I deleted the spare hard disk and then without running live, I installed ubuntu from the DVD. The installation went well and finally ask to reboot the machine.
After booting the machine, the login screen comes and I entered username and password. 
Here come the surprise, it plays the jugle sound and then blank screen and then come back to log in screen again asking the uname and pass.
If I enter wrong username and pass, then ubuntu will tell that. But its not that, it cannot go through and asking the uname and pass again and again. 
Anyone has any idea why this is happening. If there is any thread that solved it then please give me the link. Is the problem related to the installation DVD (or, recording speed)? I will burn a live CD and try again tomorrow. I had already tried with another live DVD from where I installed Ubuntu in my laptop but that live DVD also asking uname and pass for this machine.

Thanks

---

### Post by phidia on 2008-08-07
It appears to have happened before there's a solved thread [here]("http://ubuntuforums.org/showthread.php?t=872376&highlight=login+screen+loop") on that problem.

---

### Post by LowSky on 2008-08-07
actually that link isn't actually solved as the OP went back to Windows...

you might need to fix a few drivers issues, on booting hit escape to get to Grub menu and choose recovery mode. from there try to run the fix video drivers.

---

### Post by shr2004 on 2008-08-07
> **LowSky said:**
> actually that link isn't actually solved as the OP went back to Windows...

you might need to fix a few drivers issues, on booting hit escape to get to Grub menu and choose recovery mode. from there try to run the fix video drivers.

Thanks for the quick reply....I'll try it the first thing in the morning. The machine has ATI graphics card, that might cause the problem. I will post whatever the outcome is. Fingures crossed.

Cheers

---

### Post by shr2004 on 2008-08-08
I have somehow get the solution, From another thread I found that uninstalling the ATI driver and the reinstall might solve the problem. So here what I did,
1. From synaptic, remove xserver-xorg-video-ati
2. Reboot.
Now I can pass through the log in process. Although it seems working I again installed the ati driver that I uninstalled earlier by using synaptic. 
My main problem is solved. Thanks to all the posters.

Ooh, I have not mentioned how went to synaptic where I was having problem in login. During login, from the "Options" in lower left in the screen, I changed the session to Gnome FAILSAFE, which allows to login in a lower graphics mode, from there I did the tricks.

---

