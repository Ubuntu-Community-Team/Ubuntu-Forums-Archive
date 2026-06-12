---
title: "Device driver"
date: 2010-03-09
forum: Programming Talk
---

### Post by eladriels on 2010-03-09
hi all,
i want to write a device driver for ubuntu.actually i dont have enough experience on kernel programming. but i want to write for my mp3 player, usb device. can anyone help me,i need your opinions, advises like where should i begin.
thanks:)

---

### Post by wmcbrine on 2010-03-09
What is it that you want to do with the player? Transfer files to it? I think almost all MP3 players show up as standard USB storage devices.

---

### Post by MindSz on 2010-03-10
Usually I start by trying to get a hold of the communication protocol of the device (maybe a manual), so you understand how to "talk" to it.

---

### Post by Zugzwang on 2010-03-10
If wmcbrine's note does not apply to your player, here's something about writing new Linux USB drivers: [http://matthias.vallentin.cc/2007/04/writing-a-linux-kernel-driver-for-an-unknown-usb-device/](http://matthias.vallentin.cc/2007/04/writing-a-linux-kernel-driver-for-an-unknown-usb-device/)

---

### Post by eladriels on 2010-03-14
thanks for all advises, but my mp3 player betrayed me:( i mean it doesnt need driver. it shows up usb storage really. i tried firstly it on virtualbox (ubuntu), i didnt work but i tried again on ubuntu(not on virtualbox) it worked. actually thats my homework wrting a driver. i wanted to learn some deep thing about linux with this homework. and i dont know now what should i do, which device i should choose.
thanks

---

### Post by eladriels on 2010-03-14
actually this is not a only homework for me, i want to improve my knowledge, and do something about linux:) i want to add this=)

---

### Post by soltanis on 2010-03-14
If you still want a list of devices I'd like a driver for I have a really good one.

---

### Post by eladriels on 2010-03-14
i would be grateful:)

---

### Post by soltanis on 2010-03-15
Broadcom's annoying wireless chips? Those pesky Ricoh webcams (the one the r5u870 driver is for but never fixes)? Thinkpad fingerprint scanners?

---

