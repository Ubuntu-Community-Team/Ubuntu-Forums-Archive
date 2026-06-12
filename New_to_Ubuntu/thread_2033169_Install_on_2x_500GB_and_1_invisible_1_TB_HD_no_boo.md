---
title: "Install on 2x 500GB and 1 invisible 1 TB HD: no boot with Grub"
date: 2012-07-25
forum: New to Ubuntu
---

### Post by pognonec on 2012-07-25
Hi there,

I installed Ubuntu 12.04 on a computer with 2 500GB HD. Did a clean install, erasing everything. It apparently went fine. Then, no way to boot: "no system found". I used Boot Repair to fix a possible GRUB problem. It went OK too, and told me to set BIOS on a 1TB HD... This 1TB is not visible in the BIOS.
What should I do? 

This is the Boot Repair log:

[http://paste.ubuntu.com/1110458/](http://paste.ubuntu.com/1110458/)

Thanks!

---

### Post by oldfred on 2012-07-25
You have RAID, the devicemapper Nvidia is RAID. Your probably do not have 1TB drive although boot-repair saw it that way but one 500GB RAID using 2 drives. Total usable space is 500GB

Also for installing on fakeraid (motherboard raid), this might help you:
[https://help.ubuntu.com/community/FakeRaid](https://help.ubuntu.com/community/FakeRaid)
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
[http://ubuntuforums.org/showthread.php?t=1777458](http://ubuntuforums.org/showthread.php?t=1777458)
[http://ubuntuforums.org/showthread.php?t=1338445&page=5](http://ubuntuforums.org/showthread.php?t=1338445&page=5)

I do not know RAID, but you do not boot from MBR of the drive, but MBR of RAID.

[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)
[http://serverfault.com/questions/9244/how-do-i-differentiate-fake-raid-from-real-raid](http://serverfault.com/questions/9244/how-do-i-differentiate-fake-raid-from-real-raid)
[https://help.ubuntu.com/12.04/serverguide/advanced-installation.html](https://help.ubuntu.com/12.04/serverguide/advanced-installation.html)

---

### Post by pognonec on 2012-08-08
I tried all links indicated (at least, the live ones), to no avail. What is most surprising to me is that this problem does not appear to be common, according to my googling on the subject.
One more detail: I tried intalling 10.04 LTS instead of 12.04, just in case "something" changed in between: same exact result. And boot repair could not fix it either.
:(
Thanx for the advice anyway!

---

### Post by Bashing-om on 2012-08-08
Are you on hardware raid or software raid ... do you even want/desire to keep raid? ... For installation of Ubie onto raid gotta use alternate CD to install ..then
"Installation/SoftwareRAID-CommunityUbuntuDocumentation" is a great reference tutorial.
  hth        and best to ya

---

### Post by pognonec on 2012-08-10
Fake raid it is. I just tried the alternate CD as suggested. It looked good. It asked me to provide a missing .bin file, that I hoped was the problem before. But after install, at first boot, same exact problem... 
Thanx for your time anyway. But it looks like Ubuntu does not like these fake raid configs.

---

