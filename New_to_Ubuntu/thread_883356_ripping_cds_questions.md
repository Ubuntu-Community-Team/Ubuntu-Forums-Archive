---
title: "ripping cds questions"
date: 2008-08-07
forum: New to Ubuntu
---

### Post by steve joe bob on 2008-08-07
so i was gonna rip a cd unto my hdd and when i used windows and had itunes or something like that i would rip it in mp3 format and usually at 320 kbs. i want the best quality and i don't care how much hard drive space it takes up. well i went to rip a cd using Audio CD Extractor or Rythmbox Music Player and set it to cd quality mp3 or whatever the option was and ripped it and it ripped it at only 128 kbs. so i went back and clicked on edit and selected that profile and hit edit again. i didn't see anywhere where i could have it rip at a higher bit rate. honestly i didn't see a whole lot in that window that i really understand :P so i'm just looking for some help. i want to rip my cds at the BEST quality regardless of how much hard drive space it take. looking forward to learning thnx in advance

---

### Post by tuxxy on 2008-08-07
Have you tried grip?

---

### Post by logos34 on 2008-08-07
> **steve joe bob said:**
>  usually at 320 kbs. i want the best quality and i don't care how much hard drive space it takes up... i want to rip my cds at the BEST quality regardless of how much hard drive space it take. looking forward to learning thnx in advance

320 is not the 'best'...you should seriously consider ripping lossless (flac) if you want to get fanatical.  For only a bit more room you will get a bit-for-bit identical copy.  But I would also encourage you to consider the fact that you achieve transparency around ~200 kbps at most no matter what encoder you're using.  From that point of view 320 (especially if it's CBR) is totally pointless

[https://help.ubuntu.com/community/CDRipping](https://help.ubuntu.com/community/CDRipping)

---

### Post by pedrogent on 2008-08-07
Welcome to the joys of the GNOME DE. You might want to open up a terminal and type in:

```
gconf-editor
```

This will open up the configuration tool for GNOME apps (so you can tinker with the bits that are hidden away).

I believe that if you open up 'system' then 'gstreamer' and continue opening until you get to 'profiles' --> 'mp3' you will find the configuration bits you want.

Could be wrong tho'. I'm still trying to figure out gconf-editor myself.

Also, when you see options in the Apps you're using, often they aren't spelled out like '320' or '256' etc. Often it will be a scale of 0-9 (with 9 being the highest quality usually).

---

### Post by mc4man on 2008-08-08
while i don't use grip it seems it should work well. If you want to stick with mp3's any of the lame parameters should in accepted in the command line box.
see > lame --longhelp  or > lame --preset help

I would just use something like -V <quality>  where quality is a number from 0-9 (best to worst)
The difference between 0-3 may depend on your equipment, ears, and or imagination.
By default grip saves to a dir. named ogg in home, that can be changed. If your creating a m3u then change in options also.

Screens show mp3 encoding, variable bitrate, quality 0, saved to mp3 dir. in home

edit: the ogg save folder is ogg only in name (doesn't mean only for ogg encodes, if your not careful making the edits to change save dir. you may have issues, safest to just leave at default

you can ignore the encoding bitrate setting in options 
If you make config changes close and reopen grip

If space and external compatibility aren't an issue then as mentioned try flac. Same song - 38.7mb w/ flac, 10.1mb w/ lame @ -V 0

---

