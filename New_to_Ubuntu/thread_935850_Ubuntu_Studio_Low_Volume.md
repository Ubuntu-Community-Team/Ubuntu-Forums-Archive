---
title: "Ubuntu Studio Low Volume"
date: 2008-10-02
forum: New to Ubuntu
---

### Post by efeurich on 2008-10-02
Hi there,

I am just using Ubuntu Studio and seem to have a problem that the volume on the system is very low.
I have read some threads on this forum and it seems to be a predominant problem.
Can any one give me some pointers on this?

Thanks in advanced.

Eric

---

### Post by billgoldberg on 2008-10-02
I suggest you switch to ALSA (under system -> preferences -> sound).

Then download gnome-alsamixer

```
sudo apt-get install gnome-alsamixer
```

Open gnome-alsamixer and max everything out.

That will do the trick.

---

### Post by efeurich on 2008-10-02
WOW!! That did the job.
Wonderful world of Linux ...i love it.

Thanks

---

