---
title: "Can't enable desktop effects+OpenGl problems"
date: 2008-10-12
forum: New to Ubuntu
---

### Post by klemperal on 2008-10-12
After uninstalling then reinstalling xserver xorg core I am no longer able to activate desktop effects.  Another thing I should mention as it could be related is that when I tried firing up a 3D game it gave me an error saying "Your openGL installation doesn't support direct rendering.  If you have an NVIDIA or ATI card youll probably need to install the proitary driver."  I have an intel card and the driver is set to "intel" in my xorg.conf.  Again, I didn't have these specific problems until after reinstalling xserver xorg core.  Let me know what I should do to fix these problems, thanks.

---

### Post by Pro-reason on 2008-10-13
Perhaps the Compiz-Check script can shed some light on this.

```

sudo wget http://blogage.de/files/4359/download -O /usr/local/bin/compiz-check
sudo chmod +x /usr/local/bin/compiz-check
compiz-check

```

---

