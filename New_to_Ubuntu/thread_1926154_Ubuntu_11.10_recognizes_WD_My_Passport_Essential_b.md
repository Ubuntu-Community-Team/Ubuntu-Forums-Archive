---
title: "Ubuntu 11.10 recognizes WD My Passport Essential but it doesn't show the files"
date: 2012-02-15
forum: New to Ubuntu
---

### Post by lfpoli on 2012-02-15
Hello Gentleman,

I am absolutely new on Ubuntu and linux world, and just installed Ubuntu 11.10 on my desktop computer.

Everything works fine: USB ports, USB flashdrives, printer.

Everything but my external HD which is a WD My Passport Essential 400 Gb.

In fact, Ubuntu OS shows it when I plug on the USB port, it shows that it is partially used (181,5 Gb), but it shows no file!

It just appears on Media/Mypassport and nothing inside! And this External HD is perfectly working on my notebook, which is windows xp.

I used lsusb and it shows

Bus 001 Device 008: ID 1058:0704 Western Digital Technologies, Inc. Passport External HDD

What is happening? All my backup files are on this external HD, which I intend to copy for the desktop computer's HD.

Can somebody help me?

---

### Post by bollucks on 2012-02-21
I have the same problem but I can't view my file son any operating system. Mac, Ubuntu, or windows. Mine is a 200 gig WD My Passport. All it shows instead is the smaller 20 MB filesystem and won't give me access to main HD. Western digital has made a crap product. Let me know if you find anything, I'll do the same.

---

### Post by fleamour on 2012-02-21
Listen closely, ear to case.  Can you hear a repeated clicking?

---

### Post by Jay Car on 2012-02-22
> **lfpoli said:**
> Hello Gentleman,

I am absolutely new on Ubuntu and linux world, and just installed Ubuntu 11.10 on my desktop computer.

Everything works fine: USB ports, USB flashdrives, printer.

Everything but my external HD which is a WD My Passport Essential 400 Gb.

In fact, Ubuntu OS shows it when I plug on the USB port, it shows that it is partially used (181,5 Gb), but it shows no file!

It just appears on Media/Mypassport and nothing inside! And this External HD is perfectly working on my notebook, which is windows xp.

I used lsusb and it shows

Bus 001 Device 008: ID 1058:0704 Western Digital Technologies, Inc. Passport External HDD

What is happening? All my backup files are on this external HD, which I intend to copy for the desktop computer's HD.

Can somebody help me?

If I remember correctly, the WD Passport series comes with its own backup software, which is for Windows (I think they may offer a Mac version too).

I've never used any of the bundled backup software that sometimes comes with ext. drives, generally the first thing I do with any new ext drive is plug it into my Ubuntu computer and delete all of the bundled software off of it and format it.  

I believe that Passport software may be at the heart of your problem. Though I don't know the exact process to use (the Passport software may be needed to get your files back), I'd be inclined to plug that drive into your Windows notebook and - if you have enough room on another drive - move those files out of the WD, then reformat it.  Maybe to NTFS, if you are going to be sharing files between Windows and Ubuntu. 

If you want to replace the old Passport software, search the Software Center for a backup program for Ubuntu. 

jcar

---

### Post by pootan on 2012-02-22
I have a Western Digital My Passport 750gig and my understanding is that the way WD formats the disks, they have a small entry at the start of the disk that can cause issues on unix -like systems. My problems were solved after I formatted the drive.

---

### Post by Jay Car on 2012-02-22
> **pootan said:**
> I have a Western Digital My Passport 750gig and my understanding is that the way WD formats the disks, they have a small entry at the start of the disk that can cause issues on unix -like systems. My problems were solved after I formatted the drive.

You described it much better than I did, but that's my understanding too.

---

### Post by Ji Ruo on 2012-02-22
Yes reformat it. The drive made that decision for me shortly after I bought one, when it became corrupted and inaccessible on both Windows and Linux. I reformatted the drive as NTFS and it has worked fine ever since.

---

### Post by lfpoli on 2012-02-22
> **fleamour said:**
> Listen closely, ear to case.  Can you hear a repeated clicking?

yes, definitely I hear a repeated clicking.

---

