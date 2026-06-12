---
title: "VLC audio lag fixed"
date: 2011-10-04
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by MacUntu on 2011-10-04
If you haven't already noticed: the damn audio lag in VLC has finally been fixed (or at least that's how it is on my two systems).

):P

---

### Post by flipper T on 2011-10-04
really ?

what version ?

or was it that ffmpeg (?) update yesterday ?

---

### Post by mc4man on 2011-10-04
The vlc desync in 1.1X was always related to pulseaudio & was said that it wouldn't/couldn't be fixed from vlc side
Possibly a pulseaudio update has had some positive effect?

Here (for myself,not testing) only use the 1.2 git version which never seemed to be affected (though not sure that it's considered immune, just what I've experienced 
One relevant LP
[https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/805807](https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/805807)

Edit: for those interested & not wishing to build 1.2-git the videolan ppa is in better shape of recent

```
sudo add-apt-repository ppa:videolan/master-daily
```

---

### Post by SpEcIeS on 2011-10-04
The 1.2 git version works really well, but was it not suppose to support unencrypted blu-ray discs? The option does not seem to be available.

---

