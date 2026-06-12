---
title: "Remove packages from Linux Mint to make it Light?"
date: 2007-11-26
forum: Other OS Talk
---

### Post by maybeway36 on 2007-11-26
I have a CD of Linux Mint Full Edition. I was wondering, is it possible to install this and then remove packages with APT to make it into Linux Mint Light Edition? Or is there a Linux Mint metapackage in their repos?

---

### Post by jken146 on 2007-11-26
I don't know anything about Mint, but you can just uninstall any packages you don't want using ```
sudo aptitude remove <package>
```

edit: Sorry, I re-read your post and I guess this isn't what you're looking for.

---

### Post by mellowd on 2007-11-26
You could, but I know the fluxbuntu mint will be coming out soon

---

### Post by dpar on 2007-11-26
Probably in the amount of time it would take you to uninstall everthing, you could just download the Light Edition.:)

---

### Post by new2*buntu on 2007-11-26
> **maybeway36 said:**
> I have a CD of Linux Mint Full Edition. I was wondering, is it possible to install this and then remove packages with APT to make it into Linux Mint Light Edition? Or is there a Linux Mint metapackage in their repos?

Do you want it to be lighter on resources or just not have the proprietary codecs and drivers which are illegal in some countries? I could not understand this from your question.
Anyway, I think that their "light" version is just there "main" version except without the proprietary codecs and drivers. So it isn't really lighter on system resources.

---

### Post by dpar on 2007-11-26
> **new2*buntu said:**
> Do you want it to be lighter on resources or just not have the proprietary codecs and drivers which are illegal in some countries? I could not understand this from your question.
Anyway, I think that their "light" version is just there "main" version except without the proprietary codecs and drivers. So it isn't really lighter on system resources.

That's right.

---

### Post by maybeway36 on 2007-11-27
I'm aware of that; however, I prefer not to have propietary codecs on my system.

---

### Post by igknighted on 2007-11-27
> **maybeway36 said:**
> I'm aware of that; however, I prefer not to have propietary codecs on my system.

w32-codecs, libdvdcss, gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly

I think those 4 are the main ones... although the xine back-end that Amarok uses has support for these codecs built in IIRC, so you might have some issues trying to get rid of that (if you want to keep amarok).  Then again, you could merely install kubuntu's amarok instead, which doesn't have the non-free codecs built in.

---

### Post by new2*buntu on 2007-11-27
I think that it would be easier to just download the "Light" edition, instead of going through the process of removing all of the licensed codecs.

---

### Post by maybeway36 on 2007-11-27
Yeah, I'll probably just remove those codecs since I don't want to go burn another CD. I have the ISO on my computer, though.

---

