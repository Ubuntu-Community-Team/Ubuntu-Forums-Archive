---
title: "trying to play a 1080p .wmv file that is WVC1 encoded?"
date: 2008-11-23
forum: New to Ubuntu
---

### Post by ijason on 2008-11-23
i've searched for a couple hours to try and find an existing thread that answers my question, but i haven't yet, so i'm posting a new one. 

i have several large (1-2gig) .wmv files i'm trying to watch. with VLC, or mPlayer i get blocky garbage peppered with few-second-long bits of the video working, and a whole lot of black screen between. i assumed this was due to chronic problems with ubuntu and the .wmv format, and maybe an issue with only having one gig of ram. 

however, when i put the .wmv file on a windows machine it promptly requested to download a codec for the WVC1 video format... which it failed to find. and now i'm reading a lot of people saying that WVC1 is only supported by Windows Media Player version 11, and that there is no support for it in the ubuntu community?

i can't find any posts newer than 2007, so any help would be really appreciated.

---

### Post by kostkon on 2008-11-23
> **ijason said:**
> i've searched for a couple hours to try and find an existing thread that answers my question, but i haven't yet, so i'm posting a new one. 

i have several large (1-2gig) .wmv files i'm trying to watch. with VLC, or mPlayer i get blocky garbage peppered with few-second-long bits of the video working, and a whole lot of black screen between. i assumed this was due to chronic problems with ubuntu and the .wmv format, and maybe an issue with only having one gig of ram. 

however, when i put the .wmv file on a windows machine it promptly requested to download a codec for the WVC1 video format... which it failed to find. and now i'm reading a lot of people saying that WVC1 is only supported by Windows Media Player version 11, and that there is no support for it in the ubuntu community?

i can't find any posts newer than 2007, so any help would be really appreciated.
Do you have the *w32codecs* installed? They will be used by *Mplayer* or *Totem*, for example, but not by *VLC*, which only uses its own codecs.

---

### Post by ijason on 2008-11-23
i have all of the codecs installed that were part of the mediabuntu project. 

synaptic gives version 20071007-Omedibuntu2 as the installed w32codecs

---

### Post by Tom--d on 2008-11-23
Its most likey your Graphics Card since 1080p needs a good GPU.

My Intel (965) card cant handle it.

Also, in Mplayer, make the video to Xv (This is then accelerated by the GPU. Not CPU.)

---

### Post by ijason on 2008-11-23
sadly, my video card is still the onboard video chip. :) i will eventually upgrade to an actual video card, but not just yet. 

any word on VLC /mPlayer support for this WVC1 codec? or support from any other program available to ubuntu?

---

### Post by bobnutfield on 2008-11-23
Type in a terminal:

> locate wvc1

If you get output like:

> /usr/lib/codecs/wvc1dmod.dll


then it is likely that you have the necessary codec to play that media.  Can't confirm, of course, but I believe you will find that as previously mentioned, 1080p requires at 256mb of dedicated graphics memory, I believe.  Someone may correct me, but I believe that is your main problem.

---

### Post by ijason on 2008-11-23
ah... thanks bob. i do get the response that indicates i have the driver for wvc1 in a .dll file. so at least that confirms i have the right driver :)

ha. i think my onboard video is 128 megs of _shared_ memory! i have seen a lot of talk about needing more ram and a substantial video card to handle the 1080p vidoes, so i think that must be my biggest problem.

---

### Post by bobnutfield on 2008-11-23
If you have an older PC with an AGP slot, you can pick up an nVidia 5500FX for about £10 ($15) on eBay.  I have that card in an old AMD64 3400 and it handles just about anything I can throw at it.

---

### Post by shifty_powers on 2008-11-23
inclduing hd 1080p? i severely doubt it.

dude, unless you have a beefy 3ghz core2duo minimum, you ain't play hd content with integrated graphics...

---

### Post by ijason on 2008-11-23
apparently not!

i'm running a real light box right now, it has a decent 3ghz processor, but only a gig of ram and still using the onboard for graphics. it has a PCIexpress card for when i eventually put in the video card. 

my biggest concern was if it was a software/codec issue.

---

### Post by Neostar on 2008-11-23
You can get graphic cards with built-in support for 1080p video. But I suggest you re-encode that video to play on your current system.

---

