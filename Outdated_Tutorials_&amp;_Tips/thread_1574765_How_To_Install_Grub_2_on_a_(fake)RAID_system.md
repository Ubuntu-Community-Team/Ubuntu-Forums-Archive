---
title: "How To: Install Grub 2 on a (fake)RAID system"
date: 2010-09-14
forum: Outdated Tutorials &amp; Tips
---

### Post by xenton on 2010-09-14
Trying to install Ubuntu on a fakeraid system will almost certainly give you an error upon installing Grub, simply select continue without installing a bootloader. Upon completion of the install boot from your ubuntu CD and run ubuntu from the CD then follow the steps below:

Click ***System>Administarion>Disk Utility*** you will see something like this:

[IMG]http://i524.photobucket.com/albums/cc323/xenton/ubuntu/Screenshot-21GBHardDisk-dev-mapper-nvidia_abjcfaad3DiskUtility-1.png?t=1285181713[/IMG]

You need to select the partition to which your ubuntu is installed from the storage devices list on the left. RAID partitions will be under the 'peripheral devices' heading. Select the one that's the same size as your ubuntu install and check the filesystem is ex3 or ex4, you now need to make a note of the device name which will be ***/dev/mapper/something*** in my case it is ***/dev/mapper/nvidia_abjcfaad3***

Now we need to make a note of the RAID ARRAY device on which your Linux partition exists it will be listed as a hard disk which is the total size of your array, and is usually the same as your Linux partition just without the number. In my case it is [I][B]/dev/mapper/nvidia_abjcfaad

[/B][/I]Now click ***Applications>Accessories>Terminal***

Type the following at the prompt:

```
sudo mount {Linux partition device name} /mnt
```so in my case I would type
```

sudo mount /dev/mapper/nvidia_abjcfaad3 /mnt
```Now type the following:
```
sudo mount --bind /dev /mnt/dev 
sudo mount --bind /proc /mnt/proc 
sudo mount --bind /sys /mnt/sys 
sudo chroot /mnt 
dpkg-reconfigure grub-pc
```Leave all the screens unchanged and click OK until you are asked where to install GRUB, select the entry that matches your RAID ARRAY device name, in my case ***/dev/mapper/nvidia_abjcfaad ***(select it with the spacebar, then press return)

You will get some messages in the terminal window about other bootloaders being detected.

You may also get messages about memory leaks, don't worry about these.

Now take your Ubuntu CD out the drive and reboot. If all has gone well you should see the Grub screen and be able to boot into Ubuntu :p

_**[SIZE=2]Credits/notes[/SIZE]**_

This guide is based on the Grub2 community documentation at [https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) and my own experience with help from [ronparent]("http://ubuntuforums.org/member.php?u=634522") and [Troublegum]("http://ubuntuforums.org/member.php?u=829821"), a big thanks to them both :biggrin:

The method for obtaining the needed device names is entirely my own, it may not be the best way but is probably the easiest way for a beginner.

---

### Post by xenton on 2010-09-22
This is my first tutorial, so if anything is unclear or needs elaborating, just reply and I'll do my best to accommodate you.

---

### Post by Tylerjd on 2010-09-22
Thank You!! I have been needing to do this, as I have been booting my system using a small hdd before using the RAID, but now this will help with my 10tb raid 6 setup! Thank you so much:D

---

### Post by xenton on 2010-09-22
Your most welcome, the excellent community here got me through, glad I can give something back via this howto. I must say as my raid is a fakeraid set-up, it was so much easier to get this working with Ubuntu than windows, and considering I have years of windows experience and am a Ubuntu newbie, it does bode well for Ubuntu!

---

