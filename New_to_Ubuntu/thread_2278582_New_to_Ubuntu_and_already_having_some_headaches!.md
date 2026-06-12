---
title: "New to Ubuntu and already having some headaches!"
date: 2015-05-17
forum: New to Ubuntu
---

### Post by MrFortyOne on 2015-05-17
First of all, Hello everyone! I'm new to this forum and new to Ubuntu aswell. My native language is not the english so excuse any dumb mistakes and bad grammar.

I've installed Ubuntu 15.04 on my laptop today and just started to explore it a bit, but I'm having this problem that seems to be well known here in the forum. One concerning my mouse clicks not working as intended.
I have a R.A.T. 3 and I've found info about this bug here [http://ubuntuforums.org/showthread.php?t=1698482](http://ubuntuforums.org/showthread.php?t=1698482) . Ok now, why haven't I solved my problem yet? Well first of all because I don't have any xorg.conf file and I have no idea how to create it, I've tried some approaches using the ctrl+alt+f1 console with the following lines:

```
sudo service gdm stop
sudo Xorg -configure
sudo service gdm start
```

But even there I fail to stop the gdm service, which btw I have no idea of what it is.

Some (maybe) relevant background on me: I've used Windows all my life ( I know, I know...) and I have little knowledge of programming, I've just started to learn python this week to.

Thanks in advance guys!

---

### Post by Vladlenin5000 on 2015-05-17
Hi ans welcome.

Before anything else let me strongly advice against doing "archaeology" in operating systems. What worked for 10.04 almost certainly won't work for 15.04. In between the aforementioned releases there were EIGHT more Ubuntu releases with HUGE changes. In a nutshell, take anything older than 12 months with a big grain of salt.

Now, please explain exactly what's happening using your own words instead of pointing to a "bug".

---

### Post by MrFortyOne on 2015-05-17
Ok thanks Vladlenin5000.

Well, if I use my laptop mousepad  everything works has expected, no problem whatsoever. When I connect my  mouse, this R.A.T.3, in the beggining nothing seems out of the usual, the  mouse still moves, but I can't click outside of the window where I am. For  example, here in firefox I can still use the click to change tabs,  change the place I'm typing to another, etc, but in the same window I  can't for example click the minimize, maximize or close button. Any  click outside the firefox doesn't work at all.

I know you advised  against "archeology" but the issue in this [link]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/615892") pretty much  sums it up, most of the details are the same for me. Like if I use the  "change mode" button in the mouse sometimes it goes back to normal,  (sometimes only), the last time I tried it (while writing this) the  mouse was "stuck with the symbol that shows when you write (that capital  i) even outside the writing area. If i use the Super+tab and go for  example to the terminal the mouse doesn't work at all ( and if I'm stuck  in that capital i thing it stays like that).

I don't know where to elaborate much further, if I can help with any logs or anything please say!

Just saying this one more time, I'm pretty sure the issue is the same as the one in the link I provided.

PS: I also relate to this incident [http://ubuntuforums.org/showthread.php?t=2143896](http://ubuntuforums.org/showthread.php?t=2143896)

---

### Post by Vladlenin5000 on 2015-05-17
What are your other specs, namely graphics card/chip?

---

### Post by Geoffrey_Arndt on 2015-05-18
This very specialized gaming mouse is going to pose a challenge to setup for Linux, but, it appears doable if you're willing to put in some extra effort.

[http://askubuntu.com/questions/92546/cyborg-r-a-t-3-gaming-mouse-stops-working-after-a-while-and-or-misbehaves](http://askubuntu.com/questions/92546/cyborg-r-a-t-3-gaming-mouse-stops-working-after-a-while-and-or-misbehaves)

***********************************************************************************************************

Another solution of course is to use the mouse while in windows for  gaming or similar graphics work, but use a standard wireless laser mouse  like the Logitech M325 for generalized, everyday computing - - works perfect in Linux.

---

