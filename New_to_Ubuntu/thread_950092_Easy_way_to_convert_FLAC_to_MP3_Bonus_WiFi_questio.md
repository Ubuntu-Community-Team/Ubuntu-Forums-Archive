---
title: "Easy way to convert FLAC to MP3? Bonus WiFi question!"
date: 2008-10-16
forum: New to Ubuntu
---

### Post by Mooschief on 2008-10-16
Hello! I am pretty new to Ubuntu, and loving it (aside from the little niggles like Compiz and Flash).

I have a lot of music that is in FLAC format. I want to convert it to MP3 (yeah, I have an iPod, so sue me). I have Googled and tried installing a million different things, with no luck.

Sound Converter works, but will only encode at up to 256CBR. I like 320CBR.

SoundKonverter will only use WAV, no matter how many codecs I install.

OggConvert only works with OGG, obviously.

Any suggestions? This seems like a trivial task, and I find it hard to believe it's so difficult to accomplish.

Also, if you could buy any PCI wireless card to work with Hardy, which would it be if you wanted it to work perfectly out of the box?

---

### Post by RATM_Owns on 2008-10-16
ffmpeg -i (name).flac (name).mp3

---

### Post by Patb on 2008-10-16
Audacity if you want a gui.

Cheers, Pat.

---

### Post by naaman on 2008-10-24
Hey Mooschief..

I did note what you wanted to get done and I would think 

```
sudo apt-get install faac faad flac lame vorbis-tools nautilus-script-audio-convert
```

is your best bet..

The nautilus-script-audio-convert tool rocks! If you install it with a file browser window open, you will need to close and re-open it to see it in the right click menu.

It is quite annoying though when you are trying to write a reply on Ubuntu Forums and the windows keep popping up..

Also, apart from looking on the ubuntuforums and the Ubuntu wikis - try searching packages.ubuntu.com - I found this tool by searching for "convert"..

Arrivederci,

Naaman.

---

### Post by naaman on 2008-10-24
> **Mooschief said:**
> Also, if you could buy any PCI wireless card to work with Hardy, which would it be if you wanted it to work perfectly out of the box?

Oooh, bonus points..  Last time I researched the "Netgear WG311 802.11g" came up with Linux kernel support, however YKMV.. (Your Kilometre-age May Vary - bigups to the metric system)..

---

