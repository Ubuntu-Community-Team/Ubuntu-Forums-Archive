---
title: "player for music and dvd's"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by edwin2105z on 2008-07-16
just installed ubuntu and was wondering if it came with a media player or do i have to install one if so were do i go?

---

### Post by maddog39 on 2008-07-16
Yes there are a couple of media players. Please check the Applications > Sound & Video menu, namely the appplications Movie Player (Totem) and Rhythmbox.

---

### Post by halitech on 2008-07-16
depending on the media you are trying to play, you may have to install codecs to get them to work. One player that seems to work if codecs are installed or not is VLC and it works for music and movies

in a terminal paste this
```
sudo apt-get install vlc
```

---

### Post by RomeReactor on 2008-07-16
Hi. Regarding DVDs, [read this first]("https://help.ubuntu.com/8.04/musicvideophotos/C/video.html#video-dvd"). If you agree to install the libraries required for DVD playback, search for **ubuntu-restricted-extras**, **libxine1-all-plugins**, and **totem-xine** in Synaptic (System->Administration->Synaptic), read their descriptions, and install them. Or, to install them from the terminal (Applications->Accessories->Terminal):
```
sudo aptitude install ubuntu-restricted-extras totem-xine libxine1-all-plugins
```
Ubuntu-restricted-extras will install Flash and Java, MP3 playback for Totem and Rhythmbox, and DVD playback for Totem. The addition of totem-xine is due to totem-gstreamer not being able to play DVD menus.

To enable WMV and ASF playback, you need [w32codecs]("http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007-0medibuntu2_i386.deb") for Ubuntu 32 bit, or [w64codecs]("http://packages.medibuntu.org/pool/non-free/w/w64codecs/w64codecs_20071007-0medibuntu1_amd64.deb") for Ubuntu 64 bit, as standalone packages. Once you have the package, double-click on it to install. Note that by installing the w32codecs or w64codecs this way won't automatically update them; you can add the [Medibuntu repository]("https://help.ubuntu.com/community/Medibuntu"), so they will update when a new version comes out.

---

### Post by halitech on 2008-07-16
Thanks Rome, I forgot about the extras that he will also need

---

