---
title: "Need advice on how to install Ubuntu without erasing everything on my hard drive"
date: 2012-03-09
forum: New to Ubuntu
---

### Post by adido on 2012-03-09
Hi,

I need some advice, please, on how to install Ubuntu Studio on my machine without loosing data. After watching video tutorials and reading about clean installations, I'm still not 100% sure how to go about it.

Currently, I'm running Win and the hard drive has 3 partitions (1xWin + 2xpersonal).

I would like to get rid of Win altogether, no dual boot, and install Ubuntu on the partition Win occupies now. Without touching/ formatting the other two personal partitions in the process.

Can someone, please, point me to a very detailed tutorial or write accurately the steps I need to take safely install U Studio without loosing personal data?

Many thanks,
Adrian

---

### Post by coffeecat on 2012-03-09
@adido, welcome to the forum!

What you want to achieve should not be too difficult, but a couple of comments first. Since you are wanting to preserve your personal data, back it up before you do anything. Replacing the partition Windows is on with Ubuntu and leaving the other two untouched is fairly straightforward, but any manipulation of partitions involves a slight risk of something going wrong with consequent loss of data. Backup now.

The other comment - your two personal partitions will be formatted either NTFS or FAT32, probably NTFS. Although Ubuntu can read-write NTFS reliably, I advise you not to use this filesystem if you do not have Windows available. NTFS is a Microsoft filesystem and needs the utility chkdsk in the event of filesystem damage. Although there is a Linux utility for fixing NTFS, it is nowhere near as comprehensive as chkdsk.

We need to see exactly what your partition layout is like before recommending something. Boot up your Ubuntu Studio live DVD or live USB (if you have one) and do one of the following. Either open Gparted, the partition editor and take a screenshot of the open window. In Ubuntu you would use the alt+PrintScr key combination for this. I don't know whether this key combo works in Ubuntu Studio as I'm not sure offhand which desktop environment Studio uses. If you can't get a screenshot, open a terminal and post the output of these two commands:

```
sudo fdisk -lu
sudo parted -l
```

Sorry to throw a couple of terminal commands at you, but this is the easiest and quickest way for getting the information needed. You should be able to copy and paste the terminal output by highlighting it with the mouse and right-clicking -> copy.

I'm assuming you have an Ubuntu Studio disc already. If not, post back and we'll take it from there.

---

### Post by adido on 2012-03-10
@coffeecat: hi & thank you for the help!

Ubuntu Studio - the last version of it - does not have a live DVD, but  you're right, all my partitions at the moment are formatted in NTFS.

I assume that if I install Ubuntu S on the current Win partition, that's  where my home and root folders will be. Then I'm left with mounting the  other two personal partitions (found info here  [http://www.tuxfiles.org/linuxhelp/mounting.html](http://www.tuxfiles.org/linuxhelp/mounting.html)). 

How can I proceed with the installation? Alternatively, if things get to  messy, I could backup everything and format the entire drive. But I  would prefer to face this learning curve head on and learn how to fix  things/ adapt step by step.

Thanks again for the help.

---

### Post by edm1 on 2012-03-10
To be honest, even considering myself relatively experienced using linux at home I would chose to back everything up then wipe the disk and start afresh. Then you will be able to use ext4 (which is rock solid) on all your partitions. You'll also be able to design your own partition table. Fr example at the moment I use 3 partitions (well 4 including swap).
1) My root filesystem - holds the operating system
2) Home - contains all my personal settings
3) Media - contains all my media. I like to keep this separate from my home. Then I symlink it to my home folder
4) Swap

It would look something like this during the installation:
sda1 20GB  /
sda2 20GB  /home
sda3 300GB /home/media
sda4 3GB   swap

---

### Post by adido on 2012-03-10
edm1, thanks!

I'm convinced. Before I dive into this, I still have a few more questions. Can you please tell me:

- taking your partition arrangement as example, which are the ones that will be automatically formatted when I will do a future clean install?

