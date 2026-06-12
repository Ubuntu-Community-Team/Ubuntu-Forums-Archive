---
title: "Resizing Partitions"
date: 2014-01-10
forum: New to Ubuntu
---

### Post by vfx1988 on 2014-01-10
Hi, 
i think i have the same problem as weizel 2 threads below..
i have a 500 gig harddisk which only has 50gigs of usable space... gparted shows none of this information but through command i can see that i only have 50 gigs... im posting afew screenshots to help.

Please let me know how i can fix this screw up that i have done.. :(

---

### Post by carl4926 on 2014-01-10
It's encrypted
What are you running there now?
What do you want to do with it?

---

### Post by vfx1988 on 2014-01-10
i have an apache2 server running and yea i chose to go yes for the encryption, was that a bad move..?
i want to use the remaining space for the applications and backups i will be having on this but cant seem to find where i lost the space lol..

---

### Post by carl4926 on 2014-01-10
There is only a small sector of unused space that I can see

---

### Post by vfx1988 on 2014-01-10
yea but i can only use 50 gig.. my 150gig ran away... :(
any idea where it could be hiding?

---

### Post by carl4926 on 2014-01-10
> [COLOR=#000000]my 150gig ran away[/COLOR]
Sorry, you lost me there
What 150GB

---

### Post by oldfred on 2014-01-10
Gparted does not currently work with LVM which is your entire drive.
You should have logical partitions inside you main LVM partition.

You have to use LVM tools to modify and view LVM.

 Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)
lvm How-To info older:
[http://ubuntuforums.org/showthread.php?t=141900](http://ubuntuforums.org/showthread.php?t=141900)
[http://tldp.org/HOWTO/LVM-HOWTO/index.html](http://tldp.org/HOWTO/LVM-HOWTO/index.html)
[http://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html](http://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html)
sudo apt-get install lvm2
sudo vgchange -ay

---

### Post by vfx1988 on 2014-01-11
> **oldfred said:**
> Gparted does not currently work with LVM which is your entire drive.
You should have logical partitions inside you main LVM partition.

You have to use LVM tools to modify and view LVM.

 Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)
lvm How-To info older:
[http://ubuntuforums.org/showthread.php?t=141900](http://ubuntuforums.org/showthread.php?t=141900)
[http://tldp.org/HOWTO/LVM-HOWTO/index.html](http://tldp.org/HOWTO/LVM-HOWTO/index.html)
[http://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html](http://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html)
sudo apt-get install lvm2
sudo vgchange -ay

thank you oldfred! you were right! they are lvms! that explains why the programs i downloaded to manage the harddisk did not work!

for anyone else struggling with lvms i suggest using the following:

sudo apt-get install system-config-lvm
they have a neat gui which lets you manage the whole thing without writing one line (well except the mount point..)!

credits to [http://www.howtogeek.com/127246/linux-sysadmin-how-to-manage-lvms-with-a-gui/](http://www.howtogeek.com/127246/linux-sysadmin-how-to-manage-lvms-with-a-gui/)

found all that missing space! 
hahaha

---

