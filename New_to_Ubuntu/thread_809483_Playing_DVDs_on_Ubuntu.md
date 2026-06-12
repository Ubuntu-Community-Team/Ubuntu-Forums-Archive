---
title: "Playing DVDs on Ubuntu"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by Jaded Misanthrope on 2008-05-27
Is it possible to play DVDs on Ubuntu, and if so, how? I have tried two DVDs (one from the Stargate SG-1 box set and Deja Vu), and both of them have made Totem load, but give a 'could not read from resource' error and would not play. Any help?

---

### Post by sayakb on 2008-05-27
Try playing the VOB files in VLC media player. If you don't have VLC:
```
sudo apt-get install vlc
```

---

### Post by Weidbrewer on 2008-05-27
First question:  do you have all the proper codecs downloaded?  I believe that the DVD ones fall under the same header as things like MP3s - totally free, but they are someone else's property, so Ubuntu can't include them on the install.

Also, try Kaffeine as a player.  I am personally fond of that one.

---

### Post by ndo on 2008-05-27
Ok.

I am having the same problem. With me, it is not a simple question of downloading codecs for Totem or opening disks with vlc or kaffeine. I have already tried this, totem still shows error and both programs just freeze up.

Here is some information about my drive:

[    0.000000] ACPI: DSDT 6FE91C37, 7FCD (r1   Acer  Navarro  6040000 MSFT  3000000)
[   37.374721] scsi 2:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ-850S  1.20 PQ: 0 ANSI: 5
[   37.471549] Uniform CD-ROM driver Revision: 3.20
[   37.471611] sr 2:0:0:0: Attached scsi CD-ROM sr0

Is it significant that ubuntu is only recognizing it as a CD-ROM drive?

I tried using the following command to enable DVD playback per another user's suggestion:

sudo /usr/share/doc/libdvdread3/install-css.sh

However, it failed and gave the following prompt:

Install debhelper and fakeroot, then run this script again

I don't have to tell you how frustrating it is to not be able to simply play a freaking DVD in Ubuntu...any help is really appreciated!

---

### Post by philinux on 2008-05-27
> **Jaded Misanthrope said:**
> Is it possible to play DVDs on Ubuntu, and if so, how? I have tried two DVDs (one from the Stargate SG-1 box set and Deja Vu), and both of them have made Totem load, but give a 'could not read from resource' error and would not play. Any help?

Click the medibuntu link and follow the instructions.

---

### Post by d.kusummmanth@gmail.com on 2008-05-27
> **Jaded Misanthrope said:**
> Is it possible to play DVDs on Ubuntu, and if so, how? I have tried two DVDs (one from the Stargate SG-1 box set and Deja Vu), and both of them have made Totem load, but give a 'could not read from resource' error and would not play. Any help?
forget totem. Totem is the worst player I've ever used.

---

### Post by Weidbrewer on 2008-05-27
> **d.kusummmanth@gmail.com said:**
> forget totem. Totem is the worst player I've ever used.

And given some of the Ubuntu players, that's saying something.

Once you get things the way you want them, Linux can make a nice media player...but getting there is a journy.   Plus, the players avalable are some very boring ones.  Makes me wish I was a programmer to make my own, but hey, no OS is perfect.

---

