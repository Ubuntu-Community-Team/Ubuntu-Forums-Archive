---
title: "Why won't my Cd writer read balnk discs"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by Midgetprawn on 2008-06-28
Once again the temperamental cd writer says it cannot mount the volume when a blank disc is installed....unless the disc is RW. I had been using Imation discs before but it has repeated this with memorex cd-r discs too. Is it me?

---

### Post by bubba_169 on 2008-06-28
What is the exact error message...

---

### Post by Midgetprawn on 2008-06-28
error reads

Mount Error
Unable to mount the selected volume
Mount:special device /dev/scd1 does not exist

---

### Post by |{urse on 2008-06-28
that's because there's no data on it to mount. Umm yeah. Can you burn cd/dvds?

---

### Post by Troll_the_Great on 2008-06-28
It might be the CD... I had allot of problems with Memorex,and I don't use them anymore..

---

### Post by Midgetprawn on 2008-06-28
I can't burn Cd's unless they are RW because the burner (brassero) says there is no disc there and the volume can't be mounted because a blank disc cannot be mounted.

---

### Post by |{urse on 2008-06-28
ah, try k3b. I've not yet met a burner it didn't support. This is a KDE app but works perfectly in Gnome as well.

```
sudo apt-get install k3b
```

---

