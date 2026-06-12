---
title: "Very Slow Video Playback"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by iain010100 on 2008-05-06
I just upgraded to ubuntu 8.04. Anytime I play a video it's really slow. I think there was something on the command line I ran to fix the problem in the last major ubuntu release that increased the cache size. Does anyone know what I'm talking about?

---

### Post by subzero316 on 2008-05-06
In the Terminal

Type:

```
sudo gconf-editor
```
Click Apps >>> Totem
In The Righthand Pane Find "buffer-size"
Double-Click It >> Change The Value  Higher

---

### Post by subzero316 on 2008-05-06
Also try, VLC player its a good one.

---

### Post by iain010100 on 2008-05-06
Hmm. Increasing the video buffer size didn't work.

> **subzero316 said:**
> Also try, VLC player its a good one.

How do I change VLC to be the default player?

---

### Post by subzero316 on 2008-05-06
> 



How do I change VLC to be the default player?



Open Applications->AlacarteMenuEditor
Go to Sound&Videos>> right click 'Movie player' and choose Properties
change "totem %U" command with "vlc",, close it.

---

### Post by iain010100 on 2008-05-08
For me VLC has no sound. And it becomes unresponsive. But when it works it isn't slow. Totem used to work just fine. But now it plays back at one frame per seconds.

---

### Post by sujoy on 2008-05-08
i uninstalled totem and now i use only vlc and mplayer

---

### Post by Ian Clark on 2008-05-11
> **iain010100 said:**
> For me VLC has no sound. And it becomes unresponsive. But when it works it isn't slow. Totem used to work just fine. But now it plays back at one frame per second.
Ditto here.  I wish I had a clue as to what it's conflicting with.  My flash plays fine in FF3 on Youtube.  My sound and video are good in other areas.  It's just that totem is on strike.

---

### Post by Ian Clark on 2008-05-11
> **iain010100 said:**
> For me VLC has no sound. And it becomes unresponsive. But when it works it isn't slow. Totem used to work just fine. But now it plays back at one frame per seconds.
I found that by uninstalling avidemux and pitivi the problem was solved.  I don't know which one was the issue, though because I uninstalled them at the same time.  If you have either of these programs try an uninstall, run apt-get update or reboot and see if that helps.

---

### Post by Kinney on 2008-05-13
I was having a similar problem but I found a different resolution for it. It seemed that my problem was with the PulseAudio Sound Server. I fixed it by going to 

System > Preferences > Sound

and I changed all the playback options from Autodetect to ALSA and everything seems to be working now.

Hope this helps

---

### Post by TomG on 2008-05-19
Thanks Kinney. 
The ALSA trick fixed my problem too.

---

### Post by tapu on 2008-07-04
sujoys soln wrkd..thnxx!!!
:)

---

### Post by SabreWolfy on 2008-07-06
> **Kinney said:**
> I was having a similar problem but I found a different resolution for it. It seemed that my problem was with the PulseAudio Sound Server. I fixed it by going to 

System > Preferences > Sound

and I changed all the playback options from Autodetect to ALSA and everything seems to be working now.

Hope this helps

Thanks. Sorted out very slow playback of flash video in Totem. Was only a problem after the latest batch of updates (from the last week or two) which I did yesterday. Prior to that, it had been working fine. Thanks though.

---

### Post by manishr on 2008-07-06
changing the sound settings from autodetect to ALSA corrected the totem video playback for me too. thanks.

---

### Post by jorge87 on 2008-08-29
Thanks Kinney

Fixed!

---

### Post by Crafty Kisses on 2008-08-29
Please mark the thread solved, thanks! :)

---

### Post by Jason Quinn on 2008-09-06
> **Kinney said:**
> I was having a similar problem but I found a different resolution for it. It seemed that my problem was with the PulseAudio Sound Server. I fixed it by going to 

System > Preferences > Sound

and I changed all the playback options from Autodetect to ALSA and everything seems to be working now.

Hope this helps


Yes! It did help thanks a lot!

---

