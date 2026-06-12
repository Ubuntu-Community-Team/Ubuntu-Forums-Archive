---
title: "How to make drive in external enlosure work?"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by cmulford on 2008-07-11
Hi everyone. I have a Thermaltake Muse A2293 external drive enclosure that I popped a western digital 250GB IDE drive in last night. Before I did this I formatted the whole drive as a single FAT32 partition using gparted. I did all of this in hopes of transferring videos and music to it so I can share between my Ubuntu box and my xbox 360. All of the research I did beforehand stated I would not have any problems on either side as long as I formatted using FAT32. The problem is neither Ubuntu or the 360 sees the drive. I did plug it into my wifes vista laptop (without installing the windows driver) and it recognized an unknown usb device, so I think it's actually working. If I plug the drive into the Ubuntu box internally, all is well.

Do I need a special driver even though I have read that I shouldn't? Could anyone shed some light on what I need to do to get this working - at least on the Linux side?

Thanks,

Skip

---

### Post by dca on 2008-07-11
It's not recognizing it as a 'block' device on either platform (MS or *nix).  Let me see if I can find something to help...  What happens when you type lsusb at CLI?  Also, after plugging in what does syslog or /var/log/messages indicate?

---

### Post by dca on 2008-07-11
Also, is it IDE or SATA?

---

### Post by DGortze380 on 2008-07-11
I had the same problem. That partition is too big for fat32. The largest I've been successful with is 80GB. Also, are you aware of the 2GB file size limit on fat32? Could be a problem if you're looking to use it for video.

Might have to look another file system for this. Is NTFS supported on the 360?

---

### Post by Gannon8 on 2008-07-11
Perhaps the enclosure needs a special driver. Dunno why, but it might. If you can stick the hard drive in your box then it's not the hard drive. Your probably not going to use it on the xbox unless you get a different enclosure. As far as I know, there isn't a way to put a driver on a game console.

Look for a CD or something that came with the enclosure, or on the website. I'd say theres a 99% chance there isn't a linux driver. But that's just me. I could be wrong :)

---

### Post by Gannon8 on 2008-07-11
> **dca said:**
> Also, is it IDE or SATA?

> **cmulford said:**
> that I popped a western digital 250GB IDE drive

:p

---

### Post by dca on 2008-07-11
Well, if it's quasi-working (the above post is correct, too) is there anything listed:  *ls /media* at CLI when device plugged in?

---

### Post by dca on 2008-07-11
...yes, I realize that now.... :)

---

### Post by DGortze380 on 2008-07-11
Ok, after a quick search I think I've got it nailed down.

NTFS is not supported. FAT32 is, but doesn't work on large drives and has a 4GB file size limit.
Format the drive as HFS+ and it will be supported in both systems with no file size limit.

Try that before you ditch the enclosure. I highly doubt it's a driver issue.

---

### Post by bumanie on 2008-07-11
I did the same thing yesterday with a cheap external case and a 160g wd ide drive I had spare. No problems at all in either ubuntu or on my friends windows - no driver disc needed etc.. Have made an external (samsung) 2.5" drive in the past, again no problems. If it's a 3.5" drive, I assume you were supplied with a step-down transformer to power the thing - a usb port will never power a 3.5" drive without an external power source. It should be 'plug & play' as you are expecting it to be. The filesystem should not matter as long as it is a common one - which FAT32 is. Double check the connections, just in case one is loose or something.

---

### Post by DGortze380 on 2008-07-11
> **bumanie said:**
> I did the same thing yesterday with a cheap external case and a 160g wd ide drive I had spare. No problems at all in either ubuntu or on my friends windows - no driver disc needed etc.. Have made an external (samsung) 2.5" drive in the past, again no problems. If it's a 3.5" drive, I assume you were supplied with a step-down transformer to power the thing - a usb port will never power a 3.5" drive without an external power source. It should be 'plug & play' as you are expecting it to be. The filesystem should not matter as long as it is a common one - which FAT32 is. Double check the connections, just in case one is loose or something.

The file system does matter if you wants files more than 4GB, and if the drive is to big for the file system. FAT32 is not the best choice for videos.

---

### Post by bumanie on 2008-07-11
> **DGortze380 said:**
> Ok, after a quick search I think I've got it nailed down.

NTFS is not supported. FAT32 is, but doesn't work on large drives and has a 4GB file size limit.
Format the drive as HFS+ and it will be supported in both systems with no file size limit.

Try that before you ditch the enclosure. I highly doubt it's a driver issue.

Can you explain why ntfs is not supported? I don't understand what you mean. External drives can be formatted to ntfs, ntfsconfig can configure external devices, windows would obviously read ntfs without issue. I have run ntfs on external hard drives without issue.

---

