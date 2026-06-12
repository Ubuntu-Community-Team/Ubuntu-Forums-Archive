---
title: "Macbook resolution wrong"
date: 2008-10-06
forum: New to Ubuntu
---

### Post by ricky0319 on 2008-10-06
I configured my xorg.conf file. I realize now this was a bad idea. My display is not detected and my resolution is set at 800x600. On the screen resolution option screen it says my display is unknown and it gives me no other resolution options. I have seen online sudo dpkg-reconfigure xserver-xorg to default to the old file, but this has not worked. Any help would be appreciated. I am using a Macbook with Hardy Heron.

---

### Post by Ryadt on 2008-10-06
Did you enable your graphic card?

---

### Post by ricky0319 on 2008-10-06
How do I enable the graphic card?

---

### Post by Ryadt on 2008-10-06
Go in System > Administration > Hardware Drivers and then select your graphic card.

---

### Post by ricky0319 on 2008-10-06
My graphics card does not show up in the list. Only my wireless card is there.

---

### Post by overdrank on 2008-10-06
> **ricky0319 said:**
> I configured my xorg.conf file. I realize now this was a bad idea. My display is not detected and my resolution is set at 800x600. On the screen resolution option screen it says my display is unknown and it gives me no other resolution options. I have seen online sudo dpkg-reconfigure xserver-xorg to default to the old file, but this has not worked. Any help would be appreciated. I am using a Macbook with Hardy Heron.

Hi and you may try using the command with the alt, F2 keys ```
gksu displayconfig-gtk
```
There you can setup your graphics.

---

### Post by ricky0319 on 2008-10-06
Im trying to set it up, but it cant detect my display and when I click on one it asks for a driver. I can't locate this driver.

---

### Post by ricky0319 on 2008-10-06
When I start my computer it goes into low graphics mode because it cannot detect my graphics card or display. I have tried to manually select my graphics card and display and it still does the same thing.

---

### Post by overdrank on 2008-10-06
> **ricky0319 said:**
> When I start my computer it goes into low graphics mode because it cannot detect my graphics card or display. I have tried to manually select my graphics card and display and it still does the same thing.

Ok I have not used a mac but have you tried the xfix option when booting into recovery mode which is usually the second choice from the grub.
What is the model of the graphics card as you can use the command lspci and look for VGA.

---

### Post by waspbr on 2008-10-06
to alter the screen resolution use the command given above by overdrank. On the screens section you try to select your manually (browse) select a generic LCD screen of the size you want (remember to check the widescreen box at the bottom). This should enable you to choose the appropriate resolution. 

As for the graphics card, well, one thing at a time

---

### Post by ricky0319 on 2008-10-06
okay i was able to fix the resolution to 1024x768. 1280x800 will not work at the moment.

---

### Post by ricky0319 on 2008-10-06
Now how do I get it to recognize the graphics card?

---

