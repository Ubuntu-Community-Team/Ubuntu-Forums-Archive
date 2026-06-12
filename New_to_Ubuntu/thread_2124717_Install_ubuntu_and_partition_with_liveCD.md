---
title: "Install ubuntu and partition with liveCD"
date: 2013-03-11
forum: New to Ubuntu
---

### Post by blackpepper on 2013-03-11
Hello, i have using ubuntu before but still kinda new to some aspect and i want to ask for advice 

first, now i cant boot up to windows 7 (i think because hdd failure my system got corrupted). I access this forum now using livecd ubuntu (a great life saver btw), now i want to format and partition the hdd for ubuntu installation  for now but i also want to install windows 7 in the future (for some reason i cant install windows 7 now) for dual booting. how i can accomplished this?

Second, im planned to using ubuntu 64 bit 12.10, if there are newer version in the future is it easy to upgrade it? will it distrurb the dual booting?

Thank You :)

---

### Post by fantab on 2013-03-11
Welcome to the forum.

First of all you need to be sure that your HDD is alright. You can check this with the utility called "DISKS", which is present in the Ubuntu LiveCD. From the Disks check the SMART status of your HDD and verify if all is OK. If not you may have to fix your HDD or replace it. Ubuntu LiveCD does not use your HDD to boot but when you install it on a corrupt HDD then you may end up with a non booting machine. First check your HDD then we'll help you install Ubuntu.

Also try Windows Repair from the Windows installation Disk, to fix your Winodows... if there are any filesystem errors then that should fix it.

Good Luck.

---

### Post by blackpepper on 2013-03-12
hei fantab thanks for replying to my problem

i've check the smart status on the disks program and it said the overall assessment is ok but with bad sector. it is possible to get rid of bad sector by formating the hdd? or it is useless? im planned of changing my hdd on this laptop but im kinda have another important thing to buy at the moment so i think i need to stick with it for a while.

regarding the windows repair i tried those but it just did not work. First time repair, my windows 7 boot up slowly and then BSOD, so i have given up on it

Thank You

SMART Screenshoot
[IMG]http://i48.tinypic.com/358qqtl.png[/IMG]

---

### Post by mastablasta on 2013-03-12
First of all your disk seem to be just fine.

now then....

> **blackpepper said:**
> 
first, now i cant boot up to windows 7 (i think because hdd failure my system got corrupted). I access this forum now using livecd ubuntu (a great life saver btw), now i want to format and partition the hdd for ubuntu installation for now but i also want to install windows 7 in the future (for some reason i cant install windows 7 now) for dual booting. how i can accomplished this?

if can still access data on win7 using ubuntu this might be a good time for backing it up.

if you want to add windows later you need to:
1. create NTFS partition. it has to be primary partition.
2. install windows to it
3. update grub using the live CD and for example boot repair tool: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

you see windows 7 will set up it's own boot manager in front of GRUB (which is the boto manager ubuntu uses) and reqrite grub. windows is only interested in having windows on disk. so by updating grub you will reainstall grub and get a nice menu where you would choose the OS on boot.

[/QUOTE]
Second, im planned to using ubuntu 64 bit 12.10, if there are newer version in the future is it easy to upgrade it? will it distrurb the dual booting?[/QUOTE]

yes it's easy to upgrade it. no it won't (shouldn't) disturb the dualbooting. windows is on separate partition. and yes there will be newr version. next one is planned toward end of April.

if you install LTS and stick to it the next LTS is going to be next year in April. LTS are every 2 years. 

well that is unless they decide to switch to roling releases.

---

### Post by blackpepper on 2013-03-12
@mastablasta

could i use gparted in ubuntu live cdto format and create ntfs partition and set it as primary partition? or i need to use windows cd?

what partition file system needed for ubuntu? how about swap partition i hear that those need to be allocated when installing ubuntu?

after i install ubuntu, then windows 7. windows then wil force it to boot in windows so i need to use livecd or boot repair tool to add windows 7 to grub, is that what you mean?

thanks!!! i think im one step closer to become ubuntu user :D

---

### Post by mastablasta on 2013-03-12
> **blackpepper said:**
> @mastablasta

could i use gparted in ubuntu live cdto format and create ntfs partition and set it as primary partition? or i need to use windows cd?[7QUOTE]
you can use gparted. you can even create it during install.


> 
what partition file system needed for ubuntu? 
you can choose the one you like during install. i suggets you go with default - ext4. don't use NTFS. if you plan to have some separate partition only for data (movies, pics...) it can be NTFS, so you can access it both from linux or windows. but do not use NTFS for the system partitions. it will cause issues.

[QUOTE]
how about swap partition i hear that those need to be allocated when installing ubuntu?

yes if you use manual partitioning it is good to create swap partition. if you have a lot of ram it might not be necessray. but it is used on hibernation and suspend. with regular/default install it is created automaticly for you in the correct size. 
swap should be about twice the ram. if you have plenty of ram (e.g. 4GB+) then it can be about the same size as ram. this can still be enlarged later on.

> 
after i install ubuntu, then windows 7. windows then wil force it to boot in windows so i need to use livecd or boot repair tool to add windows 7 to grub, is that what you mean?


yes, in other words.

---

### Post by blackpepper on 2013-03-12
When im trying to format using gparted or ubuntu installation the same error occur

"[B]Input/output error during read on /dev/sda"

[/B]what does it means? im not mounted the hdd were it means i have bad hdd?

---

### Post by fantab on 2013-03-12
I would recommend that you run "chkdsk" from Windows 7 install media and repair those bad sectors. (CHKDSK is a better option since the file system you have on your HDD is NTFS). You can run "chkdsk" from Windows 7 install media. See [**here **]("http://www.sevenforums.com/tutorials/682-command-prompt-startup.html")if you don't know how to boot into a command prompt with windows 7 install media and [**here**]("http://www.sevenforums.com/tutorials/433-disk-check.html") to use 'chkdsk' at command prompt.

Run 'chkdsk' a couple of times to be on the safe side.

Then re-format your C: partiton to NTFS and Install Windows 7. If you need more NTFS partitons create them as well. Once you have a bootable Windows then proceed to Install Ubuntu. When dual booting Windows and Linux it is better to install Windows first.
We will offer more assistance as you go along.

Good Luck...

---

