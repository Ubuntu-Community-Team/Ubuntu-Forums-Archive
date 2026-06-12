---
title: "[SOLVED] playing WMA files"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by sammasaurus on 2008-11-09
[SIZE="2"][FONT="Arial"]Hello!  I just switched to ubuntu and have zero experience.  I can't find anything that will allow me to play my WMA files on Audacious or Rhythmbox -- any ideas?  Also, I will need moderately detailed instructions if you'd be so generous.  Thank you!

Sam[/FONT][/SIZE]

---

### Post by SunnyRabbiera on 2008-11-09
well lets start, what version of Ubuntu are you using?
I heard there were problems with playing WMA in Ibex but lets see.

---

### Post by Crafty Kisses on 2008-11-09
You should be able to play WMA files in VLC.
```
sudo apt-get install vlc
```

---

### Post by pirattrev on 2008-11-09
if they are the DRM'd windows files I don't think you'll be able to play them. If they aren't DRM'd then VLC Media Player will be fine.

---

### Post by SunnyRabbiera on 2008-11-09
right there are some WMA files that wont work because of digital restrictions management, I also know some WMA files that work with WMP 10 and 11 wont work in ubuntu due to encoding crap.

---

### Post by ad_267 on 2008-11-09
If you go to System - Administration - Synaptic Package Manager, then search for and mark for installation "ubuntu-restricted-extras" you will get codecs for playing mp3, wma and other things like Sun Java. WMA files are working fine for me on Intrepid.

---

### Post by frankleeee on 2008-11-09
> **ad_267 said:**
> If you go to System - Administration - Synaptic Package Manager, then search for and mark for installation "ubuntu-restricted-extras" you will get codecs for playing mp3, wma and other things like Sun Java. WMA files are working fine for me on Intrepid.

Yes I have never run across a WMA that couldn't be played on a Free OS (Ubuntu)

---

### Post by ad_267 on 2008-11-09
> **frankleeee said:**
> Yes I have never run across a WMA that couldn't be played on a Free OS (Ubuntu)

Unless they are encrypted.

---

### Post by sammasaurus on 2008-11-09
Ok, so I already had the restricted-thing downloaded, no avail.  And what in Intrepid?  Can't find it in the Synaptic PM ..

---

### Post by sammasaurus on 2008-11-09
I have VLC already, but if I try to load my music folder it always poops out on me.  I think the folder might be too large for VLC to handle or something

---

### Post by Crafty Kisses on 2008-11-09
Go to **System ---> Administrator ---> Synaptic Packet Manager**.

---

### Post by sammasaurus on 2008-11-09
I already have VLC.  It opens and can handle a movie, but I'm looking for a program that I can load 6k songs through and listen to all of the files, regardless of their type.

---

### Post by ad_267 on 2008-11-09
> **sammasaurus said:**
> I already have VLC.  It opens and can handle a movie, but I'm looking for a program that I can load 6k songs through and listen to all of the files, regardless of their type.

Rhythmbox can do this if you install ubuntu-restricted-extras.
VLC can also play pretty much all media types.

---

### Post by frankleeee on 2008-11-09
The xmms2-plugin-avcodec  in the universe database is supposed to read wma but personally I always install all the gstreamer stuff along with vlc and the Ubuntu restricted extras. I am installing it now but it removes libavcodec-unstripped-51, 
but installs libavcodec51 (3:0.svn20080206-12ubuntu3) so if you have problems the history in synaptic will tell exactly what was added and removed, good luck.

---

### Post by sammasaurus on 2008-11-09
Well, thank you everyone.  It seems all of my RHCP songs, specifically, do not work.  Some other WMA files do, however.  Is there a way to convert WMA to MP3 to save these & other non-playable wma files, or should I just toss them (sadly)?

---

### Post by eolson on 2008-11-09
Will this help?

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by sammasaurus on 2008-11-09
I believe I have the newest Ubuntu, 1.0-something?  They are only listed up to 8.-something on that page.

---

### Post by mc4man on 2008-11-09
Before you toss those tracks have you tried playback in any xine engine player (amarok, totem-xine -  with libxine1-ffmpeg installed) or mplayer?
If they are wma *lossless*, vlc, rhythmbox, totem-gstreamer won't play

---

### Post by sammasaurus on 2008-11-09
> **mc4man said:**
> Before you toss those tracks have you tried playback in any xine engine player (amarok, totem-xine -  with libxine1-ffmpeg installed) or mplayer?
If they are wma *lossless*, vlc, rhythmbox, totem-gstreamer won't play

A friend installed xine for me.  But I have to say I hate the program, for aesthetic and functional reasons.  I'm looking for a program as similar to Winamp as possible.

---

### Post by ad_267 on 2008-11-09
If you're looking for something like Winamp try Audacious.

My guess is your RHCP songs have been encrypted. Did you rip the CD on Windows Media Player? I had a whole lot of songs on one computer that were unplayable on any other computer because WMP had encrypted them.

---

