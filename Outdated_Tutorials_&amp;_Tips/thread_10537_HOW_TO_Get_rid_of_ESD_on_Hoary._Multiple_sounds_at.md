---
title: "HOW TO: Get rid of ESD on Hoary. Multiple sounds at once support aswell."
date: 2005-01-09
forum: Outdated Tutorials &amp; Tips
---

### Post by xhaker on 2005-01-09
This process will remove ESD and install polypaudio, a better and esd-compatible sound server. This process will work only on Hoary.
From polyaudio site:> polypaudio is a sound server for Linux and other Unix like operating systems. It is intended to be an improved drop-in replacement for the Enlightened Sound Daemon (ESOUND). It is my ultimate ambition to get Polypaudio into Gnome as a replacement for ESOUND. First you need to enable the universe repositories. (check Ubuntu Starter Guide, if you're reading this you should have them enabled tho :D )
Now for the real deal:
```

sudo apt-get update && sudo apt-get install polypaudio polypaudio-alsa libesd-alsa0
sudo shutdown -r now

``` 

PS: If you used another process before to hear multiple sounds at once make sure you don't have /etc/asound.conf, your esd.conf is not configured with "-d default" and such.
PS1: I'm not sure if this doesn't disable i.e.: gaim sounds. I need you to test :D

---

### Post by YorHel on 2005-01-15
hmm... well, I did this, and the gnome, totem, and gmplayer-sounds didn't work anymore (I couln't get them working)
but sounds in games (tuxracer, Scorched 3D) and gaim, work fine now

but still, I can't hear multiple sounds at once...I still can't listen to music with xmms and hear gaim sounds/watch videos with xine at the same time

---

### Post by baylisscg on 2005-01-15
Hi,

    I installed libpolyp0, libpolyp0-glib2.0, libsamplerate0, polypaudio, polypaudio-alsa, polypaudio-clients and polypaudio-x11. But it doesn't quite work. I had libesd-alsa0 from my ESD install. No sound servers are started ( esd or polyp ).

> 
$ polypaudio -nC
main.c: read() failed: No such file or directory


    Which looks pretty terminal. Running "polypaudio -nC" is suggested by the polypaudio website to test the install. Like YorHel I get some audio. totem, rhythmbox and the test button in GStreamer properties work. Gaim and system sounds do not. I would guess anything which uses ESD is dead.

    To me it looks like the polypaudio package is broken taking anything that uses ESD with it.

EDIT:

  I probably should state that I'm using Hoary.

---

### Post by xhaker on 2005-01-15
i got it working for multiple sounds at once. 
like: Totem and rythmbox but gaim sounds wouldnt work if you had any of those open.
I reverted back to ESD because i cant use polypaudio sink in gstreamer-properties, i compiled something called polypsink but  couldnt select it at the dialog.
I guess polypaudio is just not ready to be used with gnome/gstreamer right now.

BTW, polypaudio is supposed to emulate a esd server  :-?

---

### Post by rwabel on 2005-01-16
[QUOTE=xhaker]This process will remove ESD and install polypaudio, a better and esd-compatible sound server. This process will work only on Hoary.
From polyaudio site: First you need to enable the universe repositories. (check Ubuntu Starter Guide, if you're reading this you should have them enabled tho :D )
Now for the real deal:
```

sudo apt-get update && sudo apt-get install polypaudio polypaudio-alsa libesd-alsa0
sudo shutdown -r now

``` 

PS: If you used another process before to hear multiple sounds at once make sure you don't have /etc/asound.conf, your esd.conf is not configured with "-d default" and such.
PS1: I'm not sure if this doesn't disable i.e.: gaim sounds. I need you to test :D[/QUOTE]

thanks for the how-to, I have indeed followed once the other how-to for multiple sounds.
Now what should I do with the asound.conf and how do I check if esd.conf is configured with -d default?

thanks

---

### Post by baylisscg on 2005-01-16
You can check for *-d default* in */etc/esound/esd.conf*. Look on the spawn options line.

---

### Post by rwabel on 2005-01-16
[QUOTE=baylisscg]You can check for *-d default* in */etc/esound/esd.conf*. Look on the spawn options line.[/QUOTE]

thanks, I removed it. What about asound.confi?
Should I just remove ?

---

### Post by baylisscg on 2005-01-16
[QUOTE=rwabel]thanks, I removed it. What about asound.confi?
Should I just remove ?[/QUOTE]
 I don't know. I use an ~/.asoundrc file instead. I tried removing it but polypaudio still will not start ( same error ). 

It would appear that polypaudio uses OSS by default. I tried installing *polypaudio-alsa* and changing the config file /*etc/polypaudio/default.pa* to load the alsa-sink module but it's still broken. All I can suggest is reinstall ESD or have a good look at the polypaudio webpage [http://0pointer.de/lennart/projects/polypaudio/](http://0pointer.de/lennart/projects/polypaudio/). Sorry.

---

### Post by szundi on 2005-06-10
What a howto  :) 

Man, just try it before writing down how-to install.  [-X I followed your instructions, and the only thing you didn't try to enable (uncomment) esound-tcp option in the /etc/polypaudio/default.pa :) it **works** now for me.  \\:D/ 

Szundi

---

### Post by rwabel on 2005-06-11
[QUOTE=szundi]What a howto  :) 

Man, just try it before writing down how-to install.  [-X I followed your instructions, and the only thing you didn't try to enable (uncomment) esound-tcp option in the /etc/polypaudio/default.pa :) it **works** now for me.  \\:D/ 

Szundi[/QUOTE]
 what is that one for?

---

### Post by Xian on 2005-06-11
Heh. What's this doing in Warty Section?  :???:

---

### Post by jdong on 2005-06-11
[QUOTE=Xian]Heh. What's this doing in Warty Section?  :???:[/QUOTE]
Not the original author's mistake. The old generic HOWTO forum turned into the Warty howto forum. This change happened just a week before Hoary's release, so understandably some Hoary docs made it in.

---

