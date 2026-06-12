---
title: "Segmented DVD Playback"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by Replicasex on 2008-10-24
Hello, I just recently configured my system (8.04 Hardy Heron) to use VLC to play DVD upon disc insertion (changed the x-content=totem.desktop to vlc) and now dvd playback comes in short segments, usually around 12 minutes apiece.  This really isn't an issue, as it doesn't affect my watching the videos, but I was wondering if there was anyway I could get VLC to play the entire part of the video, so I could track it all easily.  

Thanks in advance.

---

### Post by Crandom on 2008-10-24
If you look in nautilus at the contents of the DVD in the VIDEO_TS folder, you will probably find that it is divided into many .VOB files, one for each chapter. VLC does not use the menus or DVD structure that link these .VOB chapters together, it merely plays each of them sequentially. To get the entire DVD to play in one go, use a player that supports DVD menus like gxine, which you can install using synaptic or the command:
```
sudo apt-get install gxine
```

---

### Post by Replicasex on 2008-10-24
That's very odd considering VLC *did* support menus with my DVDs and never gave me this strange segmentation before.  But I will take your advice and see if gxine works.

---

### Post by Replicasex on 2008-10-24
Well it does have menu support and it doesn't read one .vob file at a time - that's great.  But do you know if gxine can play as many formats as VLC?  That's one of the main reasons I used it in the first place.

Also, if I wanted it to be the program that opens up upon disc insertion would I just change the x-content/video=vlc.desktop to gxine.desktop?  Thanks.

---

### Post by Crandom on 2008-10-24
gxine supports as many filetypes as you have xine codecs. A just change it to gxine.desktop if you have a shortcut to gxine on your desktop (i think).

---

### Post by northern lights on 2008-10-24
Do you have the medibuntu repository enabled and have you installed *libdvdread3*?

If not, see [https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats") for references.

---

### Post by mc4man on 2008-10-24
Check the default launch command of vlc - in hardy it is  vlc %U which is unsuitable for autoplaying dvds.

Right click on Applications -> edit menus. Highlight sound and video and on the right side, right click on vlc -> properties. If the command shows vlc %U then change to vlc %f.

---

