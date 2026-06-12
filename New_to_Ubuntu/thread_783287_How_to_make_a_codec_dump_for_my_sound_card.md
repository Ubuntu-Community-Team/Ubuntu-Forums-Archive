---
title: "How to make a codec dump for my sound card?"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by shuRe on 2008-05-05
Hi guys,

I simply wondered if someone could guide me how to make a linux codec dump for my sound card (into a txt file).

Thanks in advance

---

### Post by dvdivx on 2008-05-18
I also would like to know this but apparently no one knows how. This thread is the number one search result but still no answer.

---

### Post by Pfuh_3z on 2008-06-19
in terminal, type (exactly with spaces and all, in one line):

```
cat /proc/asound/card0/codec#1 > ~/Desktop/codec_dump.txt
```

depending on which distro of ubuntu you're running, it is possible
that you'll need to change codec#1 to codec#0 or codec#2,
if you're getting an error saying codec#1 file doesn't exist.

if you don't get any error, it should have worked fine,
and you will find the file codec_dump.txt on your desktop,
if you open it you should see a bunch of info on your soundcard!

hope it works for you

Grtz
Pfuh_3z

---

