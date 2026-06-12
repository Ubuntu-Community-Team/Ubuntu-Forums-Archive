---
title: "Installed nvidia graphics card in 10.10; returned card &amp; now no boot to desktop"
date: 2011-12-01
forum: New to Ubuntu
---

### Post by swarup on 2011-12-01
I had purchased and installed an invidia graphics card in my Dell Dimensions desktop machine. With a bit of googling around I was able to get the driver installed for it and it was working fine. Now for other reasons I have had to return the graphics card to the store. And without the graphics card, the computer boots to a screen looking like a terminal window. That is, can't get it to boot to the desktop. It doesn't give any error messages; just doesn't go to the desktop. 

I tried this command:

```
sudo service gdm start
```

But it replies that it is already running. 

What command is needed to get it to go to the desktop? Do I need to install the nvidia driver in order for the video integrated in the motherboard to work again?

---

### Post by jockyburns on 2011-12-01
Can you enter bios when you start your computer up? If so have a look around there. It could be that the bios is set up to use a graphics card and not the onboard graphics. I've had a similar problem recently when my graphics card stopped working. When I removed it and used the onboard graphics card, I got the boot screen then absolutely nothing, as the computer was trying to use the non existent PCIe Graphics card. I entered the bios settings and changed the graphics to use the onboard instead of the PCIe card. 
Usually when your computer starts, you get an option screen which tells you to press an F key to enter bios or boot menu (Mine is F2 for bios, or F11 for boot)

---

