---
title: "Trying to install new ATI Radeon driver (fglrx updates)"
date: 2011-10-01
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by jcphil on 2011-10-01
I can install fglrx amdcccde, but when I go to activate the new driver in Jockey it fails. The log shows this:

```

2011-10-01 12:06:37,703 DEBUG: fglrx_updates is not the alternative in use
2011-10-01 12:06:37,755 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-01 12:06:37,755 DEBUG: fglrx_updates is not the alternative in use
2011-10-01 12:06:37,910 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-01 12:06:37,911 DEBUG: fglrx_updates is not the alternative in use
2011-10-01 12:06:37,963 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-01 12:06:37,963 DEBUG: fglrx_updates is not the alternative in use
2011-10-01 12:06:38,064 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-01 12:06:38,064 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking

```

---

### Post by dino99 on 2011-10-01
purge ALL the video drivers installed and jockey* too, then reinstall

---

### Post by jcphil on 2011-10-01
Maybe I'm not understanding. Do you mean to purge the X driver as well? And what do you mean by "purge"? I tried "remove" and "remove completely" but neither had any effect on the problem. The logs show the same failure.

---

### Post by MAFoElffen on 2011-10-01
> **jcphil said:**
> Maybe I'm not understanding. Do you mean to purge the X driver as well? And what do you mean by "purge"? I tried "remove" and "remove completely" but neither had any effect on the problem. The logs show the same failure.
I believe he meant to uninstall and purge all of the ati drivers... You can also do from the commandline if you did an ATI install instead of Ubuntu packaged propietary...

---

### Post by effenberg0x0 on 2011-10-01
Hey,

Purge means using sudo apt-get remove --purge <package_name>. Not only the packages will be uninstalled, but they will be completely removed from your system. 

Jockey is broken, and not installing drivers correctly all the time now. You are better of installing the drivers without it.

So, what is being recommended to you here is that you purge nvidia*, fglrx* and then reinstall fglrx (sudo apt-get install fglrx). 

[B]Pay attention when you use this commands. APT will inform exactly which packages it will remove. If, by any change, is suggests you that it will remove many other packages, you have to answer no, unless you really know what you're doing.
[/B]
Have a look here for more detailed info:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Regards,
Effenberg

---

