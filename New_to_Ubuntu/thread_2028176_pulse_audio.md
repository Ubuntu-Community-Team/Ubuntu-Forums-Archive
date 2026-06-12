---
title: "pulse audio"
date: 2012-07-17
forum: New to Ubuntu
---

### Post by degarb on 2012-07-17
Is pulse audio and audacity the best way to get degradation free sound recording through the sound card do hicky device?

---

### Post by cek on 2012-07-17
No.  For that you want to use Jack ([http://jackaudio.org/](http://jackaudio.org/)), and the recording suite of your choice.  Audacity may work for simple tasks.  I use Ardour ([http://ardour.org/](http://ardour.org/)), it's a full-featured digital audio workstation.

Setup can be a bit of a pain, but there are a lot of resources out there (like: [http://wiki.linuxmusicians.com/](http://wiki.linuxmusicians.com/)).

---

### Post by idoitprone on 2012-07-18
If you want low latency recording, then read this wiki

Altough it might be over kill
[https://help.ubuntu.com/community/UbuntuStudio/RealTimeKernel](https://help.ubuntu.com/community/UbuntuStudio/RealTimeKernel)

I heard people also like 
con kolivas bfs scheduler since it focus on low latency
here the ppa

[https://launchpad.net/~chogydan/+archive/ppa](https://launchpad.net/~chogydan/+archive/ppa)

---

