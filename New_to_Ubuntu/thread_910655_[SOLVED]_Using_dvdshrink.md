---
title: "[SOLVED] Using dvdshrink"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by Elephantman5 on 2008-09-04
I did dvdshrink install through crossover.
Relatively easy, works slightly. Although, this weird error that I never had before keeps happening.
As far as, when I restart and try dvdshrink again it works. I don't know what to look for, I already tried to do another installation of it through cross over and it keeps doing the same thing. (Crossover 7) (Hardy Heron 8.04 x64bit) (Latest dvdshrink)
I really do hate the linux dvd ripping programs out there.
I was checking into one of them, which required some earlier version of python, and it wouldn't let me install with the latest version; it was CLI, and I don't mind CLI at all, would prefer it actually. Just something simple to copy losslessly.
DVd shrink comes up with this error right as it starts to copy: 
```
DVD Shrink encountered an error and cannot continue. 
Failed to read file "D:\" 
Not ready.
```

I'm not running anything else that's using the drive. Finding this a bit weird. Another article said something about enabling DMA, but when I went to go do the commands, the directories weren't there, and I don't even know what DMA is. ;)
I've got all the lastest dependencies I think. 

If you have any suggestions fopr CLI dvd ripping programs (or why this problem is happening) that would be great.
Only as iso files, not that avi crap.

---

### Post by halitech on 2008-09-04
I think you need to make sure the dvd is mounted properly in Ubuntu and also tell WINE that D:\ is the same as /dev/cdrom(0, 1, whatever it is in your case) as it sounds like Crossover might be looking elsewhere for your dvd

---

### Post by mc4man on 2008-09-04
> Just something simple to copy losslessly.

try vobcopy
rips to title name folder with VIDEO_TS inside. (if you want an iso then make one from the VIDEO_TS
Basic command
> vobcopy -v -m -F 16   (assumes disk is mounted at /media/cdrom0
If different append command as such
> vobcopy -v -m -F 16 /media/cdrom1

k9copy also works well
If you don't want it to transcode set target sectors above disk size

If vobcopy starts showing a series of skipped blocks then the disk probably has structure protection, use k9 or DVDFABHD DECRYPTER in wine instead

---

### Post by bumanie on 2008-09-04
Hi there. I'd suggest you try k9copy a KDE application that works as well on KDE as it does on gnome

---

### Post by stinger30au on 2008-09-04
easy as pie

install wine from here

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

then install dvdfab free edition to copy the dvd to hdd as an .iso with all protections removed

[http://www.dvdfab.com/free.htm](http://www.dvdfab.com/free.htm)

once you have the .iso saved to your pc you can either run dvdshrink on it or run the linux native app dvd95convertor to convert from dvd 9 to dvd 5

---

### Post by Elephantman5 on 2008-09-04
Appreciated.

I really do not prefer k9, when I tried it, kind of felt like I was getting worse quality, and I got plenty of signs of that. (Preview image was screwed, )(errors.)
And I'm just doing iso's, so the program's transcoding features turned me off. 

DVD FAB gives worse compression rates then DVD shrink, at least in my experience.

I will post further news, (I'm installing Arch Linux) later. Not questions, just what I got working.
For example, there are a million other programs I can find, maybe I'll find a really good one I can share with you all.

Good day's night's.

---

### Post by anjilslaire on 2008-09-05
> **Elephantman5 said:**
> 
DVD FAB gives worse compression rates then DVD shrink

Incorrect.
The free version of DVDFab HD Decrypter does not shrink or compress. It rips a straight copy (minus encryptions) to the hard drive. I use it to get the movie in file format, not ISO. 

Afterwards, I use dvdshrink to compress, or acidrip to convert to xvid.

---

### Post by Elephantman5 on 2008-09-05
> **anjilslaire said:**
> Incorrect.
The free version of DVDFab HD Decrypter does not shrink or compress. It rips a straight copy (minus encryptions) to the hard drive. I use it to get the movie in file format, not ISO. 

Afterwards, I use dvdshrink to compress, or acidrip to convert to xvid.

You may be able to rip a straight copy, but when I directly compared the sizes of DVDshrink and DVDfab the latter was a noticeable amount over.
And who cares anyway, it's all a matter of preference.
I really don't feel like running my loot through 2 different conversions just for a backup.

In windows it was Anydvd and DVD shrink side by side. One conversion.
In linux, I'm looking for a CLI, and something similar to dvd decrypter. Who knows.

---

