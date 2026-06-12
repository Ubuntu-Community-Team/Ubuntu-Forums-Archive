---
title: "mp4 encoder for zune"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by fate_ on 2008-10-26
So I found and avi to mp4 encoder for the zune but the zune software said the the mp4 file was invalid. any idea what I did wrong?

I used this encoder

mencoder original.avi -o new.mp4 -oac copy -ovc lavc -lavcopts vcodec=mpeg1video -of mpeg

---

### Post by SunnyRabbiera on 2008-10-26
Just remember the Zune is a MS product, so its not going to like linux stuff :D

---

### Post by Xiong Chiamiov on 2008-10-26
I don't know anything about mencoder, but mp4 is short for mpeg4, while you're encoding it into mpeg1.  It doesn't matter what the file extension is; it's the codec that your Zune doesn't like.

---

### Post by fate_ on 2008-10-26
oh ok, do either of you know of good encoder to zune acceptable codecs I could use? Im pretty new to linux as well. Also I have another question that probably should need another thread but whats the command to show basic inforation about your computer?

---

### Post by fate_ on 2008-10-26
bump

---

### Post by rotwang888 on 2008-10-27
open system> administration> system monitor

---

