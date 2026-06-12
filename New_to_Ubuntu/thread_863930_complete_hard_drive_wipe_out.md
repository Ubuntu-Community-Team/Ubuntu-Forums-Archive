---
title: "complete hard drive wipe out"
date: 2008-07-19
forum: New to Ubuntu
---

### Post by moose4204l on 2008-07-19
is there a free prog or way to completely wipe out my hard drive so there is no data whats so ever left for recovering. i want to sell my laptop or give it to charity and i have important information on my laptop. how do i completely wipe it out?

---

### Post by pikabuntu on 2008-07-19
> **moose4204l said:**
> is there a free prog or way to completely wipe out my hard drive so there is no data whats so ever left for recovering. i want to sell my laptop or give it to charity and i have important information on my laptop. how do i completely wipe it out?
Use a live cd and use the partition editor and delete all of the partitions.  I don't think its possible to make it impossible to completely wipe everything off without destroying it, tho.

---

### Post by bab1 on 2008-07-19
Start here:
[http://www.webopedia.com/DidYouKnow/Computer_Science/2007/completely_erase_harddrive.asp]("http://www.webopedia.com/DidYouKnow/Computer_Science/2007/completely_erase_harddrive.asp")
[http://wipe.sourceforge.net/]("http://wipe.sourceforge.net/")

---

### Post by dhughes on 2008-07-19
And of course everyone's favourite Lived CD hard drive eraser Darik's Boot and Nuke (DBAN).

[http://dban.sourceforge.net/](http://dban.sourceforge.net/)

---

### Post by Inxsible on 2008-07-19
> **dhughes said:**
> And of course everyone's favourite Lived CD hard drive eraser Darik's Boot and Nuke (DBAN).

[http://dban.sourceforge.net/](http://dban.sourceforge.net/)+ 1 for DBAN. I used it on my machines before I gave them away to charity.

---

### Post by Shippou on 2008-07-19
Hello:)

Are you up to a destructive experiment?

Well, since you are REALLY PREPARED TO LOSE DATA COMPLETELY, you can tyr sudo rm -rf.

Then post your results here.

But then please read the link in my signature.

I don't want to commit another infraction.

To the mods: This is only a suggestion. 

To others: please don't flame me.

---

### Post by bumanie on 2008-07-19
Change the drive name to what your drive is but dd  will do it > dd if=/dev/zero of=/dev/sda bs=4k conv=notruncThis write zeroes over the entire drive, extrememly hard to get anything meaningful off it after. Can also use > dd if=/dev/urandom of=/dev/sda bs=4k conv=notruncThis write random data over the whole disk, again extrememly hard to get anything meaningful off it after. Otherwise dban "Boot and NUke"

---

### Post by JimBuntu on 2009-02-25
Just down loaded DBAN to a usb drive. How do I use it? Do I just stick the USB stick into the computer I want to wipe, then open the .exe file? The computer I want to wipe is an Ubuntu OS will the .exe work?

---

### Post by jaminux on 2009-02-25
From the Live CD terminal:

1) Mount the hard disk you want to wipe.

2) cd to the root of the hard disk

3) type sudo find -type f -execdir shred -u -f -z '{}' \;

All the files (I think) should be gone safely gone, and cannot be recovered. The directories will be left. To remove the directories:

sudo rm -r */

I did test this. I am by no means an expert though.

---

### Post by jaminux on 2009-02-25
> **Shippou said:**
> Hello:)

Are you up to a destructive experiment?

Well, since you are REALLY PREPARED TO LOSE DATA COMPLETELY, you can tyr sudo rm -rf.

Then post your results here.

But then please read the link in my signature.

I don't want to commit another infraction.

To the mods: This is only a suggestion. 

To others: please don't flame me.

The problem with this is (I believe) is that, contrary to popular belief, when you delete a file in the normal way the actual data on the hard disk is not gone (even when you empty the recycle bin). It can be restored.

A program like shred is required to write over the data a few times to make sure there is nothing left.

This is how police use the computers of "naughty people" as evidence against them when they commit crimes.

---

### Post by yther on 2009-02-25
DBAN may be faster, I haven't tried it.  What I do is boot up a copy of System Rescue CD and type in "shred -n 10 /dev/sda"... then I come back in a few hours.  (The default is 25 passes, which takes waaaay too long for large drives.)  This writes random junk to the entire drive, blowing away all files, directories, partitions, etc.  Unless you're worried about professional spooks reading your files, this should be more than sufficient.

Of course this is a general-purpose LiveCD so it takes a minute or two to boot up.  The "Boot & Nuke" disc does one thing only, so I imagine it might be quicker to get started.  :)

(I think I just like the fact that I'm using a "rescue" CD to destroy data.  Ho ho ho.)

---

### Post by JimBuntu on 2009-02-25
Ok so how do you use DBAN?

---

### Post by Philo1 on 2009-02-25
Simply download the app: [http://www.dban.org/](http://www.dban.org/)

From there you can burn it onto a cd/dvd or utilize a usb key if you wish.

After post it should load the kernel and take you into a area where you can automatically take the default option and start wiping. Otherwise, I believe you can hit "f6" or something along those lines. (The options are displayed) This will take you into an area where you can select the partitions on the drive to wipe and wipe method.

---

### Post by anjilslaire on 2009-02-25
```
dd if=/dev/zero of=/dev/hda
```

should be sufficient

---

### Post by egalvan on 2009-02-25
> **JimBuntu said:**
> Ok so how do you use DBAN?

If you downloaded the CD image (iso file), then just burn it to a blank CD. Note... it must be burned as an image.

If you downloaded the .exe file for floppy or thumb-drive, then you will need a DOS/Windows machine to execute this file.
Running the .exe will copy the program to either floppy or thumb-drive.

Then, insert the media you made, boot from it, and follow the instructions.

---

### Post by anjilslaire on 2009-02-26
> **egalvan said:**
> If you downloaded the .exe file for floppy or thumb-drive, then you will need a DOS/Windows machine to execute this file.
Running the .exe will copy the program to either floppy or thumb-drive.


hmm, might have to test under wine...

---

### Post by Therion on 2009-02-26
> Darik's Boot and Nuke ("DBAN") is a self-contained **boot** disk. 
You create the bootable CD or thumb drive and then... Boot to it.

---

### Post by Kareeser on 2009-02-26
> **jaminux said:**
> The problem with this is (I believe) is that, contrary to popular belief, when you delete a file in the normal way the actual data on the hard disk is not gone (even when you empty the recycle bin). It can be restored.

A program like shred is required to write over the data a few times to make sure there is nothing left.

This is how police use the computers of "naughty people" as evidence against them when they commit crimes.

Correct. What that command (and other "quick format" options) does is write over the master boot record. So while the data still exists, the hard drive no longer acknowledges it as readable data, and writes it over at the earliest opportunity.

---

### Post by Kevbert on 2009-02-26
The most secure way is to physically destroy the hard disk platters as there will be some residue information left on the hard disk (which may be read with 'specialist' software) even with a full format and rewite to disk. In most cases you've got nothing to worry about....

---

