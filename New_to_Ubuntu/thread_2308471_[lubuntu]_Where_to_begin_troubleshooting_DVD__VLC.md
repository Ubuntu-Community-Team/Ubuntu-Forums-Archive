---
title: "[lubuntu] Where to begin troubleshooting DVD / VLC?"
date: 2016-01-03
forum: New to Ubuntu
---

### Post by nginmu on 2016-01-03
I installed lubuntu 15.04 i386 on a 2006 Compaq Presario V6000 series (V6254EA) 32bit intel core2 based laptop with a LG GSA-T10N IDE DVD unit, alongside the previous Windows XP installation that was on it, as a dual boot setup.

I then installed the current version of VLC media player through synaptic.

I have a selection of test DVD films, all of which play fine in the Windows XP installation using VLC.

In lubuntu however, I'm finding certain of the DVDs won't play.

In some cases VLC's 'open disc' option works straight off the gun. Other times, a DVD will play but only if you use VLC to manually navigate the DVD to the required video file. Sometimes either option will initially work but I'll be taken to the DVD's root menu, from then on it's unresponsive and clicking e.g. 'play all' does nothing. Sometimes VLC seems to want to have no truck with a DVD at all.

Strangely, sometimes it's the oldest dirtiest scratchiest home-recorded DVDs with the most obscure file systems that play just fine, whilst brand spanking new shop-bought cellophane wrapped titles fail.

One thing I did try on one 'failing' DVD, was to copy a video file from it to the lubuntu desktop then try to play it from there. It failed. but the first indication something was wrong was actually at the point where I used lubuntu's file manager to copy the video file from the DVD to the desktop. lubuntu said, "**Error** **Splicing** **File**: Input/Output **Error**"

This all makes me think;
- the DVD drive is okay because everything works just fine in XP
- VLC is basically ok with all the DVDs I have, since it plays them in XP ok
- the problem is something to do with how lubuntu interfaces with the DVD unit (splicing error on attempted file copy before even seeing VLC)

I considered replacing the DVD drive with a new one, or re-flashing it's firmware, but because it all works fine in XP I'm not sure if that would help

What I'd like is not so much a comprehensive solution served up on a plate, as some help and pointers as to where I should even begin researching! Thanks for any suggestions.

---

### Post by brian-mccumber on 2016-01-03
You should have to install Ubuntu Restricted extras to get the correct codecs for reading/viewing dvd videos. It is available in the repository or you can install your version using the guide at this link - [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats). Make sure to pick the lubuntu install under the Easy Install section and then do not forget to add libdvdcss using the instructions found under Add libdvdcss. I did not install libdvdcss on my desktop and it wouldn't play newer videos until I ran that one line from Add libdvdcss section in the terminal. I do not use vlc I use the videos app that came with Ubuntu after I installed restricted extras and libdvdcss and I haven't had anything that wouldn't play since.

---

### Post by nginmu on 2016-01-04
Thank you Brian :-)

Upon "pick the lubuntu install under the Easy Install section", It asked me if I wanted to use "AptURL" to "Install additional software?" - I selected "Install". I then got a popup that read "! Requires installation of untrusted packages". It only had one option - "Close".

I clicked "Close", unfortunately after that there seemed to be no obvious indication of anything significant happening on my system - all related dialogs just closed themselves.

I'll try having a look in Synaptic to install lubuntu-restricted-extras the alternative way, before running the terminal code suggested to add libdvdccs.

---

### Post by nginmu on 2016-01-04
> I'll try having a look in Synaptic to install lubuntu-restricted-extras  the alternative way, before running the terminal code suggested to add  libdvdccs. 				

that did the trick. Family Guy DVD hitherto unplayable, now playing fullscreen on VLC like a good'un :-)

many many thanks.

---

### Post by Geoffrey_Arndt on 2016-01-04
Do both, starting with the"restricted extras" package using command line or synaptic.

---

