---
title: "Conflict on 'mount point's Using LUKS encryption (or trying to..)"
date: 2015-09-16
forum: New to Ubuntu
---

### Post by Jack_Wilborn on 2015-09-16
Hello all, usually I use Debian, but I've wanted to try encryption, so I though I'd try the live version install of ubuntu, suggested by Martin Paul Eve.  The partitions are built via Gparted, then cryptsetup is called to do the initial encryption, format, and open.   This is done with a live ubuntu running.  In fact the whole process occurs before a reboot, so you are in and out of the ubuntu install, with a chroot terminal and a normal root terminal.  Mr. Eve states, "The way that I achieved this was to follow a modified version of Mark Loiseau's excellent guide on encrypting using aes-xts-plain64."  I can't seem to find this, yet.

This is the code to do cryptsetup:
```

sudo dd if=/dev/urandom of=/mnt/root/root/keyfile bs=1024 count=4 > keyfile      # generate a key file, instead of entering it...

sudo cryptsetup luksFormat -c aes-xts-plain64 -s 512 -h sha512 /dev/sdc4 keyfile  # partition 4 is the root file system, 
                                                             # setting up encryption format
sudo cryptsetup --key-file keyfile luksOpen /dev/sdc4 crypt           # just opens the 'file'.  'crypt' is like a label, I believe as it's related to the dev mapper
                                                       # in the mk file system step next.
sudo mkfs.ext4 /dev/mapper/crypt                                      # the file system encryption

```

The next step is to complete the ubuntu install onto these drive partitions.  Skip to the nutshell if this boars you.

The problem I seems to have is that when I step though the install, I have to edit the partitions and set items like mount points.  The suggested mount point by Mr. Eve is that '/dev/mapper/crypt', as root, as is the 'root' of the OS partition (although he says this in different places).  Down the 'window' is the physical drives, where the 'root' partition is also.  When I try to continue, it states that two devices(?) have the same mount point.  That being 'dev/mapper/crypt' and the Linux root drive.  I've tried to remove one, but it says it won't be able to use it if I proceed.  It's not very clear here what is happening, so if anyone out there has any idea, please elaborate.

In a nutshell

The death point is when is asks to write this to the disk.  The installer claims one of two things, that we have two mounted at the same mount point (i.e. '/dev/mapper/crypt' and the OS root). The other side is when I remove it so it doesn't conflict, it says I won't be able to access it if it doesn't have a mount point.

It may be as simple as ignoring one of the messages (somehow I doubt it), and letting it install.  I guess I'm lost on the encryption software works.

Thanks for wading though all of this and any assistance you can be.

Jack

---

### Post by sandyd on 2015-09-16
Hi, can you post the following
- Screenshot of install window at the partitioning stage where two root partitions are enabled
- ```

sudo fdisk -l
sudo parted -l
```

---

### Post by Jack_Wilborn on 2015-09-18
I was running a live CD of ubuntu at the time and could never get it installed properly, as I was trying to get it up on a new 3 TB drive.  After failing to install (multiple times), I finally re-formatted and installed Debian.   I needed to get the box up again.  I will attempt this again and when I do I'll keep that in mind.  I have never used encryption (as in 'full disk' before), although the guide I followed is by Mr. Martin Paul Eve.  You can find the guide pretty easily if you google '"mark loiseau" guide'.  I will do that and capture it next time, but hit the end with the encryption and when I couldn't get the installer in ubuntu to work, I went back to Debian.

Thanks

Jack

---

### Post by sandyd on 2015-09-18
> **Jack_Wilborn said:**
> I was running a live CD of ubuntu at the time and could never get it installed properly, as I was trying to get it up on a new 3 TB drive.  After failing to install (multiple times), I finally re-formatted and installed Debian.   I needed to get the box up again.  I will attempt this again and when I do I'll keep that in mind.  I have never used encryption (as in 'full disk' before), although the guide I followed is by Mr. Martin Paul Eve.  You can find the guide pretty easily if you google '"mark loiseau" guide'.  I will do that and capture it next time, but hit the end with the encryption and when I couldn't get the installer in ubuntu to work, I went back to Debian.

Thanks

Jack

I haven't used the Ubuntu Desktop installer in a while, but if I remember correctly, it only supported full disk encryption. As a result, I went back to take a look at Ubuntu Server.

