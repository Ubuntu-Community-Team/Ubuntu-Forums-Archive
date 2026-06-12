---
title: "drives"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by adobrakic on 2008-05-29
i keep reading topics about people having drives such as nvidia or something. Should everyone get this, and are there other drives that people should get?

---

### Post by LaRoza on 2008-05-29
> **adobrakic said:**
> i keep reading topics about people having drives such as nvidia or something. Should everyone get this, and are there other drives that people should get?

**Driver** you mean. Drivers are programs that are used to use hardware. For example, you get a new printer and you will need drivers so the computer can use it. For HP printers, this is very easily done in Ubuntu. For Windows, you get a disk with the drivers on it.

When you install Ubuntu, it will autodetect and use the drivers it needs if it can. For me, I use all compatible hardware so my video, web cam, printer, etc all work out of the box. Ubuntu has a restricted drivers manager which will all you to install drivers for other hardware.

What is you computer's hardware?

---

### Post by Inxsible on 2008-05-29
nVidia is a manufacturer of graphics cards. So is ATI. To enable all the features of the graphics card that you have on the machine, you need the drivers (not drives).  Decent graphics cards are required to enable all the fancy effects and still have a computer that is usable

---

### Post by adobrakic on 2008-05-29
> **LaRoza said:**
> **Driver** you mean. Drivers are programs that are used to use hardware. For example, you get a new printer and you will need drivers so the computer can use it. For HP printers, this is very easily done in Ubuntu. For Windows, you get a disk with the drivers on it.

When you install Ubuntu, it will autodetect and use the drivers it needs if it can. For me, I use all compatible hardware so my video, web cam, printer, etc all work out of the box. Ubuntu has a restricted drivers manager which will all you to install drivers for other hardware.

What is you computer's hardware?

how do i figure out my computer's hardware on here?

---

### Post by LaRoza on 2008-05-29
> **adobrakic said:**
> how do i figure out my computer's hardware on here?

What hardware do you have?

It is possible you won't have to do anything like me. There is a chance you will have to enable a restricted driver (it is easy, it is a popup and you click on it after you install), there is also the chance that something won't work well at all, however that is relatively rare.

You can tell us what computer you have (it should be on the front or side of the case or on the manual), and I'll look it up on my own and post it.

---

### Post by adobrakic on 2008-05-29
I have a compaq presario 6000
all i know off the top of my head is that i have like 735 ram and a 1.6ghz processor
i dont know anything about my graphics, monitor, sound card, etc.

---

### Post by LaRoza on 2008-05-29
> **adobrakic said:**
> I have a compaq presario 6000
all i know off the top of my head is that i have like 735 ram and a 1.6ghz processor
i dont know anything about my graphics, monitor, sound card, etc.

Everything should work fine.

Unless you are added a video card, you have a supported video. You can go to the device manager in Windows for more information. (You have nVidia)

---

### Post by adobrakic on 2008-05-29
does this mean i could use the visual effects?

---

### Post by Inxsible on 2008-05-29
Open up a terminal and type in ```
lspci | grep VGA
``` That will tell you what graphics card you have. Post it back here so we can tell you where and how to get the drivers for it, if required

---

### Post by LaRoza on 2008-05-29
> **adobrakic said:**
> does this mean i could use the visual effects?

Probably.

---

### Post by adobrakic on 2008-05-29
> **Inxsible said:**
> Open up a terminal and type in ```
lspci | grep VGA
``` That will tell you what graphics card you have. Post it back here so we can tell you where and how to get the drivers for it, if required


ado@ado-desktop:~$ lspci | grep VGA
01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266]

---

### Post by adobrakic on 2008-05-29
bump, sorry :x

---