- to have a setup like yours, do I choose the option 'manual' during installation (13th image from the top) -  [https://help.ubuntu.com/community/Ubuntu%20Studio%20Fresh%20Install](https://help.ubuntu.com/community/Ubuntu%20Studio%20Fresh%20Install)

- and the slightly silly question: if I want to select multiple options during the installation process, is Ctrl + Space the way to do it? (first image under 'Software Selection' section [https://help.ubuntu.com/community/Ubuntu%20Studio%20Fresh%20Install](https://help.ubuntu.com/community/Ubuntu%20Studio%20Fresh%20Install))

Many thanks!

---

### Post by edm1 on 2012-03-10
1) If you are still planning on backing everything up, wiping everything, then reloading your data you dont even be wanting to format any of them. Just delete all the existing partitions and start afresh.

2) Yes, chose manual if you would like to set up separate partitions. If you decide you just want 1 partition with everything on then go for use entire disk.

3) Ive always installed using the desktop live usb and have never used the alternate install method that Ubuntu Studio uses but it looks like you just move down the list and click space to select.

---

### Post by audiomick on 2012-03-10
> **adido said:**
> which are the ones that will be automatically formatted when I will do a future clean install?
If you use the "manual" partitioning option (and to answer your question, yes, that is the option you want to use to set up your own partitioning scheme), nothing is done automatically. Only the partitions that you select to be formatted will be formatted. That is the value of a partitioning scheme as edm1 suggested. If the machine falls on it's head, you can just re-install the / partition where the system is and simply re-mount the partitions with your data without formatting them. All your configurations are in the /home/user folder, so when you re-install the applications they come back up just as they were before the re-install.

> 
- and the slightly silly question: if I want to select multiple options during the installation process, is Ctrl + Space the way to do it? (first image under 'Software Selection' section [https://help.ubuntu.com/community/Ubuntu%20Studio%20Fresh%20Install](https://help.ubuntu.com/community/Ubuntu%20Studio%20Fresh%20Install))

Ah, that step is not intuitive at all. If I remember rightly, it is up and down arrows to choose, space bar to select or deselect, and enter to continue. I remember it being somehow not quite the same as the preceding steps. Don't panic, though. If you accidently tell it to go on without having selected them all, you can very  easily install the missing bits via Synaptic when the install is finished. There are packages in the repository that correspond exactly to the options in the installer.

---

### Post by adido on 2012-03-10
People, thank you so much for the help and for the super-fast replies!

It's done, installed and looks excellent!

For reference sake, here are some links I kept handy while going through the installation:

[http://www.howtoforge.com/the-perfect-desktop-ubuntu-studio-11.10](http://www.howtoforge.com/the-perfect-desktop-ubuntu-studio-11.10) - a very detailed guide, with more print screens than the one on Ubuntu Studio wiki

[http://www.linuxbsdos.com/2011/05/04/manual-disk-partitioning-guide-for-ubuntu-11-04/](http://www.linuxbsdos.com/2011/05/04/manual-disk-partitioning-guide-for-ubuntu-11-04/) - might be of some help although the interfaces are quite different

+ the occasional Google to find out about Primary partition and whether I should make the partition at the beginning or end.

Now I have a first headache with the network manager that is missing and I have no idea how to set up the wireless - works perfect with the cable though. But I'll start another thread for that.

Cheers to all!
Adrian

---

### Post by adido on 2012-03-11
Before I let this topic go, I need to shed some light on how I partitioned the drive:

My intention was to have, as @edm1 suggested:
sda1 20Gb /
sda2 50Gb /home
sda3 86Gb /media {it did not allow me to call it /media, so I chose the default option /usr}
sda4 4Gb swap

Now, when I run the df -h command to find out disk space, I get these results:
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              19G  1.5G   16G   9% /
udev                  991M  4.0K  991M   1% /dev
tmpfs                 400M  996K  399M   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                 1000M  732K  999M   1% /run/shm
/dev/sda3              46G  328M   44G   1% /home
/dev/sda4              79G  4.0G   71G   6% /usr

How is this different from what I wanted to achieve?
Why does /usr has 4Gb occupied? That was suppose to be the partition for my media files.

Cheers,
Adrian

---

### Post by oldfred on 2012-03-11
/usr is a system folder. It now is controlled by / (root) and is used by the system. All the defaults on the installer are to allow the creation of different partitions for all system folders. Used by servers not needed on desktops.

Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

You either needed to partition in advance or as part of the install just leave the space and come back and create then new media partition and mount it manually.

---

### Post by adido on 2012-03-11
Thanks to all for the replies. I eventually reformatted the drive into 3 partitions: swap, / and /home.

Have fun,
Adrian

---

