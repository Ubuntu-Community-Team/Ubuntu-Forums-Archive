---
title: "Two Quick Noobie Questions"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by Ninelivez on 2008-05-19
Hey all, I'm finally taking the jump to Ubuntu and I have a few questions.

1. Can I access my Windows Partition in Ubuntu?

I recently got some bad malware on my Windows PC and the only thing stopping me from just overriding that windows install with Ubuntu is my music. Most of it is hard to find and I haven't backed it up yet. I can't even transfer it to a few DVDs to just put on the Ubuntu Partition. So I just wanted to install Ubuntu on my other HD, boot it up, transfer my music to it from the Windows Partition, then just delete the Windows Partition. 

2. Do I need to swap/take out my other HD when installing?

My "Main" HD right now has windows on it, I plan on installing Ubuntu on my other HD which just has some random stuff on it, nothing I want to keep. Do I need to take out or swap either drive when I install Ubuntu? Or can I specify what HD I want it to install on and thats it. 

Thanks a lot to whoever answers these. I hope this all made sense, I'm just a little tired from work today and now I have to come home to new PC acting up. Thanks again!

---

### Post by sdennie on 2008-05-19
1) Yes, it should be perfectly readable from Ubuntu.

2) You shouldn't need to take out any disks while installing.  Just make sure you choose the right disk during the installation process.  One thing you may have to do is set your secondary disk as the boot disk in BIOS if you plan to later re-install Windows on the first disk.  However, it's been a while since I've installed a 2 hard drive system so I'm not positive about that last step.

---

### Post by Ninelivez on 2008-05-19
Ah ok. Thanks a lot for the info. I'll probly have to go into the BIOS to set the second drive as the primary boot device, but thats not a problem. And "phewwwww" I was worried that I wouldn't be able to transfer my music, that atleast is going to make this process SO much easier.

Thanks again for your help, really appreciate it.

---

### Post by bferd on 2008-05-19
If you install the latest version of Ubuntu it checks your other partitions for operating systems. If you already have Windows installed, Ubuntu will automatically add it to a boot menu during installation. You will have a choice to select Ubuntu or Windows to boot to when you turn your computer on.

---

### Post by bferd on 2008-05-19
You don't have to switch the bios. Ubuntu uses a boot menu program called grub to handle multiple operating systems. Grub is intalled on the MBR of your boot drive

---

### Post by sdennie on 2008-05-19
> **bferd said:**
> You don't have to switch the bios. Ubuntu uses a boot menu program called grub to handle multiple operating systems. Grub is intalled on the MBR of your boot drive

Right.  But, I believe that means that if you install it on a two disk machine, it will install grub on the Windows disk.  If you later re-install Windows on that disk, I believe it will blast grub.

---

### Post by nick_h on 2008-05-20
> **vor said:**
> Right.  But, I believe that means that if you install it on a two disk machine, it will install grub on the Windows disk.  If you later re-install Windows on that disk, I believe it will blast grub.

If you overwrite grub it is very easy to re-install it - [How to install Grub from a live Ubuntu cd](http://ubuntuforums.org/showthread.php?t=224351)

---

