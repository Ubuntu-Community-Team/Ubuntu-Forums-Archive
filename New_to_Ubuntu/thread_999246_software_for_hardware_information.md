---
title: "software for hardware information"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by damian15 on 2008-12-01
I just installed ubuntu for the first time and i needed to know if there is a way to get the information of my motherboard using a linux or online app. I should also say that I have never use linux before and I have no idea what im doing :). Everything I have found online so far is for windows which makes it really hard. Any help is really appreciated.

---

### Post by lettermachine on 2008-12-01
System>Adminstration>Device Manager

For very detailed info:
```
sudo lshw
```

---

### Post by damian15 on 2008-12-01
> **lettermachine said:**
> Run this:

```
sudo dmidecode
```


where do I run this? Thanks

---

### Post by hyper_ch on 2008-12-01
```

sudo lshw -html > ~/Desktop/hardware.html

```

that will create a html file that you can open in your browser.

---

### Post by kostkon on 2008-12-01
Install the *lshw-gtk* package. It will give you a nice GUI for *lshw*.

---