This includes screenshots, but it seems i'm limited in the number of images I can have in a post, so i will just leave a link.....
If you want to view the screenshots + instructions, see imgur gallery -> [http://imgur.com/a/6sfKG](http://imgur.com/a/6sfKG)

After going through keyboard detection, user creation, etc, I landed at the following partition screen.
[http://i.imgur.com/5gEonsSs.png](http://i.imgur.com/5gEonsSs.png)
I chose manual and ended up here. There were no partitions nor a partition table on the drive, so I went to create one by selecting the drive and pressing <ENTER>
[http://i.imgur.com/5U9D0vJ.png](http://i.imgur.com/5U9D0vJ.png)

It resulted in this. I then navigated over to free space and hit enter.
[http://i.imgur.com/Y9OYiRj.png](http://i.imgur.com/Y9OYiRj.png)
Choose to create a new partition
[http://i.imgur.com/CqnnSFy.png](http://i.imgur.com/CqnnSFy.png)
Boot partition needs to be unencrypted and is 1G because I don't feel the need to ever delete any kernels (I'm lazy?)
[http://i.imgur.com/uQywR3a.png](http://i.imgur.com/uQywR3a.png)
Partition created is a primary partition
[http://i.imgur.com/iNoa0yR.png](http://i.imgur.com/iNoa0yR.png)
It's stored at the front because I have a tendency to think of the first partition as the boot partition.
[http://i.imgur.com/f0U0gM5.png](http://i.imgur.com/f0U0gM5.png)
Set the mount point as /boot, bootable flag as on, and went on.
[http://i.imgur.com/QbaZMRW.png](http://i.imgur.com/QbaZMRW.png)
Now looks like this
[http://i.imgur.com/FCBnupC.png](http://i.imgur.com/FCBnupC.png)
===== Create encrypted partition =====
I now create another partition that will be encrypted. Create the partition as normal, when you get to the step where you set the mount point, choose the following options. The partition can be logical or primary, it doesn't really matter. You can choose to erase the previous data if you want.
[http://i.imgur.com/aGZChQ3.png](http://i.imgur.com/aGZChQ3.png)
It now looks like this
[http://i.imgur.com/sCCmtoA.png](http://i.imgur.com/sCCmtoA.png)
The partition is not setup yet, choose "Configure encrypted volumes", and choose to apply changes to disk.

Here, choose "Finish" and type in a passphrase.
[http://i.imgur.com/vi1didC.png](http://i.imgur.com/vi1didC.png)
It now looks like this
[http://i.imgur.com/WAOY9KO.png](http://i.imgur.com/WAOY9KO.png)
There are two ways you can now go, they are both here. Read through them to see which one you like

a) Encrypted LVM (recommended)
Creates an encrypted partition with a LVM physical volume in it. It's useful when you want to have multiple encrypted 'partitions', but one password to unlock them all. LVM also makes resizing the partitions not a pain and allows you to add additional disks to the LVM pool when you run out of space

b) Traditional encrypted partition
Creates a single filesystem in the now-encrypted partition.

===== Continuing Setup (Encrypted LVM) =====
So now, I go create a LVM physical volume in the encrypted partition. Choose the encrypted volume and press enter
[http://i.imgur.com/FGYK3w7.png](http://i.imgur.com/FGYK3w7.png)
Change "Use As" to "Physical Volume for LVM"
[http://i.imgur.com/aGZChQ3.png](http://i.imgur.com/aGZChQ3.png)
LVM now shows up under the encrypted volume
[http://i.imgur.com/Ow4sgjY.png](http://i.imgur.com/Ow4sgjY.png)
Choose "Configure Logical Volume Manager"
[http://i.imgur.com/RX3XLqB.png](http://i.imgur.com/RX3XLqB.png)
Choose "Create Volume Group"

Typed in a name for my volume group
[http://i.imgur.com/lj79VOa.png](http://i.imgur.com/lj79VOa.png)
For some reason, the installer has never been able to only show LVM physical volumes in the list, but it doesn't matter. Choose the first one that starts with "/dev/mapper" and ends in "crypt" by pressing spacebar.
[http://i.imgur.com/ZARiBD5.png](http://i.imgur.com/ZARiBD5.png)

We now have our volume group and physical volume setup. We can go ahead and setup some logical volumes for home (/home) and root (/)
[http://i.imgur.com/gQLilYa.png](http://i.imgur.com/gQLilYa.png)
Choose "Create Logical Volume". We only have one volume group, so just hit enter on the next screen

Give a name
[http://i.imgur.com/lj79VOa.png](http://i.imgur.com/lj79VOa.png)
I created a 5G root which is quite unusable for an actual desktop system.
[http://i.imgur.com/tCgtOpV.png](http://i.imgur.com/tCgtOpV.png)
Repeat for /home and then choose finish

The LVM entries are now here and usable.

Select each LVM, and change the root FS to something other than "do not use". I suggest ext4. I started with the root partition, so I set the mount point to root (/).

Now looks like this.
[http://i.imgur.com/rlyge25.png](http://i.imgur.com/rlyge25.png)
Repeat for /home

Now looks like this
[http://i.imgur.com/MmGB9EU.png](http://i.imgur.com/MmGB9EU.png)
This is what happens when you forget swap space, I went back and re-created the /home LV so that I could get a swap partition....
[http://i.imgur.com/BGtJwcR.png](http://i.imgur.com/BGtJwcR.png)
Now looks like this, after creating the swap partition, I set the LV to be used as swap.
[http://i.imgur.com/PYk8eo6.png](http://i.imgur.com/PYk8eo6.png)
Seems to be installing properly, i'm going to go upload this as an imgur gallery while it does that...
[http://i.imgur.com/sdiKju9.png](http://i.imgur.com/sdiKju9.png)
===== Continuing Setup (Traditional encrypted partition) =====
After creating the encrypted partition, it should already have formated the encrypted partition as ext4, simply set the boot as /root, and you can go on. You will need to create another encrypted partition for the swap if you want any.

---

### Post by Jack_Wilborn on 2015-09-21
Thanks for all the help and it answered a couple of questions.  I pulled the Hard drives out of my desktop and replaced it with a 500 GB hard disk for a laptop, and attempted an install on that.  Every time, it failed at the grub installation.  At which point, I clicked OK on the GUI with the error message and it hung.  I tried both the netinst and DVD install with the same results.

However back to the point..  I was attempting this on my Debian system, but didn't like having to enter the passphrase for every partition on boot (5 I think).  I found this 

[https://www.martineve.com/2012/11/02/luks-encrypting-multiple-partitions-on-debianubuntu-with-a-single-passphrase/](https://www.martineve.com/2012/11/02/luks-encrypting-multiple-partitions-on-debianubuntu-with-a-single-passphrase/)

and was following what he was doing on a ubuntu system.  That's what started down the trail...  You went far beyond what I asked and am very indebted to you and your types that go the extra mile knowing it will help someone.  Maybe I should just try your version, for some reason I never thought to check as ubuntu is a Debian clone.  I assume this works on multiple partitions with only one passphrase entry?  Which is the basic problem I was trying to solve..

I now have a ubuntu 15.X.X on this machine, could never get any of the 14.X versions to load, all died on the grub2 stage (even a straight install.)

Thanks again...

Jack

---

### Post by sandyd on 2015-09-23
> **Jack_Wilborn said:**
> Thanks for all the help and it answered a couple of questions.  I pulled the Hard drives out of my desktop and replaced it with a 500 GB hard disk for a laptop, and attempted an install on that.  Every time, it failed at the grub installation.  At which point, I clicked OK on the GUI with the error message and it hung.  I tried both the netinst and DVD install with the same results.

However back to the point..  I was attempting this on my Debian system, but didn't like having to enter the passphrase for every partition on boot (5 I think).  I found this 

[https://www.martineve.com/2012/11/02/luks-encrypting-multiple-partitions-on-debianubuntu-with-a-single-passphrase/](https://www.martineve.com/2012/11/02/luks-encrypting-multiple-partitions-on-debianubuntu-with-a-single-passphrase/)

and was following what he was doing on a ubuntu system.  That's what started down the trail...  You went far beyond what I asked and am very indebted to you and your types that go the extra mile knowing it will help someone.  Maybe I should just try your version, for some reason I never thought to check as ubuntu is a Debian clone.  I assume this works on multiple partitions with only one passphrase entry?  Which is the basic problem I was trying to solve..

I now have a ubuntu 15.X.X on this machine, could never get any of the 14.X versions to load, all died on the grub2 stage (even a straight install.)

Thanks again...

Jack
Sadly, the Ubuntu installer, even in the server form, does not offer keyfile functionality, only passkey functionality. It's why I suggested using LVM, as you can create "volumes" in LVM. There is not much need for multiple partitions on a Ubuntu install unless you have multiple drives and/or a dual boot. As a result, you would only need to create one encrypted partition for one physical LVM volume that contains multiple LVM logical volumes.

---

