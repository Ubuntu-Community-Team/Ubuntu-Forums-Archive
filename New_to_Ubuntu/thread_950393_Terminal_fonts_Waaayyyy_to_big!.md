---
title: "Terminal fonts Waaayyyy to big!"
date: 2008-10-17
forum: New to Ubuntu
---

### Post by BillyBlaze on 2008-10-17
Okay I have most everything set up here on my new linux machine here with the exception of one thing. When I log into terminal and I mean TRUE terminal (ctrl alt f1-f6) the fonts are huge. So big that I can only enter my user name then password after that I can't see anything else on the screen. 

I've combed through the forms to find a answer and came up empty handed. 

Is there somebody out there that can help me?

Thanks.

---

### Post by philinux on 2008-10-17
Easy gui way.
Install from synaptic or
sudo apt-get install startupmanager

Run it from the sys>admin menu

Change the display resolution there. It affects usplash and tty.

---

### Post by prshah on 2008-10-17
> **BillyBlaze said:**
> the fonts are huge. 

when booting, press esc to enter the GRUB menu; scroll to the usual booting option, but press "e" instead of enter. Scroll down to the second (?) line (the one that starts with "kernel") then press "e" again to edit it. At the end of the line, add the phrase
```
vga=771
```

then press enter; then "b" to boot.

This should put it in regular text mode (80 x 25); if it doesn't, repeat the above process and change "vga=771" to "vga=ask".

If either of these work, post back on how to make it permanent.

---

### Post by philinux on 2008-10-17
This is what startupmanager does.:)

---

### Post by BillyBlaze on 2008-10-17
Thanks for the help. Worked out great

I can finally make out the words. 

The fonts are still kinda big for my liking. Is there a way to make them even smaller? or maybe with higher resolution? It just looks so basic.

Thanks again.

---

