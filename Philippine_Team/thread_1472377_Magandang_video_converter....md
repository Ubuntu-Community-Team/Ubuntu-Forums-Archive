---
title: "Magandang video converter..."
date: 2010-05-04
forum: Philippine Team
---

### Post by zilu54 on 2010-05-04
Hi gusto ko sanang humingi ng tulong sa inyo tungkol sa pag convert ng video para sa isang tutorial sa aming forum.

Nag record kasi ako gamit ang 'recordmydesktop' at nag save ito sa .ogv format, then pagkatapos kong mag upload sa youtube, napansin ko na medyo fuzzy yung video pero yung audio naman ay malinaw kaya naisipan ko na lang i-convert ito sa .avi or .flv baka sakaling maganda ang pag kalalabasan nito, walang problema naman sa pag uuload lalo na sa internet connection.

Nasubukan ko na ang 'winff' kaso hindi rin maganda ang kinalabasan nito. Sana matulungan nyo ako...maraming salamat.

Umaasa akong may sasagot sa aking katanungan. :)

---

### Post by Script Warlock on 2010-05-04
> **zilu54 said:**
> Hi gusto ko sanang humingi ng tulong sa inyo tungkol sa pag convert ng video para sa isang tutorial sa aming forum.

Nag record kasi ako gamit ang 'recordmydesktop' at nag save ito sa .ogv format, then pagkatapos kong mag upload sa youtube, napansin ko na medyo fuzzy yung video pero yung audio naman ay malinaw kaya naisipan ko na lang i-convert ito sa .avi or .flv baka sakaling maganda ang pag kalalabasan nito, walang problema naman sa pag uuload lalo na sa internet connection.

Nasubukan ko na ang 'winff' kaso hindi rin maganda ang kinalabasan nito. Sana matulungan nyo ako...maraming salamat.

Umaasa akong may sasagot sa aking katanungan. :)

miksoft, winff, devede, handbrake

---

### Post by zilu54 on 2010-05-05
Maraming salamat Script Warlock, gumana ng maayos yung DeVeDe at naiconvert ko na siya sa .amv

maraming salamat ulit :)

---

### Post by kidsodateless on 2010-06-03
ano magandangvideo converter for ogv to flv?

---

### Post by zilu54 on 2010-06-03
> **kidsodateless said:**
> ano magandangvideo converter for ogv to flv?

Try 'transmageddon' matagal ku na rin siya ginagamit pang convert sa mga screencasts ku.

---

### Post by guitar_man on 2010-06-03
+1 sa winff....simple pero useful.

---

### Post by Samhain13 on 2010-06-03
Subukan mo din kalikutin yung settings ng RecordMyDesktop. If you're using the GTK GUI, you'll find additional settings by clicking the "Advanced" button below Video/Audio Quality.

Sa akin, laging nakacheck ang "Full shots at every frame" at "Zero Compression". If you want finer video, gawin mong 30 yung Frames Per Second.

Kung talagang pangit pa din, I recommend FFMpeg. It's available in the repos. It's simple to use and it's faster than the GUI-based "transcoders".

Converting your out.ogv (from RecordMyDesktop) to AVI is as simple as:
```
ffmpeg -i out.ogv -b 1024kb your_desired_filename.avi
```

Ang importante diyan ay yung "-b 1024kb" option at yan yung bitrate nung video. Usually, tama na sa akin ang 1024kb pero puwede mong subukan gawin 2048kb para lang tumaas yung threshold.

Kung .ogv to .flv naman, palitan mo lang yung extension ng "your_desired_filename". .3gp to .avi, .flv to .avi, .mp4 to .flv, etc. same thing. LOL. Gusto mo, puwede ka din mag-extract ng audio track mula sa isang video file.

:)

---

### Post by kidsodateless on 2010-06-04
@all thanks, okey na.. I used devede to convert ogv to avi.. hd kinalaban.. :D

---

### Post by ysNoi on 2010-06-05
> **guitar_man said:**
> +1 sa winff....simple pero useful.

+2 here...Nice..

---

### Post by nerdtron on 2010-06-05
Ang VLC pwde rin mgconvert ng audio and video files. Eto ang link [http://maketecheasier.com/5-things-you-didnt-know-vlc-could-do/2010/05/06?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+MakeTechEasier+%28Make+Tech+Easier%29&utm_content=Google+Reader](http://maketecheasier.com/5-things-you-didnt-know-vlc-could-do/2010/05/06?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+MakeTechEasier+%28Make+Tech+Easier%29&utm_content=Google+Reader)

---

