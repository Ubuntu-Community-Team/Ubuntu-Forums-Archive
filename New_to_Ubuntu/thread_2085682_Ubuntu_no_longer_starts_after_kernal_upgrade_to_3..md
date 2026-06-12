---
title: "Ubuntu no longer starts after kernal upgrade to 3.2.0-33"
date: 2012-11-18
forum: New to Ubuntu
---

### Post by ohnoplus on 2012-11-18
Hello,
     Last time I was using my computer I installed updates which required a restart.  After shutting down and starting up my computer I found that it hung on start up after the grub2 screen.  No ubuntu logo with the little white dots that turn red.  I have found that I can start the computer if I select previous linux versions and run the 3.2.0-32 version.
     I suspect this means that last time I ran upgrades I upgraded to a newer kernal which doesn't work with my system.
    I was wondering if anyone has advise about either 1) reinstalling or fixing the new kernal so it works this time, or failing that 2) getting the computer to default from starting from the old kernal that works.
    Oh, I'm running Ubuntu 12.04.  And am happy to provide any additional information about my system.
Thanks for any help.

---

### Post by ohnoplus on 2012-11-18
I was able to revert to the old kernal following these instructions.

[http://askubuntu.com/questions/192033/after-update-the-kernel-ubuntu-12-04-wont-boot](http://askubuntu.com/questions/192033/after-update-the-kernel-ubuntu-12-04-wont-boot)

---

### Post by Aaron Christianson on 2012-11-18
I'd suggest booting to the old kernel and reinstalling the new kernel.

Similar thing happened to be me a few times, but the last time was years ago.

---

### Post by Peripheral Visionary on 2012-11-19
I've never had that problem but I always get scared when Update Manager lists a new kernel.  My question is, since I use auto-logon instead of logging in every time I turn my computer on, I never see that grub screen. What should I do if and when the next kernel update won't boot?  Should I stop using auto-logon just in case, or will it go to the grub screen if it fails to automatically log on?

---

### Post by martinhr on 2012-11-19
> **Peripheral Visionary said:**
> I've never had that problem but I always get scared when Update Manager lists a new kernel.  My question is, since I use auto-logon instead of logging in every time I turn my computer on, I never see that grub screen. What should I do if and when the next kernel update won't boot?  Should I stop using auto-logon just in case, or will it go to the grub screen if it fails to automatically log on?

Grub2 is something different from logon screen. Grub2 helps your computer to boot up,do some stuff like loading kernel,init and so on.
When i update my ubuntu it always leave the previous kernel in "Previous" section in grub2 menu.
If new kernel works perfect,you can find the old one in synaptic and remove it.
:)

---

### Post by Peripheral Visionary on 2012-11-19
> **martinhr said:**
> Grub2 is something different from logon screen. Grub2 helps your computer to boot up,do some stuff like loading kernel,init and so on.
:)

I never see a "Grub screen." Because I auto-logon, I only see the little blue Xubuntu screen for a few seconds, then my desktop.  My question is, **will the Grub screen appear if Xubuntu won't boot up automatically** after one of those kernel upgrades?  I know I could just quit using auto-logon and it wouldn't be an issue. But I prefer auto-logon and I'd rather not give my computer password to my parents, lol. If they need to use my computer, I'd rather that they just turn it on and use it.

Thanks!

---

### Post by llmunro on 2012-12-08
I think I might have a similar problem to that mentioned in the original post--after today's kernel upgrade (not sure how to check what kernel version?), my Samsung laptop freezes on the login screen and nothing short of manually killing it with the power button will work.

I booted into an older kernel, but is there a way to get rid of the most recent kernel version and revert to an earlier one?  Is booting into an older kernel version going to damage anything?  Will future kernel upgrades fix or bork things further?

This is the first time this has happened to me with ubuntu.  I'm backing up to an external drive right now in case of anything else bad happening.

Thanks for any thoughts and suggestions about this.
Best,
Lisa

---

### Post by GameX2 on 2012-12-08
Glad to see I'm not alone with problems related to the 3.2.0-33 Kernel.

I'm not sure if this is related, but on the 3.2.0-33 kernel, Ubuntu randomly rebooted 3 times.  No warning, instant reboot.  I'm pretty sure this problem occured after the new kernel installation.

I've chosen to boot on the 3.2.0-32 kernel by default, and Ubuntu do not reboot randomly anymore, now.
Weird.

---

