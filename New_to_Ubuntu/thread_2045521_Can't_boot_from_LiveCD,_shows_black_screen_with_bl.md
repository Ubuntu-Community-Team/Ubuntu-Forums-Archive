---
title: "Can't boot from LiveCD, shows black screen with blinking cursor."
date: 2012-08-21
forum: New to Ubuntu
---

### Post by Aftrumpet on 2012-08-21
I figured I'd try out Ubuntu 12.04 by running it from a CD, but when I try to boot from the CD nothing happened except for a black screen with a blinking cursor. I set up the CD by downloading the *.iso file and burning it with InfraRecorder on Windows XP. Also of note is that when I try to open a file from the CD, I get an error message saying, "Cannot open the [filename] file. Make sure a disk is in the drive you specified." I don't think this is a computer-specific problem because I tried it on another computer and the same black screen showed up.

---

### Post by Morderwurst on 2012-08-21
Did you turn down the write speed before burning?

---

### Post by Aftrumpet on 2012-08-21
No. Was I supposed to?

---

### Post by mikechant on 2012-08-21
Did you make sure to burn the iso file as an image, not as a file?

Can you open the disc with Windows Explorer? If you can, and you see the .iso file on the disc, then this is wrong and you need to  re do the disc using the 'image' option. This should be a separate option in InfraRecorder.

---

### Post by Aftrumpet on 2012-08-21
I can see the individual files, not just the iso file.

---

### Post by Morderwurst on 2012-08-21
It may be worth burning it again at slowest speed to rule out disk/write errors(?) I've had problems with this in the past. 

Also you could check [md5sum]("http://en.wikipedia.org/wiki/Md5sum") of the iso to verify its integrity.

---

### Post by marlow59 on 2012-08-21
The problem is definetly from the cd. Try to reburn it and make sure you are burning it as an ISO image. Also slow down the writing speed when burning and do not move your computer while burning.
 Report back for further problems. Hope it helps.

---

### Post by mikechant on 2012-08-21
You should not be able to see the .iso file on the CD at all if it is burned correctly. 

The following is the correct way to burn with Infrarecorder, is this what you did?

> Insert a blank CD in the drive and select Do nothing or Cancel if an autorun dialog pops up.
Open Infra Recorder and click the 'Write Image' button in the main screen.

Alternatively you can select the 'Actions' menu, then 'Burn image'.

Select the Ubuntu CD image file you want to use, then click 'Open'.
In the dialog, click 'OK'.

(The above was extracted from this page: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto))

---

### Post by Aftrumpet on 2012-08-21
I'm reburning now (and yes, I did do "write image" before and there was no iso file on the disc), but I keep getting a write error (failed to write lead-in). Do I need to clear the disk before I start again?

---

### Post by mikechant on 2012-08-21
So you're using a CD-RW disc? Yes, you should probably blank/erase it first - but it's usually better to use a CD-R (or DVD-R if relevant) - CD-RWs are much more likely to be troublesome.

---

### Post by Aftrumpet on 2012-08-21
No, it's a CD-R. But how do I wipe it (when I try to delete all the files, the wubi.exe can't be deleted because it is read-only)?
Edit: just found out what that meant. Oh well, I'll just burn another disc.

---

### Post by Aftrumpet on 2012-08-21
After burning another CD at the slowest speed, I'm getting the same issue.

Should I try re-downloading the iso file? And does it mean anything that the CD I'm using says "Audio" on it? I don't think it would, but I want to make sure.

---

### Post by mikechant on 2012-08-21
Do an md5sum on the iso file as per these instructions:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Note it includes instructions for doing md5sum on Windows if you haven't got a usable Linux install.

If it's wrong, you need to download again; it it's right there's no point.

> And does it mean anything that the CD I'm using says "Audio" on it?


There used to be a requirement to use special 'audio' CDs in standalone CD recorders, but PC CD writers have always been able to use these 'audio' CDs for data.

Are your blank CDs very old? The dye might have deteriorated if so. Try a different batch if possible.

The other thing you can do is try to verify the CD after you have burned it, but I'm not sure what the best way to do this on Windows is. The CD contains its own verify program but you need to get through to the inital boot menu to run this so I don't think that helps.

---

### Post by Morderwurst on 2012-08-21
You could also try _[making a bootable USB stick]("http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows")_

---

### Post by Aftrumpet on 2012-08-21
If I make a bootable USB stick on one with other files, will that wipe it? I only have one, and I have a lot of information on it.

---

### Post by mikechant on 2012-08-22
> If I make a bootable USB stick on one with other files, will that wipe it?

Yes

> I only have one, and I have a lot of information on it.

Buy some more - they're cheap and useful!

In the mean time you could maybe back your USB stick up (e.g. to CD/DVD) (you should have a backup anyhow if the info is at all valuable to you, since USB sticks can and do fail).
When you've backed it up you can use it for the install and restore the original data after.

---

