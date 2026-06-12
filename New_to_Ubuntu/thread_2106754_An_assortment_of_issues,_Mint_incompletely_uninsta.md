---
title: "An assortment of issues, Mint incompletely uninstalled and apt-get can't get lock."
date: 2013-01-20
forum: New to Ubuntu
---

### Post by Tommy The Cat on 2013-01-20
Hi. I installed Ubuntu 12.10 today on my MacBook 4.1. I also used Linux Mint 14 for about a week before and I liked that. But, I terminally (no pun intended) screwed up Mint 14 in the process of trying to get my iPhone to update with it and long story short, I moved to Ubuntu because support for misc odds and ends was going to work out of the box more easily (iSight and and broadcom wireless drivers aside) and Unity works a lot like OS X that I'm used to. Oh, and Ubuntu just looks sexier.

BUT... 

rEFInd still shows Mint 14 as my primary boot OS, even though I've completely reformated the partition where it previously resided and where Ubuntu now risides. Also, if I'm not careful to hold down the option/alt key on boot, my computer will jump strait to Mint 14's recovery mode. I suppose this alone is an EFI issue that needs to be fixed from rEFInd.

BUT... whenver I go to use a sudo apt-get command, I get this error:

```
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```

The last line of this makes me think the ghost (if you will) of Mint 14 is somewhere in the file system preventing apt-get to do it's thang. However, I'm pretty well still a newb so I'm going to stop speculating there and let you guys tell me whether or not these issues are related and point me in the right direction on fixing them. 

Thanks!

---

### Post by sudodus on 2013-01-20
There are ```
sudo apt-get 'something'
``` complaints, when there is another update-upgrade-install manager running at the same time. For example, you need to close ***Synaptic*** before apt-get gets the permission to use those resources.

After
```
sudo apt-get update
``` and
```
sudo apt-get upgrade
```
you can run ```
sudo update-grub
``` and then mint should be wiped from the boot menu unless grub points to another partition. Then you need to run
```
sudo grub-install /dev/sdx
``` where you need to put the correct drive letter instead of x. If one drive, it is typically /dev/sda.

Read more at

[[COLOR="Red"]https://help.ubuntu.com/community/Grub2/Installing[/COLOR]]("https://help.ubuntu.com/community/Grub2/Installing")

---

### Post by cariboo on 2013-01-20
Did you try to remove the lock file in /var/lib/dpkg? If not, open a terminal and type the following command:

```
sudo rm /var/lib/dpkg/lock
```

then try to update again.

---

