---
title: "xmms2 and repository?"
date: 2006-05-07
forum: Repositories &amp; Backports
---

### Post by TitusDalwards on 2006-05-07
i wanna download xmms2 and i tried```
sudo aptitude install xmms2
``` and it returns me with an error > couldn't find package i don't want to install it from its binary(because of the depencies problem) so do you know any repo  for it?

---

### Post by arnieboy on 2006-05-07
The following instructions are for breezy.

```
sudo gedit /etc/apt/sources.list
```
add the following line at the end:
> deb [http://exodus.xmms.se/debian](http://exodus.xmms.se/debian) stable main
save and exit
```
sudo apt-get update
sudo apt-get install xmms2 xmms2-decoder-mad xmms2-decoder-vorbis
```

---

### Post by TitusDalwards on 2006-05-07
thank you so much, for your help i'll try it quickly

---

