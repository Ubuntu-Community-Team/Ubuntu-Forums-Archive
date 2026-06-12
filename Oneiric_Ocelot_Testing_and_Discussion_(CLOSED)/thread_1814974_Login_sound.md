---
title: "Login sound"
date: 2011-07-30
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by cecilpierce on 2011-07-30
I don't hear a login sound any more.
Sound works with FireFox but just seems like system sounds are off, I hear sound effects in sound settings but under hardware, internal audio, test speakers, nothing heard.
Its set at Analog Stereo Duplex,
Thanks for any help or ideas

---

### Post by Harry33 on 2011-07-30
> **cecilpierce said:**
> I don't hear a login sound any more.
Sound works with FireFox but just seems like system sounds are off, I hear sound effects in sound settings but under hardware, internal audio, test speakers, nothing heard.
Its set at Analog Stereo Duplex,
Thanks for any help or ideas

Check from sound settings => sound effects, that the sound themes produce a sound.
Login sound is produced by the package gnome-session-canberra.
It uses the program canberra-gtk-play
from /usr/bin folder.

---

### Post by cecilpierce on 2011-07-30
@Harry33

I hear sounds when I change sound-themes.
What else can I do ?

---

### Post by 23dornot23d on 2011-07-30
I had to load the libcanberra libraries to get mine to work .... 

was reporting canberra-gtk missing or something .... earlier ......... no error now though ...

> 
errors so far
load canberra-gtk-module

g_settings_get_key_info: assertions  settings>priv > schema Null

Got HUP on stdin exiting ....                                              
you may have a different problem to me though as yours is allowing you to run Gnome-shell
mine was not ...... ( unless I used LXDE - and did gnome-shell --replace then it went in and showed me the error too  )

---

### Post by cecilpierce on 2011-07-30
Thanks Keith, I just re-installed everything and added all the libcanberra stuff in synaptic and still no sys sounds, I give up !
I've been trying to get it fixed for a long time, heck with it.
Well it works OK in my other 2 O.O.

---

### Post by 23dornot23d on 2011-07-30
Sounds are the one thing that I can never track down well

Lidex seems to be the one on here that can solve problems to do with sound
there may be others too ..... but Lidex was pretty thorough with a problem I had once.

Not sure what else to say other than looking at all the levels and settings .... but if you
have had it for a while its probably something either related to pulseaudio or alsa
and if it messes up the only thing is to go through all the sound settings and make sure
something silly is not muted or turned low .....

other than that ..... I could not say .... as you say you get other sounds working .......

[B]sudo aptitude install alsa-utils

alsamixer[/B] 

 I think I loaded once and ran it to see what was on and off ....   also supplies other info too

[SCREENSHOT]("http://img405.imageshack.us/img405/2667/screenshotat20110730210.jpg")

---

