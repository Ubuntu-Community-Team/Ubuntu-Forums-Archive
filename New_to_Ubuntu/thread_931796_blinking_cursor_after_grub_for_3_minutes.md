---
title: "blinking cursor after grub for 3 minutes"
date: 2008-09-27
forum: New to Ubuntu
---

### Post by bwaits on 2008-09-27
1Ghz Via Processor
1 Gig Ram
Booting from USB stick

Ubuntu 8.04
Gnome 2.22.3


Install went great. No problems at all. System runs fine once booted. Maybe a bit of 1 second freezes in firefox, nothing major.

I have removed the splash screen and watched the boot process. I also installed bootchart.

I searched but seem to only find black screen issues after the login screen.

My situation is before that point. When I boot I see grub loading. After 30 seconds I have a count down to hit escape for the menu. After the count down the screen goes to a black screen with blinking cursor at top left.

It will sit at the cursor for 3 minutes. Then it will say "loading, please wait". Then it will go into the splash boot screen. By boot chart only counts for about 60 seconds. 

Any ideas on where this 3 minutes is from? It does this every boot so I do not think it is checkdisk.

Thanks,
-billy

---

### Post by Xiong Chiamiov on 2008-09-27
It sounds to me that your bios is cycling through different boot options.  When it can't boot off of the primary hard drive/floppy/cd/whatever, it will move on to the next, after some time.

---

### Post by bwaits on 2008-09-27
All the BIOS stuff happens in a few seconds. No errors. I did just edit the BIOS and removed all other boot options per your suggestion.

Wouldn't the BIOS controlled boot drive already be established by the time grub is loading? Isn't grub located on the usb stick?

-billy

---

### Post by bwaits on 2008-09-28
Grub takes 25 seconds, 3 minutes of black screen with blinking cursor, Then 45 seconds of the splash screen (or text if splash removed). I have noticed the light on the usb drive is blinking the entire 3 minutes of the black screen.

Could it be the usb drive is not un-mounted before shut down so the checkdisk runs at every boot?

-billy

---

### Post by drs305 on 2008-09-28
You use the term 'checkdisk' but I'll assume you are talking about the linux 'fsck' which checks partitions for errors.

To eliminate the possibility that it is an fsck check on your usb drive that is causing the problem, you should try to disable fsck operations on that drive.

Check your fstab and if the usb drive is listed, make sure the last digit on the line is a "0". If it isn't, change it to a "0". This will disable fsck checks on that partition. If the drive isn't an ext2 or ext3 format, the fstab entry should end with a zero at all times.
```

cat /etc/fstab

```

For ext2/3 partitions, you could also use tune2fs to ensure the next scheduled check is not on the next boot. For example, set the max count to 30 and set the current count at 1:
```
sudo tune2fs -C 1 -c 30 /dev/sd***XX***

```

You might also want to ensure there isn't a flag to perform an fsck on the next boot (change to the usb mountpoint):
```
sudo find ***/media/mountpoint***/ -name forcefsck
```

Finally, if this is an ntfs partition and it was used by windows, you might want to mount it in windows and perform a normal shutdown to make sure there are no errors due to an 'unclean' shutdown.

These steps may not solve your problem but should help determine whether the delay is being caused by an fsck check on boot.

---

### Post by bwaits on 2008-09-28
Thanks for the help, yes, 'fsck'.

I changed the 1 to a zero on sda1. I then ran the next command to set, check in 30 and reset the count to 1.

The last command had an error. I do have a /media folder but the only thing inside is /cdrom0

I have /filesystem and the contents of the usb drive are there. It is the only drive connected other than the cdrom.

The drive has never been in a windows machine. It was purchased new just for this project. 

-billy

---

### Post by drs305 on 2008-09-28
> **bwaits said:**
> The last command had an error. I do have a /media folder but the only thing inside is /cdrom0

