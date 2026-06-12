---
title: "accessing 2nd hard drive, problems..."
date: 2008-06-07
forum: New to Ubuntu
---

### Post by PsycoGeek on 2008-06-07
I have Ubuntu installed on /dev/sdb.  The system boots OK, no problems there.  I have installed a 2nd hard drive that I want to use to share files via samba over my home network.  the drive is /dev/sda, and the mount point is /media/disk.  The problem is I cannot create folders or files on it, or share the entire disk.  All the options are greyed out.  What am I doing wrong?

The disk partitions were edited in GParted.
Ubuntu 8.04 i386 desktop.

---

### Post by rickycodie on 2008-06-07
i'm confused, is the drive on the same computer and you are trying to access it with samba? or is it on another computer?

---

### Post by nebu on 2008-06-07
i thought ubuntu install path was always /media/sda

---

### Post by PsycoGeek on 2008-06-07
> **rickycodie said:**
> i'm confused, is the drive on the same computer and you are trying to access it with samba? or is it on another computer?

The hard drive is on the PC I'm working on.  I want to share the drive so client machines can access it.

<edit>  Let me clarify... yes, the hard drive is on the same computer.  It is to be used as the shared area where clients computers will access files through samba...

ubuntu server: Drive1= /dev/sdb (/root;/home;/swap)
               Drive2= /dev/sda (/shares -or at least this is how I want to set it up)

---

### Post by PsycoGeek on 2008-06-07
:bump:  This is causing me serious delays in getting the system usable.  Any help would be appreciated.

---

### Post by bumanie on 2008-06-07
This may sound silly, but have you formated it and put a filesystem on it yet or is it still a 'raw' drive?

---

### Post by PsycoGeek on 2008-06-07
> **bumanie said:**
> This may sound silly, but have you formated it and put a filesystem on it yet or is it still a 'raw' drive?

I created a primary partition and formatted it to ext3.  I have also tried ext2 with the same results.  I have to be doing something wrong, but what?

When I go to "Places" and click on the drive (it shows up as 41.2 GB Media in the menu) it mounts, but then I can't do anything with it.

C'mon... help me get outta the Vista hell I'm in.

---

### Post by Jessethenoob on 2008-06-07
hey guys im having a similar problem if one of you could PLEASE help. i have a few hard drive that were from windows, and i am using my grandpas 80GB hard drive for this new computer i just made. So i wiped XP off and i used the ubuntu partitioner from the live cd, to reformat the drives to ext3. but it still isnt letting me mount them. it says that i am not privilaged to mount volume FRED, haha which is my grandpa's hard drive. is this because im not using the sudo command or could it be from something from windows?  sorry im trying to learn Ubuntu and i like it so far im just figuring it all out. haha and my name says it. i am a noob with linux so far.

---

### Post by PsycoGeek on 2008-06-07
Update:  If I format the partition with fat32 and mount it I can do whatever I want.  But I don't want a fat32 volume in the system! :confused::confused::confused:

---

### Post by bumanie on 2008-06-07
Hmm, this is odd. How about trying to format it to ntfs seeing ntfs-3g allows read/write from linux? Not a perfect solution, but may be enough to get you started and if your clients have windows computers it would be easier for them. Gparted from within ubutnu usually works well, just in case it has not installed properly (or something - a long shot), you could try the gparted live cd and see if that does any better.

---

### Post by PsycoGeek on 2008-06-07
Thanks bumanie... I'm trying to stay away from fat and ntfs.  The clients are going to be my own PC's (home network), and I am trying to move everything from Windows based systems and networking to Ubuntu.  Windows will stay in dual-boot for those games that won't run in Wine (Flight Simulator X, and a few others), but everything else will be done under Ubuntu.

Funny thing is that I wiped the hard drive with my gparted live CD and figured I would do the rest from within Ubuntu.  That is going to be my next course of action.  Thank you for bringing it up because I didn't think of it.  Will post the results in a bit.

I can't take much more frustration right now.  Between this and trying to find a Wii Fit for my son I'm gonna loose it...

---

### Post by |{urse on 2008-06-07
its sda if its the primary sata
its sdb if its a secondary sata drive
its generally hda if its ide
hdb, hdc  etc.

if you need to format the drive

> sudo mkfs -t ext3 /dev/sdb

in order to mount and see your drive follow these few steps..

type 

> mount

look for your drive, should be /dev/sdb

then create a folder where you would like your drive mounted, /media/something is preferred so

> sudo mkdir /media/drive2

then 

> mount /dev/sdb /media/drive2

---

### Post by bumanie on 2008-06-07
Try and relax. I can understand one wishing to avoid ntfs if possible, but it may be an OK 'stop-gap' solution, for an interim period. By the way what brand of hard drive is it? I know there have been some issues with some external drives not behaving too well with ubuntu, but haven't heard about any internal drives being problematic as yet.

---

### Post by PsycoGeek on 2008-06-07
Thanks |{urse...  Right now I have the drive formatting via the gparted live cd.  I had to take a break and play some Mario Kart Wii with my son, and eat dinner.  Will let you know what is happening with it a bit later.

bumanie, the primary drive is an older Maxtor 8gig IDE, low profile drive (it has hardly been used, so it is pretty fresh as far as wear), the secondary is an IBM Deathstar (Deskstar) 40gig IDE.  Both drives are stop-gap measures in and of themselves, and will hopefully be replaced by 160gig + SATA drives within a few weeks.  You can call this a practice and learning build that will make it a lot easier on my when I have to do it again.  A third drive is going to join these two after I get it working smoothly, and it is a Western Digital 120gig IDE.  I may even go for some really cheap IDE drives as the motherboard has built in RAID (for 4 drives), as well as 4 SATA drives.

---

### Post by PsycoGeek on 2008-06-08
> **|{urse said:**
> its sda if its the primary sata
its sdb if its a secondary sata drive
its generally hda if its ide
hdb, hdc  etc.

if you need to format the drive


in order to mount and see your drive follow these few steps..

type 



look for your drive, should be /dev/sdb

then create a folder where you would like your drive mounted, /media/something is preferred so



then

I followed all the steps and mounted /dev/sda1 (that's what it keeps coming up as, even though it is an IDE drive) to /media/shares.  It is labeled correctly but I still have no permissions to write any data to it.

BTW, some Mario Kart Wii, a little bit of Battlefield 2, and watching some TV with the wife (who is doing a grand total of 4 double shifts for her next paycheck, she's an LPN) and son really hit the spot for a bit of relaxation.

Any idea where to go from here?

>2nd edit< Also, I can't unmount after it is mounted, but it disappears on a re-boot.

---

