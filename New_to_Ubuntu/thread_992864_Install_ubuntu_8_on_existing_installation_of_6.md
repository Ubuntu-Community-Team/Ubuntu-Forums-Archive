---
title: "Install ubuntu 8 on existing installation of 6"
date: 2008-11-25
forum: New to Ubuntu
---

### Post by kaprasanna on 2008-11-25
Hello,

I have installed Ubuntu 6 (gnome) on my IBM laptop along with Windows XP.(Dual)
When I turn on my laptop I get GRUB loader and some 3-4 choices of Ubuntu and then Windows.
I had done this installation a year or so ago.
There is a 5gb partition especially for this installation on my hard drive.
Now I have the installation cd of Ubuntu 8 with me.
I don't know how to install Ubuntu 8.
When I insert the cd and restart my machine I get the same options as above and when I select Ubuntu it boots to my normal Ubuntu. And when I ask my machine to boot from cd same thing happens.

I want suggestion about these :
Do I have to remove the current installation?
Can I upgrade (automatically) to 8?
How do I make sure I don't loose the data?
How do I install Ubuntu 8?

Thanks.

---

### Post by go_beep_yourself on 2008-11-25
It sounds like the cd isn't being booted. You need to go into your computers bios settings to fix this. Usually it's done by holding the del key when your system first boots up. Then you need to change the boot order, so the cd drive comes before the hard drive. Or if your computer supports it, you can hold down a key to get a boot menu when your computer first boots up. With that, you can choose to boot from the cd drive instead of the hard drive. On my computer, it is done by holding f8, but I've seen other f keys used on different computers as well.

---

### Post by go_beep_yourself on 2008-11-25
> **kaprasanna said:**
> 
Do I have to remove the current installation?
Can I upgrade (automatically) to 8?
How do I make sure I don't loose the data?
How do I install Ubuntu 8?

[https://help.ubuntu.com/community/Installation/UpgradeFromOldVersion](https://help.ubuntu.com/community/Installation/UpgradeFromOldVersion)

---

### Post by kaprasanna on 2008-11-25
> **go_beep_yourself said:**
> Usually it's done by holding the del key when your system first boots up. Then you need to change the boot order, so the cd drive comes before the hard drive. 
In my laptop I need to use Enter key to choose the boot order.
This has worked for me in the last 4 years of my laptop's possession.
When I use it for this Ubuntu cd, the same thing happens. (Boots to current installation of Ubuntu).

---

### Post by MeURi on 2008-11-25
No, go_beep_yourself meant that you have to enter the bios settings. Pressing DEL, F2, F8, or whatever, has to be done _before_ you get the GRUB menu.

Since you always get GRUB, it means that your computer boots from hard drive first.You have to change the behavior so that it boots from cd/dvd-rom first.

Also, check out the link posted. And, as a side note, I always prefer doing clean installations, backing up sensible data and configurations before wiping my partitions :-)

---

### Post by kaprasanna on 2008-11-25
MeURi,

> **MeURi said:**
> No, go_beep_yourself meant that you have to enter the bios settings. Pressing DEL, F2, F8, or whatever, has to be done _before_ you get the GRUB menu.

I know. I have tried that with failure.

> **MeURi said:**
> And, as a side note, I always prefer doing clean installations, backing up sensible data and configurations before wiping my partitions :-)

As this is the 1st time I am 'trying' to upgrade to latest version, I didn't know what is the normal practise. 
So, thanks so much for encouraging me to do a clean install.

---

### Post by evilkastel on 2008-11-25
agree, GRub should not be displayed when you try to boot from cd. The link is quite self explanatory. And definitely you should make a clean install, backing up your data, since such a big upgrade is likely to go badly.

---

### Post by kaprasanna on 2008-11-25
> **evilkastel said:**
> And definitely you should make a clean install, backing up your data, since such a big upgrade is likely to go badly.

Yes, I understand.
Thanks.

---

### Post by go_beep_yourself on 2008-11-25
If you have your bios configured to boot from cd/dvd before trying the hard drive and it still doesn't happen, then I suspect something is wrong with the cd, and maybe you should burn it again at a slow speed.

---

