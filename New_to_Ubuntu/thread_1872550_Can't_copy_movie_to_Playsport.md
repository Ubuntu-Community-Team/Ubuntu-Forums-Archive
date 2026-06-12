---
title: "Can't copy movie to Playsport"
date: 2011-10-30
forum: New to Ubuntu
---

### Post by dndrich on 2011-10-30
Ubuntupals:

My brother is running Ubuntu 10.04. He wants to be able to take movies captured using his Playsport Kodak camera off the camera, and then put them back on when he wants to play them on the TV. The device has a high speed SD card. He can't do it. Now, I have the same camera, so I can experiment. OK, I plug the camera into my Mac, pull the movies off, reformat the card, copy the movies back onto the card, and they play fine on the camera. Now, trying the same thing with my Ubuntu 10.04 box, I can copy the movies off into Ubuntu no problem. Then I reformat the card and try to move the movies back on. No go. Looks like they are copying, but it is choppy to copy and slow. Once completed, the movies do not show up as playable on the camera. What is the story here?

---

### Post by dndrich on 2011-11-01
Anybody? "crickets..."

---

### Post by vanhenryjr on 2011-11-01
I have 11.04 and have a playsport. I however have not been able to do much more than move my video/picture from the SD card to my computer. I assume what you are saying is you can't copy from your computer to the SD card and put that in your playsport?

I was hoping to attach my playsport to my computer via the HDMI cable, but have not figured that one out yet.

good luck-hope someone else has some ideas

---

### Post by dndrich on 2011-11-01
> **vanhenryjr said:**
> I have 11.04 and have a playsport. I however have not been able to do much more than move my video/picture from the SD card to my computer. I assume what you are saying is you can't copy from your computer to the SD card and put that in your playsport?

I was hoping to attach my playsport to my computer via the HDMI cable, but have not figured that one out yet.

good luck-hope someone else has some ideas

Yes, that is the issue. No problem copying the files from the Playsport to the computer under Ubuntu. The problem is copying the other way. Works fine on my Mac, but not on Ubuntu. Can't figure out why that would be.

---

### Post by dndrich on 2011-11-06
OK, turns out I was able to fix this problem. I reformatted the card from the disk utility on Ubuntu. I am now able to transfer files back to the camera. But it turns out you cannot rename the files. You have to leave them in their obscure dos style names. Must be a limitation of the camera.

---

### Post by hansdown on 2011-11-06
Hi, dndrich.

It is a permissions issue.

If you open a terminal,

ctrl+alt+t,

Then enter...

```
gksudo nautilus
```

you will have read and write permissions, on your files.

---

