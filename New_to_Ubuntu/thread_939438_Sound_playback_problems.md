---
title: "Sound playback problems"
date: 2008-10-05
forum: New to Ubuntu
---

### Post by mitchlourens on 2008-10-05
I have a Microsoft Lifechat LX3000 headset that I use for my sound playback.  Sound works perfectly fine for everything other than firefox sounds, as in youtube videos etc.  Does anyone know why? How can I fix that.  If I watch a movie in Totem, or send an IM with pidgin, it works fine.

It did this both in 8.04 and in the new 8.10-beta releases.

---

### Post by vikramaditya on 2008-10-05
see if dis post do be da mack daddy...

[http://ubuntuforums.org/archive/index.php/t-462907.html](http://ubuntuforums.org/archive/index.php/t-462907.html)

:)

---

### Post by minky311 on 2008-10-06
System->Administration->Synaptic package manager
Do a search for default sound card.
Install asoundconf-gtk.
Then you can set your headset as the default soundcard by going to System->preferences->Default Sound card.

---

### Post by kansasnoob on 2008-10-06
This tutorial solved my pulse audio problems in Hardy:

[http://ubuntuforums.org/showpost.php?p=5587712&postcount=472](http://ubuntuforums.org/showpost.php?p=5587712&postcount=472)

Note: it's only for Hardy!

---

### Post by kansasnoob on 2008-10-06
For Intrepid:

[http://ubuntuforums.org/showthread.php?t=866965](http://ubuntuforums.org/showthread.php?t=866965)

---

