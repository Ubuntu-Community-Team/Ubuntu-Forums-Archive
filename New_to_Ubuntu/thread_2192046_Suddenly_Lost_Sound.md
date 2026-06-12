---
title: "Suddenly Lost Sound"
date: 2013-12-05
forum: New to Ubuntu
---

### Post by playing_with_matches on 2013-12-05
Didn't run any updates at the time, but I was running Rhythmbox and lost my sound all of a sudden.  Now anytime I boot up Ubuntu, I don't have any sound at all.  Volume Control is up, and it's not on mute.  Windows boots fine with sound so it's not my speakers.  Any ideas?!  I'm really at a loss.

---

### Post by ibjsb4 on 2013-12-06
Thats weird .. Try

```
sudo apt-get -f install
```

See if any packages are broke.

---

### Post by tl.bk on 2013-12-17
Hi,

I'm having exactly the same problem. I've spent the whole morning on the internet to look for solutions but there isn't any. I've tried reinstalling alsa-base, pulseaudio and so on but that didn't work. I don't think there is any problem with my sound driver. I think the sound might be muted somewhere but I've unmuted all those in sound settings, alsamixer and /etc/libao.conf.

I'm using Ubuntu 13.10. The problem starts few days ago but I was able to solve it by rebooting the PC. But now rebooting doesn't work.

I really hope someone can help. Thank you.

EDIT: None of the packages are broken though.

---

