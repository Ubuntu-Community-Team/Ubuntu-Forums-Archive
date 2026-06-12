---
title: "flash player 10 upgrade"
date: 2008-10-15
forum: New to Ubuntu
---

### Post by tjefferson on 2008-10-15
Ubuntu 8.04: I've never been able to use flashplayer, as it makes my cpu usage skyrocket. It's been disabled since the os upgrade. Adobe released version 10 today, so I downloaded the .deb file from their site. Installation was smooth, with no hitches. However, Ff refuses to recognize the new version, insisting that 9 is the only one there. What can I do? This might be my only hope for watching youtube online, rather than downloading every video.

---

### Post by SunnyRabbiera on 2008-10-15
try exiting Firefox, if you had firefox open during installation it wont work right away.
What version of firefox are you using?

---

### Post by Perfect Storm on 2008-10-15
Might try purge the previous version first.

---

### Post by iKonaK on 2008-10-15
open synaptic, search for flash, select completly remove all the flashe's most probably flash-nonfree or something; and then install the deb from adobe, it works much better than the old one.
hope this helps :)

---

### Post by tjefferson on 2008-10-15
Ff 3.0.3 was closed during installation. I'll try purging, but how do I do that? I'm still pretty unexperienced with terminal...

---

### Post by kansasnoob on 2008-10-15
> **tjefferson said:**
> Ff 3.0.3 was closed during installation. I'll try purging, but how do I do that? I'm still pretty unexperienced with terminal...

```
sudo apt-get remove --purge flashplugin-nonfree
```

```
cd ~/.mozilla
rm flashplayer.xpt libflashplayer.so
```

Then reinstall Flash 10.

---

