---
title: "Need Help with Ubuntu [Black Screen]"
date: 2013-08-26
forum: New to Ubuntu
---

### Post by sid_dev2 on 2013-08-26
Hi.

I just installed Ubuntu, on my HP computer. I used a disk, and I downloaded Ubuntu and followed all the instructions. When I rebooted my computer, I was greeted by a black and white screen which read these options:

- Try Ubuntu without installing
- Install Ubuntu
- Check disk for defects

I clicked "Install Ubuntu". For a while, I had a completely black screen. After about 15 minutes of waiting, I decided to turn my computer off and try again. This next time I clicked "Try Ubuntu without installing", same luck. I clicked "Check disk" and I received the screen I was hoping for, but it just checked my disk and returned me to this black and white screen. I am not too familiar with computer hardware and software as I'm more of a design person on my computer, so please excuse the amount of questions I will ask. 

Thanks!

---

### Post by SweetAurora on 2013-08-26
Sounds like an UEFI PC according to what you are saying, also the screen issue is likely due to either a bug in the screen brightness, or the laptop has dual-graphics, descrete graphics, or optimus.

---

### Post by sid_dev2 on 2013-08-26
Any solutions?

---

### Post by Old_Grey_Wolf on 2013-08-26
Boot from the disk. When you get the screen that has Try Ubuntu without installing, Install Ubuntu, Check disk for defects, press F6 key. You will get the other boot options. Selecting nomodeset. If nomodeset doesn't work the next one to try would be apci=off. After selecting the extra boot commands select "Try Ubuntu" and see if it will boot.

---

### Post by sid_dev2 on 2013-08-26
There is no response when I hit F6. It's all black and white and it says at the top GNU GRUB version 1.99.

---

### Post by Old_Grey_Wolf on 2013-08-26
Did you get the screen with "Try Ubuntu" at all or just the black screen?

---

### Post by Jonathan Precise on 2013-08-26
> **sid_dev2 said:**
> There is no response when I hit F6. It's all black and white and it says at the top GNU GRUB version 1.99.

That's normal, as it seems like a PC with UEFI. Does the screen look like this?

[IMG]http://pix.toile-libre.org/upload/original/1347445084.png[/IMG]

If it does, then press 'e'. Then after 'quiet splash' add [FONT=courier new]nomodeset[/FONT].

If it doesn't work, try [FONT=courier new]xforcevesa[/FONT].

---

