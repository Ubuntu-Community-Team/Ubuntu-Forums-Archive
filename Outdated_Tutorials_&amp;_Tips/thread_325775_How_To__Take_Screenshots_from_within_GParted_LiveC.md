---
title: "How To:  Take Screenshots from within GParted LiveCD"
date: 2006-12-26
forum: Outdated Tutorials &amp; Tips
---

### Post by Bartender on 2006-12-26
Partitioning questions are fairly common on the forums.  I've been experimenting with the GParted Live CD (GPLCD) and think it's a great tool.  However, trying to describe how to do something within GPLCD via text is virtually impossible.  Screenshots are really worth a thousand words.

Below is a guide to saving screenshots from GPLCD to a thumbdrive so you can attach to a post.

First off you'll need a [GPLCD]("http://gparted.sourceforge.net/livecd.php") 
Once you download the latest version, burning to a CD is just like burning a Linux .iso.  Then you boot from the CD just like an install CD.  

Once GPLCD comes up, you'll need to locate three of the icons in the panel.  There's a screenshot icon, a terminal icon, and one for Thunar, a file browser.  (Note:  Twice now the panel has come up incorrectly.  I could only see the top of it.  I right-clicked on the panel, clicked on "Customize Panel", then bumped the pixels up from 48 to 50.  The panel displayed properly.  I bumped the pixel count back to 48 and it still displayed properly, so it's just a glitch)

I stumbled onto a [sticky]("http://gparted-forum.surf4.info/viewtopic.php?id=191") at the GPLCD forum that explains how to mount a USB drive while working from within GPLCD. Pasted  below is the part that's the most helpful...

[COLOR="Blue"]Open a terminal from the panel, by clicking the terminal icon
and then type the following :
# fdisk -ul > myfile.txt
plug your usb key
type :
# fdisk -l | grep sd*
search for your just plugged key : it could be something like sda1, or if you have sata or scsi hard disk, it could be sdb1 or even sdc1... try to guess : may be you could unplug your key and run the "#fdisk -l" command again to see the differencies...
Imagine your key is plugged on sdb1, then type :
# mkdir /tmp/usb
mount /dev/sdb1 /tmp/usb
cp myfile.txt /tmp/usb
ls /tmp/usb (there you MUST see myfile.txt !)
umount /tmp/usb
unplug your key and plug it on your pc (after you have booted your OS), to get the file and past it here ....[/COLOR]

OK, the description details how to save a .txt file.  If you just want to save screenshots, here are the modifications to the above...

I plugged my thumb drive in before even booting the GPLCD. Once GPLCD was up on the screen -

Opened a terminal 
Typed in:
```
fdisk -l | grep sd*
```

Do you know how to make that odd "|" character? On my plain jane Dell qwerty us keyboard it's the key just below "Backspace". Lower case on that key is "\", upper case looks like two dots on the key but makes that solid line on the screen.

Found the usb key as 'sdb1'

So I typed:
```
mkdir /tmp/usb
```
```
mount /dev/sdb1 /tmp/usb
```

Then I opened the Thunar file browser and looked in 'tmp'. Sure enough, the usb drive was there, and I could browse the existing files.

So I went back to the partitioner and took a screenshot, which saves to "root/gparted.jpeg".  GPLCD tells you where it's going to save the shot. When the screenshot appeared to be done, I closed the associated windows on the desktop, opened Thunar, found the root folder, found 'gparted.jpeg', right-clicked on it, and Cut it. Backed out of that folder, went to 'tmp' folder, opened the usb folder, Pasted. If you're taking multiple screenshots you'll have to rename the .jpeg or the next one will try to overwrite the previous one.  If you're only taking one screenshot you don't have to rename it.

Then before closing out of GPLCD I typed in:
```
umount /tmp/usb
```

to unmount the usb drive.

Hope that helps someone who's experimenting with a GParted LiveCD!

- This was done on a GParted LiveCD version 3.0
- "This guide is to be used at your own risk"

---

### Post by Tobyb on 2008-04-22
With the recent 0.3.6 LiveCD version of Gparted I didn't see Thunar anywhere.  

This task of copying a screenshot to a drive seems way too complicated. I'll try this instead from within my installed Ubuntu Gparted application. Okay, that's better... I can take a screenshot here...

---

