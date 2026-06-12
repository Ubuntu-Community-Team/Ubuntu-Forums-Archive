---
title: "6800Gt Nvidia Driver problem"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by Damned666 on 2008-05-13
Hi guy,

i managed to install the NVIDIA Driver from NVIDIA.COM and having my machine not freezing on me. I now have the problem that i can't login at all in ubuntu. The login screen stays black. I can do CTRL-ALT-F1, it works fine but no gui. Envyng didn't work for me neither do the restricted Driver.

Please help, i'm a bit desperate right now.

---

### Post by KingWilliam on 2008-05-14
you could try to reconfigure your xorg.conf file.
```
 sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by hermes0710 on 2008-05-14
Can you post the log file? ```
/var/log/Xorg.0.log
```

---

### Post by Damned666 on 2008-05-14
how can i post my Xorg.0.log ? I don't have access to my gui ...

---

### Post by Damned666 on 2008-05-14
i tried sudo dpkg-reconfigure -phigh xserver-xorg and it doesn't work. Instead of having the nvidia settings in the Xorg.Conf it come back to a configured video device

---

### Post by HypNemes on 2008-05-14
this might be totaly noobish..

but have you tried using cmd "startx" ?

---

### Post by Damned666 on 2008-05-14
yes ... and i got a black screen instead of any gui. I gonna try to reinstall an older driver now ...

---

### Post by Damned666 on 2008-05-14
I managed to boot in the gui using 96.xx.xx driver from nvidia but i only have 800*600 & 640*480 in the screen resolution screen.

---

### Post by Damned666 on 2008-05-15
Anyone got something ? it's really annoying, it's been a week of trial and error on this one.

---

