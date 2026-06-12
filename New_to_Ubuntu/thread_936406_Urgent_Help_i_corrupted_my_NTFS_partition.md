---
title: "Urgent Help i corrupted my NTFS partition"
date: 2008-10-02
forum: New to Ubuntu
---

### Post by lamagy on 2008-10-02
hi all i installed ubuntu 8.04 to an external drive in partition (hd2,5) or sdc5.

it wasn't loading up so i did a root (h2,5) then setup (hd2)(got a success comment)

got one step further as grub now showed up on a blank screen.

did some mount commands ect,ect.

then gave up, loaded up xp and selected the first partition on the external drive and i get a corrupted msg telling me if i want to restart?

i haven't tried to access it via linux live cd, but if i cannot what can i do? or what command can i try to salvage it..

thanks in advance.

lamagy.

---

### Post by Gannon8 on 2008-10-02
I do not think your partition is corrupt. Just follow these steps:

1. Unplug your USB HDD
2. Boot a livecd
3. Go into a terminal
4. Do the following:
```
sudo grub
grub> find /boot/grub/stage1
[should return your Ubuntu partition in the form (hdX,Y), use that:]
grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
5. Restart
6. Follow the instructions on the following web site for installing ubuntu to a portable HDD: [http://www.pendrivelinux.com](http://www.pendrivelinux.com)

---

### Post by bumanie on 2008-10-02
The setup command should have been  (hd2,4) as grub starts counting at zero, therefore, partition five on the hard drive according to grub would be one less than the partition number on the drive. As far as windows goes, either output the exact error message, do a chkdisk via console mode or install ntfsprogs in ubuntu and in terminal, > sudo ntfsfix /dev/sdx,x replacing the sdx,x with the windows partition and drive number. This forces the windows filesystem to be checked at the next boot.

---

### Post by lamagy on 2008-10-02
so should the 

Quote:
sudo ntfsfix /dev/sdx,x  

command fix my drive back? don't know why it shows up corrupt, as for the other comment to do a root then setup, well that's what i did and got me to this problem.

also what do i put in the x's?? if i got find /boot/grub/stage1 it comes up with (hd2,5) should i put that in or should i put 'scd,1'???

my main worry now i get my ntfs main partition back forget ubuntu and grub..

---

### Post by bumanie on 2008-10-02
Well, if find /boot/grub/stage1 is coming up with (hd2,5) that will be correct, but the installation will actually be on partition 6 of the drive. You could download super grub disk and try that. To salvage your windows drive try the ntfsfix, it is a linux initiative that has been designed to fix errors in the ntfs file system. Can I guarantee it will work, "No, I can't", but it works well, but won't fix every error to do with windows. If that doesn't work, you could try testdisk which is a partition/hard drive recovery program. It may be that the partition table is corrupt, if this is the case, testdisk is very good at re-writing partition tables and it can salvage entire partitions. Take your time and read the documentation on the testdisk site carefully. There is also a tutorial [here]("http://www.users.bigpond.net.au/hermanzone/p21.html").As a worst case scenario, you could copy your important information off windows via the ubuntu live cd and then reinstall.

---

### Post by lamagy on 2008-10-02
thanks for that mate...

i'll try that as soon as i get home...

linux should really get their installation process in check...

or at least provide a formal installation guide for different system configurations, at the moment there are only third party ones which are incomplete or faulty.

if i do manage to recover my stuff, how should i install it? what should i do to this drive? i need the ntfs on it for storing ntfs files.

---

### Post by bumanie on 2008-10-02
> linux should really get their installation process in check...When things go wrong it is easy to feel that way, but I have installed dual-boot systems multiple times and never had windows become corrupted as a result. One thing worth noting is that prior to shrinking partitions etc. windows needs to be defragged 2-3 times first. As i said, take your time if the information is important. In 99% of cases your files will still be on windows and they are usually recoverable. Ask more questions if you need to and someone will try to help. Just to let you know I have recovered partitions with testdisk as well as re-writing a partition table that was whacked and gparted said there was no hard drive there. Testdisk does work, but don't rush things. If you have a large enough external hard drive or space on your internal drives, you could copy the windows partition to that so that you have an exact copy of it in case something goes wrong when you try to resurrect it. Off a live cd > sudo dd if=/dev/sda of=/dev/sdbNOTE: Change the drive names if your drive names differ. 
PS: gparted live cd also has a function for copying partitions and entire hard drives, it has GUI, so you may find that easier. Right click on the windows partition and it is basically a copy/paste process form one partition to another.

---

### Post by WWSmith36 on 2008-10-02
> then gave up, loaded up xp and selected the first partition on the external drive and i get a corrupted msg telling me if i want to restart?

I am reading this right?  Both ubuntu and windows are both installed on your external drive.  What may I ask is on the internal hard drives?

---

### Post by lamagy on 2008-10-03
no only the ubuntu is installed in the external drive.

what is on the external drive is the main ntfs partition with 150gb's of data..

there are about 5 partitions on the drive, now the main partition is corrupt in windows.

---

