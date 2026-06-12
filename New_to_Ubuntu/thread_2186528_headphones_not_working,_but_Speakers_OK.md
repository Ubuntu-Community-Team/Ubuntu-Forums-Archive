---
title: "headphones not working, but Speakers OK"
date: 2013-11-07
forum: New to Ubuntu
---

### Post by fube00 on 2013-11-07
Hi there,
after connecting headphones I can hear noise in background (not muted!), but sound comes only from speakers.

My audio device is integrated in the mobo (gigabyte h61m-usb3h), and  command:
     cat /proc/asound/card0/codec* | grep Codec
produces:
     Codec: Realtek ALC887-VD
     Codec: Intel CougarPoint HDMI
and no corresponding model is present in file HD-Audio-Models.txt.gz.

alsa infos:
[http://www.alsa-project.org/db/?f=224a44745ba412433fbcde7cc8ded1c32d8c2dd7](http://www.alsa-project.org/db/?f=224a44745ba412433fbcde7cc8ded1c32d8c2dd7)

I hope you guy can support!
thank you very much,
fube00

---

### Post by fantab on 2013-11-07
Open 'System Settings' -> 'Sound' and see if you Headphones are recognized and active.

---

### Post by fube00 on 2013-11-08
thank you for replying... At the second restart the issue was solved by itself!

just for info, headphones were already visible and active in "sound".

Thanks!

fube00

---

