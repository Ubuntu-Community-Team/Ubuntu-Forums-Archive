---
title: "Performance on old laptop with Windows XP"
date: 2012-10-12
forum: New to Ubuntu
---

### Post by colorfuldaegu on 2012-10-12
Hi all, first time posting here and new to linux.

My situation: I saved an old Dell Latitude C640 laptop from the garbage and upgraded the RAM to 1Gb and stuck an IDE SSD drive in it (maybe a waste of an SSD but it's faster now) and installed XP first and then Xubuntu alongside it.

I've noticed that watching videos in XP works perfectly, but I get really slow and choppy video in Xubuntu. I saved the old laptop to connect to an old CRT TV to watch movies (my new laptop only supports a digital signal) and I was wondering why Xubuntu can't handle video files. I use VLC Player on both OSs.

Interestingly, Windows XP refuses to recognize that my laptop is connected to a CRT via s-video link (even with updated graphics drivers) but Xubuntu auto-detected everything on install. So I can watch videos great in XP but can't send to the TV. I can't watch videos at all on Xubuntu, but it detects my TV without problem.

Here are the system specs:
Dell Latitude C640
Pentium 4 2GHZ Processor
1 GB DDR RAM
30 GB IDE SSD
ATI Radeon 7500

If I install Xubuntu alongside Windows XP does it greatly reduce the performance of Xubuntu? As it stands now, XP boots faster but I want to play around with Linux. My problem is when I play video, it is very slow and the audio and video doesn't sync well. Even when I try the same video file in Windows XP it works perfectly fine using the same program.

I don't know how to find the drivers or update them with Linux. Is my laptop fast enough to run Xubuntu properly? I could install Ubuntu but it was incredibly slow, I'm guessing it's because of the old processor.

Thank you for your help and advice!

---

### Post by pqwoerituytrueiwoq on 2012-10-12
to my knowledge ATI was not good about linux support (before AMD bought them)
this is likely the issue, xp just has better drivers for the gpu (edit: [http://www.thinkwiki.org/wiki/ATI_Mobility_Radeon_7500#Linux_driver_-_proprietary](http://www.thinkwiki.org/wiki/ATI_Mobility_Radeon_7500#Linux_driver_-_proprietary) )

did not know they made any IDE SSDs

---

### Post by squakie on 2012-10-12
Are you talking about any video, or from commercial DVD?  If commercial DVD, there are some steps you have to take first.  I don't know if we are allowed to mention them on the forum or not.  If you search the forum for something like:

can't play dvd

it will hopefully show some things.  If not, post back and we'll go from there.

---

### Post by squakie on 2012-10-12
For commercial DVD's, be sure you have libdvdread4 installed (I *think* that's what it's called) - it might be part of the ubuntu-restricted-extras package but I'm not sure.

After it is installed, do the following from a terminal window:

sudo /usr/share/doc/libdvdread4/install-css.sh

That will download and install the decryption parts of playing a DVD.  It can't be included with Ubuntu for legal reasons, and you should be aware of the legality in what ever country you live in.

---

### Post by shreepads on 2012-10-12
Burn a LiveCD of Puppy Linux and try playing video with that...

---

### Post by DarkAmbient on 2012-10-12
> **colorfuldaegu said:**
> 
Dell Latitude C640
Pentium 4 2GHZ Processor
1 GB DDR RAM
30 GB IDE SSD
ATI Radeon 7500

My laptops specs:
Acer Ferrari 3200
AMD Mobile Athlon 64 2800+ / 1.6 GHz
512.0 MB DDR SDRAM ( 2 x 256 MB )
ATI Mobility Radeon 9700 - (AGP 8x) 128.0 MB DDR SDRAM

I can "almost" watch 720p matroska-videos (low framerate) with that specs in Arch Linux with xfce. Computer boots in 10~ seconds too. But with your slighly better specs (and using a SSD-disk) it sounds like Arch could be an option. :) Ive tested Xubuntu (ubuntu with xfce) too, it's not as lightweight as Arch with xfce.

Arch isn't all that easy to install & setup though.

I'll stop rambling now :)

---

### Post by mips on 2012-10-12
I've got a laptop of similar age but slightly lower spec (1.4GHz Celeron OC'ed to 1.8GHz, **Intel GPU**, 1.5GB RAM) and I can play any vidoes up to 720p in fullscreen without skipping a beat.
720p videos uses about 40-85% cpu while all other content is below 25%

Now you have a higher spec laptop with a higher spec GPU so you should be able to play videos just fine which leads me to believe your issue lies with the ATI GPU drivers.

That said Xubuntu is pretty heavy resource wise so maybe try a Ubuntu netinstall and then xfce or whatever you prefer (openbox, lxde etc). Alternatively there is Arch but if that does not appeal look at Manjaro.

Also try the latest drivers from the xorg-edgers PPA first, [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

---

### Post by Mark Phelps on 2012-10-12
Actually, before AMD bought ATI, they had better Linux driver support, at least, for older video chipsets.  They haven't written Linux drivers for that chipset in years.  The PPA drivers might work better, but if they don't you're stuck, as the current AMD drivers definitely will not work.

---

### Post by colorfuldaegu on 2012-10-12
Wow lots of support on this forum! Thank you all for the replies!

I am only trying to watch downloaded video files. mpeg-4 files don't play very well, 720p won't play well at all. What confuses me is that these same files play with no problems at all in Windows XP so it must be a problem with drivers.

I noticed on the forums many people say the older ATI video cards do not have any linux support. I will give Puppy Linux a try, but in the meantime I'll try a few other solutions.

Everything else in Linux runs really well and I really like the look and feel of Xubuntu, I hope I can work something else out. Thank you all for your support and advice!

---

### Post by mips on 2012-10-12
> **colorfuldaegu said:**
> 
I noticed on the forums many people say the older ATI video cards do not have any linux support.

Not from ATI/AMD.

Try the latest opensource Radeon drivers, look in the xorg-edgers ppa I listed above.

---

### Post by squakie on 2012-10-13
> **pqwoerituytrueiwoq said:**
> to my knowledge ATI was not good about linux support (before AMD bought them)
this is likely the issue, xp just has better drivers for the gpu (edit: [http://www.thinkwiki.org/wiki/ATI_Mobility_Radeon_7500#Linux_driver_-_proprietary](http://www.thinkwiki.org/wiki/ATI_Mobility_Radeon_7500#Linux_driver_-_proprietary) )

did not know they made any IDE SSDs
Yep, but from everything I've seen they are a bit pricey!

---

### Post by squakie on 2012-10-13
> **colorfuldaegu said:**
> Wow lots of support on this forum! Thank you all for the replies!

I am only trying to watch downloaded video files. mpeg-4 files don't play very well, 720p won't play well at all. What confuses me is that these same files play with no problems at all in Windows XP so it must be a problem with drivers.

I noticed on the forums many people say the older ATI video cards do not have any linux support. I will give Puppy Linux a try, but in the meantime I'll try a few other solutions.

Everything else in Linux runs really well and I really like the look and feel of Xubuntu, I hope I can work something else out. Thank you all for your support and advice!
Let us know how things have gone with your testing.  I'm also curious as to the buss speed and the memory speed on your PC.  Do you know what type of memory is used in your PC?

Also, you may want to see if you have the ubuntu restricted extras package installed, as well as the gstreamer good, bad, and ugly packages.  I know some of those include extra codecs that may help in video playback.

---

### Post by mardybear on 2012-10-14
hi colorfuldaegu.

Your system rocks compared to my specs (700MHz celeron, 512MB ram, onboard graphics only), which is a dual boot system consisting of WindowsXP and Ubuntu 10.04. WindowsXP is a much older/leaner OS (~2001 release) and runs much snappier on my system too but because me likes Linux better i typically boot into Ubuntu.

Regarding your comment, installing Ubuntu alongside WindowsXP has no effect on performance. It only reduces your available hard drive space.

As already mentioned, some Linux OS and software will run leaner on your system than others. Puppy Linux is very snappy on my old system but I still prefer Ubuntu. It's a personal preference and a trade-off between performance and happy user :)

mardybear

---

### Post by mips on 2012-10-14
> **squakie said:**
> I'm also curious as to the bus speed and the memory speed on your PC.  Do you know what type of memory is used in your PC?

CPU: Pentium 4-M, 512KB L2 Cache, 2GHz, 400MHz FSB (100x4), 1.3V, 32Watt, Socket 478.
RAM: DDR SDRAM @ 266MHz (PC2100)

---

### Post by MoebusNet on 2012-10-14
My old laptop runs a 1.4 Ghz Pentium-M, 2 Gb RAM, 32 Mb Nvidia Geforce4 Ti 4200 Go video card on Lubuntu 12.04. The limiting factor for our older machines is the video card, because of driver support as you mentioned.

As far as multimedia, have you read this?

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

This has been the standard by which all multimedia is measured on Ubuntu for quite a while now.

---

### Post by marsi on 2012-10-14
ooo a lot of informatins here..thnx a lot
[http://www.lajm-shqip.com](http://www.lajm-shqip.com)

---

