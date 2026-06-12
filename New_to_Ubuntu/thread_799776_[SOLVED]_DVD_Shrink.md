---
title: "[SOLVED] DVD Shrink"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by CoCoKnots on 2008-05-19
I started to install DVD Shrink as per [www.mrbass.org](www.mrbass.org) instructions.
The Terminal command in the instructions comes back with no such file found.
I tried both options...

[COLOR="Blue"]Verify DMA is enabled for your DVD burner
hdparm /dev/hdd
It should say using_dma = 1 (on)
If not sudo /etc/hdparm.conf and append the following:
/dev/hdd {
dma = on
}
Now reboot and verify DMA is enabled[/COLOR]

I've used DVD Shrink before with Windows XP. This looks like there is
a lot of issues using it with wine. Is this easier than it looks? 
Or perhaps there is another copy program more compatible with Ubuntu?
Thanks,
Cal

---

### Post by TeoBigusGeekus on 2008-05-19
Have you tried k9copy?
It's in the Add/Remove Programs, in the sound and video section.

EDIT: Check DVD95 Converter as well.

---

### Post by CoCoKnots on 2008-05-19
Thanks TeoBigus,
I haven't tried either of these yet... I didn't know if there was anything out there to try that might be a little less stressful. Thanks Again, Cal

---

### Post by mc4man on 2008-05-19
> Is this easier than it looks? 
Those instructions are very dated, with any of the recent wine versions just install shrink and it will run fine. Just make sure in winecfg it's set to win nt 4.0 or win xp and that you've run auto detect drives. You can choose to have it install desktop icon for ease of access.
+1 also for k9copy

---

### Post by CoCoKnots on 2008-05-19
Thanks MC4Man. How do I set the wine config to windows XP? I assume that is a sudo command... Q: I heard wine can be a security issue... Is that correct?

---

### Post by bumanie on 2008-05-19
Try k9copy first. It does the same as dvd shrink. If you don't like it, then go down the track with wine. I believe that would be the easiest way to go.

---

### Post by stchman on 2008-05-19
> **CoCoKnots said:**
> I started to install DVD Shrink as per [www.mrbass.org](www.mrbass.org) instructions.
The Terminal command in the instructions comes back with no such file found.
I tried both options...

[COLOR="Blue"]Verify DMA is enabled for your DVD burner
hdparm /dev/hdd
It should say using_dma = 1 (on)
If not sudo /etc/hdparm.conf and append the following:
/dev/hdd {
dma = on
}
Now reboot and verify DMA is enabled[/COLOR]

I've used DVD Shrink before with Windows XP. This looks like there is
a lot of issues using it with wine. Is this easier than it looks? 
Or perhaps there is another copy program more compatible with Ubuntu?
Thanks,
Cal

I have a script to install DVDShrink in Ubuntu.

[http://www.stchman.com/tools_page.html](http://www.stchman.com/tools_page.html)

Look in the Scripts section.  I recommend K9Copy as it works the same.

---

### Post by Ryadt on 2008-05-19
hi..give dvd::rip a try...

---

### Post by mc4man on 2008-05-19
> How do I set the wine config to windows XP? Run winecfg from either terminal or app menu (configure wine), it's in a drop down on bottom of main page

edit: if you get a preloader error on winecfg see here
[http://wiki.winehq.org/PreloaderPageZeroProblem](http://wiki.winehq.org/PreloaderPageZeroProblem)

---

### Post by stchman on 2008-05-19
Remember DVDShrink does not burn DVDs.  It merely rips encrypted DVD into the corresponding AUDIO_TS and VIDEO_TS folders.

After that then choose the burner app you like and away you go.

---

### Post by CoCoKnots on 2008-05-19
OK... I went to Applications/Add&Remove... I added everything I could fine for GStreamer. However, I couldn't find anything for K9 or K9Copy... It sounded like it should already be in my 'add/remove' list.

---

### Post by TeoBigusGeekus on 2008-05-19
Try from terminal
```
sudo apt-get update
```
```
sudo apt-get install k9copy
```

---

### Post by mc4man on 2008-05-19
> OK... I went to Applications/Add&Remove look in synaptic if not ck. admin -> software sources and make sure the first 4 are checked in ubuntu software

> After that then choose the burner app you like and away you go. if you end up installing wine you might as well avail yourself of the best iso creator, burner - Imgburn  [http://www.imgburn.com/](http://www.imgburn.com/)
older ver. for rare wine version issues - [http://www.filehippo.com/download_imgburn/2242/](http://www.filehippo.com/download_imgburn/2242/)

---

### Post by CoCoKnots on 2008-05-19
OK... I found all kind of toys. I now have k9copy, Dvd95 & K3B for burning. Does this sound like a full tool box or is there something else I require for this project?

---

### Post by CoCoKnots on 2008-05-19
Thanks Raydt,

I am not certain which ver of DVD::Rip to use. I have Ubuntu 7.10 I believe that is Gutsy.

---

### Post by Ryadt on 2008-05-19
It should be in Add/Remove...

---

### Post by mapes12 on 2008-05-19
I agree with the other posts and have had great results with K9copy. It does the shrinking for you. Also, it's work having K3b on your box as well.

---

