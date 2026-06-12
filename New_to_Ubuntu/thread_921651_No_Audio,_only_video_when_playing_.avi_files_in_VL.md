---
title: "No Audio, only video when playing .avi files in VLC"
date: 2008-09-16
forum: New to Ubuntu
---

### Post by Delslayer on 2008-09-16
Just installed VLC and I get no audio when watching a .avi video file.

I've already tried

sudo apt-get install vlc-plugin-*

but so far nothing has worked. can anyone think of a fix for this sittuation?

---

### Post by mahiyar on 2008-09-16
Did you try any other player like m-player etc or is this problem typical of VLC

---

### Post by Delslayer on 2008-09-16
I orginally tried using M-player but that gives me no audio and the video plays frame by frame very slowly

---

### Post by mahiyar on 2008-09-16
can you play audio at all on your computer mp3, music files etc.

---

### Post by markbuntu on 2008-09-16
In VLC/Settings/Preferences/Audio/Output Modules you need to select Pulseaudio audio output or Alsa audio output.

---

