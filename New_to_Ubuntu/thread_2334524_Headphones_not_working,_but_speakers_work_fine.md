---
title: "Headphones not working, but speakers work fine"
date: 2016-08-20
forum: New to Ubuntu
---

### Post by adm6l on 2016-08-20
yesterday everything was great, but today after booting up headphones failed to work.
ubuntu 16.04LTS on asus icore7

alsamixer
[ATTACH=CONFIG]270760[/ATTACH]
 added this to/etc/modprobe.d/alsa-base.conf :
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2
options snd-pcsp index=-2
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=laptop
options snd-hda-intel position_fix=1 enable=yes
..
still not working
more > [http://www.alsa-project.org/db/?f=5704fcac009e8de0bb3db23f7b918185efbd9370](http://www.alsa-project.org/db/?f=5704fcac009e8de0bb3db23f7b918185efbd9370)
..
waiting your support :)

---

