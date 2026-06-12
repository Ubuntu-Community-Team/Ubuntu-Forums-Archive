---
title: "Iriver u10 video encoding on linux"
date: 2007-10-29
forum: Outdated Tutorials &amp; Tips
---

### Post by theonhighgod on 2007-10-29
Just incase someone has a u10 and wants to know how to encode video in linux then heres a little script, to find out how to use it run "u10ner.sh --help"


the critical line i found on a forum, but i cant find it again so if you need it its:

```
/usr/bin/mencoder "outputfile.avi" -o "inputfile.avi" -ovc xvid -xvidencopts bitrate=384:max_bframes=0 -oac mp3lame -lameopts mode=0:cbr:br=128  -ofps 14.9 -af resample=44100:1:2 -vf-add scale=320:240,expand=320:240 -vf-add harddup -quiet 
```

seems to work flawlessly!

---

### Post by andrew.46 on 2007-10-29
Hi,

 Hmmm.... I have seen the same syntax here and there on the internet. Would be improved by double pass encoding?

      Andrew

---

### Post by theonhighgod on 2007-10-30
the u10 has a very nice screen for an mp3 player but its still an mp3 player, i think quicker encoding is probably more useful then two passes? 

the biggest problem is as the iriver doesn't support B frames it gets out of sink a lil, after 20 if mins, but pausing and skipping around a lil sorts that,

---

