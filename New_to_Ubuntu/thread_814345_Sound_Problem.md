---
title: "Sound Problem"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by londonlad on 2008-05-31
hi all,

when i start ubuntu, i get the normal lil drumroll at the beginning, but when i go to watch a movie file or an .mp3 file..........i get no sound at all! :(

---

### Post by linux4life88 on 2008-05-31
I would say that your sound card is under a restricted driver, but since you get sound when the computer comes on, this theory probably won't help any. Are you running Ubuntu 8.04? I've heard of problems with alsa, the sound layer for the new Ubuntu. Some programs don't play nice with alsa. This is not a problem that I've had myself but I know of others who have had this problem. Sorry if I'm not much help.

---

### Post by sayakb on 2008-05-31
Open a terminal and execute:
```
sudo apt-get install ubuntu-restricted-extras vlc
```
Skip VLC if already installed. VLC is an outstanding media player with extensive media support.

---

### Post by londonlad on 2008-05-31
boohoo! how do i uninstall what i just installed via the terminal? it makes no difference! :(

---

### Post by avtolle on 2008-05-31
Have you looked at the applications to see what output plugin they are set to? Under 8.04, Pulse Audio is the sound "whatever" in use. For example, under VLC, under Preferences, Audio, Output Modules, does Pulse Audio appear in the selection window? Similarly, Pulse Audio should be selected in Totem, et al, to utilize the native sound modules. Take a look and select the plugin, module, whatever the application calls it, for Pulse Audio; then try to play the movie or mp3 file, and "see" if there is sound. HTH.

---

### Post by londonlad on 2008-05-31
still no sound! :(

---

