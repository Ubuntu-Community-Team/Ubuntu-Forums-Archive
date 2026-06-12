---
title: "Does this mean a file is actually mpeg-2?"
date: 2013-11-27
forum: New to Ubuntu
---

### Post by squakie on 2013-11-27
I've been having a ton of problems and not really finding a way around them.

I use mediainfo on a video file  and the top part of the output says:

```
General
Complete name                            : Angels.and.Demons.m4v
Format                                   : MPEG-PS
File size                                : 1.76 GiB
Duration                                 : 2h 13mn
Overall bit rate mode                    : Variable
Overall bit rate                         : 1 883 Kbps

Video
ID                                       : 224 (0xE0)
Format                                   : MPEG Video
Format version                           : Version 2
Format profile                           : Main@Main

```

The first "Format" says MPEG-PS.  For the Video, it says the Format is "MPEG Video" with "Format version "Version 2".

Does this mean the video is MP2?  If so, does that mean I would need libdvdcss to play it?

*I have libdvdcss already installed, but having the problem with another system.  That system does not have libdvdcss available, but I can buy a mpeg-2 license for the hardware decoder.  If I know that the Video is actually mpeg-2 then I can buy that license.

---

### Post by 3rdalbum on 2013-11-27
> **squakie said:**
> I've been having a ton of problems and not really finding a way around them.

I use mediainfo on a video file  and the top part of the output says:

```
General
Complete name                            : Angels.and.Demons.m4v
Format                                   : MPEG-PS
File size                                : 1.76 GiB
Duration                                 : 2h 13mn
Overall bit rate mode                    : Variable
Overall bit rate                         : 1 883 Kbps

Video
ID                                       : 224 (0xE0)
Format                                   : MPEG Video
Format version                           : Version 2
Format profile                           : Main@Main

```

The first "Format" says MPEG-PS.  For the Video, it says the Format is "MPEG Video" with "Format version "Version 2".

Does this mean the video is MP2?  If so, does that mean I would need libdvdcss to play it?

*I have libdvdcss already installed, but having the problem with another system.  That system does not have libdvdcss available, but I can buy a mpeg-2 license for the hardware decoder.  If I know that the Video is actually mpeg-2 then I can buy that license.

Where did this file come from? It looks like it's an MPEG-2, but it's named like an MPEG-4. Try changing the filename extension to .mpg - I know it's dumb but some Linux video players require a valid filename extension like Windows.

Do you have the ubuntu-restricted-extras package installed? You will need that in order to play any MPEGs at all. You don't need libdvdcss, that's only for decoding DVDs.

And no, you don't need to buy an MPEG-2 license if you have the ubuntu-restricted-extras package.

---

### Post by squakie on 2013-11-27
This one I thought came from a disk - but I had to run it through makemkv because handbrake couldn't handle the DVD for some reason.  makemkv reported some errors as well, but the result was playable.  I believe the output type from it is mk4.  The rest I'm having trouble with came from scanning in VHS tapes in Windows XP via a Easycap device and the include Honestech VHS to DVD software.  What kind of output it put out I'm not sure, but they all say .mp4 I think, but come out with the same mediainfo output.

These all play fine in fact in Ubuntu.  My media center is a Raspberry Pi running OpenELEC (w/XBMC).  For some reason XBMC on the Pi doesn't  play the video - sound only.  They play fine in XBMC on ubuntu.

So, the only real difference I can figure out is that I have libdvdcss installed in ubuntu, whereas for the Pi I don't currently have the MP2 decoder license.

So I'm hoping they are mp2 so that all I have to do is buy the decoder license for the Pi's and they will play there as well.

That's why I was wondering if these are considered mp2, or if at least the video is mp2 - that would mean I just need the license on the Pi's.  If not, I'm stuck!

Thanks!

---

### Post by squakie on 2013-11-27
Okay, so I misunderstood what libdvdcss actually doesn't do, so obviously there are codecs involved from the restricted extras in Ubuntu (already had all of that installed).  So, I'm really hoping it's the mp2 thing - I have ordered the license for one of the Pi's to test out that theory.  Hopefully it works.  Thanks for the input on it looking like a mp2.  I did try the mpg thing but still only got sound, no video.

---

### Post by squakie on 2013-11-28
Had same problem posted in another forum.  Got an answer right away.

---

