---
title: "If you were buying a new laptop what would be the best makes for Ubuntu?"
date: 2012-02-08
forum: New to Ubuntu
---

### Post by chickenPie4breakfast on 2012-02-08
What I mean is if you were going for best compatibility experience with regard to
video drivers etc.  what makes of computer would give you the best chance of having next to no problems?

---

### Post by philinux on 2012-02-08
> **chickenPie4breakfast said:**
> What I mean is if you were going for best compatibility experience with regard to
video drivers etc.  what makes of computer would give you the best chance of having next to no problems?

Have a look here. [http://ubuntuforums.org/forumdisplay.php?f=332](http://ubuntuforums.org/forumdisplay.php?f=332)
I decided on an Acer 1410. Works 100% out the box. People have said in the past to steer clear of ATI graphics card. I have no idea if that has changed but I know that nVidia and Intel play nice.
> 
Intel Celeron M (ULV 743) 1.3GHz 1MB (L2 Cache)
CPU Bus Speed:800MHz
2048MB (4096MB) DDR2 SDRAM
250GB 5400RPM Serial ATA Hard Drive
11.6in Acer CineCrystal LED backlit TFT LCD
Optimised 2nd Generation Dolby Sound Room audio enhancement
HDMI, 3x USB 2.0
Multi-in-1 Card Reader
Gigabit Ethernet 10/100/1000Mbps Integrated
802.11 a/b/g/draft n
Intel Graphics Media Accelerator 4500MHD Shared System Memory
Integrated CrystalEye Webcam, 0.3 Megapixels
Microsoft Windows 7 Home Premium
6 Cell battery
1.4kg 

---

### Post by Paqman on 2012-02-08
> **chickenPie4breakfast said:**
> what makes of computer would give you the best chance of having next to no problems?

Generally speaking Intel chipsets will just work across the board, but that does mean you'll miss out of really good graphics. What do you intend to use the machine for?

---

### Post by SuaSwe on 2012-02-08
I've so far run Ubuntu on a Packard Bell EasyNote MZ35, a Hewlett Packard ProBook 4510s and most recently an Acer Aspire 4830T, all Intel chipset. All important hardware elements (ethernet, wireless, graphics, audio, etc) have worked out of the box and more or less stably with every Ubuntu release so far. :)

---

### Post by ikt on 2012-02-08
[http://www.ubuntu.com/certification/](http://www.ubuntu.com/certification/)

I also tend to google around a bit

"hp dm1 linux" for example.

And I'm pretty happy with it. :)

---

### Post by QIII on 2012-02-08
People did say in the past, and continue to say, to stay away from ATI.  ATI, when it was ATI, before it was bought by AMD, was horrible.

ATI was bought by AMD 5 or 6 years ago.

AMD is a member of the Linux Foundation.  I don't know that NVIDIA is.

Take a look at ikt's link.  Notice how many of those machines run AMD graphics.

At any rate, these two things are true about ATI cards:

1.  You have to run the following in the terminal after installing the driver and before shutting down to generate an xorg.conf

```
sudo aticonfig --initial
```

(You may add the flag -f) or you'll get a black screen on reboot.   That is the most frequent "problem" with ATI cards and easily corrected by entering recovery mode, dropping to root and issuing the command above.

2.  There are a couple of extra steps to get true 3d acceleration.

While it is true that neither is required for Nvidia, it is not true that AMD/ATI cards are any more or less problematic than Nvidia.

Both make fine products.  It is simply a matter of your choice and sensibilities.

---

### Post by PapaGary on 2012-02-08
This is probably not going to help much as my three Dell laptops are at least 5 years old (and all Intel)  but trying/installing Ubuntu went without a hitch with everything working after bootup. My new Toshiba was a different story but after a few tweaks works well.

---

### Post by Penguinnerd on 2012-02-08
System76. Although I haven't yet owned one of their systems, I look forward to buying my next PC from them as soon as my current one can't "keep up" anymore.

---

### Post by GraeW on 2012-02-08
buying a new laptop, depending on what I can afford, I might look at the System76 systems available. Otherwise Acer and HP seem to have good reviews and performance (I am currently running Ubuntu 11.10 on a 5 year old Acer Aspire 5050 with no real issues).
 
I would love to get one of those Macbook Air wannabes and put Ubuntu on there, but I have not heard how they have done with installs yet..

---

### Post by tersogar on 2012-02-08
I bought one from System76 two years ago and very happy with my choice.:popcorn:

---

### Post by Mark Phelps on 2012-02-08
Check the specs on anything you're considering -- and avoid anything that mentions Switchable Graphics or Hybrid Graphics. That's not implemented well (some would say, not at ALL) in Linux.

Unfortunately, this seems to include the recent HP laptops.

---

### Post by Henkdroid on 2012-02-08
I have a Lenovo ThinkPad T61 and it works 100% and it also worked well on a HP ProBook 4575 (I think) but I think most of the big brand computers will work well. With System 76 I don't think you will have any problems as they are shipped with Ubuntu.

---

### Post by chickenPie4breakfast on 2012-02-08
Thanks for the replies, I must admit I had never heard of Sytem76 ! will check it out, Glad to hear also that Acer gets a mention as that is what I am using now (TravelMate 2410).

As for hardware I know I will be avoiding Canon printers from now on as my current one is useless Ipixima2000  will go with HP.
Has anyone got devices like the TOMTOM to work with linux?

---

### Post by SeijiSensei on 2012-02-08
HP laptops are a pain in the neck if you want to create a dual-boot system.  That's because HP partitions the hard drive into four primary partitions leaving no place for Linux to be installed.  [Here are the steps]("http://ubuntuforums.org/showpost.php?p=11299287&postcount=5") I had to take to install Ubuntu on my daughter's HP dv6t.

---

### Post by 23senick on 2012-02-08
[SeijiSensei]("http://ubuntuforums.org/member.php?u=698195") has a point, I also had to fiddle with HP partitions (HP dm1 4020).  Surmountable but a pain.  I'd also check type of wireless card - Broadcom cards seem to cause a few problems. Mine now works most of the time but still occasionally requires wifi disconnect for a few minutes after boot, then reconnect.  I also have an Acer Aspire One A110L which has been excellent with Xubuntu 10.04.

---

### Post by alphacrucis2 on 2012-02-08
The major problem with graphics for both AMD and NVIDIA are laptops that run hybrid Intel/AMD or Intel/NVIDIA. I have a Lenovo laptop with Optimus (Intel/NVIDIA) graphics and it was a right PITA, even using bumblebee. Luckily Lenovo allow you to disable the optimus in the bios so that only the NVIDIA graphics is seen by the OS. It probably means a bit higher power usage but I don't really care as I rarely run on battery.

---

### Post by uuugrrrl on 2012-02-08
Oh Papa, can you help me? My Toshiba windows 7 stalled during Wubi installation then the remaining time began to increase instead of decrease! You mentioned that Toshibas' have special needs--What do I need to do get wubi installed? I've tried several times with no luck and would really appreciate your help.

---

### Post by PapaGary on 2012-02-09
> **uuugrrrl said:**
> Oh Papa, can you help me? My Toshiba windows 7 stalled during Wubi installation then the remaining time began to increase instead of decrease! You mentioned that Toshibas' have special needs--What do I need to do get wubi installed? I've tried several times with no luck and would really appreciate your help.
I had wireless and sound problems. I don't know anything about WUBI.

Sorry.

---

### Post by wildmanne39 on 2012-02-09
Hi, I have an older hp laptop that works great with ubuntu and it uses nvidia graphics, but there are so many different configurations of computers there is no way to say that everything will work out of the box.

It is true that optimus which is hybrid graphics should not be bought for now.

Also remember if any of the components in the computer have just came out and have not been around long enough for the linux community to develop drivers for them then component is not going to work.
Thanks

---

### Post by wolfen69 on 2012-02-09
> **Mark Phelps said:**
> Check the specs on anything you're considering -- and avoid anything that mentions Switchable Graphics or Hybrid Graphics. 

I agree with this. If you are not a gamer, stay with Intel graphics. It is well supported. Optimus and AMD hybrids are a nightmare right now.

---

