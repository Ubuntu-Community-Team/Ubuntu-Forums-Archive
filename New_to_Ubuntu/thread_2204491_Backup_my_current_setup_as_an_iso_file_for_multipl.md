---
title: "Backup my current setup as an iso file for multiple installs"
date: 2014-02-08
forum: New to Ubuntu
---

### Post by Benjamin5th on 2014-02-08
I have done some research on this topic but most resources are outdated. What I am trying to do is setup either Ubuntu, Lubuntu, or Puppy Linux and then back it up as an iso file so I can install it on multiple computers. The reason is I am going to be updating lots of friends and family members old Windows XP computers, and will be doing some serious themeing to help them get used to Linux. I would rather do this once instead of 10+ times. 

Any way to do this? Preferable easy with no terminal work but I'll do what I have to.

---

### Post by david98 on 2014-02-08
Would it not be easier just to clone your hdd drive this has helped me save a lot of time in the past here's a quick tutorial [http://www.howtogeek.com/howto/19141/clone-a-hard-drive-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/19141/clone-a-hard-drive-using-an-ubuntu-live-cd/). Hope this helps

---

### Post by Benjamin5th on 2014-02-08
So how do I transport this new drive? use a DVD/Flashdrive?

---

### Post by monkeybrain20122 on 2014-02-08
If you want them to be identical installations you can clone the original install with fsarchiver and restore it to different targeted machines. 

 Unlike clonezilla it doesn't have restrictions on the size of the target as long as it is big enough to hold the contents so it is ideal for installing to different machines with varying hard drive capacities.  (clozilla requires that the target partition has to be >= the  originally one even if the original one is mostly empty, so it may be  good for backup purpose but not very good  if you want to restore to other machines or external drives where the size of the partitions may well be smaller)

It doesn't make .isos, but archives called .fsa files. However it is fast and easy to use and very reliable, I have used it for such purpose with great success (except for Fedora it is a bit tricky..)

You can run fsarchiver even when you are using your computer (use the options -a and -A : sudo fsarchiver -a -A savefs ...) So you can install fsarchiver in the machine you want to clone, create the clone with it and store the .fsa file in an external storage. Make a Ubuntu live usb with fsarchiver installed for restoring to other machines,--so need to make the live usb with persistence, or alternatively get the rescue cd with fsarchiver following the links in the fsarchiver website, see link below. Boot the targeted machine off the live usb, then attach the storage where the .fsa file is and run fsarchiver in the live usb to restore the .fsa to the target machine.

[http://www.fsarchiver.org/Main_Page](http://www.fsarchiver.org/Main_Page)

---

### Post by Benjamin5th on 2014-02-08
Oh okay, this seems better, so I just use fsarchiver to install it onto the new computer or do I use a different program for that?

---

### Post by monkeybrain20122 on 2014-02-08
See my edit.

---

### Post by Benjamin5th on 2014-02-08
Okay, thanks ;)

---

### Post by monkeybrain20122 on 2014-02-08
To save you some time from reading the manual, there are only two commands you need. 
To clone /dev/sda1 without directories A and B:
```
sudo fsarchiver -v -jn -zn -a -A savefs /path/to/storage/backup.fsa /dev/sda1 --exclude=directory_A --exclude=directory_B 
```

Here -jn is the number of thread used, n= 2.. etc. -zn is the compression level, n can be 2, 3 etc. see fsarchiver's quickstart guide to find the level that suits you.  /path/to/storage.. is the path to the storage device where you want to save the .fsa file which is called "backup.fsa" here. -a and -A if you want to clone drives which are currently mounted and running. If you are cloning drives that are not mounted (say you clone with the live usb booting off your original machine) then you don't need them. -v for verbose, it is good to have outputs on the terminals or I get nervous. :) --exclude=.. are optional for you to exclude directories. For examples, --exclude=Downloads --exclude=Music  etc. In terminal type man fsarchiver for options.

To restore clone to sda2 in same or other machines
```
sudo fsarchiver -v -jn restfs /path/to/storage/backup.fsa id=0,dest=/dev/sda2
```

Edited: if your usb driver for making the live usb is big enough to hold your .fsa file you won't need an additional storage device. Just make an extra partition in your usb drive for that purpose (I would format it to ext4 but it shouldn't matter as long as it supports the partition size,--FAT doesn't e.g)

---

### Post by bc.haynes on 2014-02-08
Thank you, I'm glad I found this. You're pretty smart for a monkeybrain.

Can you copy backup.fsa to a large USB stick and use it to install multiple machines?

---

### Post by monkeybrain20122 on 2014-02-08
> **bc.haynes said:**
> Thank you, I'm glad I found this. You're pretty smart for a monkeybrain.

Can you copy backup.fsa to a large USB stick and use it to install multiple machines?

Yeah. But if you format your usb stick to FAT it will only support 4 Gs, so format it to Ext4, e.g. If you have a large usb stick you can make a small FAT partition for a live usb with persistence where you install fsarchiver and a large partition to hold the .fsa file. 

I don't use a usb for this as I have a full blown Ubuntu installation on an external driver which I boot off different machines. I install fsarchiver there and use it to clone and restore other Linux installs and simply store the .fsas in the Downloads dirctory there, but idea is the same.

---

### Post by bc.haynes on 2014-02-09
Thanks, again.

---

### Post by Nopposan on 2014-03-20
Hiyaah!

I am definitely going to try this with my Lubuntu install. Much faster than dd, right? 'Been looking for something like this.

Thanks.

I'll get back to you to tell you how it went.

---

### Post by Nopposan on 2014-03-20
Besides hard-drive capacity, what is the danger of cloning to a machine that is different? I mean, let's say both are i386 but the source is a Toshiba laptop and the target's a Dell? Will the OS run on the Target? Or, will it be all screwy?

'Sorry. I know that there will sometimes be hardware differences, like different graphics cards, that will cause problems, but I was wondering what your experience is as you sound as though you have plenty of experience cloning drives to other machines. I'm just wondering to what extent we need to make sure we have clones that are customized just for certain machines. Mostly we'll be working on old laptops and trying to keep them out of the scrap heap. It would be fantastic if we could clone, rather than start with a fresh install, even to computers that aren't sharing all of the same hardware.

Please advise.

Thanks.

---

