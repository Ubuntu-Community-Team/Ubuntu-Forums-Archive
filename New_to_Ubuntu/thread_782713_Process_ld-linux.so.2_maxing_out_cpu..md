---
title: "Process ld-linux.so.2 maxing out cpu."
date: 2008-05-05
forum: New to Ubuntu
---

### Post by philinux on 2008-05-05
Anybody else had this. What is this process it was really bashing the cpu's. Logged out then in and it went away. Maybe it was the updates?

---

### Post by billgoldberg on 2008-05-05
I don't know what ld-linux.so.2 does but this guy has some problems with it combined with acroread

[http://citadel.tistory.com/158](http://citadel.tistory.com/158)

But according to google people have problems with it combined with other programs.

---

### Post by philinux on 2008-05-05
Ok, I'd just fired up the pc. No desktop effects. Ran google-earth then quit that. Ran firefox and one page had a pdf. I was then browsing when I noticed my cpu monitor was going crazy.

Since I logged out and in it's been behaving.

---

### Post by obnibolongo on 2008-05-15
I think ld-linux.so.2 appears on my computer after a failed OR a supposedly failed hibernation (supposedly failed means: Gnome tells me it failed to hibernate but it did hibernate).

It uses all CPU available.

```
killall ld-linux.so.2
```
works like a charm, though it ought to be a better solution than an "ugly" killall...

---

