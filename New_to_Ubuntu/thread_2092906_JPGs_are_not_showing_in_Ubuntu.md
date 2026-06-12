---
title: "JPGs are not showing in Ubuntu"
date: 2012-12-09
forum: New to Ubuntu
---

### Post by mrnewtothis on 2012-12-09
I set up a dual boot system with XP pro and Ubuntu 10 4 and I have a plug and play hard drive that I store stuff on that I do not want to loose, or that I may need to move to a laptop with win 7 on it. Things like photographs on it.

The plug and play is formatted as NTFS.

The problem is that some folders full of JPGs, not all. are showing as empty in Ubuntu, it may be other folders but not totally sure.
One folder that is full is empty and the another is showing ten photographs out of seventy or more.

I tried copying the contents to a second folder.
Tried to look at them in the new Ubuntu 12 but they are still missing.

Is there a way to make them appear and hopefully without loosing the tags.

Thanks for any help

I have got enough room on hard drive to reformat the second disc, if needed.

---

### Post by Impavidus on 2012-12-09
Do any of the jpegs have a file name starting with . (that is, full stop)? If so, they are considered hidden files on ubuntu. You can make them visible in your file manager by typing control-h.

---

### Post by rnerwein on 2012-12-09
> **mrnewtothis said:**
> I set up a dual boot system with XP pro and Ubuntu 10 4 and I have a plug and play hard drive that I store stuff on that I do not want to loose, or that I may need to move to a laptop with win 7 on it. Things like photographs on it.

The plug and play is formatted as NTFS.

The problem is that some folders full of JPGs, not all. are showing as empty in Ubuntu, it may be other folders but not totally sure.
One folder that is full is empty and the another is showing ten photographs out of seventy or more.

I tried copying the contents to a second folder.
Tried to look at them in the new Ubuntu 12 but they are still missing.

Is there a way to make them appear and hopefully without loosing the tags.

Thanks for any help

I have got enough room on hard drive to reformat the second disc, if needed.
are they shown in windows XP ? try that first !

---

### Post by rnerwein on 2012-12-09
> **mrnewtothis said:**
> I set up a dual boot system with XP pro and Ubuntu 10 4 and I have a plug and play hard drive that I store stuff on that I do not want to loose, or that I may need to move to a laptop with win 7 on it. Things like photographs on it.

The plug and play is formatted as NTFS.

The problem is that some folders full of JPGs, not all. are showing as empty in Ubuntu, it may be other folders but not totally sure.
One folder that is full is empty and the another is showing ten photographs out of seventy or more.

I tried copying the contents to a second folder.
Tried to look at them in the new Ubuntu 12 but they are still missing.

Is there a way to make them appear and hopefully without loosing the tags.

Thanks for any help

I have got enough room on hard drive to reformat the second disc, if needed.
are they shown in windows XP ? try that first !
are you unplug the drive savely ( then the buffers are synced) if not you are the loser.
hope you will get your pictures back.
cheers

---

### Post by Impavidus on 2012-12-09
> **rnerwein said:**
> are they shown in windows XP ? try that first !
are you unplug the drive savely ( then the buffers are synced) if not you are the loser.
hope you will get your pictures back.
cheers
Indeed, always remove your drive savely. Unlike windows, linux doesn't automatically sync usb drives after each write, so if you write something and then simply pull the plug the files may not be on the removable drive.

---

### Post by Bartender on 2012-12-09
What do you mean a "plug & play" drive?

Is this an off-the-shelf external HDD, like a Seagate FreeAgent or a WD MyBook?  Almost all of them have a small circuit board inside with firmware that's designed to recognize & interact with a Windows PC.  My worst experience was with a WD that tried to install itself as a virtual CD-ROM.  It was useless in Linux.  

I finally ripped the thing open, then stuck the HDD into a dock.  No problems after that.  

However, Ubuntu couldn't access *any* of the data on that WD drive.  It sounds like you're able to access some of the data.

+1 on previous comments - plug the thing into a couple of Windows PC's and see what happens.

Hey, I found this [old thread]("http://ubuntuforums.org/showthread.php?t=1612483") of mine, from when an external went sideways.

Try running chkdsk from a Windows PC, as described in the thread.

If I understand it correctly, Linux writes to an external USB device differently than Windows.  It's important to properly unmount any USB device before unplugging!

---

### Post by mrnewtothis on 2012-12-09
[Impavidus]("http://ubuntuforums.org/member.php?u=1417721")
 
no there is no full stop, They are named with a date and the name like 23 11 12 Louie.
 
[rnerwein]("http://ubuntuforums.org/member.php?u=972890")
 
Yeah they still show up in XP and win 7.
 
yeah I noticed there was some difference when switching from ubuntu to win 7 I ended up with a trash file, as ubuntu had not deleted the files after delete and I think I forgot to empty the bin before switching.
 
[Impavidus]("http://ubuntuforums.org/member.php?u=1417721")
 
These were created in XP, which is a puzzle.
 
[Bartender]("http://ubuntuforums.org/member.php?u=52039") 
 
it is one of those USB boxes you add your own hard drive into.
 
I'll try run chkdsk and see if that helps.
 
 
Thanks for the answers I will try out the suggestions and get back.

Just completed the disk check and it is working. Now I can see all the files in all of the folders thanks again for all the help.

Not sure how to mark this as answered.

---

