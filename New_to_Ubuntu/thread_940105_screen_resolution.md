---
title: "screen resolution"
date: 2008-10-06
forum: New to Ubuntu
---

### Post by olican101 on 2008-10-06
ok so i had windows 98 and i could et a really high resolution but now ive gone with ubuntu i can only get 600x800 AT THE HIGHEST i know my screen is capable of more and i know there is a programme but when i go to add it its tiked but theres no programme there please help by the way i have a dell TX78682 pleassssssse help

---

### Post by olican101 on 2008-10-06
it used to be 1600x1200

---

### Post by alphacrucis2 on 2008-10-06
> **olican101 said:**
> it used to be 1600x1200


Most likely you are missing the correct driver. What graphics card does your machine have?

---

### Post by olican101 on 2008-10-06
i dno lol :-P how do i check? im new to ubuntu

---

### Post by roger_1960 on 2008-10-06
Hi

In applications-accesories-terminal

type sudo displayconfig-gtk

then enter your password (it wont appear)

In the GUI which appears, edit the model to suit as best you can and you can change the resolution.  Log out and back in to make the change.

---

### Post by asmoore82 on 2008-10-06
> **roger_1960 said:**
> Hi

In applications-accesories-terminal

type sudo displayconfig-gtk

then enter your password (it wont appear)

In the GUI which appears, edit the model to suit as best you can and you can change the resolution.  Log out and back in to make the change.

minor correction
```
**gksudo** displayconfig-gtk
```

---

### Post by olican101 on 2008-10-06
nope the highest i can go is still 800x600

---

### Post by olican101 on 2008-10-06
oh i have a voodoo 3 (generic) card thats faded out in graphics card and its saying driver: none whitch is also faded out

---

### Post by whereiskevin on 2008-10-07
> **olican101 said:**
> oh i have a voodoo 3 (generic) card thats faded out in graphics card and its saying driver: none whitch is also faded out

Hello,

I had the same problem as you and I followed the instructions as stated in this thread and now my ubuntu environment shows a black screen with the OSD saying: resolution not compatible. I can't boot in to Ubuntu anymore.  (probably have to scrap this project and revert to XP)

Prior to this I also tried to download the latest driver from Nvidia.  I have the Nvidia 7300 LE card, but the extension of the file was .run and I didn't know how to execute that file.

Did the solution mentioned above work for you?

---

### Post by Ryadt on 2008-10-07
Try to boot in recovery mode. Then do ```
startx
```

---

