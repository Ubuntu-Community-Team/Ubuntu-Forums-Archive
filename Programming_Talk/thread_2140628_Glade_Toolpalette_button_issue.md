---
title: "Glade: Toolpalette button issue?"
date: 2013-04-30
forum: Programming Talk
---

### Post by fallenshadow on 2013-04-30
So recently I have changed up the toolpalette on my program. Ive become more and more frustrated with the quirks of Glade and I don't understand why this is happening. All I have done is added a new group above the "Tools" one and everything just goes haywire.

[ATTACH=CONFIG]241987[/ATTACH]

Any ideas as to how I can solve this with Glade? I want the "Tools" buttons to still be in two columns.

---

### Post by fallenshadow on 2013-05-01
Right I have gotten closer I think, but still not there yet.

[ATTACH=CONFIG]242041[/ATTACH]

The buttons are now made 32x32 but somehow they still display in a vertical line despite more than enough room for 2 columns. Is this a bug with GTK or what?

Im seriously considering putting my fist through the monitor or switching to QT at this point. T_T

---

### Post by alexfish on 2013-05-01
Have you tried to reduce the size of the images from 32 to  '22px or 16px

see what happens

can use convert from the command line to alter images

HTH

Alex

---

### Post by fallenshadow on 2013-05-02
Thanks for the suggestion!

The icons are smaller now but that didn't affect the layout of them. :/

[ATTACH=CONFIG]242079[/ATTACH]

I have noticed if I remove the Colours toolpalette group it will go back to the proper layout but I do need/want 2 colour selection buttons above it.

---

### Post by fallenshadow on 2013-05-02
Seems its solved for now. The trick is to not use a toolpalette group for the colour buttons. Instead use a "box" above the toolpalette. :)

---

