---
title: "Screen tearing within Compiz environment"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by AncientPC on 2008-11-12
My screen tears whenever running Compiz, it never did this in 8.04.1 . . .

Edit: Never mind, now it's tearing occasionally in Metacity as well.  I'm running 8.10 on a Dell E6500 with an Intel 4500 MHD video card. :(

It also tears in high action scenes within Totem, I think this is a video card driver issue.

---

### Post by Shwefty on 2008-11-12
Me too! BUMP

---

### Post by nhasian on 2008-11-12
Hmm thats either a video driver problem, or bad video memory.  (the memory on your video card, not the system memory)

---

### Post by AncientPC on 2008-11-13
> **nhasian said:**
> Hmm thats either a video driver problem, or bad video memory.  (the memory on your video card, not the system memory)
Pretty sure it's a video problem as Vista doesn't ever give me screen tearing.  Also, it's an integrated graphics card sharing up to 384MB from system memory.

---

### Post by binbash on 2008-11-13
Please run [http://forlong.blogage.de/entries/2008/5/16/Compiz-Check-04-released](http://forlong.blogage.de/entries/2008/5/16/Compiz-Check-04-released)
compiz check and be sure your card driver is not in blacklist

---

### Post by Linux user 66 on 2008-11-13
Though you have an integrated Intel GPU and not an NVIDIA VGA card, maybe there's something helpful in this post about a problem I recently had:

[http://ubuntuforums.org/showthread.php?t=972949](http://ubuntuforums.org/showthread.php?t=972949)

---

### Post by AncientPC on 2008-11-13
> **binbash said:**
> Please run [http://forlong.blogage.de/entries/2008/5/16/Compiz-Check-04-released](http://forlong.blogage.de/entries/2008/5/16/Compiz-Check-04-released)
compiz check and be sure your card driver is not in blacklist

Everything gets a green OK after running compiz-check.

> **Linux user 66 said:**
> Though you have an integrated Intel GPU and not an NVIDIA VGA card, maybe there's something helpful in this post about a problem I recently had:

[http://ubuntuforums.org/showthread.php?t=972949](http://ubuntuforums.org/showthread.php?t=972949)

Enabled v-sync, doesn't help. :(  Also, I get this in Metacity as well so I'm pretty sure it's not a Compiz problem (only much more often / worse in Compiz).

---

### Post by cbonar on 2008-11-16
If it happens approximately every 10s, you could try disabling the "Detecting RANDR (monitor) changes" service : [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/275152](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/275152).

---

