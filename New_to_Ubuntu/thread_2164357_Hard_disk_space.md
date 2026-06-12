---
title: "Hard disk space"
date: 2013-07-31
forum: New to Ubuntu
---

### Post by ernv84 on 2013-07-31
Hi guys,

I installed Ubuntu for learning prposes and chose automatic partition and it looks like system assigned all my HD space to root. 

Now i am wondering if i can change it to my user without reinstalling ubuntu or if not where do i store my data??

Would appreciate a quicker response. 

Thanks in advance

er

---

### Post by ernv84 on 2013-07-31
Forgot to add...

/dev/mapper/Bucephalus-root 957015724 8274632 900127512   1% /
udev                          2013816       8   2013808   1% /dev
tmpfs                          809364     916    808448   1% /run
none                             5120       0      5120   0% /run/lock
none                          2023408     224   2023184   1% /run/shm
/dev/sda1                      233191   76606    144144  35% /boot

---

### Post by Cheesemill on 2013-07-31
You only have one partition which is used for everything, your user files included. Nothing to worry about.

Think of it like one big C: drive in Windows.

---

### Post by NikTh on 2013-07-31
> **ernv84 said:**
> 

Now i am wondering if i can change it to my user without reinstalling ubuntu or if not where do i store my data??

Would appreciate a quicker response. 

When the user selects the automatic partitioning, Ubuntu creates a root partition and the /home partition hosted under root. So you can store your data without problems. The only difference here is that you don't have a separate /home partition, but /home in under root. 
```
cd /
ls
```


> **ernv84 said:**
> Forgot to add...

/dev/mapper/Bucephalus-root 957015724 8274632 900127512   1% /

Did you select the LVM during installation ? If yes, read here about LVM 
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)

I've never used it.

---

### Post by ernv84 on 2013-07-31
Does it mean my /home is under root now??? So i can keep all my data in home directory and it will use space from that 950G ?

---

### Post by Vladlenin5000 on 2013-07-31
> **ernv84 said:**
> Does it mean my /home is under root now??? So i can keep all my data in home directory and it will use space from that 950G ?

Yes.

---

### Post by angryfirelord on 2013-07-31
This somewhat dated chart pretty much explains what the file system hierarchy looks like: [http://2.bp.blogspot.com/-VidzeWdctO4/TtMRBEzlGjI/AAAAAAAAAy0/F4SAx-_R4wM/s1600/file+hierarchy.png]("http://2.bp.blogspot.com/-VidzeWdctO4/TtMRBEzlGjI/AAAAAAAAAy0/F4SAx-_R4wM/s1600/file+hierarchy.png")

If you designate only one partition for root (/), everything else still falls under it. You can split these directories into multiple partitions if you want, but for a desktop machine, that's not really necessary.

---

### Post by gordintoronto on 2013-07-31
The biggest drawback is in the future, when you want to move to, for example, Ubuntu 14.04 LTS. The safest way to do this is by a normal install, which will wipe out all your data.

On my system, I have separate partitions: 36 GB for /, 4 GB for swap and the rest for /home. I have installed new versions without losing any of my data. (But I still have excellent backup, as one slip of the fingers might wipe it all out.) And I actually have another partition for fooling around with new versions/distros. And a second hard drive which currently has the Preview of Windows 8.1.

---

### Post by Paqman on 2013-07-31
> **gordintoronto said:**
> The biggest drawback is in the future, when you want to move to, for example, Ubuntu 14.04 LTS. The safest way to do this is by a normal install, which will wipe out all your data.


No it won't. The Ubuntu installer has been clever enough not to overwrite existing /home folders on a root partition for some time now. The justification for having separate /home partitions is pretty much zero now. I still have mine on separate partitions, but that's only because it's a leftover from the old days. I should probably get around to consolidating next time I reinstall.

---

