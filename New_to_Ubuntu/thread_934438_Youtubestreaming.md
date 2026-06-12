---
title: "Youtube/streaming"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by Siouxsy on 2008-09-30
Hey, I'm not that knowledgeable when it comes to Ubuntu. 
Every time i go to watch a video i.e youtube, flash...videos on the internet, it doesn't play right. it  freezes lags, sometimes no actual video plays just sound. Its okay playing videos on my computer its just the internet where streaming is a problem. Even songs on myspace don't work.
Can you help?

---

### Post by leo3307 on 2008-09-30
have you install the driver for flash player and if you want to download the videos from youtube you could use qttube
sudo apt-get install qttube

---

### Post by crjackson on 2008-09-30
> **Siouxsy said:**
> Hey, I'm not that knowledgeable when it comes to Ubuntu. 
Every time i go to watch a video i.e youtube, flash...videos on the internet, it doesn't play right. it  freezes lags, sometimes no actual video plays just sound. Its okay playing videos on my computer its just the internet where streaming is a problem. Even songs on myspace don't work.
Can you help?

Using your menu bar, go to --> System-->Administration-->Software Sources. From there enable EVERYTHING from each tab **EXCEPT** - _CD ROM_ & _PROPOSED UPDATES_.

From there tell it to close and it will prompt you to RELOAD. After it has reloaded and the GUI is closed do this.

Using your menu button --->Applications-->Accessories-->Terminal

Once that is opend and you see the box in the middle of your screen, copy the LONG code below, and paste it inside the command line box:

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list && wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install -y ubuntu-restricted-extras non-free-codecs w32codecs totem-mozilla libdvdcss2 libdvdnav4 gxine totem-xine xine-ui libdmx1 libxine1 libxine1-ffmpeg libxinerama1 libdvdread3
```

This is for 32-bit Ubuntu Hardy BTW.

---

### Post by simtaalo on 2008-09-30
check you have the latest version of flash (beta 10 is what im using) and latest firefox 3.0.3. then try a reboot and see if that makes any difference.

---

### Post by Siouxsy on 2008-10-01
hey i tried that the first bit error box saying

 E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please repor

came up what does that mean and what can i do?

---

### Post by billgoldberg on 2008-10-01
> **Siouxsy said:**
> hey i tried that the first bit error box saying

 E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please repor

came up what does that mean and what can i do?

Open up a terminal (applications -> accessories -> terminal)

and type this in:

```
sudo dpkg --configure -a
```

Press enter.

You'll be prompted for you password, enter it. You won't see any kind of visual sign you are typing it (no *** or something like that. After you entered the password, press enter again and it should fix itself.

---

