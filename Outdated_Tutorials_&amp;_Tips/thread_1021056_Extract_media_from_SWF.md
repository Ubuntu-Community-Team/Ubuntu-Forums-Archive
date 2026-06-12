---
title: "Extract media from SWF"
date: 2008-12-24
forum: Outdated Tutorials &amp; Tips
---

### Post by evilkastel on 2008-12-24
My college has a ridiculous course with online interection, the trouble is, the "multimedia content" comes in .exe packages, that are, flash packages. So, since i just need the audio and not the crappy interface, i decided to find out a way to do this on ubuntu. 

Before everything, this files or the swf attached to them WON'T play in firefox, or vlc. Also, i do not use wine in my box.

is not that hard, just run

```
sudo apt-get install swftools
```

this will install the swftools suite. There are a few tools included, they are listed in the package description. Anyway,Then run:
```
swfextract ~/Annoyingfile.swf
```
The output will tell you if any content was detected.
By running
```
swfextract
```
you can find out how to extract Images, and a few other things. Since i care for the audio, i run
```
swfextract -m /Annoyingfile.swf
```
By default the output is on /home/user and has a generic name, but you can change it.

Ok, another thing i do not need windows for.
Cheers

---

### Post by SeanHodges on 2008-12-29
Very cool, thanks for the tip.

---

### Post by bimaljr on 2008-12-29
Thanks..

---

