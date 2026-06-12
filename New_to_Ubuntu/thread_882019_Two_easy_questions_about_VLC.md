---
title: "Two easy questions about VLC"
date: 2008-08-06
forum: New to Ubuntu
---

### Post by diablo75 on 2008-08-06
1.  Every time I start VLC, the volume control (inside VLC) is maxed out at 100%.  This causes distortion for me, and I have to take it down to about 50% for things to sound okay.  Is there a way for me to change the default volume level when VLC is first started.

2.  I'm not sure if this has been a problem before, but when I double click on an MP3, it will play.... but when I go for another one, instead of changing the song, it opens a second instance of VLC.  How do I change this?

Thanks!!

---

### Post by silkstone on 2008-08-06
Settings > Preferences > Default audio volume may help with the first one.

Not sure about the second - sorry.

---

### Post by OffAxis on 2008-08-06
> 2. I'm not sure if this has been a problem before, but when I double click on an MP3, it will play.... but when I go for another one, instead of changing the song, it opens a second instance of VLC. How do I change this?

Settings-->Preferences-->Advanced-->Check in Checkbox for "Allow only one running instance"

(you'll need to have a check already in the "Advanced Options" Checkbox in the bottom right corner so that this option will be displayed)

---

### Post by diablo75 on 2008-08-06
Slam dunk!  Thanks guys.

---

### Post by diablo75 on 2008-08-06
> **OffAxis said:**
> Settings-->Preferences-->Advanced-->Check in Checkbox for "Allow only one running instance"

(you'll need to have a check already in the "Advanced Options" Checkbox in the bottom right corner so that this option will be displayed)

Ehhh, wait a sec.  This looked correct, but there is no "Allow only one running instance" in my Advanced settings menu...

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=80471&stc=1&d=1218050738[/IMG]

---

### Post by WRDN on 2008-08-06
> **diablo75 said:**
> Ehhh, wait a sec.  This looked correct, but there is no "Allow only one running instance" in my Advanced settings menu...


The feature currently is not available for the Linux version of VLC, so unless someone creates the function, there is no solution :(

---

### Post by billgoldberg on 2008-08-06
Just use another audio player than vlc.

Totem doesn't have this problem, so you could use that.

---

### Post by OffAxis on 2008-08-06
Sorry about that, I'm away from my ubuntu box right now :oops:
So much for cross platform compatibility...

According to the developer notes here:
[http://www.videolan.org/developers/vlc/NEWS](http://www.videolan.org/developers/vlc/NEWS)
the latest 'Unix' version under development has this option now (I'm not sure if that includes the Linux version).
 It can be downloaded here:
[http://nightlies.videolan.org/#debian](http://nightlies.videolan.org/#debian)

---

