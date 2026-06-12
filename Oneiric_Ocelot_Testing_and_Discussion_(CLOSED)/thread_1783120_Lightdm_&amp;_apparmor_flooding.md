---
title: "Lightdm &amp; apparmor flooding"
date: 2011-06-15
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by dino99 on 2011-06-15
got lot of these lines logged:

localhost kernel: [32348.619450] type=1400 audit(1308148732.425:3550): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/firefox-5.0/firefox{,*[^s][^h]}" name="/var/run/lightdm/authority/2" pid=30923 comm="firefox-bin" requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000

seems to be something wrong

---

