---
title: "Hardy Problems"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by spaceship.rodeo on 2008-08-01
So I finally got around to upgrading to Hardy Heron and there were some complications (again).  For some reason, it's not detecting my video card (GeForce 7900 GS) and it's running in reduced graphics mode, or whatever, and my resolution is down to 800x600.  And when I tried to get on the internet to see how I could fix this problem, it wasn't detecting any internet connection!  I'm posting this using the live cd for hardy.

So anyway, if anyone could help me out here I'd appreciate it.

---

### Post by phidia on 2008-08-01
With some exceptions (few) when you upgrade the kernel you need to re-install the nvidia driver. How did you install it previously? Note that Hardy's xorg has changed-see the [Community Docs on video]("https://help.ubuntu.com/community/Video").

For the network issue what type of connection do you have? Some commands you might try: "ifconfig" "lshw -C network"

---

### Post by spaceship.rodeo on 2008-08-01
Uh, I'm pretty sure I just did a clean install with Gutsy.  When I tried to use the restricted drivers manager, but for some reason it wouldn't open and I'm not sure what might be causing that.  Actually, I don't think any programs will open.  

Anyway, I'll try those commands and get back to you.  Thanks.

---

### Post by bobnutfield on 2008-08-01
Just a thought, and it may not be your issue, but some who upgraded from Gutsy found themselves booting into the wrong kernel on the first reboot, and it caused issues similar to what you are describing.  Type:

> uname -a

Just to verify you have the correct kernel running.  Gutsy's last stock kernel was 2.6.22, I believe.

---