### Post by phr0ze on 2008-07-11
It's a problem with the enclosure or the way you hooked the enclosure to the drive. I strongly recommend you check the drive jumpers too. Maybe in the system you had the drive set to slave. Put the drive in Master Mode. If that doesn't work, then try CS. 

If all that fails, the enclosure is bad.

If it was a problem with FAT32 and the size of the disk then it wouldn't work if you plugged the drive directly in either.  So it's not that.

---

### Post by cmulford on 2008-07-11
hmm, the specs say it uses a "Cypress AT2+ chip"
Listed compatibility is "Windows SE/ 2000/ XP; Mac OS 9.x and up"
Yes, there is a driver disc with drivers for windows
[here]("http://www.thermaltake.com/product/Storage/525_Solutions/a2293/a2293.asp") is the page for the enclosure.

No, xbox doesn't recognize ntfs.. go figure =)

Yes I can use the drive as it is formated when I attach it internally to the Ubuntu box. Maybe I should try formatting with Macdrive? When I get home in a couple hours I will list the output of lsusb.

---

### Post by bumanie on 2008-07-11
> **DGortze380 said:**
> The file system does matter if you wants files more than 4GB, and if the drive is to big for the file system. FAT32 is not the best choice for videos.

I know for large files FAT32 is not the best choice, but it was stated that the drive was not recognized, however, I took a while to post and there have been a heap of posts since I first saw the post, I meant as far as the drive being recognized the filesystem wouldn't matter. May be I misread the original post. You are quite right that FAT32 is limited to 4g per file - anyway, not going to quibble, I may have misunderstood/misinterpreted what I initially read, so I will say no more.

---

### Post by cmulford on 2008-07-11
> **phr0ze said:**
> It's a problem with the enclosure or the way you hooked the enclosure to the drive. I strongly recommend you check the drive jumpers too. Maybe in the system you had the drive set to slave. Put the drive in Master Mode. If that doesn't work, then try CS. 

If all that fails, the enclosure is bad.

If it was a problem with FAT32 and the size of the disk then it wouldn't work if you plugged the drive directly in either.  So it's not that.

I tried both master and CS already. Like I said, the vista laptop recognized it in some fashion even though I didn't install the windows driver from the disc.

Thanks,

Skip

One other item of interest [this]("http://www.phoronix.com/scan.php?page=article&item=349&num=1") review of the enclosure was done by some Linux guys who said it was auto-detected.  I really want to get this working because it's a nice box.

---

### Post by DGortze380 on 2008-07-11
> **bumanie said:**
> Can you explain why ntfs is not supported? I don't understand what you mean. External drives can be formatted to ntfs, ntfsconfig can configure external devices, windows would obviously read ntfs without issue. I have run ntfs on external hard drives without issue.

NTFS simply isn't supported for the 360. Ubuntu, Windows and OS X all support it, but not the XBox 360.

HFS+ is the only file system (for large files) that is support in Ubuntu and XBox. (FAT32 also works if files are under 4GB)

------------

This thread seams kind of all over the place, I'm just going to sum things up to try and fidn this guy a solution.

FAT32 may be a problem on a drive of that size, or depending on the files you'll be storing.
Drive jumpers have been check, doesn't make a difference.
The drive is not bad if it works when internally connected.
The enclosure is not bad if the vista computer recognizes the drive externally.
There may be a driver issue with the enclosure, but I doubt this is the case. That's rather rare.

Are you using external power? Or just the USB cable? Right now I think this may be the issue. It would explain why one computer recognizes the drive but your linux box and xbox don't.

---

### Post by DGortze380 on 2008-07-11
> **bumanie said:**
> I know for large files FAT32 is not the best choice, but it was stated that the drive was not recognized, however, I took a while to post and there have been a heap of posts since I first saw the post, I meant as far as the drive being recognized the filesystem wouldn't matter. May be I misread the original post. You are quite right that FAT32 is limited to 4g per file - anyway, not going to quibble, I may have misunderstood/misinterpreted what I initially read, so I will say no more.

Sorry, didn't mean to flame. Just a lot of info coming in all at once, I was trying to sift through it and only responded to that one statement. I should have read more carefully.

---

### Post by dca on 2008-07-11
The reason why everyone jumps up and down when using NTFS for ext drives is because up until recently Linux had terrible r/w support for that FS.  So, the easy thing to do is format for FAT32 so that way there would be no problems migrating files between any other OS...

---

### Post by cmulford on 2008-07-12
Well, to make a long story shorter, I stopped on the way home yesterday and bought an el cheapo enclosure, put the hdd in and attached it to the Ubuntu box and it automatically showed up. Carried it to the 360, and tada, it works fine there too.  That Cypress AT2+ interface must have been the issue (or the thing was just plain old busted.

Thanks for the quick help and suggestions!

Skip

---

