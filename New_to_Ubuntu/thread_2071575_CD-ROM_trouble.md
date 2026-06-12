---
title: "CD-ROM trouble"
date: 2012-10-15
forum: New to Ubuntu
---

### Post by Populus on 2012-10-15
Hi,

I'm having problems playing a CD-Rom. The sound tracks work fine but when I try to play the video portion, it freezes and I have to eject the disc. I can play DVDs and audio CDs with no problems. Any clues?

---

### Post by lazarojhr16 on 2012-10-15
what are you using to view the video portion? I would recommend using vlc

---

### Post by Populus on 2012-10-15
I tried to open it using VLC but each disc option produced the following message: *VLC is unable to open the MRL 'dvd:///dev/dvd'. Check the log for details*.
I tried to eject it but a box came up saying Wineserver was still running; I couldn't stop this from running so I had to restart my laptop. The initial frame of the video shows on screen but it won't start running.

---

### Post by daslinkard on 2012-10-15
You can try the following sudo command
```

sudo -E wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```
Followed by

```
sudo apt-get update && sudo apt-get install libdvdcss2
```

Hopefully this solves this for you!

---

