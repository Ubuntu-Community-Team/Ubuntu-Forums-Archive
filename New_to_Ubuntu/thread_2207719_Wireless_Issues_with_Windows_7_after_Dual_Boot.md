---
title: "Wireless Issues with Windows 7 after Dual Boot"
date: 2014-02-24
forum: New to Ubuntu
---

### Post by MentheAddikt on 2014-02-24
Hi, I was wondering if anyone could help me. I've searched the forums extensively, and cannot find a solution to my problem.

When I try to dual-boot my laptop with Windows 7 and Ubuntu 12.04 LTS, it works perfectly except that the wireless on the Windows 7 side stops working. All I've seen on the forums is that the linux side stops working, but that is not my issue.

My laptop:
Gateway M-6332 (Part Number 2906081R)
Intel Premium Dual CPU T2390
Intel GMA X3100
Marvell MC868P

Link to specs - [http://support.gateway.com/s/Mobile/2008/Avalon/2906081R/2906081Rsp2.shtml](http://support.gateway.com/s/Mobile/2008/Avalon/2906081R/2906081Rsp2.shtml)

Does anyone have any thoughts or solutions? Thanks!

---

### Post by Bucky Ball on 2014-02-24
Welcome to the forums. Well, this can have nothing to do with Ubuntu if you are running an actual dual-boot as both are on separate partitions. When you are booted into Windows, Ubuntu has nothing to do with it and vice versa.

If, on the other hand, you are running Wubi, i.e. Ubuntu inside Windows, that is another matter and is NOT a dual-boot. It is Wubi. If you are running Wubi I'd reconsider. It is no longer supported, hardly anyone here used it when it was so scant info, and a real dual-boot is the best option.

---

### Post by MentheAddikt on 2014-02-24
Thanks for responding!

It is an actual dual-boot, not Wubi.

I was wondering if using another distro of linux would fix that issue, or if it's solely to do with windows being finicky. I'm not that great with using scripts or the terminal, so I'm not sure if it something withing ubuntu that is messing the windows side up.

---

### Post by Bucky Ball on 2014-02-24
> **MentheAddikt said:**
> ... I'm not sure if it something withing ubuntu that is messing the windows side up.

That would be nigh on impossible. Like I say, when you boot Windows, Ubuntu is asleep. Windows can't even mount EXT* drives. There are no configuration files or anything else shared between the two. You may as well have them running on two different physical machines. You might be able to access Windows NTFS or FAT partitions from Ubuntu, but that's about it. Unless you intentionally and manually do something to screw up the Windows internet config from the Ubuntu side, it is not the issue.

This is 99.9% a Windows problem. Did you change anything on your router to get Ubuntu wireless/cable internet to work? If so, that could be causing an issue.

---

