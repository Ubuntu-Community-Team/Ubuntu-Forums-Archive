---
title: "Fullscreen YouTube video--very buggy!"
date: 2008-07-10
forum: New to Ubuntu
---

### Post by erans on 2008-07-10
When I full screen a flash video, I see elements of my desktop (my network icon, Pidgin, etc) flashing on the video. When I try to exit fullscreen, I get a TON of weird bugs, like the image I was viewing is superimposed onto my desktop and panels and taskbar and won't go away until I do something that requires the system to refresh the image. 

Anyone else have this problem? I ran firefox from terminal and didn't receive any error messages.

---

### Post by Dark_Stang on 2008-07-10
Welcome to the world of Adobe's crappy programming and support.

---

### Post by erans on 2008-07-10
Is there a solution to this problem?

---

### Post by Canis familiaris on 2008-07-10
> **erans said:**
> Is there a solution to this problem?


If you have Compiz.
Then Zoom in to the video by:
Super + Scroll Wheel

Super key = Windows key

---

### Post by erans on 2008-07-10
I don't have Compiz (at least I don't think so). This is a fresh installation of Ubuntu and I don't *think* I had this problem with my old installation, though I could be mistaken. Does everyone have the same problem, or what?

---

### Post by dracayr on 2008-07-10
which browser? which player?

dracayr

---

### Post by Canis familiaris on 2008-07-10
> **erans said:**
> I don't have Compiz (at least I don't think so). This is a fresh installation of Ubuntu and I don't *think* I had this problem with my old installation, though I could be mistaken. Does everyone have the same problem, or what?

Yes most of us have the same problem. Blame Adobe for that.

---

### Post by dracayr on 2008-07-10
If it's only Adobe, why don't you use gnash?

dracayr

---

### Post by Canis familiaris on 2008-07-10
> **dracayr said:**
> If it's only Adobe, why don't you use gnash?

dracayr

Sadly not compatible with many sites :(

---

### Post by erans on 2008-07-10
Using the latest Firefox and the latest Adobe Flash. I tried swfdec and gnash as well. Gnash wasn't loading youtube videos and swfdec would launch a new window for fullscreen.

---

### Post by erans on 2008-07-12
Hey, I think I found a solution to this problem. I'll post it here since apparently other people have the same thing. 

I had to reinstall Ubuntu because of.. well, I'm not really sure why, but I had to do it anyway. YouTube was not misbehaving after I installed it, but after I installed a bunch of packages to install XMMS, it started freaking out again. 

So I removed all of the packages that I was instructed to install to compile XMMS (I got the information from a blog), rebooted, and YouTube works like a charm. 

```
autotools-dev automake1.9 libtool gettext libasound2-dev libaudiofile-dev \
libgl1-mesa-dev libglib1.2-dev libgtk1.2-dev libesd0-dev libice-dev libmikmod2-dev libogg-dev \
libsm-dev libvorbis-dev libxxf86vm-dev libxml-dev libssl-dev
```

One (or some of these) were causing problems. Hope this information helps someone else.

---

