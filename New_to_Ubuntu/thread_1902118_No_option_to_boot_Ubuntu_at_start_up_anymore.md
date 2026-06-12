---
title: "No option to boot Ubuntu at start up anymore"
date: 2011-12-30
forum: New to Ubuntu
---

### Post by Jp3isme on 2011-12-30
I have been using ubuntu for a while now and for the most part i thought i was pretty good at installing and running operating systems and stuff and well, i guess not. My hard drive had two partitions, one for windows 7 and one for ubuntu and usually it'd give me the option to boot ubuntu. I decided to reinstall windows 7 because of registry errors and such but when i did so the option to but ubuntu was gone so i assumed it had over written that partition. So, i ran the live CD and when i clicked install and went through the first two steps it told me that ubuntu 11.10 was already installed. If that partition is still there I'd like to be able to access it because for one, the live CD is ubuntu 11.04 and for two, i don't want to lose my files, so is there any way i can still access this partition? Any help would be greatly appreciated, thanks.

---

### Post by Ctrl-Alt-F1 on 2011-12-30
Ubuntu is still installed as is Windows 7.  However Windows has installed it's own bootloader that has overwritten GRUB, which is the bootloader that comes with Ubuntu and is what you usually use to select your operating sytem.

Here's the run down for how to reinstall Grub:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Jp3isme on 2011-12-30
Thanks! i will try this.

---

