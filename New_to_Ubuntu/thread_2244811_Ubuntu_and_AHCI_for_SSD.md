---
title: "Ubuntu and AHCI for SSD"
date: 2014-09-18
forum: New to Ubuntu
---

### Post by snowmobiler on 2014-09-18
So my plan to build up a Dell Latitude D820 fell thru because AHCI is not supported for SSDs(something about use of a SATA to PATA bridge). I am working on a Compaq Presario CQ60 running Vista. I did a fresh install awhile ago on a new drive. In the BIOS, changing the SATA controller is not available. I have found that Vista OS and after are AHCI compatible but if the Bios wasn't set to that before install, then windows doesn't install the SATA controller to be able to set it to AHCI(not known by me at the time). So my question is, if I am going to load Ubuntu on an SSD where the SATA controller is not available, do I need to load the Vista driver (for this example), that will put the driver in the BIOS or does Ubuntu install a SATA controller driver into the BIOS that I can change to AhCI afterwards? I looked at my Dell Optiplex G620 which has Ubuntu 14.04 installed, and it also doesn't give the ability to change the SATA driver controller (could be that it was an XP machine previously). I don't want to waste the money on an SSD if I can't find ways to optimize its use, and the change to AHCI is one of the first changes suggested. 

Thanks again from the newbie!

---

### Post by oldfred on 2014-09-18
I had XP and promised for several years to shut it off. Adding AHCI drivers to it was complicated and a reinstall. And two years ago I got an inexpensive SSD.

But I was just able to turn on AHCI and Ubuntu booted. But XP did not. I was able to turn AHCI off and XP then would also boot. But I had SSD and needed AHCI so I finally shut XP down.

It is my understanding with Windows 7 you can just add a driver for AHCI, do not know about Vista.

It is my understanding you need AHCI for trim to work.

---

### Post by snowmobiler on 2014-09-19
Oldfred, from what I have read, AHCI is supported by Vista,7,8, Linux "out of the box" as they say. My Presario CQ60 (vista) laptop and CQ61(7) don't seem to have options to change it. So as with the Dell PC, I am wondering if it is hardware limited as opposed to BIOS limited. If you load 7 and the BIOS is not in AHCI mode, and then you switch it, you can get bmod errors on boot. I get that. But gotta have the option to change it first. Reading reviews of SSDs, many people have resurrected old laptops. But they might not be using them mostly for Linux. AHCI allows for hot-swapping (if you are using an SSD for a second drive) and yes I see its needed for TRIM. Just have to figure out if I don't have an option to change it, is it there by default, or not supported.

*edit* Also in my searching, I am finding that users in the past could not 'downgrade' the same laptops to XP. it would load, but on boot they would get blue screen errors. These users were searching for the SATA controller drivers so they could turn AHCI off which doesn't work with XP. So again I wonder, is it automatically enabled (I will have to check in Computer Management)? And then will I be fine with Ubuntu, since TRIM is automatically handled by the OS (like vista, and 7).

---

### Post by Michael_McKenney on 2014-09-19
Vista to Windows 8.1 support ACHI.  I would not do SSD drives on XP Pro.  You don't get full support for the drivers for it.  Trim does not work well or at all in XP Pro.    By the way, you can't reactivate XP Pro, if you break it.  Microsoft cancelled activation of it in April.  So if you really need XP Pro to keep working, don't add Ubuntu to it.  You break it, you will never get it working again.

---

### Post by snowmobiler on 2014-09-19
> **Michael_McKenney said:**
> Vista to Windows 8.1 support ACHI.  I would not do SSD drives on XP Pro.  You don't get full support for the drivers for it.  Trim does not work well or at all in XP Pro.    By the way, you can't reactivate XP Pro, if you break it.  Microsoft cancelled activation of it in April.  So if you really need XP Pro to keep working, don't add Ubuntu to it.  You break it, you will never get it working again.

Michael, 

My laptops are running Vista and 7, with no way to change the BIOS to AHCI. But I am now assuming it's actually in that mode. I plan on some point doing a full Ubuntu on an SSD (no other MS OS) to one of them. I just need to know my SSD will be running in AHCI mode otherwise its a waste of money.

---

### Post by Michael_McKenney on 2014-09-19
[http://www.tomshardware.com/forum/248858-32-latitude-d820-that-compatible](http://www.tomshardware.com/forum/248858-32-latitude-d820-that-compatible)

According to this post your D820 does not support ACHI.  I would check with Dell to confirm it.

---

### Post by snowmobiler on 2014-09-19
> **Michael_McKenney said:**
> [http://www.tomshardware.com/forum/248858-32-latitude-d820-that-compatible](http://www.tomshardware.com/forum/248858-32-latitude-d820-that-compatible)

According to this post your D820 does not support ACHI.  I would check with Dell to confirm it.

Yes, I figured that out before I purchased all the things I was going to for that laptop. My question now is about my Presarios (CQ60 and 61). I 'think' they are running in AHCI mode without the ability to change it because what I have read is that users trying to downgrade to XP on either of those, can't, because the driver to _change_ it is not installed and XP cant run in AHCI mode. That's what has me confused. I will check disk management when I get home and if it says the SATA controller is 'standard AHCI mode' (like someone else posted somewhere else), then I can only assume that the BIOS is already in AHCI mode and putting an SSD with Ubuntu install will be just fine as it will utilize its speed and be able to run TRIM.

---

### Post by Michael_McKenney on 2014-09-19
AHCI is Vista and newer.  I would just put a normal hard drive in that laptop.  My friends have cutting edge workstations with SSD drives.  After 2-3 months of hard use, the SSD drive performance degrades 10-20%.  At home I run SAS RAID and 15K SAS drives in my workstation for performance.  SSD drives degrade to fast for my use.  Even the newer Trim technology does not prevent it.  Can you get the optimized drivers to take full advantage of the SSD on that laptop?  Is it worth getting a better laptop with the SSD money instead?

---

### Post by snowmobiler on 2014-09-19
I understand your point completely Michael. It's what I get for taking on something new (Ubuntu) and SSDs at the same time. But its not so much about 'needing' a better laptop. It's about experimenting and learning, while at the same time not throwing money out the window. From what I have read, the Samsung EVO SSDs get great reviews so I wouldn't expect a tremendous dropoff in performance. In all reality, the biggest hurdle might be getting the CQ60 apart and back together. When my wife crashed the original drive, I put in a new drive, new power jack and I had more problems with plastic pieces breaking on this cheap laptop when I took it apart. Not from my doing, peices were just falling. I'd have to figure out where they came from and glue them back (some received screws). You live and learn. Its what its all about. Thanks for your input!!

---

### Post by Michael_McKenney on 2014-09-19
I would spend $1000s a year on cutting edge server hardware to play with.  I had $2000+ server boards, Xeons or Opterons, 16GB of RAM and best video cards.  SAS RAID cost $2200.  It was the best investment I ever made.   1.097 GB/s cached reads and 850 MB/s cached writes on my Windows 7 workstation.  My friends SSD drives get 300-400 MB/s reads and 200-250 MB/s writes.  Photoshop CS6 can do 75 RAW to JPG conversions a minute.  2 hour DVD encoding with 4X burn takes 79 minutes with 15 minutes for the burn.  I play with very high end server hardware.  I learned a lot from it.   I would research what motherboards work best with that SSD drive.  Some motherboards only fully support some SSD drives.  LSI Logic only recommends 3 SSD drives for my SATA / SAS RAID controller.   You want your chipset and controller to fully support that SSD drive firmware.

---

