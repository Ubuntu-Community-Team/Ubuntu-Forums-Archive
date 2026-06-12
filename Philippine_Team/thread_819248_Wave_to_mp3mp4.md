---
title: "Wave to mp3/mp4"
date: 2008-06-05
forum: Philippine Team
---

### Post by mobster on 2008-06-05
Meron po bang pang convert ng wave file to mp4/mp4 voice lang po kc ito tapos ang laki pag wave eh. salamt po

---

### Post by loell on 2008-06-05
try mo yung [Audacity sound editor]("apt:audacity")

or 

kundi naman , [ffmpeg]("apt:ffmpeg")

then sa command line 

**ffmpeg -ab 128 -ac 2 voice.wav voice.mp3**

---

### Post by gbutalid on 2008-06-05
Try mo Sound Converter. Click on Edit>Preferences to set your output to mp3.

---

### Post by kstella on 2008-06-05
If you want a web-based converter, upload the file to zamzar.com. You'll get a link to your converted file in your e-mail.

Zamzar doesn't just convert sound files, but also documents, archives, images, and videos.

---

### Post by Samhain13 on 2008-06-06
ffmpeg din ang gamit ko. 
ffmpeg2theora kung video (.avi, o .mpeg to .ogg)

mencoder din magandang command line tool para sa transcoding.

Kung images, andiyan ang Phatch sa repositories.
Puwede din ImageMagick, kung command line tool and gusto.

:D

---

