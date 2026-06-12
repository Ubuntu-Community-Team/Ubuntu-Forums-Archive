---
title: "first installation"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by AvengerX9 on 2008-09-04
I installed Ubuntu today and when I was finished I got a checkerboard all over my screen where the black squares was transparent and the white ones were not. In other words I could see half of my screen so I re/installed windows, but now my 2nd hardrive appear unformatted. 

Is there a way to make it accessible in windows? I dont wanna loose 1TB with music and movies :(

Thanks

---

### Post by mevets on 2008-09-04
I hope you didnt install to that second hd. Do you remember what drive you installed ubuntu to?

---

### Post by crispy_420 on 2008-09-04
Which drive did you install to?

Multi hard drive system?

Maybe, did you install to your music hard drive? If so, you may have some loss if you installed on top of your data. And if so you may not be able to easily recover it since it was reformatted.

---

### Post by genesis2seven on 2008-09-04
If you didn't install onto your second hard drive then it should be listed when in Ubuntu you click "Places" from the main bar as a mountable drive.

If you did install to the second hard drive then you've got problems.

Also, I've found that installing with an active internet connection tends to go smoother for some reason.

---

### Post by AvengerX9 on 2008-09-04
thanks 

I did install on C, the other drive is physical G.

Im in windows now but cant see it as anything than unformatted

---

### Post by AvengerX9 on 2008-09-05
just went into Ubunto again. I choose to try (no changes to your computer this time) and I got the checkerboard all over and I cant see the "disk" in the computer either. Just C, floppy and cdroms

---

### Post by falcon61102 on 2008-09-05
If you could, go back into Ubuntu with the LiveCD and open up a terminal.  Go to Applications>Accessories>Terminal.  That will open up a window that looks like a dos command prompt.  Enter the following code and post the results here:
```
sudo fdisk -l
```
-l is a lower case L

That will give us some information about your partitions and drives so we can help you.

---

### Post by AvengerX9 on 2008-09-05
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2ac6adf8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4869    39110211    7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       16708   134206978+   7  HPFS/NTFS

---

### Post by Corrupt3d on 2008-09-05
Both of your hardrives are formatted w/ ntfs? o.O
How did you install Ubuntu?
Did you format it back to ntfs afterwards?

---

### Post by AvengerX9 on 2008-09-05
I re-installed windows on the 40gb. Did nothing with the 1000gb drive and thats the disk I want to "fix" if possible

---

### Post by Sef on 2008-09-05
> Device Boot Start End Blocks Id System
/dev/sda1 * 1 4869 39110211 7 HPFS/NTFS

> I re-installed windows on the 40gb. Did nothing with the 1000gb drive and thats the disk I want to "fix" if possible 

If you had installed Ubuntu to sda1 (C: in Windows terminology), then Windows overwrote it when XP was re-installed. 

To dual boot with two hard drives, read the [Illustrated Dual Boot's tutorial]("http://www.herman.linuxmaniac.net/p24.html").

---

### Post by falcon61102 on 2008-09-05
As far as you 1TB drive is concerned, you may just need to run chkdsk in Windows on that drive.  If it gives you errors about needing to be formatted, don't.  Just leave it be then.  You're best bet at that point would be to install the dual boot system only using the 40 gig HD.  

If you want to really make sure nothing else happens to your 1TB drive, disconnect it for now and then once the install is finished, connect it again.

Ubuntu is a little more forgiving at reading drives and has many more aps to aide  you in recovering that drive so once you have Ubuntu installed, your options are  much better.

---

### Post by AvengerX9 on 2008-09-05
I didnt choose try, I went on with the installation and passed all the steps until this one

[IMG]http://www.herman.linuxmaniac.net/p24/013.png[/IMG]

I chose the 2nd option, guided and I also remember that I choosed the 40GB disk.

When I got into Ubuntu I had this checkerboard all over (still have) so I decided to quit. I installed windows again after noticing that it had been wiped of C:

When I got into windows, it could not recognize the other drive so I would really appreciate some help to find out what to do :)

---

### Post by Bucky Ball on 2008-09-05
Disconnect that 1TB drive before you get into trouble (unless you are *really* confident about this). This will also leave absolutely no doubt for any of us that you are working on 1 drive and 1 drive only with no partitions on it to start. :)

Follow the correct method. Install windoze and when you get to the partition section, delete all partitions on that  C/ drive. Then make a partition for you windoze install, nothing else. Leave the rest free space. Boot and make sure windoze is happening. Then install Ubuntu and use the free space for this. Once you get there, let us know if you are getting the chequerboard response and we can try to fix that up (possibly a video driver) and get your machine dual booting. Don't panic, if you have done the first two installs this is no biggie to fix. Your grub menu is just looking in the wrong place.

Let us know how you went. One step at a time. If you get to the stage where you have windoze installed and ubuntu is giving you the chequerboard, *don't* start the reinstall merrygoround with windoze and ubuntu. They are already there and just a matter of tweaking a few things. :)

---

### Post by AvengerX9 on 2008-09-05
hi there :)

Im in Ubuntu now and the checkerboard is gone so Im ready to try whatever might improve the chances for saving the content on my disk :)

---

### Post by Bucky Ball on 2008-09-05
Cool! Good news. Outline *exactly* what it is you want to do and we'll see if we can help (include machine specs if possible). Is the dual boot happening? You could mark this thread as solved (go to 'Thread Tools') and repost your *specific* question in the appropriate forum ... or post here. 

Problem with the latter is that 'first installation' is not very descriptive for others looking to help and we have fixed the original problem. Up to you. Good luck either way. :)

---

