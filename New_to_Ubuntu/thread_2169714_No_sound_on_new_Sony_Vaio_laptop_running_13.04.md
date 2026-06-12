---
title: "No sound on new Sony Vaio laptop running 13.04"
date: 2013-08-23
forum: New to Ubuntu
---

### Post by tdeleeuw2 on 2013-08-23
I have a new Sony Vaio SVF152C29M laptop. I installed Ubuntu 13.04 but I have no sound.

---

### Post by Quackers on 2013-08-23
Welcome to UF.
Are you sure the sound isn't just muted? It can happen sometimes that the installation mutes sound. I don't know why this is but I have had this too.

---

### Post by Corry_de_Leeuw on 2013-09-01
I just found out that it is working well with earplugs. In the sound settings I see that the output is configured for analog output. On another laptop it is set to loudspeakers.

---

### Post by tdeleeuw2 on 2013-09-01
Solved:

[COLOR=#333333][FONT=UbuntuMono, courier, monospace]sudo apt-add-repository ppa:ubuntu-audio-dev/alsa-daily
[/FONT][/COLOR][COLOR=#333333][FONT=UbuntuMono, courier, monospace]sudo apt-get update[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuMono, courier, monospace]sudo apt-get install oem-audio-hda-daily-dkms


[/FONT][/COLOR]

---

