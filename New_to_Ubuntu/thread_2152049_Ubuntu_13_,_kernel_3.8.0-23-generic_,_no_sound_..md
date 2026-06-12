---
title: "Ubuntu 13 , kernel 3.8.0-23-generic , no sound ."
date: 2013-06-06
forum: New to Ubuntu
---

### Post by antoniovandre on 2013-06-06
As every night, before sleep, i do "apt-get update;apt-get upgrade -y;apt-get dist-upgrade -y".

Today, 06/06/2013, i waked and my Ubuntu was no sound.

Can anyone help me?

---

### Post by Frogs Hair on 2013-06-06
Check volume on the panel and in sound settings and provide some information about the computer , sound card if applicable, and driver . I have not had sound problems ,but others have and may be able to help. The type of audio is listed under output in the sound settings.

---

### Post by antoniovandre on 2013-06-06
I found the solution in other forum.

My mothership is Intel. And i add the line "options snd-hda-intel model=generic" in the file "/etc/modprobe.d/alsa-base.conf".

Thanks for attention.

---

