---
title: "Flash Videos don't have sound when other applications with sound are playing"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by giordun on 2008-05-17
I can play them if I like exit Firefox, close rhythmbox and then go on Firefox again.

But that's really annoying.

Is there a fix for that?

---

### Post by shadow-of-sin on 2008-05-17
Install libflashsupport:
```
sudo apt-get install libflashsupport
```

---

### Post by Apple Ink on 2008-05-17
Or better still, install VLC from the package manager. 
It automatically brings along aloads of othe format supports as well!

---

### Post by freddybob on 2008-05-17
This bug also occurs in reverse - other applications have no sound after playing Flash in Firefox.

Closing Firefox and then restarting the application fixes it.

---

### Post by philinux on 2008-05-17
Like the previous poster said, check you have libflashsupport installed.

It's a pulse audio problem, bugged at launchpad.

---

### Post by billgoldberg on 2008-05-17
You could install libflashsupport, that will fix that problem.

But it will make the flash player a bit unstable, thus it can crash and take firefox with it.

You could instead of using libflashsupport, go to "system -> preferences -> sound" and change everything to "ALSA", that will also take care of the problem, but flash won't be so unstable.

---

### Post by freddybob on 2008-05-18
libflashsupport does not fix the problem with Zattoo (which uses Flash to stream TV signals)

---