You should change that to reflect the folder the usb drive is mounted in. For example, if it was mounted to a folder called "myfiles" on /mnt, you would type it as " /mnt/myfiles ".  

This command was only trying to ensure that there wasn't an fsck check scheduled for the next boot. It wasn't a critical part of the process since there is only a slight chance of that being the case...

---

### Post by bwaits on 2008-09-28
Thanks once again.

I have actually worked out that it is fact the usb drive.

I decided to do a clean install on a 30gig hard drive. Install went smooth, boot up in under a minute and no more "split second freezing" within firefox.

I put the usb drive in another computer running windows. It could not see the contents so it must be 100% linux file system. I then made sure to "eject" the drive properly from windows.

Same hang up when I went to boot off the usb drive again. Even the login screen has "split second freezes" when typing uname and pass.

I am building a car-puter and wanted to stay away from a HD, figure USB stick would be perfect. Seems they are just not fast enough - or - at least this one is not.

I will continue to move forward with the standard HD and maybe pick back up on the USB boot times later.

Thanks again for all your help.
-billy

---

### Post by unutbu on 2008-09-28
Maybe post a question here: 
[http://ubuntuforums.org/showthread.php?t=789528&page=7](http://ubuntuforums.org/showthread.php?t=789528&page=7)

Herman has experience with installing Ubuntu on USB flash drives. He may be able to help.

---

### Post by krychek on 2009-04-25
I have the same issue now and couldn't find much on the internet, only this thread. I have the blinking cursor only for 40 seconds, not 3 minutes luckily. I'm also booting from an USB drive. Were you able to find out what's causing this after all?

---

### Post by wispygalaxy on 2009-04-25
> **krychek said:**
> I have the same issue now and couldn't find much on the internet, only this thread. I have the blinking cursor only for 40 seconds, not 3 minutes luckily. I'm also booting from an USB drive. Were you able to find out what's causing this after all?

That happened to me once on Debian, but I wasn't booting from a USB drive.  However, it occurred right after I upgraded to Debian Lenny.  This never happened to me again, and I didn't even do anything to fix it.  :S  I guess the problem just went away for me haha.

---

### Post by krychek on 2009-04-25
I wasn't expecting such a quick reply. :)
I think I started having this problem after upgrading to Hardy from Gutsy and now I still have it with Jaunty.

Is there a way to put grub in a verbose mode so I could see what it's doing before the OS starts booting?

I also reported this on launchpad.. who knows.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/247960](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/247960)

---

### Post by drs305 on 2009-04-25
> **krychek said:**
> Is there a way to put grub in a verbose mode so I could see what it's doing before the OS starts booting?



There are a great number of log files available for viewing by going to System, Administration, Log File Viewer. One of the logs is "dmesg", which details what is happening on your computer during the first part of the boot process. It wouldn't show grub's commands per se but it does detail what is happening as the system starts loading modules and drivers.

---

### Post by krychek on 2009-04-26
drs305: You can see my dmesg here:

[http://launchpadlibrarian.net/25930519/dmesg-jaunty-cold-boot.txt]("http://launchpadlibrarian.net/25930519/dmesg-jaunty-cold-boot.txt")
[http://launchpadlibrarian.net/25930529/dmesg-jaunty-reboot.txt]("http://launchpadlibrarian.net/25930529/dmesg-jaunty-reboot.txt")

I only get the delay on cold boot and I think it happens before all the dmesg logs.

---

### Post by wispygalaxy on 2009-04-26
> **krychek said:**
> I wasn't expecting such a quick reply. :)
I think I started having this problem after upgrading to Hardy from Gutsy and now I still have it with Jaunty.

Is there a way to put grub in a verbose mode so I could see what it's doing before the OS starts booting?

I also reported this on launchpad.. who knows.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/247960](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/247960)

Hehe, you just happened to post right as I clicked on this board!  I'm so sorry; I don't have enough knowledge to help you anymore.  :(  Filling out a bug report is the smart thing to do.  Good luck!  :D

---

