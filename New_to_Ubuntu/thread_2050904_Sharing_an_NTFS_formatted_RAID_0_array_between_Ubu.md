---
title: "Sharing an NTFS formatted RAID 0 array between Ubuntu 12.04 and Windows 7"
date: 2012-08-31
forum: New to Ubuntu
---

### Post by adamantium on 2012-08-31
Hey all,

I'm not completely new to Ubuntu, but haven't used it as my main OS before and would really like to try to now.  I don't game as much as I used to so don't really need Windows as much.

So, to try to ease my transition I'm dual booting for now until I know I can be comfortable letting go.  I've got almost everything setup great except for one problem; I can't for the life of me get Windows and Ubuntu to share the RAID 0 array I have setup.

So here's my setup:

-1 Kingston HyperX 240GB SSD split for Ubuntu and Windows
-1 Kingston HyperX 240GB SSD used only for Steam and Origin in Windows 7
-2x WD Black Edition 1TB drives in RAID 0 (fakeraid)

No matter which OS I format the RAID 0 array in NTFS with, the other one has a problem seeing it.  I format it in Windows and Ubuntu sees it as an unknown file system in gparted.  I format it in Ubuntu and Windows sees it as used space but can't identify it in Disk Management tool.  At one point (can't remember exactly what I was doing at the time between the gazillion reboots and reformats) Both OSs could read the RAID array fine but could only see the files that were transferred to it by itself.  (Ubuntu could only see things Ubuntu transferred, same in Windows)  I have read the fakeraid guide ([https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)) and it stated to use fakeraid when sharing between Windows and Linux, but that seems to not be working for me.

For the record I do have dmraid installed.  I have broken down and rebuilt the raid but that didn't do anything.  I have tried converting the array to GPT and Dynamic disk to see what would happen but didn't matter.

Can someone please tell me what I'm doing wrong, or tell me what I'm doing is just not possible so I don't waste anymore time? :confused:

I appreciate any help anyone can give.  Thanks!

---

### Post by adamantium on 2012-09-20
Bump!

---

