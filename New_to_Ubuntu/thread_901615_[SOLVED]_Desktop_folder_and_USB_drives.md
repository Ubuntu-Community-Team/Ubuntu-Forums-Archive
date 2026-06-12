---
title: "[SOLVED] Desktop folder and USB drives"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by Pa100ka on 2008-08-26
Ubuntu 8.0.4 on a bog standard laptop.

I'm just curious about this one. When I mount a USB drive, an icon appears on my desktop. But when I go into /home/<username>/Desktop in terminal, and do ls -a, there is nothing. How so? What is going on under the hood?

It's not a big deal, but one of the things which attracted me to Ubuntu was its straightforwardness and transparency, as opposed to the Windows "You don't need to know that; Nanny knows best" paradigm.

Thanks,
Pa100ka

---

### Post by PurposeOfReason on 2008-08-26
That is because nautilus draws mounted icons on the desktop. It's not the real location. You can turn it off if you want.

---

### Post by Pa100ka on 2008-08-26
Thanks for the advice. I know this is stupid, but I have been into Nautilus and chosen Edit -> Preferences. There were many options, but none seemed to control whether or not newly mounted media is displayed as an icon on the desktop. Would you mind amplifying a little for the benefit of the uninitiated?

Thanks,
Pa100ka

---

### Post by PurposeOfReason on 2008-08-26
Sure. In a terminal type 'gconf-editor'. Browse to apps - nautilus - and look in there. Should have something about mounted volumes.

---

### Post by -Zeus- on 2008-08-26
the location of the usb drive is /media/something

---

### Post by Pa100ka on 2008-08-27
> **PurposeOfReason said:**
> Sure. In a terminal type 'gconf-editor'. Browse to apps - nautilus - and look in there. Should have something about mounted volumes.

Yes, got it. Very many thanks for your help.

Palooka

---

