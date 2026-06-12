---
title: "DVD Playback in Ubuntu"
date: 2008-08-17
forum: New to Ubuntu
---

### Post by diego898 on 2008-08-17
I've followed all of the enable media guides for ubuntu. I've installed restricted extras etc etc. Now, when I put in a DVD, VLC opens up but nothing happens. It just stays open and nothing plays. I press play, the drive just keeps making this repeated reading noise, thats about half a second in length and about half a second apart, so about two "clickes" a second. When I close VLC and open Totem, it plays but it is very grainey and low quality. Any ideas?

UPDATE - The smaller version plays good but fullscreen doesn't look good.

---

### Post by nicedude on 2008-08-17
You probably need to install libdvdnav which is a package that enables DVD menu support.

---

### Post by diego898 on 2008-08-17
synaptic sais I already have that installed

---

### Post by Separ on 2008-08-17
This is not supported by Ubuntu but it works wonders.

[This Link]("http://lifehacker.com/350015/enable-dvd-playback-in-ubuntu-in-two-commands") Will give you a guide on how to enable DVD playback in 2 commands.

---

### Post by diego898 on 2008-08-17
I can play the DVD in totem only, not in VLC. AND it plays fine when its small, just looks bad when its large

---

### Post by pi.boy.travis on 2008-08-17
Is this DVD encrypted?

Try:

sudo /usr/share/doc/libdvdread3/install-css.sh

in a terminal, assuming you already have the libdvdread3 package.

---

### Post by diego898 on 2008-08-18
VLC still doesnt work and it is still making that weird sound. Can anyone please help me?

---

### Post by nathanielnavidson on 2008-08-18
I have dvd playback but the video is all tinted blue.  Any advice?

---

### Post by diego898 on 2008-08-19
Can anyone offer any advice with my problem?

---

### Post by pi.boy.travis on 2008-08-20
Hmm. . .  Could we get some system specs please?  Anything more to work with at this point would be advantageous.

---

### Post by diego898 on 2008-08-20
any one command I can use to paste you its exact output?

---

### Post by Grateful Canuck on 2008-08-20
In a Google search engine, type the following:

libdvdcss (32 bit machine) or libdvdcss2 (64 bit machine)

The 32 bit version is also available on the VLC website. If you have a 64 bit machine, you're going to need debian-multimedia.org. 

I truly hope this helps you view DVD's in Ubuntu.

---

### Post by fedex1993 on 2008-08-20
IF you havnt already install libdvdcss2 i had the same problem.

---

### Post by diego898 on 2008-08-20
I CAN view DVDs but NOT in vlc. And when I CAN view DVDs they are low quality in full screen.

---

### Post by diego898 on 2008-08-23
Help my community I cant let this issue die!

---

