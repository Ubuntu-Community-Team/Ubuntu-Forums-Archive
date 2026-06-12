---
title: "Accessing motherboard RAID possible?"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by w2irt on 2008-07-22
Hi all,
Pre-absolute-beginner here (i.e. haven't even DL'd the distro yet), and I have a couple of "can I even do this" questions.

I have a 5 year old XP Pro box that's just too bloated to live. It's current life function is a file and FTP server.

My goal is to wipe the OS and have this box do the job right with Linux. The thing is, the stuff I need to access is currently on a motherboard-installed RAID array, which is formatted with NTFS. Can I bring this over after reformatting the OS (the OS is on a separate physical HDD)?

I need to be able to read from and write to this RAID-1 array from both Macs and PCs, and set up an FTP server similar to what I have running now.

Is what I've proposed somewhat viable? How can I get Ubuntu to "see" the NTFS hardware RAID? The contents of this array consists of my life's work, all my music and every digital photo I've ever taken, thus "doing it right" and knowing what to do when it inevitably throws a wobbly are very important for me.

Any/all suggestions would be greatly appreciated.

---

### Post by northern lights on 2008-07-22
> **w2irt said:**
> The thing is, the stuff I need to access is currently on a motherboard-installed RAID array, which is formatted with NTFS. Can I bring this over after reformatting the OS (the OS is on a separate physical HDD)?
Yes, Ubuntu reads from and writes on ntfs partitions. Yes, it can handle RAID.

> **w2irt said:**
> I need to be able to read from and write to this RAID-1 array from both Macs and PCs, and set up an FTP server similar to what I have running now.
Not a problem. Linux is imho the best OS to run any server from.

Long story short:

Wipe the system hdd, setup ubuntu, reconnect the RAID drives, setup a server. It's pretty straight forward.

---

### Post by w2irt on 2008-07-22
> **northern lights said:**
> 

Wipe the system hdd, setup ubuntu, reconnect the RAID drives, setup a server. It's pretty straight forward.

OK, it's pretty straightforward for anyone familiar with non-M$ OSes :) Remember: rank n00b here :) Even playing with my wife's Mac gives me fits.

If I understand your post, it's simply a matter of downloading Ubuntu and loading it on the system drive, and it will see the NTFS hardware RAID without my needing to do anything more? If so, great. If not....hmmm.

Where can one learn how to setup the box as a server and to establish an FTP server on it? I'm an old-phart with only M$ experience, so please be gentle. Many thanks, as always.

---

### Post by northern lights on 2008-07-22
Mkey, didn't wanna make it sound like you can't possibly encounter problems here and there. Nonetheless, there ain't no need to be afraid of doing it.

Ubuntu nowadays reads from and writes to ntfs as if it was any other format. Out of the box.

The RAID1 it should handle out of the box also, depends a bit on the controller your board came with. But if it won't do so on its own, it can be solved quickly, especially if you return to the forums for help.

As for the data on the RAID hdds, Ubuntu definitely won't screw 'em up. Unless, for example, you'd accidentally select to format the drives during setup, which is why I recommended to unplug 'em during the setup process, just to be safe.

Of course you'll have to get to know your new OS for a bit, but especially Ubuntu has become as userfriendly as any other OS.

The ftpserver obviously needs to be setup manually, yet since you're already running one under XP, your experience should suffice. I'd recommend "ProFTPD" as server software, but you can certainly choose differently.

---

