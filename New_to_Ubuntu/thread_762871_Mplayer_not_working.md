---
title: "Mplayer not working"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by siretfel on 2008-04-22
Hello all,

Mplayer plugin in my firefox is NOT working at all. It doesn't stream video at all from any website.Apart from that when it RARELY does I cannot resume playback unless I buffer the whole video. 

Questions:
1. Does mplayer plugin in firefox work for you?
2. Does Hardy Heron has the same issues?

Thanx in advance

---

### Post by Nepherte on 2008-04-22
1. Yes, works perfect here
2. Don't use Hardy

Are you sure the mplayer plugin is installed correctly? Go to about:plugins in firefox and see if it's listed there. Do you have all the necessary codecs?

---

### Post by siretfel on 2008-04-22
DivX Browser Plug-In

    File name: mplayerplug-in-dvx.so
    mplayerplug-in 3.40

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

MIME Type 	Description 	Suffixes 	Enabled
video/divx 	DivX Media Format 	divx 	Yes
video/vnd.divx 	DivX Media Format 	divx 	Yes


Also all the media player plugins are using mplayer and all are enabled. Don't have a clue on what else to do.

Thanx for your answer though!

---

### Post by Saint Angeles on 2008-04-22
1) mplayer is my player of choice. it works beautifully.

2) hardy heron works way better than gutsy gibbon ever did. nepherte must not know much about hardy.

---

### Post by Chelidon on 2008-04-22
Do you have the necessary codecs? 
Use your package manager and pick up the Gstreamer plugins good, bad, and ugly, plus any others that would seem helpful to you.

---

