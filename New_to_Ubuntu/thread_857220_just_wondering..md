---
title: "just wondering."
date: 2008-07-12
forum: New to Ubuntu
---

### Post by barfy on 2008-07-12
I've been off running around for a bit since my last posting it seems.  just downloaded a copy of Wubi-8.04.1 and just had to try it out and was interested to know if it scans the system for drivers?  Since you have been working closer with dell and others lately I thought your base would be rather large by now and I would try umbuntu on my old percission 420.  If memory serves me this one had problems with the hedgehog version or previous ones (I think it was sound and scsi but I'm kinda fuzzy about that) Since this is the only one I have online and I had some conectivity issues with the other versions I figure I would try my ISP's software in wine I can configure the dang thing but can't find out how to make the dam pc dial the dang number, so hence the hesitation I've had in deploying umbuntu in general. By the way, Yes, I'm useing a dial-up connection. life is sad for those of us on the slow end. figure if I hook up every night before I go to sleep I'll have the thing downloaded in about 5 nights.  talk about anticipation!!!  :lolflag:

---

### Post by utsuprainfra on 2008-07-12
I used to use minicom to set up a slirp session, but that's a whole different kettle of fish.  I'd approach your issue like this:

1.  Determine what the ppp settings are for your ISP without their emulated software
2.  Determine what modem your machine has and work on that, I would guess that someone has probably tried to make your modem go before.
3.  Use the gui networky stuff maybe to configure your ppp settings.
4.  You may have to manually add entries to /etc/resolv.conf if that file is still around.  Or DHCP should do it.

That's a rough idea.  Let me know if you get it worked out or you have any specific questions.

---

### Post by L815 on 2008-07-12
From what I know it scans your hardware and picks the best drivers to use. Some are generic that work on almost anything, and others are Open Source drivers. There also is a hardware drivers thing that will tell if you hardware you'd need to approve drivers for and enable it manually.

As for updates, I did a fresh install yesterday and was only 78mb in updates (backports and everything). Shouldn't take all night on dialup :P

---

### Post by LowSky on 2008-07-12
gnome-ppp should help with dial up

```
sudo apt-get install gnome-ppp
```

---

### Post by barfy on 2008-07-12
You are way more vearsed in networking then I. Fraid I haven't any programing skills either. but the modem seems to be working right now (it is the one I'm on at the moment). but having gone through this with several postings I've had no configuration problems. I just can't figure out how to tell the PC to start dialing the number. maybe when I install my ISP's Auto dialing software in wine then this wont be anything to worry about. :eek::eek:I hope I didn't jinx myself there. LOL.

---

### Post by hyper_ch on 2008-07-12
it is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

a generic topic title like "noob here" or "need help" does not help at all. As you may have notices, just about everyone posting in here has some kind of a problem or issue or question ;)

---

