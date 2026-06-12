---
title: "Question on where I can install Ubuntu"
date: 2014-02-17
forum: New to Ubuntu
---

### Post by RussellXPD on 2014-02-17
Hi all
I've had some good help here on installing and trying Ubuntu, 12.0.4 in my case. And I've got going, particularly on a 2-y-o Windows 7 (+ 12.0.4) system. Thanks to the lads.
On an older PC I have Pentium 4 CPU, 2.80 Ghz with 2Gb RAM running XP, 100 Gb HDD.
My question is: if I install 12.0.4 onto the PC, must it go into C drive? Or could it go into E drive with 30 Gb+ space? Or could I boot and run it from a 1 tb external disk?
I've been advised to use Kubuntu because it's lighter, but would prefer to try what I've got right now.
 Any tips gratefully received.
RussellXPD

---

### Post by oldfred on 2014-02-17
Only wubi installs inside NTFS partitions and it is being discontinued. Best to install to a Linux formatted partition.
But if you have all those partitions you may have used all 4 primary partitions?
Best to see current layout. Post this from terminal in liveDVD/Flash drive

sudo parted -l

I have a somewhat newer dual core laptop with 1.5GB of RAM and Intel video. I have full 64 bit Ubuntu installed but do not try to run Unity. I convert to the old menu system with fallback which also is lighter weight. I still see slowdown (swap use) if I try to launch too much at once.

---

### Post by 3rdalbum on 2014-02-17
> **RussellXPD said:**
> Hi all
I've had some good help here on installing and trying Ubuntu, 12.0.4 in my case. And I've got going, particularly on a 2-y-o Windows 7 (+ 12.0.4) system. Thanks to the lads.
On an older PC I have Pentium 4 CPU, 2.80 Ghz with 2Gb RAM running XP, 100 Gb HDD.
My question is: if I install 12.0.4 onto the PC, must it go into C drive? Or could it go into E drive with 30 Gb+ space? Or could I boot and run it from a 1 tb external disk?
I've been advised to use Kubuntu because it's lighter, but would prefer to try what I've got right now.
 Any tips gratefully received.
RussellXPD

"C drive" and "D drive" are Windows terms. They mean nothing for any operating system except Windows.

I take it then that you have two partitions on the 100gb hard disk? You can't install Ubuntu to any of your existing partitions, but the installer will allow you to downsize one of them and use the free space to create another partition for Ubuntu. If you have a large external hard disk, sure, you can install Ubuntu to that. Just remember: If you install Ubuntu to an existing partition, it will be formatted and you will lose any data on that partition. If your 1tb hard disk has stuff on it already, either move it or downsize its partition.

Before performing any partitioning operations, back up all the data on the disk that is being partitioned.

Generally, a Pentium 4 is a fast enough CPU to run Ubuntu. 2 gigs of RAM is ample for Ubuntu. The only mystery is your graphics - if your GPU is an Intel or ATI chip from the time, it might be a bit too slow for Ubuntu, and you would need to use Lubuntu or Xubuntu. If it's a bit more recent it might work well enough. Ubuntu does not run well on a lacklustre GPU but anything from the last five years should be fine.

---

### Post by Bucky Ball on 2014-02-17
Ubuntu will happily exist on any partition, any drive, a primary partition or a logical partition inside an extended partition. ;)

I am typing this on my old P4 3GHz which, until recently, was running Xubuntu just fine with 1Gb of RAM. I've just chucked in 4Gb and an SSD and it flies.

But anyway, with your specs, you might like to try Xubuntu or Lubuntu, as suggested.

---

### Post by RussellXPD on 2014-02-17
Thanks all
Point taken about Windows designated partitions.  
As to the hard disk, I have three partitions. If it were useful, I could create a fourth partition with say 30Gb by shrinking the amount allocated to System, Programs, Files.
I'm generally well backed up.
On my EDD I've again three partitions with 300 Gb each. The first one is designated PRIMARY, and the second 2ND PRIMARY. Both are 40% full. No problem moving stuff elsewhere to provide blank space.
I would prefer to run from the external drive.
As before, I'm still a beginner so please forgive me if I pick nits so that I'm clear on what I'm going to try to do. But I've been okay so far!
The Graphics controller is [SIZE=2]Intel(R) 82865G
Russell[/SIZE]

---

### Post by oldfred on 2014-02-17
Some old BIOS will only boot from first 137GB of a hard drive. So either a smaller / (root)  (20GB) fully inside first 137GB of drive or separate /boot may be required. Often more common on USB external drives also. Then use rest of drive as /home or for data partition(s).

       Install to external drive. Also any second drive.
And you want this screen to choose where to install the grub2 boot loader which is only available with Something Else or manual install
[https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29](https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29):
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)
Older screens shown but process is same.

 Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

### Post by RussellXPD on 2014-02-18
Thanks OldFred
I need to read these carefully. I understand the principle, but a bit shaky on some of the ideas. I'll build up a plan and ask later if it's reasonably safe.
Trouble is, you mainly learn by making mistakes!
Russell

---

### Post by Bucky Ball on 2014-02-18
> **RussellXPD said:**
> Thanks OldFred
Trouble is, you mainly learn by making mistakes!


As long as you've made a plan beforehand to backup then all should be fine if you do something ludicrous! When doing full reinstalls and working with a blank slate it is nice to know everything is safely on another drive in a drawer or cupboard in another room! Then you can screw up majorly, make a bunch of mistakes before getting things exactly how you want them and learn something on the way, THEN put the important data back ... ;)

---

### Post by mastablasta on 2014-02-18
> **RussellXPD said:**
> Thanks OldFred
I need to read these carefully. I understand the principle, but a bit shaky on some of the ideas. I'll build up a plan and ask later if it's reasonably safe.
Trouble is, you mainly learn by making mistakes!
Russell

let's say you would want to replace "E: drive" with ubuntu. nothing could be easier. asuming BIOS can boot from higher disk parts all you would need to do is delete the e drive (create unalocated/unformatted disk space) and then installer will offer to install Ubuntu to largest free disk space (former e: drive). everything else is done automaticly (linux partition, swap, GRUB...). you can still use external drive(s) for data etc.

if however you would really want to install to external drive this needs some manual approach. also you would be doing all via USB port which is a lot slower than internal disk.

remember, you will be able to access widnows drives (NTFS and FAT32 formated) from Ubuntu.

---

### Post by RussellXPD on 2014-02-20
Thanks to all of you. I take your point, BuckyB, about backups. In fact my first target is to install 12.0.4 on the first of three partitions on a 1 Tb disk. Completely empty, 450 Gb. 

Mastablasta says *this needs some manual approach. also you would be doing all via USB port which is a lot slower than internal disk.* Well, I've got a 4Gb flash handy, but the machine is 7 years old (otherwise sound) and won't boot from USB. Can I get past this first hurdle - will that be a problem?

---

### Post by RussellXPD on 2014-02-23
Hi all
I managed to install 12.0.4 as dual boot on the hard drive with XP.
Success! Thank you fellows for your info.

I expect I'll be back soon because this is day one on a new OS - granted I've been trying out for some time on two different computers, but there's a disincentive when the machine 'forgets' anything you've done on a try out session.

Marking thread solved ......

RussellXPD

---

