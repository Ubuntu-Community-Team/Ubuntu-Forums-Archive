---
title: "What to backup for full system restore???"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by roccivic on 2008-06-26
I'd like to make daily backup on my office computer, just in case I get a big problem with Ubuntu (and, of course, I'd like the backup file to be as small as possible).
So that I can just format the HDD, install Ubuntu, install all applications that used to be on the PC, unroll the backup and have everything just as it was.

Does this even sound reasonable? If it does:

/boot
/home
/etc
/usr

What else?

Rouslan

---

### Post by gn2 on 2008-06-26
Have you considered using [**Partimage**]("http://www.partimage.org/Screenshots")?
It's in the repositories and can be installed via Synaptic, Add/Remove or ```
sudo apt-get install partimage partimage-doc partimage-server
```

---

