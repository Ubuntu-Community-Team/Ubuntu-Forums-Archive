---
title: "White Screen!"
date: 2008-07-10
forum: New to Ubuntu
---

### Post by bikinguy77388 on 2008-07-10
Hi Guys,

Been a few weeks but got my new used computer in. Thought I would load kubuntu using wubi to ck it out.

Setup went great and as I have a 256 meg ati card thought I would download compiz and customize the desktop. 

I activated it and my whole screen turned white with just the mouse pointer showing. I just logged off and back on same thing.
Then I did a total reboot logged in and again the white screen.


Any suggestions ?

---

### Post by DGortze380 on 2008-07-10
Enter the grub menu while booting and boot in either safe graphics mode or recovery mode (not sure that the options are in kubuntu) and uninstall compiz.

---

### Post by Canis familiaris on 2008-07-10
Disable Compiz by KWin

```
kwin --replace
```

---

### Post by bikinguy77388 on 2008-07-10
thanks guys

I just deleted the os and installing ubuntu.

---

