---
title: "Dual Boot with Windows 8 on HP - Partitions"
date: 2013-06-14
forum: New to Ubuntu
---

### Post by AlexRich20 on 2013-06-14
Hello,

I have installed linux on various computers before but never as a dual boot where the windows 8 was already taking up too many partitions. I want to know how I can get rid of one of them so that I am able to install ubuntu. Its a hp g6 and last time I tried to dual boot by deleting and backing up a partition I was then unable to boot into windows on my old hp. Under disc management I have recovery partition (400mb), EFI system partition (260mb), c drive (439mb) and recovery (d) 25mb (this is listed twice for some reason).

Am I right in saying I could back up a recovery (which recovery is it to backup) and how?

Thanks !

---

### Post by oldfred on 2013-06-14
IF it is Windows 8 pre-installed you have the new gpt partitioning. Now the limit is 128 partitions, no 4 primary, extended nor logical partition issues.

So all you have to do is from inside Windows shrink the NTFS partition & reboot to let Windows run its chkdsk and make repairs.

But with Windows 8 there is a lot of other UEFI secure boot (Thanks Microsoft) issues. 
And if an UltraBook issues with Intel SRT and dual video. 

See my signature for more details.

---

### Post by Cheesemill on 2013-06-14
If this is a machine that came with Windows 8 pre-installed then it uses the new GPT system which doesn't have a 4 partition limit. It will also use UEFI which can be tricky to get working on some hardware. I suggest you start by reading this...

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by gordintoronto on 2013-06-14
There may be a Windows program to create a set of DVDs based on the recovery partition. At that point, you could blow away the recovery partition. (This was true for Windows 7 on my HP G62.)

---

