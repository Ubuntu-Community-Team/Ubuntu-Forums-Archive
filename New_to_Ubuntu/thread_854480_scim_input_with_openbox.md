---
title: "scim input with openbox"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by theRightNee on 2008-07-09
just installed the openbox window manager but i am now having issues with SCIM input (when i type the chinese pinyin i do not get the chinese word desired) is there some connection between the two>

---

### Post by ChameleonDave on 2008-07-10
> **theRightNee said:**
> just installed the openbox window manager but i am now having issues with SCIM input (when i type the chinese pinyin i do not get the chinese word desired) is there some connection between the two>

I suppose you had SCIM working correctly in GNOME before, right?

With Openbox, you can enter an actual Openbox session, or you can run a GNOME session but using Openbox instead of Metacity.  Which in which cases does it fail for you?  Is it now failing even in default GNOME?

---

### Post by theRightNee on 2008-07-10
i am using openbox only...and more specifically when i enter the pinyin, the wrong characters show up, which to me means its SCIM, but i cannot figure out whats wrong

---

### Post by ChameleonDave on 2008-07-10
> **theRightNee said:**
> i am using openbox only...and more specifically when i enter the pinyin, the wrong characters show up, which to me means its SCIM, but i cannot figure out whats wrong

There are many input methods available in SCIM, including some strange ones based on the shape of the character rather than its pronunciation.  It sounds to me like you have the wrong one enabled — not actually a SCIM error.

---

### Post by urukrama on 2008-07-10
Have you seen [the page about autostarting apps]("http://icculus.org/openbox/index.php/Help:Autostart") in Openbox on the Openbox Wiki? It tells you how to properly start scim in Openbox. Perhaps that will solve the issue.

---

