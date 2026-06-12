---
title: "How to re-establish internet"
date: 2008-10-14
forum: New to Ubuntu
---

### Post by _MsG_ on 2008-10-14
Hi guys,

I upgraded a week ago from Hardy to Intrepid, but because of the evil driver they put out I got no internet at all. But I downloaded a Intrepid live disk and made a bootbale USB stick with intrepid of it, and that one HAS internet, so it has been fixed already. But how can I get this fix onto my local ubuntu installation? What is the easiest way? I have a Windows partition, a Ubuntu partition with Intrepid (which has no internet), and the Intrepid live USB stick, based on this ISO: [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/) (and then of course the intrepid ISO)

---

### Post by phidia on 2008-10-14
You could chroot into your install from the live cd. Check out man chroot in a terminal.

Can you just plug in a wired connection and update through that?

---

### Post by _MsG_ on 2008-10-15
Lol the problem was that I was connected wiredly, but that Intrepid ****** it up :).

I did the following thing to make it all work again:

Booted from USB Intrepid Live Stick, then copied the whole /etc/network directory and paste it in my local filesystem. And voila, back online :).

---

