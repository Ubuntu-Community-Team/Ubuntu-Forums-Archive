---
title: "Playing Dvd's"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by joseph1223 on 2008-05-20
I want to be able to play dvds through movie player, how would i do that?
i tried it before, and it came up with an error each time

---

### Post by Maestro23 on 2008-05-20
What was the error?

---

### Post by joseph1223 on 2008-05-20
"could not read from resource"

---

### Post by wadelewis4 on 2008-05-20
If it's not happening with other DVDs then it's probably a defective disc or your drive is just being persnicketty.

If it's any DVD you try then
my suggestion is this..

In a terminal type: 

```
sudo apt-get install libdvdread3
```

And my personal DVD player of choice is Ogle (get it via Synaptic) - the menu support kicks booty.

---

### Post by joseph1223 on 2008-05-20
i did what you said, and i tried 3 more dvds, none of which work

---

### Post by crjackson on 2008-05-20
> **joseph1223 said:**
> I want to be able to play dvds through movie player, how would i do that?
i tried it before, and it came up with an error each time
Try this...

Go to SYSTEM>ADMINISTRATION>SOFTWARE SOURCES and enable the extra repositories first...

Start from scratch and don't worry if you've already done some of this before.  It will just skip any uneeded items.  This is for 64-bit Hardy...

Go to your menu - Applications>Accessories>Terminal and click!

Next cut and paste the following into the terminal screen.

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

```
sudo apt-get install libdvdcss2 w64codecs gxine totem-xine xine-ui libdmx1 libxine1 libxine1-ffmpeg libxinerama1 totem libdvdread3
```

---

### Post by joseph1223 on 2008-05-20
i have 64 bit hardy

---

### Post by Exsecrabilus on 2008-05-20
Do what Crjackson said, but for the last part, do this:

```
sudo apt-get install libdvdcss2 libdvdnav4 libdvdread3 totem-xine w64codecs
```

Now go **System** >> **Preferences** >> **Main Menu**.
Go to **Sound & Video** tab and uncheck **Movie Player** and enable **Movie Player (Xine)**.
This is due to Gstreamer's inability to read DVD menus and its inconveniences.

---

### Post by joseph1223 on 2008-05-20
thank you very much :)
works fine now :)

you guys get a star now :KS and a concert :guitar:

---

### Post by Maestro23 on 2008-05-20
Glad you got it working man.  Please mark this thread "Solved". :smile:

---

### Post by crjackson on 2008-05-20
> **joseph1223 said:**
> i have 64 bit hardy

I edited the post to service 64-bit Hardy instead of 32-bit.

---

### Post by wadelewis4 on 2008-05-21
I'm glad you got it resolved - and for future users who find this forum I'd like to leave an alternative means of achieving DVD playback: It helped me a while ago (sorry I didn't remember it sooner...) 

[DVD Playback in 2 Commands - LIFEHACK]("http://lifehacker.com/350015/enable-dvd-playback-in-ubuntu-in-two-commands")

---

### Post by masonfoley on 2008-05-21
I followed the instructions for 8.04 [here]("https://help.ubuntu.com/community/RestrictedFormats") and I still get the same error message when attempting to load a dvd to play:

> The source can't be read.

May be you don't have enough rights for this, or source doesn't contain data (e.g. no disc in drive).  (Error reading from DVD.)

I was able to play DVDs in Feisty with the same hardware so I'm almost certain it isn't that (besides, I installed the system from this drive).

Any other gotchas I'm not considering?

---

