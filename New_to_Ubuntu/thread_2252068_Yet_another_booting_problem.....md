---
title: "Yet another booting problem...."
date: 2014-11-08
forum: New to Ubuntu
---

### Post by Yusuf_Ibrahim_Rama on 2014-11-08
I used Ubuntu 14.04 and then I upgraded to Ubuntu 14.10 on my Acer Aspire E 14 laptop, yet both versions posed me the same problem: booting issues. Ubuntu wouldn't boot normally and I had to choose booting via the recovery mode when asked by the GRUB-thing, but this was not even a solution. The chance of successfully booting from recovery mode was low as well: I could roughly conclude that it had a 1/5 chance of booting successfully from recovery mode and the rest 4/5 chance would have the screen stuck on a text saying "Mapper loaded", and thus I had to force-restart the laptop.

Now I am using Linux Mint. I thought switching to this OS would end the problem, and yet I found that Linux Mint had quite the same problem. But since I like Ubuntu more than Linux Mint, I hope somebody can tell me what's wrong and how I should fix it. I really want to switch back to Ubuntu, but I want to switch back to it without getting troubled anymore.

Oh, and I believe that the issue has something to do with my graphics card or something? Then my graphics card is Intel Corporation ValleyView Gen 7.

---

### Post by westie457 on 2014-11-08
Welcome Yusuf_Ibrahim_Rama if the problem is really your graphics card maybe this slightly aged link will be of some use to you. [http://forums.linuxmint.com/viewtopic.php?f=59&p=825687](http://forums.linuxmint.com/viewtopic.php?f=59&p=825687)

As for it sticking at 'Mapper loaded' I have absolutely no idea on how to fix if that is the problem.

---

### Post by oldfred on 2014-11-08
/device/mapper... is RAID or LVM.
Did you install with full drive LVM or encrypted full drive which also is a full drive LVM?
LVM is a bit more advanced.

       LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)

---

### Post by Yusuf_Ibrahim_Rama on 2014-11-09
> **oldfred said:**
> /device/mapper... is RAID or LVM.
Did you install with full drive LVM or encrypted full drive which also is a full drive LVM?
LVM is a bit more advanced.

Yes, I did install Ubuntu with LVM since the description was tempting, without really knowing what I was doing. Now I have reinstalled Ubuntu without checking the LVM option and now it can boot normally. Problem solved, then. Thanks.

---

