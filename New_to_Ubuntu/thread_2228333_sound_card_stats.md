---
title: "sound card stats?"
date: 2014-06-06
forum: New to Ubuntu
---

### Post by vinny3 on 2014-06-06
Im running Ubuntu 14.04 LTS.

what is the process for seeing what type of sound card I am using?
[h=2][/h]

---

### Post by tgalati4 on 2014-06-06
Open a terminal:

```
aplay -l
```

---

### Post by DuckHook on 2014-06-07
```
*aplay -l*
```returns rather cryptic results which can be useful for determining numbers and types of channels, but are not the most human-readable. Try:```
sudo lshw -C multimedia
```or```
lspci -vv | grep -iA12 audio
```

---

### Post by Rob Sayer on 2014-06-07
I've found with this sort of stuff it's much quicker to enter "ubuntu display <whatever> adapter" in your search engine.  I usually use startpage HTTPS or duckduckgo ... there's too much ad related noise in Google.  I don't even use Google for searches much in Chrome.

With startpage I get an initial screen of mostly entries from askubuntu or here.  *Very* handy.

Askubuntu is very good because the users are ranked by votes so the answers are vetted.  For novices that's important.  I'm finding there are quite users here who have been using linux for 2 weeks but are nevertheless happily giving bad advice.  It takes a little while for novices to be able to tell the difference.

---

### Post by MartyBuntu on 2014-06-07
...and DuckHook's answer would be the correct one.

---

