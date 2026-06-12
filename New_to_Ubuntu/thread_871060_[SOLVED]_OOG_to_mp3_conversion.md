---
title: "[SOLVED] OOG to mp3 conversion?"
date: 2008-07-26
forum: New to Ubuntu
---

### Post by djvasco on 2008-07-26
I'm having trouble with importing music into my iPod from my CDs.  I've used **Audio CD extractor** to rip my CDs into oog files.  I've tried to use **Sound Converter** to convert the files into mp3s.  I get an error message saying source files cannot be converted.  I've tried to create copies of the files but I'm having trouble with that also.:confused:  Any suggestions?

---

### Post by SuperSonic4 on 2008-07-26
I think soundKonveter can but it is kde and may have dependencies which would take up a lot of room. Have you got the mp3 codec installed? 

I like using sound juicer to rip audio CD's (I installed it onto KDE mint)

```
sudo apt-get install sound-juicer
``` It could be a problem with the ripping though?

---

### Post by djvasco on 2008-07-26
Found the problem; I didn't have all the necessary plug-ins installed.  I just finished converting my files w/ Soundconverter.

---

### Post by gjoellee on 2008-07-26
> sudo aptitude install soundconverter
and then 
> apt-get install gstreamer0.10-plugins-ugly-multiverse 
i think that should be it...

---

