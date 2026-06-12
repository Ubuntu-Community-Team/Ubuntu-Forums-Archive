---
title: "Drive Imaging from within Ubuntu"
date: 2008-10-01
forum: New to Ubuntu
---

### Post by AlbinoClock on 2008-10-01
I'm running hardy in the first partition of my master drive and have an XP install on my slave. I'd like to clone the windows drive and put it on the second partition of this drive for a dual-boot. Is it possible to clone a drive from within Ubuntu?

---

### Post by PocketDog on 2008-10-02
Tricky. Actually cloning and moving the Windows drive/partition is pretty simple. But Windows will try to operate from the original location - requiring you to re-label the partition at least. Editing Window's registry and boot.ini to re-point all instances of, say, E: to D: may be required otherwise. Which, of course, is also tricky becaue you'll be trying to use a Windows installation which won't boot. So, while it's theoretically possible, lots of things can (will?) go wrong. They're better off on seperate drives anyway. Please re-consider :lol:

---

### Post by Rolcol on 2008-10-02
Like PocketDog said, It seems possible to image to a partition as long as you don't overwrite the MBR.  Is the partition the same size as the partition/drive of the other one with windows?  You should only image the partition because imaging the whole drive will also copy over the MBR.  You should be able to image it like this: (as root or sudo)```
dd *if=/dev/sdb1* **of=/dev/sda3** bs=1M
``` The *italicized* text is the slave drive first partition.  The **bolded** text is the master drive 3rd partition assuming that the first is ubuntu's root and the second is an extended partition for swap.  Another thing you could do is get an md5 checksum as you're imaging so you can check both partitions for consistancy.  I'm not positive that this works but:
```
dd *if=/dev/sdb1* ibs=1M | tee **/dev/sda3** | md5sum -f -
```

---

### Post by AlbinoClock on 2008-10-02
I tried sudo dd etc on the right partitions in the way you said to and my terminal is now doing something that it's not telling me about (or at least not bringing me back to the prompt), I don't hear any drives being accessed though. Do I need to install something for dd to work?

PocketDog, you said to keep them on separate drives. How do I dualboot from a master and slave? I'd prefer to get a bit more room out of the whole process but as long as I can get both OSes running I'd be pretty happy.

---

### Post by b0b138 on 2008-10-02
Are you dual booting now?

---

### Post by KillerSponge on 2008-10-02
You can't move Windows from one disk to another and expect it to boot. Because it won't, believe me, I've tried ;)

It's like PocketDog said, all the drive letters will change, which will confuse the hell out of Windows. It is a lot easier and faster to just reinstall it.

---

### Post by AlbinoClock on 2008-10-02
> **b0b138 said:**
> Are you dual booting now?

No, I put an empty drive on master and moved the xp drive over to slave hoping that I could work on it from the ubuntu install.

If this stuff doesn't really work what's up with Norton Ghost? Could I use that instead?

---

### Post by b0b138 on 2008-10-02
There is a chance moving it would work as windows wouldnt know what to do with an ext3 partition and still call the second partition c:  Maybe. I guess you could unplug your windows drive, boot to an xp disk, get to the partitioning and see what it would call that second partition.

But then again, why would you want it on a second partition if its already on a seperate drive?

---

### Post by ubername on 2008-10-02
> **AlbinoClock said:**
> I'm running hardy in the first partition of my master drive and have an XP install on my slave. I'd like to clone the windows drive and put it on the second partition of this drive for a dual-boot. Is it possible to clone a drive from within Ubuntu?

Are you using Grub?

I have a setup with Ubuntu ntrepid on a partition of a USB hard drive, and Hardy and Windows Vista on various partitions of my only hard drive in the main machine. Grub can handle it.

---

### Post by b0b138 on 2008-10-02
Oh ok. You should put xp back as master (since thats where it was and the drive assignments wont get screwy) and install ubuntu to the second drive. The installer will see xp and automaticlly let you dual boot

---

### Post by halitech on 2008-10-02
XP (and windows in general) doesn't play well if its not installed on the primary master (that being said I had a system with a dead primary controller and got it to load on secondary master) so put your XP disk back and then install Ubuntu. Tell it to install on sdb (second hard drive seen as windows should show as sda) and then install grub to the mbr and it will let you pick which OS to boot when you start the computer.

---

### Post by ubername on 2008-10-02
I really don't think you need to move your operating systems to different partitions - you just need to use something like Grub to point to the right drives when you boot.

---

### Post by AlbinoClock on 2008-10-02
> **b0b138 said:**
> There is a chance moving it would work as windows wouldnt know what to do with an ext3 partition and still call the second partition c:  Maybe. I guess you could unplug your windows drive, boot to an xp disk, get to the partitioning and see what it would call that second partition.

I'll give that a shot but I still need to get something like dd working.

> But then again, why would you want it on a second partition if its already on a seperate drive?

Normally this machine has a 30gb drive with XP and an 80gb with media, which is starting to fill up. I would like to replace this setup with an 80gb drive partitioned as master and leave my media drive as slave. If I were to install Ubuntu on what would become the new media drive I'd have even less space instead of significantly more.


What if I put windows on the primary partition and ubuntu on the second?

---

### Post by PocketDog on 2008-10-02
If you're looking at re-installing, that makes things easier. Install XP first (it's simpler) on the primary, then install Ubuntu afterwards, re-sizing the XP partition during the Ubuntu install to put both OSs on the first drive. All that's pretty straightforward. That'll leave you dual-booting with your slave drive free for data for either OS to use

___

edit:

To add to the above: if you're really concerned about moving Windows intact, while keeping installed programs you don't want to lose, then moving the partition wholesale will almost certainly royally mess up your installation. It's theoretically possible but difficult and risky.
Re-installing both OSs on the first drive won't affect the media already stored on the slave Windows drive - it'll just make the original OS on the slave drive unbootable (You *may* be able to boot both XP installs using something like Paragon Partition Manager but then things get complicated). You'll still be able to access the videos/photos/music/etc on it using the XP or Ubuntu installations you install.

Does that make sense? I've read it twice and it kinda does to me ;)

---

### Post by AlbinoClock on 2008-10-03
> **PocketDog said:**
> If you're looking at re-installing, that makes things easier. Install XP first (it's simpler) on the primary, then install Ubuntu afterwards, re-sizing the XP partition during the Ubuntu install to put both OSs on the first drive. All that's pretty straightforward. That'll leave you dual-booting with your slave drive free for data for either OS to use

___

edit:

To add to the above: if you're really concerned about moving Windows intact, while keeping installed programs you don't want to lose, then moving the partition wholesale will almost certainly royally mess up your installation. It's theoretically possible but difficult and risky.
Re-installing both OSs on the first drive won't affect the media already stored on the slave Windows drive - it'll just make the original OS on the slave drive unbootable (You *may* be able to boot both XP installs using something like Paragon Partition Manager but then things get complicated). You'll still be able to access the videos/photos/music/etc on it using the XP or Ubuntu installations you install.

Does that make sense? I've read it twice and it kinda does to me ;)

It does. Thank you. There are a couple of things that I'm concerned about reinstalling but I guess I'll give it a shot. I once successfully moved a program from Windows to Linux by moving registry keys, do you happen to know if this is possible from Windows to Windows?

---

