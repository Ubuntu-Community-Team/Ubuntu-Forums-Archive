---
title: "playing .wmv files with mplayer"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by marcusesses on 2008-08-08
Hi, 

I'm having trouble playing movies (downloaded or streaming) with mplayer (which I installed because they wouldn't play in Totem).

I've installed restricted-extras, xine-plugin, ffmpeg in gstreamer and w32-codecs...when I try to play movies, it runs either really slow, or it just doesn't play at all (both with no sound).

I'd appreciate any help. I'm certain someones posted this problem before, but searching through the forums provided no new insight. 

Thanks!

---

### Post by Stemp on 2008-08-08
Hi,

Try to change the preferences settings.
In Audio (if you are on Hardy) it should be Pulse.
In Video, try XV

---

### Post by marcusesses on 2008-08-08
I'll try that...

I installed VLC player, however, and it seemed to play downloaded videos(not sure about streaming)...but now there's no sound at ALL on my computer, and Rhythmbox if refusing to play music (after it finally started working last night...)

I'll try the fix you suggested, and perhaps back out of some changes I made...(BTW, I installed vlc-plugin-alsa , which didn't work, nor did Pulse)

UPDATE: audio was pulse and video was xv...Any fixes for mplayer or VLC are welcome...

---

### Post by Stemp on 2008-08-08
What video drivers are you using ?
And for the sound I guess you have a bigger problem with pulse if there is no sound :(

---

### Post by marcusesses on 2008-08-08
*-display:0 UNCLAIMED
             description: VGA compatible controller
             product: Mobile GM965/GL960 Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list
             configuration: latency=0
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile GM965/GL960 Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0


I think (???) this lists it...

---

### Post by Stemp on 2008-08-08
There were some problems with Intel GMA cards, compiz and XV. But I don't know if it's still revelant.
Try using the X11 video output.

---

### Post by marcusesses on 2008-08-08
How do I do that?

It's also not responding once it's finished playing a video, and I have to force quit

AND....whenever I open any video with VLC, the brightness on my monitor turns down to below half..does VLC require this in some systems for the videos to play? I can turn up the brightness once the video is playing, with no ill effects...

---

### Post by Stemp on 2008-08-08
In mplayer and vlc in preferences, choose X11 in Video Mode.
Gmplayer: right click, Preferences, Videos... choose X11
Vlc : Menu Parameters, Preferences, Video, Output, choose X11

---

### Post by marcusesses on 2008-08-08
No change for VLC.
I tried it for mplayer, but there are about 7 options, 5 of which are X11 (and I think I'm going to stick to VLC anyway).

Any more suggestions/ideas?

I am trying to remember what I did to kill the sound.,..

---

### Post by Stemp on 2008-08-08
You tried to restart pulseaudio in a Terminal ?

---

### Post by marcusesses on 2008-08-08
BAH!

All I needed to do was reboot....Rhythmbox and VLC now both work(and VLC doesn't dim the monitor)...I'll update in a few minutes about streaming video though (I need to watch the Olympics!)

UPDATE: And now all of a sudden it stopped working again! I checked a test page to see if it would play WMV (which it didn't, and now it crapped out again!)

---

