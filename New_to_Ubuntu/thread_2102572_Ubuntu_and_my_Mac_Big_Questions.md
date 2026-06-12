---
title: "Ubuntu and my Mac: Big Questions"
date: 2013-01-07
forum: New to Ubuntu
---

### Post by Camerin on 2013-01-07
**Computer Specifications:** Mid-2011 iMac, 21.5-inch model.
**Tool used to boot Ubuntu:** rEFIt.
**Version of Ubuntu:** 12.10.

Hello.

Recently, I decided it was time for a change, so I burned an ISO of Ubuntu 12.10 on to a DVD, installed rEFIt on to my iMac, and gave Ubuntu a try.  I liked what I saw, so I decided to give 100GB of my 500GB drive to Ubuntu.  I did this through Mac's Disk Utility (by simply dragging my current Macintosh HD partition up and creating free space for Ubuntu).

While I was using Ubuntu from the CD, my Apple Wireless Mouse and Wireless Keyboard weren't functioning all too well.  The mouse would work after a few seconds, but it took a lot of keyboard moving and hitting the 'discoverable' button to get the keyboard to show up properly.  I finally got the keyboard to work, though, and I installed Ubuntu alongside Mac OS X.  Once it was finished, I shut the computer down, took out the disk, and used rEFIt's Partitioning Tool to make sure my tables were in sync.  The tool said they were, so I started up Ubuntu.

Unfortunately, my keyboard and mouse would not connect to Ubuntu this time.  Nothing I did would work.

I currently have no USB mouse or keyboard, nor do I have the money to run out and buy one.  As a result, I have this great Ubuntu partition on my computer that I can't use!

I decided to open up Disk Utility in OS X and take a look at my new Ubuntu partition.  What I saw there was a little strange.  The Partition screen still showed a bunch of free space where my Ubuntu partition should be.

For reference, here is a screenshot of what I mean:

The disk03, disk04, and disk05 options are partially invisible because Ubuntu asked to unmount them during the install.  I cannot mount any of those disks, and my computer tells me they need to be repaired.

Everything on my Mac works absolutely fine.  There are no booting problems of any sort.  Ubuntu also boots perfectly, too, and the only reason I'm not using it is because I can't use my keyboard or mouse.

So, here are my questions.

1.  Is something wrong with my Ubuntu partition?
2.  If so, how do I remove it?  I still have the CD I used to install Ubuntu.

3.  If nothing is wrong with my partition and I am just being paranoid, is there any way I can get my keyboard and mouse to work with Ubuntu?  I really do want to use it (hence why I installed it!).

The first question is the most important.  I need to know ASAP if there is a problem with my install and, if so, how to fix it.

Any assistance for this first-time partitioner would be of great value.

Thanks!

---

### Post by iMac71 on 2013-01-07
if you've downloaded the 64-bit PC (AMD64) desktop image, you might try to substitute it with the[ 64-bit Mac (AMD64) desktop image]("http://releases.ubuntu.com/quantal/ubuntu-12.10-desktop-amd64+mac.iso") which should be more specific for your computer.

---

### Post by Camerin on 2013-01-07
I don't think I understand you.  I downloaded the 64-bit ISO from here and saw no option for a Mac version.

---

### Post by jerome1232 on 2013-01-07
> **Camerin said:**
> I don't think I understand you.  I downloaded the 64-bit ISO from here and saw no option for a Mac version.

His link is a direct link to the download. Click it.

---

### Post by tgalati4 on 2013-01-07
I'm not sure if the Mac Disk Utility can read or write to ext4 partitions, so you would need to verify that before using the Mac Disk Utility to check those partitions.  The DVD/CD boot menu has a "Check Media" option that will go through and check the files and checksums for the entire disk.  This can take several minutes, but it lets you know if you have a good install disk.

---

### Post by iMac71 on 2013-01-07
> **tgalati4 said:**
> I'm not sure if the Mac Disk Utility can read or write to ext4 partitionsthese partitions are greyed, i.e. they're unreadable by Mac Disk Utility.

---

### Post by tgalati4 on 2013-01-08
That is what I thought.  So you need other methods to ensure their integrity.  Do your partition checking with a Live Ubuntu CD (if you can get it to boot properly) or a Live USB and use gparted or fsck tools.  Use the Mac Disk Utility to only check and repair the Mac partition.  Since it is greyed out, you should be OK, but don't think in the future you can simply expand the Mac partition without borking your Ubuntu install.

I have an older powerbook, so I can't help with your trackpad/keyboard issue.  I would track down an optical mouse to use in the meantime, because it is difficult to navigate without one.  You can install a soft keyboard such as:

matchbox-keyboard - on-screen keyboard
xvkbd - software virtual keyboard for X11

Start searching the garage sales.  If you can afford a Mac, you can certainly afford a $2 used mouse.

---

### Post by iMac71 on 2013-01-08
for managing OS X partitions from Ubuntu, you might install [hfsplus tools]("https://launchpad.net/ubuntu/+source/hfsplus"); all these tools are accessible from the command line, i.e. the Terminal.

---

