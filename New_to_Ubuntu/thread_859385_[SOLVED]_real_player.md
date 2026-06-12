---
title: "[SOLVED] real player"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by DarinB on 2008-07-14
i installed realplayer but can't find the launcher.
in it in the /bin file 
it shows up in synaptic but thats it 
i got it from the medibuntu web site and after i downloaded it i got an auto update on it
realplay in terminal shows not found??????

---

### Post by bumanie on 2008-07-14
alt + F2 then type realplayer in the box. It should launch.

---

### Post by DarinB on 2008-07-14
error message
could not open file

---

### Post by bumanie on 2008-07-14
Found this that my help. I hope it does.
Open a terminal window and type in:
sudo apt-get install realplayer
killall gnome-panel

The second command refreshes the GNOME panel.

After that you can find RealPlayer 10 in the Gnome menu under Applications -> Sound & Video.

---

### Post by DarinB on 2008-07-14
i am stumped this is what is installed
RealPlayer for Linux
RealPlayer is a media player with the aim of providing solid media
playback locally and via streaming. It plays RealAudio, RealVideo, MP3,
3GPP Video, Flash, SMIL 2.0, JPEG, GIF, PNG, RealPix and RealText,
Windows Media, and more. The RealPlayer 10 for Linux builds on top of
the popular open-source Helix Player.

(Converted from a rpm package by alien version 8.69.)

---

### Post by bumanie on 2008-07-14
I have never installed realplayer, but what I posted above seems to indicate that killall gnome-panel is important. Did you  do that? - I can't guarantee it is right though, as I have never done it as indicated.

---

### Post by DarinB on 2008-07-14
yeah i cut and pasted what ever you posted. 
i know it killall gnome panel since i saw it refresh
still no real player 
i reinstalled the package as well

---

### Post by LowSky on 2008-07-14
Do you need realplayer for anything?

Can I suggest VLC.. it runs nearly everything without a glitch

or use try plain helix

---

### Post by DarinB on 2008-07-14
i got some audio books (says real player only)that won't play on vlc and i got helix from synaptic also won't play.
i am thinking of giving up. bummer

---

### Post by DarinB on 2008-07-14
thank you for all the time you gave me...i found a link on this site to debian and got it working great apparently helix conflicts with it.
so i removed both completely with synaptic and got the player working from the debian site...too bad the .wav files still won't play.
that i can't figure out why even audiocity won't open them i thought i could convert them to mp3 but still no go
thanks again

---

