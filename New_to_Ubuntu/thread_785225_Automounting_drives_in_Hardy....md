---
title: "Automounting drives in Hardy..."
date: 2008-05-07
forum: New to Ubuntu
---

### Post by wabbster on 2008-05-07
Hi,

I recently upgraded to Hardy Heron from Gutsy (clean install). Among other things, I noticed that other drives, like my windows partition and my USB flash drives don't mount automatically. I have to mount them by clicking on corresponding drive name in the Places menu. Is there a way to avoid this step altogether and just auto mount the drives?

Also, when I mount the drives, I'm asked for my password. Can this be avoided as well?

Any help would be appreciated. :)

Wabb.

---

### Post by Joeb454 on 2008-05-07
Is it an NTFS Drive (i.e. with Windows on)?

---

### Post by wabbster on 2008-05-07
Windows is on NTFS. My USB drives are FAT.

---

### Post by Joeb454 on 2008-05-07
Ok the Windows drives are easy enough :) Install NTFS-Config from synaptic manager and run that when no drives are mounted :)

I'm currently writing a how-to on this :)

---

### Post by wabbster on 2008-05-07
Great. Let me try this... Looking forward to the how-to. :)

---

### Post by Joeb454 on 2008-05-07
Ok there's a link to it at the bottom of my Signature now :)

---

### Post by Bloch on 2008-05-07
You say you did a fresh install, so this might not apply to you, but it is worth checking for those with a problem with automount

[http://ubuntuforums.org/showthread.php?t=773996](http://ubuntuforums.org/showthread.php?t=773996)

---

### Post by tyroeternal on 2008-05-07
I know its a bit late, but psychocats has a great guide to mounting partitions.  If you're interested in seeing how to do it by hand you should check out this:

[http://www.psychocats.net/ubuntu/mountwindows]("http://www.psychocats.net/ubuntu/mountwindows")

---

### Post by bumanie on 2008-05-07
Editing /etc/fstab will sort out most drive mount issues. Post output of > cat /etc/fstab and someone can help with the editing.

---

### Post by kjbyrne on 2008-05-07
Hi,

I can get this method to work except that I then dont seem to be able to rename them to something meaningful.

I have two physical drives.

The first has my windows partition (C: in windows) plus the linux ext3 and swap partitions.

The second is divided into 6 NTFS partitions (d: to I: in Windows).

On a previous install of Gutsy I had also included a FAT partition for keeping common files but with Hardy being advertised as able to read and write to NTSF out of the box I didn't include one this time.

My Problem is that after installing NTFS-config and naming them as C Drive etc they still show up on my desktop with names such as 63.6 gbyte media or 26.6 gbyte media and all of the 6 drives on the 2nd physical disk are all the same size which is very confusing.

In case I have done something wrong could you also tell me how to unmount the drives if I have to start from scratch again.

Keith

---

### Post by bumanie on 2008-05-07
To rename your drives follow [this]("https://help.ubuntu.com/community/RenameUSBDrive") I think it works for hard drives too. To unmount you should be able to right click on the drive and choose unmount form the menu.

---

### Post by wabbster on 2008-05-07
Joeb454's method worked for me, actually.

@kjbyrne: I'm kind of a newbie too, but by editing /etc/fstab, you can change the output folder to whatever you wish and hence changing the way the mounted drive appears on your desktop.

Don't shoot me if it doesn't work! As I said, I'm learning too. :)

Wabb.

---

### Post by t.septekin on 2008-05-07
I believe the easiest way is to boot into Windows, name your drives to your liking and return to Ubuntu. After all, you had to pay for Windows, get your money's worth.

---

### Post by Joeb454 on 2008-05-09
> **t.septekin said:**
> I believe the easiest way is to boot into Windows, name your drives to your liking and return to Ubuntu. After all, you had to pay for Windows, get your money's worth.

This is how I named mine XP & Vista ;)

---

