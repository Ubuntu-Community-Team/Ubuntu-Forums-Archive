---
title: "rythmbox &amp; totem dont work.. why?"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by lunaluna on 2008-05-16
any info you'll need for fixing this just ask.. :)

---

### Post by wolfen69 on 2008-05-16
do they start up? do they start up then crash? cant play certain video formats?

---

### Post by Canis familiaris on 2008-05-16
What exactly is the problem?

---

### Post by NightwishFan on 2008-05-16
](*,)

If you need codec support run this command in terminal:
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by lunaluna on 2008-05-16
they do start up but no playback
run them through terminal:
rhyth..:

> (rhythmbox:9657): Rhythmbox-WARNING **: Could not open device /dev/radio0

totem:
> 
** Message: Error: Resource not found.
gstfilesrc.c(977): gst_file_src_start (): /play/source:
No such file "/home/ginseng-ginger/%U"


sometimes they play sometimes they just don't...
i don't have anything extra installed also

---

### Post by lunaluna on 2008-05-16
> **NightwishFan said:**
> ](*,)

If you need codec support run this command in terminal:
```
sudo apt-get install ubuntu-restricted-extras
```

already have them

---

### Post by NightwishFan on 2008-05-16
Odd. Is this a fresh install?

It may be a plugin issue so try disabling them in rhythmbox.

---

### Post by lunaluna on 2008-05-16
not really...3 weeks counting until today

---

### Post by lunaluna on 2008-05-16
> **NightwishFan said:**
> Odd. Is this a fresh install?

It may be a plugin issue so try disabling them in rhythmbox.

i dont think so..
because i reinstalled just in case this fix the problem...

---

### Post by lunaluna on 2008-05-16
bump

---

