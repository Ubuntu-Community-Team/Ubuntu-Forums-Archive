---
title: "ATI Card Problems"
date: 2008-09-20
forum: New to Ubuntu
---

### Post by Unanimated on 2008-09-20
EDIT: lspci -nn | grep VGA reports my graphics card to be:
```
00:08.0 VGA compatible controller [0300]: ATI Technologies Inc Rage 128 PP/PRO TMDS [Xpert 128] [1002:5050]

```
Which, of course, is discontinued by ATI. Great. 

My old, trusty NVIDIA card recently failed on me, so I installed a spare ATI card lying around the house. However, my problem is that I can't find a driver for it. Ubuntu doesn't list a proprietary driver, and Envy can't detect my card model. The card is Rage something, I can't remember the rest. When I went to the low-graphics mode setup screen, my driver was listed, but it's not listed on the ATI site. Help?

---

### Post by overdrank on 2008-09-20
Hi and yea the graphics card it old and should be supported with the driver that comes with Hardy. If you are having issues I would use the xfix option when booting to recovery mode. This should correct any issues with the resolution but I doubt the card can handle any 3d.

---

### Post by Unanimated on 2008-09-20
Yeah, it can could barely handle the simple 3D in my other screensaver, and Frets On Fire is almost unplayable, which is a real bummer.

---

