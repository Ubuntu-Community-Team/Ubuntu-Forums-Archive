---
title: "Hard drive with bad sectors"
date: 2008-11-06
forum: New to Ubuntu
---

### Post by jasontu on 2008-11-06
I used Partition Editor to reformat a hard drive a while back.  I barely use it, but I noticed awhile ago that it wasn't appearing in Ubuntu.  I finally checked it out through an Ultimate Windows Boot Disk.  While the Windows disk did detect the 500 GiB drive as having only 8GiB, it did detect the drive.  When I ran a health scan it was coming up all red (bad sectors.)

Is there a fix disk or similar type function in Ubuntu?  How do I use it if Ubuntu isn't even detecting the drive?  Is there a live CD or boot disk that will fix the disk?  Was the Windows Boot disk counting linux partitioning as a bad sector when it shouldn't have?

Thank you!

---

### Post by B34ST1Y on 2008-11-06
have you tried double checking your partition settings? Are you dual booting? Check to make sure your partition on the drive is correctly set to utilize the full capacity on your hard drive.

Also, I would definitely recommend running a hard drive integrity check tool. DFT (drive fitness test) comes standard on the ultimate boot cd. ([http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)) try running that, and see if it passes DFT. If not, then you've definitely got a bad hard drive on your hands. If it passes all green, then you may just have an improperly configured disk...or a corrupt partition table

---

### Post by jasontu on 2008-11-10
Drive Fitness Test apparently only works with certain brands.  I have a Seagate I believe so I used SeaTools and I attempted to Zero Out the drive.  I set that in motion over night, but I awoke to find my wife on the machine.  She said it was just off.  I checked the drive and it was still not appearing in Ubuntu, still reporting around 8 GiBs of space and giving errors.

What other steps do I have left?  I have no idea what could have messed up the drive.  It's relatively new.  I partitioned it with gparted I think, but aside from that I can't think of what could have caused errors.  What can I do to completely reset the drive to factory settings?  Thankfully there's no data on the drive I want to save.  There was nothing on it to begin with.

Thanks for the help.

---

### Post by psusi on 2008-11-10
sudo apt-get install smartmontools
sudo smartctl -a /dev/sda
sudo smartctl -t long /dev/sda

Replace sda with whatever the drive in question is.  It will take some time to run the long test, and you can check on the results with sudo smartctl -l selftest /dev/sda.

---

### Post by jasontu on 2008-11-11
The only issue with the solution offered above is that the drive does not show up in Ubuntu.  It shows up on DOS based diagnostic tools, but not in Ubuntu for some reason.

Is there a way to run this program outside of Ubuntu or to force Ubuntu to find the drive?

Thanks.

---

### Post by B34ST1Y on 2008-11-11
download from [http://www.tacktech.com/display.cfm?ttid=287#seagate](http://www.tacktech.com/display.cfm?ttid=287#seagate)  - see if those tools dont work for you. I believe theyre on the ultimate boot cd

---

### Post by B34ST1Y on 2008-11-11
otherwise you could always try using [http://www.dban.org/download](http://www.dban.org/download) darik's boot and nuke to *completely* erase ALL information on the hard drive, and start from scratch

---

### Post by Kellemora on 2008-11-11
Hi Jason

I picked up the computer I'm on right now used.  I think the guy sold it because he THOUGHT the hard drive was failing.
The Winders test showed 149 bad blocks.
GParted wouldn't work and showed 8 bad blocks.

Since I bought this for Ubuntu Only in the first place, I just reformatted the entire drive ext3, but was a little nervous about it, so I reformatted it in Fat32 so I could check it on windows again, this time it came up no errors, and GParted showed no errors as I played around with that.

I reformatted it to ext3 again and have been using it ever since, I don't think even Super Grub found anything wrong with it either.

Now that I think back, I did use a program that wrote 1's I think all across the disk and then changed the 1's to 0's during one of the tests that was data destructive but checked it right down to the nitty gritty, it found no errors either.

But GParted (the one on the Ubuntu Distro) still shows errors on it, but not the GParted LIVE disk, it shows zero errors too.

TTUL
Gary

---

