---
title: "Toshiba Equium (Satellite?) A100-027 hd audio totally disappears after 2nd reboot"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by darrelljon on 2008-06-26
I have a Toshiba Equium (Satellite) A100-027 with Intel HD Audio. Kubuntu 8.04 detects this and plays sound fine when I run it off the live CD and on the first boot after installation. However, after the second reboot it seems to fail to detect it properly as I cannot hear any sound. I've reinstalled it and the problem manifests itself in the same way. Do I need to add options to

/etc/modprobe.d/alsa-base
?
I tried adding the line

options snd-hda-intel model=auto

but it didn't seem to have an effect as there was still no audio.
The volume is turned up and there are no error messages when playing audio in AmaroK.

---

### Post by lisati on 2008-06-26
Don't know if this will help: I had sound troubles on my A100 after a fresh  install of Ubuntu 7.04, and found that installing all the system updates cured the problem.

---

### Post by darrelljon on 2008-06-26
Is there a particular package that needs updating?

---

