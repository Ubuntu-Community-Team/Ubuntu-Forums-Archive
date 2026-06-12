---
title: "AMD driver for 15.10?"
date: 2015-11-08
forum: New to Ubuntu
---

### Post by william92 on 2015-11-08
So there seems to be no driver which leaves me using Windows 10 since changing refresh rate without catalyst controlpanel feels close to impossible. I have been trying out xrandr without any success. When applying a the new settings, the window transitions still seems to stay at 60hz.

---

### Post by ajgreeny on 2015-11-08
There are one or two bugs about this problem in 15.10 (see [https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1493888](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1493888)) which can apparently be overcome by carefully enabling the proposed repos in software-sources and upgrading just the packages needed for fglrx to work, then disabling proposed again.

I will search for more details which I can't find at the moment and try to post back.

I'm sure that it will eventually be a bug that is squashed, but at present it is a problem for a lot of AMD users.

---

