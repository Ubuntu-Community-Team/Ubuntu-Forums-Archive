---
title: "How to rip dvd's?"
date: 2011-09-18
forum: New to Ubuntu
---

### Post by mschooler93 on 2011-09-18
I have Ubuntu 10.04, and I would like to know how to rip a DVD. It is not a movie, like you can buy in the stores, but it is a DVD for a school play I was in. 
If it helps, there are two folders in it (when I open it in a folder) 
AUDIO_TS (0 Items)
VIDEO_TS (11 Items)
(contents of VIDEO_TS): 
VIDEO_TS.BUP
VIDEO_TS.IFO
VIDEO_TS.VOB
VTS_01_0.BUP
VTS_01_0.IFO
VTS_01_0.VOB
VTS_01_1.VOB
VTS_01_2.VOB
VTS_01_3.VOB
VTS_01_4.VOB
VTS_01_5.VOB

So, I just want to make it into a video, like .avi, or something (whatever format is best, or available)

---

### Post by GWBouge on 2011-09-18
[Handbrake]("http://handbrake.fr/") (3rd party repo)
[Arista Transcoder]("http://www.transcoder.org/")
[dvd::rip]("http://www.exit1.org/dvdrip/")
[AcidRip]("http://www.togaware.com/linux/survivor/AcidRip_Simple.html")

to name a few ...

---

### Post by adit on 2011-09-18
> Handbrake (3rd party repo)
Arista Transcoder
dvd::rip
AcidRip
What is the advantage of using the above programs?  Why not just copy the .vob files to the hard drive?

---

### Post by mschooler93 on 2011-09-18
Installed Handbrake, and ripping now, but it is going painfully slow. Update soon.

---

### Post by mschooler93 on 2011-09-18
> **adit said:**
> What is the advantage of using the above programs?  Why not just copy the .vob files to the hard drive?

I tried to open them, but they wouldn't play by themselves.

---

### Post by adit on 2011-09-18
> I tried to open them, but they wouldn't play by themselves.
vlc player can play .vob files.

---

### Post by mschooler93 on 2011-09-18
> **adit said:**
> vlc player can play .vob files.

It will play the last 4 .vob files, but not the first one, or the other one. And there are no subtitles, and part of the play is spoken in french. But, other than that, vlc does play them.

---

### Post by GWBouge on 2011-09-18
I suppose you could make a ~/MyDVD folder, and copy the DVD's contents into there, then use VLC to load the ~/MyDVD directory to get all the menus, etc ... but, even though encoding takes forever, I generally find it easier to just rip'em into an avi or mkv or whatever, for the sake of simplicity and portability.

---

### Post by fooman on 2011-09-18
if all of the files are in their own folder.....just *right*-click on the folder and choose "open with > vlc media player" from the content menu.  that should play the entire dvd and include any menus.  if there was any sort of a subtitle track included in the folder (.sub, .srt, etc...),  it would show those as well.

---

