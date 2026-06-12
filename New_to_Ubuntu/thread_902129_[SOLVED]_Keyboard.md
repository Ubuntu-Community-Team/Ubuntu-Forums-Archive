---
title: "[SOLVED] Keyboard"
date: 2008-08-27
forum: New to Ubuntu
---

### Post by gunner ra on 2008-08-27
Hi Guys I recently pressed recovery mode by mistake on boot up. I found that my keyboard had reverted to US. I.E. """ instead of @@@' I thought that the keyboard had reverted to the default US? However it was still showing UK as default. I had to re-install US layout as the default, then add UK and delete US. Any ideas as to why this should have happened Guys. Thanks Gunner RA

---

### Post by Elfy on 2008-08-27
I had a similarly odd problem with the keyboard layout going awol.

I added the alyout I need in my xorg and have had no problem since.

> Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    [COLOR="Red"]Option         "XkbLayout" "uk"[/COLOR]

---

### Post by gunner ra on 2008-09-03
Hi Forestpixe I must apologise for the delay I have been away. I followed your suggestion. Thanks issue solved Gunner RA

---

