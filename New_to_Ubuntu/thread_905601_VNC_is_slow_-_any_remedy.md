---
title: "VNC is slow - any remedy?"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by CryptiniteDemon on 2008-08-30
Okay I remote desktop into one of my window machines from across the internet and it's speed is just fine. However, whenever I try to do a VNC connection into my ubuntu box, it's insanely slow.  Both computers are at 1600x1200 resolution.  

I also use XRDP to remote into the linux machine.  Even if I remote in from inside my own network VNC tends to be choppy and slow.  

Are there any sort of optimizations I can apply to VNC?

---

### Post by gmxgeek on 2008-08-30
You woudn't happen to have any P2P software up would you? That eats a network connection for breakfast, and creates a bunch of connectivity problems while it's running. If you have wireless, check to see if the neighborhood scamps aren't using your connection to dl their pr0n :P

---

### Post by CryptiniteDemon on 2008-08-30
I don't use an P2P software.  And the only clients on my network are my computers.

---

### Post by sonicb00m on 2008-08-30
What are you using as a client?

I tried connecting with vinagre but it feels like no compression or resizing is applied and it's dog slow compared to xtightvncviewer with some params.

xtightvncviewer host::port -compresslevel 9 -quality 4 -depth 8'

---

### Post by HermanAB on 2008-08-30
VNC is almost always the wrong solution for connecting to a Linux box.

$ ssh -X -C -c blowfish username@linuxbox gnome-panel

---

### Post by cprofitt on 2008-09-21
HermanAB:

Dude that solution rocks... but for those of us coming from Windows it is an alien way of thinking -- fantastic tip man!!

---

### Post by mattman85 on 2008-12-10
> **HermanAB said:**
> VNC is almost always the wrong solution for connecting to a Linux box.

$ ssh -X -C -c blowfish username@linuxbox gnome-panel

What if one is trying to remote from their windows box to their ubuntu box?  Is there a way to get this command to work with PuTTY?

I just got PuTTY working, and was able to use RealVNC viewer in XP to tunnel my VNC through SSH, but it seems sluggish because it's rendering the background..  Yet, I can't find a way to tweak settings to make the connection faster.

---

