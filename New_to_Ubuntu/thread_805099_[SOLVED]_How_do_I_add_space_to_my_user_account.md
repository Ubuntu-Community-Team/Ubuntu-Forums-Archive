---
title: "[SOLVED] How do I add space to my user account?"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by CSEatOSU on 2008-05-23
I installed 8.04 via Wubi in XP.  Went great for the first couple weeks with the 30Gb install, until I ran out of disk space.  So I did some searching and found how to increase the disk space to allow Ubuntu to use another 30Gb.  I used the instructions [here]("https://wiki.ubuntu.com/WubiGuide#head-fda2b476cbe51b911313b25d55e6bf70c6134b2b") by running the script

```
sudo sh wubi-add-virtual-disk /home 30000

```

That worked fine, I can see my Ubuntu install is now ~60Gb.  But my question is this:

I can see I have 22.3Gb free on / but only 4.1Gb free on /home/username.  How do I allow my user (username) to take that space that I freed up using the script above?

Any help is greatly appreciated.

---

### Post by shifty_powers on 2008-05-23
did you create a separate partition for /home than tyou did for / ?

---

### Post by CSEatOSU on 2008-05-23
> **shifty_powers said:**
> did you create a separate partition for /home than tyou did for / ?

No, I installed Ubuntu via Wubi.  Therefor it is virtual space on the one and only Windows partition.  So there is no real *partition* for my linux install.

---

### Post by CSEatOSU on 2008-05-23
I am semi-noob to linux but after much research... should I do something like this?

```
sudo mount -o loop /host/ubuntu/disks/root.disk /home

```

My understanding is after I mount /home (home.disk) into root.disk, it is essentially putting /home back into / (root directory).  Thus making /home available to the 22Gb I created earlier in / (root directory)?

---

### Post by CSEatOSU on 2008-05-23
To add to all this...

So basically when I ran the script ```
sudo sh wubi-add-virtual-disk /home 30000
```, I thought it would just increase root.disk from 27GB to ~60GB but instead it moved /home to a virtual-disk, home.disk and added 30GB to the / (root/disk)

So...

**What I have now**
/host/ubuntu/disks/root.disk   27GB
/host/ubuntu/disks/home.disk   27.9GB

**What I want**
/host/ubuntu/disks/root.disk   **~60GB**

So my real question goes like this, how do I get from where I am to where I want to be?

Thanks again!!

---

### Post by CSEatOSU on 2008-05-24
Anyone? C'mon someone must have a solution for me. :confused:

---

### Post by CSEatOSU on 2008-05-26
Anyone? Bueller... Bueller?

---

### Post by CSEatOSU on 2008-05-27
Help please.  I really need to fix this.

---

