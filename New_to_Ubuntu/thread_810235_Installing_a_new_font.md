---
title: "Installing a new font"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by heiowge on 2008-05-28
I use this font as well as Berlin Sans in a few documents that I want to add to:

[http://www.findfreefonts.net/fontweb/font/9919/Air-Millhouse--Italic/view.aspx](http://www.findfreefonts.net/fontweb/font/9919/Air-Millhouse--Italic/view.aspx)

I edit these documents in Word atm, but I want the option to add to them in OOo Writer.

The problem is that the fonts are not recognised (Berlin Sans may be - can't remember, but Air Milhouse Italics isn't!).

If I edit then save, I'll have to change everything in Word, and it's less effort just to switch over to XP (which I'd rather not do!).

Can I install this (these?) fonts to use in Ubuntu?  If so, how?

---

### Post by sayakb on 2008-05-28
At a terminal:
```
gksudo nautilus
```
Now make a new folder called MyFonts at /usr/share/fonts/truetype
Copy these fonts to /usr/share/fonts/truetype/MyFonts
But make sure that the font extensions are "ttf" (all in small letters, no block letters)

---

### Post by heiowge on 2008-05-28
Done, but it still doesn't use the font!  Any suggestions?

---

### Post by sayakb on 2008-05-28
Just reboot. It will show-up in OO.

---

### Post by iaculallad on 2008-05-28
> **heiowge said:**
> Done, but it still doesn't use the font!  Any suggestions?

If you're using 8.04, try this:

Open you're home folder, press Ctrl+H to show all hidden folders (or you could just click on the View->Show Hidden Files). Locate **.fonts** folder, if its not there, create a folder named .fonts (that is with a period). Once created, open .fonts folder and paste/copy that TTF font you want to use. The font will be automatically loaded to the application that will be using it.

---

