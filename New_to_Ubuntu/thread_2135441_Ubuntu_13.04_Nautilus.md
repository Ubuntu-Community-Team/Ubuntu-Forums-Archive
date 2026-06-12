---
title: "Ubuntu 13.04 Nautilus"
date: 2013-04-14
forum: New to Ubuntu
---

### Post by 0N3 on 2013-04-14
Nautilus is not showing thumbnails for any files but if I open nautilus as root it is showing thumbnails of files im using Ubuntu 13.04 this did always work.

---

### Post by zrdc28 on 2013-04-14
I am not at home now but if you will search you will find a place to set thumbnails or textview.

---

### Post by VinDSL on 2013-04-14
> **zrdc28 said:**
> I am not at home now but if you will search you will find a place to set thumbnails or textview.
Here ya go...

[ATTACH=CONFIG]241350[/ATTACH]

---

### Post by converted on 2013-04-18
I don't think that's what the OP talking about.  I have the exact same problem, regardless of settings.

I hadn't thought to try opening as root, but did so just now, and sure enough I get thumbnails then...

---

### Post by converted on 2013-04-22
Ok, I got it.

If the OP problem is the same as mine, somehow root owns /home/yourusername/.cache/thumbnails

So you just have to do this:

```
sudo chown -R yourusername:yourusername ~/.cache/thumbnails
```

This will change the ownership of the folder to your user and group.

I didn't need to logout or restart nautilus or anything - as soon as I went back to that directory it was fixed.

---

### Post by jota1971 on 2013-06-20
It works perfectly.

---

