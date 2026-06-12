---
title: "Firefox sound?"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by gustasonfrever on 2008-08-01
I've been having a lot of problems lately with ubuntu and audio. At first I was using VLC to watch a movie and then when I tried to open firefox and play some video I could get no audio. I restarted and this time I opened firefox first and started watching video. But when I opened VLC, I couldn't get any audio. After restarting once again I tried using VLC and then firefox, and was unable to listen to audio through firefox. All other programs still work, such as amarok. Do I just need to uninstall and then reinstall firefox? I've used Pulse Audio Applet and when I open it VLC and Rythmbox show up but firefox just flickers in and out, and won't stay in the list. 
This problem is becoming very frustrating as I can no longer use firefox for audio.

---

### Post by mevets on 2008-08-01
This is a pulse audio problem. There are ways to fix it supposedly but the best way I have found is to just use ALSA.

Go to System > Preferences > Sound and then set everything to ALSA.

---

### Post by gustasonfrever on 2008-08-01
I've already tried this, and it still doesn't work even after restarting. 
I have also figured out that it may be a problem with Flash, I was stumbling and found a trailer that began playing audio but then after I directed firefox to youtube audio wouldn't play on any video.

EDIT:
I just figured out how to fix the problem, I just needed to download libflashsupport

---

### Post by mevets on 2008-08-01
This also worked for me at one point:
> 
Be Default, libflashplugin (Flash 9 support in Firefox) doesn't work properly with PulseAudio.

Update: libflashsupport is available in Hardy as a package via the synaptic package manager.

Go to logicalnetworking.net to download the libflashsupport .deb and install it:

```

wget http://logicalnetworking.net/other/libflashsupport_1.0~2219-1_i386.deb
sudo dpkg -i libflashsupport_1.0~2219-1_i386.deb
```

Restart Firefox to enable simultaneous audio output from flash and other sources (rhythmbox, totem, etc). 

Though I must say this, it really made firefox start to crash a lot. After I uninstalled it, I still could play audio simultaneously (hope I didnt imagine this).

PS - [https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)

---

### Post by joshzam on 2008-08-01
libflashsupport fixed my Flash audio as well (and also started crashing Firefox OFTEN), but I still can't get audio from VLC. Movie Player plays my AVIs just fine, but VLC is giving me real headaches...

---

### Post by Xenoguy on 2008-08-01
this also works for the flash player 10 beta.

---

