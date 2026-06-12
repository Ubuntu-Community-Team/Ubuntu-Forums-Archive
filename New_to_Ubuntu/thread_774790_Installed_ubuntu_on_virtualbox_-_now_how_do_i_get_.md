---
title: "Installed ubuntu on virtualbox - now how do i get sound?"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by gottabeandrew on 2008-04-29
Ok, i can access the xorg.conf file and edit it but the file doesn't contain a part for sound so i need somebody to show me what that bit would say so i can add it to my file and then change the driver to "vbox_____" (i dunno what the ____ would be).

I hope this makes sense.

---

### Post by Oldsoldier2003 on 2008-04-29
> **gottabeandrew said:**
> Ok, i can access the xorg.conf file and edit it but the file doesn't contain a part for sound so i need somebody to show me what that bit would say so i can add it to my file and then change the driver to "vbox_____" (i dunno what the ____ would be).

I hope this makes sense.

Open virtualbox and then select your VM and click settings. Select audio then mark enable audio. you should probably use pulse audio.

---

### Post by robalcorn on 2008-04-29
Try loading up virtualbox again ,highlight ubuntu ,click on settings  than under General you will see audio in the left tab from there enable audio and select the driver you need. ie alsa,oss, pulse.One should work for you.

---

