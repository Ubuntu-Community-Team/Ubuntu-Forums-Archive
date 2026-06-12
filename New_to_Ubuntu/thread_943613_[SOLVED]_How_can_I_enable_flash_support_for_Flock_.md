---
title: "[SOLVED] How can I enable flash support for Flock browser."
date: 2008-10-10
forum: New to Ubuntu
---

### Post by crjackson on 2008-10-10
I have flashplugin-nonfree installed from the restricted-extras in synaptic. Flash works just fine in Firefox 3.0.3.

What do I have to do for it to work in Flock 2.0b3 ?

---

### Post by gandaran on 2008-10-10
easy, get the flash plugin **libflashplayer.so** file and chuck it in the flocks plugins folder, either in /usr/lib/flock/plugins or the hidden home flock/plugins folder
to get the libflashplayer.so file copy the one installed in /usr/lib/flashplugin-nonfree or download from adobe site the flash tar.gz package and unpack the package

---

### Post by crjackson on 2008-10-10
> **gandaran said:**
> easy, get the flash plugin **libflashplayer.so** file and chuck it in the flocks plugins folder, either in /usr/lib/flock/plugins or the hidden home flock/plugins folder
to get the libflashplayer.so file copy the one installed in /usr/lib/flashplugin-nonfree or download from adobe site the flash tar.gz package and unpack the package

That makes perfect sense and I looked for something like that. However neither of those folders exist on my system.  I'll create them and see what happens.

---

### Post by crjackson on 2008-10-10
Okay, I tried both.  /user/lib/folck/plugins didn't work /home/flock/plugins did.

Neither of these folders were created by the install btw.

---

