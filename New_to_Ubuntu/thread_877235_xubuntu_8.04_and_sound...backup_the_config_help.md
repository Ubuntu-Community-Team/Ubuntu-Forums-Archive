---
title: "xubuntu 8.04 and sound...backup the config help"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by pcrussell50 on 2008-08-01
sound on my mother's pc always worked fine in xubuntu 7.10 and older versions.  when i upgraded to 8.04, which i always do with a clean install, i got no sound, nor could i get a screen resolution above 800 x600.

then i had a wacky idea...i reinstalled 7.10 to get my sound and screen res back, and then i used the "upgrade to 8.04" button in synaptic, instead of a fresh format and install.  lo and behold, i have sound and graphics!  sweet. so, in order to save my graphics for future installs, i made a copy of the known-good /etc/X11/xorg.conf file.

BUT, what configuration file to i need to save in order to keep my sound configuration available for future upgrades?  is it the same xorg.conf, by chance?  this is why i'm asking in the ABT forum :)

-Peter

---

### Post by K2712 on 2008-08-01
Using alsa?

/etc/alsa/alsa.conf

and I believe OSS is here:

/usr/lib/oss/conf

but I'm not 100% sure.

---

### Post by pcrussell50 on 2008-08-01
> **K2712 said:**
> Using alsa?

/etc/alsa/alsa.conf

and I believe OSS is here:

/usr/lib/oss/conf

but I'm not 100% sure.

thanks for the effort.  however neither of those files exist in my versions of either xubu8.04 or ubu8.04

what is oss, btw?

---

### Post by K2712 on 2008-08-01
Hmmm, sorry about that, I'm not in front of my Ubuntu machine at the moment.  Maybe /etc/asound.conf?

And OSS is an alternative to alsa.

[http://www.opensound.com/oss.html](http://www.opensound.com/oss.html)

---

### Post by caljohnsmith on 2008-08-01
Here are some ALSA config files you could backup:
```
/usr/share/alsa/alsa.conf
/etc/modprobe.d/alsa-base
~/.asoundrc   <--only if you at one point created it to use special options
```

---

