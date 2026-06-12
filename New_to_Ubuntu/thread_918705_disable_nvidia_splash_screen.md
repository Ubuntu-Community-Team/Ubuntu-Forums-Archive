---
title: "disable nvidia splash screen"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by fallen seraph on 2008-09-13
I use nvidia proprietry drivers. I've always had "NoSplash" = "True" in my xorg.conf file. Recently I've had to install nvidia-settings in order to fix my refresh rate, and now I've got an nvidia splash screen that happens after the ubuntu one. I rather dislike this :| does anyone know of a way to get rid of it?

---

### Post by Sef on 2008-09-13
moved to absolute beginners.

---

### Post by StOoZ on 2008-09-13
a stupid commercial for nvidia , I would like to remove that too.

---

### Post by alancanniff on 2009-06-22
This worked on Jaunty for me - 
[http://www.funnestra.org/ubuntu/gutsy/]("http://www.funnestra.org/ubuntu/gutsy/")

---

### Post by kpkeerthi on 2009-06-22
You need to add "NoLogo" under "Device" section in xorg.conf.

---

### Post by somewhere2go on 2009-06-22
Try:

```
sudo gedit /etc/X11/xorg.conf

Section "Device"
     Option "NoLogo" "True"

```

---

### Post by m2xtreme on 2010-02-21
Thank you somewhere2go, it worked perfectly for me :)    I use a dual monitor set up so I added the

Section "Device"
     Option "NoLogo" "True"

under both the Section "Device" headers in the xorg.conf file.  I'm not sure if it was necessary to do both but it works now so I'm not gonna try it any other way

---

