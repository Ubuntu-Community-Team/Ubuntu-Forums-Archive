---
title: "Font path disappears on restart"
date: 2011-09-09
forum: New to Ubuntu
---

### Post by peterson43 on 2011-09-09
I am running Ubuntu 11.04 on my desktop computer. I can use Mathematica on the school network if I ssh -X into the school network. However, in order to get Mathematica to run correctly on my computer, I need to add the mathematica fonts. 

I saved the fonts to a folder in my home directory. In order to add the fonts to my X server I run 
```
 
xset fp+ /home/peterson/MathematicaFonts/Type1/,/home/peterson/MathematicaFonts/BDF/

```

If I then type
```
xset q
```
I see that these font paths have been correctly added, and when I try to run Mathematica through ssh -X things work fine. 

However, if I turn off my computer, when I re-start it I can no longer run mathematica through ssh -X, and if I check my font paths using 'xset q' I no longer see the Mathematica fonts listed. How can I get the Mathematica font paths added to my X server on a permanent basis so that I don't have to add them again every time I restart my computer.

---

### Post by Enigmapond on 2011-09-09
You may have to copy them into /user/share/fonts either that or update the font cache by running:

```
sudo fc-cache -f -v
```

Or both.. :)

---

### Post by peterson43 on 2011-09-09
> **Enigmapond said:**
> You may have to copy them into /user/share/fonts either that or update the font cache by running:

```
sudo fc-cache -f -v
```

Or both.. :)

I tried all combinations of the above and it didn't work. First I just updated the font cache. Then I just moved the MathematicaFonts folder to the /usr/share/fonts/ folder, and then I did both. Every time when I re-started the computer the MathematicaFonts don't appear when I run 'xset q'. 

Any other ideas?

---

### Post by peterson43 on 2011-09-09
I just noticed that the font paths also disappear when I log out, not just when I turn the computer off.

---

### Post by peterson43 on 2011-09-12
I've created a temporary fix to the problem. I created a keyboard shortcut (Ctrl+Alt+f) that runs the xset fp+ command that sets the Mathematica font paths. This is a nice quick way to add the font paths, but I still would like to figure out why the font paths disappear when I log out.

---

