---
title: "System Question..."
date: 2008-05-31
forum: New to Ubuntu
---

### Post by redfox1160 on 2008-05-31
I'm sorry if this is really simple to find out, but I can't seem to find it. I was wondering where I would go to find out system information (HDD space, RAM, etc.). Any help is appreciated. Also, is this where I would go to find out what kind of video card, sound card, etc. that I have? Thanks.

---

### Post by Maestro23 on 2008-05-31
In Gnome:

System>>Admin>>System Monitor

Will give processor, RAM, HDD space, etc...

---

### Post by shifty_powers on 2008-05-31
```
sudo dmidecode
```

and

```
lspci
```

thought the first one will give you LOTs fo info ;)

---

### Post by avtolle on 2008-05-31
You might also consider installing sysinfo through Synaptic (or Add/Remove, if you wish). It will give you most of the information you are seeking in a graphical form. Once installed, it may be accessed through Applications>>System Tools. HTH.

---

### Post by logos34 on 2008-05-31
> **shifty_powers said:**
> ```
sudo dmidecode
```

I've been looking for that command for ages!  The Bios info alone is priceless.  Came across it long time ago in some thread and then I lost it.

Thanks.

---

### Post by shifty_powers on 2008-05-31
heh, no problem. and yes, it can be handy ;)

---

