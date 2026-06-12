---
title: "can i recover files after installing Ubuntu 8.10 without partition"
date: 2008-11-30
forum: New to Ubuntu
---

### Post by vadik32 on 2008-11-30
So, I'm pretty new to this linux thing but decided to break from the windows pack and add ubuntu 8.10.

what i didn't realize is that you needed separate partitions for dual boot and installed Ubunutu simply on the only hard drive on my laptop (i figured if it was going to erase anything or not allow dual boot this way it would at least let me know).  So now only Ubunutu 8.10 starts and theres no way to start windows.

I'm wondering if there is anyway for me to recover at least some of my files (if not all of my files) like pics, docs, music, etc that i Had under XP professional

If anyone can help me please let me know....

Thanks very much in advance

---

### Post by mikewhatever on 2008-11-30
Yes, you can recover some of the files with Photorec, but you have to stop using that HDD as soon as possible.
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

---

### Post by wilbbe01 on 2008-11-30
I think the default option is to use free space on the drive and install ubuntu to that.  I would say the easiest way to check would be to go to the "Places" menu in Ubuntu and see if a volume is listed there such as "750GB Volume" or something like that.  You can then click on it and hopefully mount the windows partition.  If you do find it and you do want to dual boot, we can go from there and add the relevant information to get Windows listed in grub when you first turn on the computer.  Also run this command

```
sudo fdisk -l
```

Post the output here.  This should tell if your windows partition still exists or not.

---

### Post by vadik32 on 2008-11-30
Mikewhatever - thank you im going to try that software.

wilbbe01 - Thanks also, I typed in the command and this is what i see

Disk /dev/sda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x922f922f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2339    18787986   83  Linux
/dev/sda2            2340        2432      747022+   5  Extended
/dev/sda5            2340        2432      746991   82  Linux swap / Solaris
test@test-laptop:~$ 

not too sure where to go from that (sorry I'm new to this).  Also, I clicked on the only volume thats presented under places but not too sure what you mean by "mount the windows partition" or how to do it, would you mind elaborating?

Thank you very much in advance.

---

### Post by Captain_tux on 2008-11-30
Did you perform a back up of your system/files before installing Ubuntu?

Do you want Windows on your laptop at all? If so, seems like you may have to perform a recovery/re-install of Windows, then re-install Ubuntu, making sure you partition the hard drive so that you can safely dual boot between the two OSs.

Either way, hope you can recover your files!

---

### Post by wilbbe01 on 2008-11-30
I'm afraid you indeed did write over windows completely, so I would suggest looking more into what mikewhatever stated in post #2.  You might happen to get lucky.  In the future I strongly recommend backing up anything important to you no matter what you are planning on doing (even if it is just check your email).  If you have backups of all of your files somewhere else your computer becomes more of a tool, and less of a necessity for file storage.  I back up all of my music and pictures on a couple of other machines, one in a completely different location from my main desktop 13 miles down the road, and the rest on a second hard drive in the same location.  I use dropbox for quick backups of everything small (like text documents and some photos).  This way I can survive any unplanned loss of data without losing any.

Sorry I can't help you anymore with recovering your files, but I do suggest going along the lines of what mikewhatever said earlier.  Good luck.

---

### Post by vadik32 on 2008-11-30
Thank you very much guys, I'm going to use Mikewhatever's advice... Didn't create a backup butr certainly learned my lessonn for the future... Thanks again

---

