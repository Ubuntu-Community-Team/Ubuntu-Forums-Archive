---
title: "ata1.00: error {UNC}"
date: 2014-01-17
forum: New to Ubuntu
---

### Post by michael-lee0 on 2014-01-17
[http://imgur.com/PC7wRNc](http://imgur.com/PC7wRNc)

Installed ubuntu 12.10 after Windows wouldn't start (failed to boot, press ctrl alt del to reRecovery).  Install went fine but the computer frequently would freeze.  Almost everything I did would raise errors in the tty1 thing.  Also, every time I'd boot, the unity interface never loaded until I would do "unity --reset" in the tty1 cli.

Eventually it got so bad that i did the REISUB thing that I read about to force a reboot.

Ever since then, I'd get "hd0 out of disk" with the grub rescue prompt.

Googling help advice didn't lepead anywhere, unfortunately.

I ran ultimatebooter or whatever it's called.  Running an hdd diagnostic for my sata drive, I get a lot of "drive not ready" responses as the hdd's sectores get checked,

---

I tried installing windows 7 again, which was what I originally had.  Unfortunately it wasn't possible because the "partition select" portion of the install process believed that the file system was not in ntfs format.

Googling this, I found that I could try to fix this via command prompt... but upon trying to reformat the drive in the windows command prompt, the computer would hang.

Eventually I decided to try and just do a fresh install of ubuntu... this time 13.10.  I would frequently hang wt the ubuntu splash screen.  So, after googling advice, i turn off the "nomodeset" feature and tell the bootable to just install the newer version.

Upon beginning the install process, I find in the tty1 interface this same loop (pictured above) causing the computer to hang.  This same loop happened and caused the computer to hang for so long that I did the REISUB command, which was ironically what set me on this path to begin with.

So yeah, that's my story.

Is my hard drive ****ed?

---

### Post by joachim_altmann on 2014-01-17
Hi Michael,
there seems to something weird with your HD. I tried to install Xubuntu on a 10 year old toshiba with a hd the same age and failed utterly with similar symptoms :-) 
"drive not ready" does not sound good, maybe even something with the cables of your hd. If your machine runs smoothly booted from USB (instructions [here]("https://help.ubuntu.com/community/Installation")) you can use the "disk utiliy" (part of ubuntu) to test your drive and if everything works fine with the exception of your hd it may be time for parting .....

---

### Post by king.of.random on 2014-01-17
Use your live Ubuntu disc to use gparted to look at your partitions on your hard-drive. I think gparted is installed by default but if not just install it from the software centre. Open this app and wait as it scans you hard drive. I believe it maybe that you don't have enough space for Ubuntu; either because your partitions are incorrect or you haven't allocated enough disc space. Partition size depends on what you want from your computer, this may help:

[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

Remember on the windows install it is recommended to do a back up and make sure that you do a thorough defrag befor allocating more space over to linux.

---

### Post by michael-lee0 on 2014-01-17
> **king.of.random said:**
> Use your live Ubuntu disc to use gparted to look at your partitions on your hard-drive. I think gparted is installed by default but if not just install it from the software centre. Open this app and wait as it scans you hard drive. I believe it maybe that you don't have enough space for Ubuntu; either because your partitions are incorrect or you haven't allocated enough disc space. Partition size depends on what you want from your computer, this may help:

[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

Remember on the windows install it is recommended to do a back up and make sure that you do a thorough defrag befor allocating more space over to linux.

When I do nomodeset and select "try ubuntu without installing", it takes me to a blank tty1 cli for a minute, then the ubuntu splash.  From here, it hangs (meaning that the computer never progresses past this point).  I press a button to bring back the cli and it's still blank.

I leave the computer alone for about 15 minutes and come back to the same situation, unchanged.

Edit:  actually that's not true, this popped up as I toggled the cli again from the splash screen:

http://imgur.com/pQtBuee

Edit^2:  5 minutes later, after toggling back and forth every minute or so as I watch tc's stream on twitch on my other computer... it booted.  I'll post again with the gparted thing.

---

### Post by michael-lee0 on 2014-01-17
Here are the "sudo parted -l" results as I wait for gparted to finished scanning (it's taking a super long time...):

[http://imgur.com/qtJ1wiR](http://imgur.com/qtJ1wiR)


Edit:  and here's the gparted results:

http://imgur.com/lGjiQby

---

### Post by joachim_altmann on 2014-01-18
Hi Michael,
the partition table does look fine for me, you have ample space. Just to ensure that there are no side effects I would remove the external USB-drive.
If first windows failed you and then the install of Linux did not work, there may be well an error with your hw. Did you try to use a diagnosis tool? Its a seagate hd, you can download the diagnosis tool here, including instructions for use
[http://www.seagate.com/support/internal-hard-drives/consumer-electronics/ld25-series/seatools-dos-master/](http://www.seagate.com/support/internal-hard-drives/consumer-electronics/ld25-series/seatools-dos-master/)

I found a bug-report for the error you reported in post #4, see below, but I cannot say if this is important whatsoever, maybe someone else can help here.
[https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1190947](https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1190947)

---

