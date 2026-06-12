---
title: "how to make text not look tiny in firefox?"
date: 2014-09-12
forum: New to Ubuntu
---

### Post by Saffo on 2014-09-12
hey so i just switched to ubuntu a few months ago, and i am still figuring a lot of things out.

i used to use a mac, and i never had any trouble with the fonts in firefox. but for some reason the default setting for most pages in firefox makes the letters look absolutely tiny. they are not unreadbly small, just annoyingly small.

i adjusted the controls and now sometimes things look too big. also i dont know any of the fonts on here, so i am not sure which to choose. i dont really want to uncheck "allow pages to choose their fonts" as i feel like that would probably just make most webpages look messed up. i just want things to not look tiny! how do i make firefox on ubuntu display pages more like they do on a mac? it feels like i always have to either squint or magnify the view on any page.

also, fwiw i'm using 14.04 on a system76 computer.


[ATTACH=CONFIG]256416[/ATTACH]

---

### Post by vasa1 on 2014-09-13
Have you tried playing with the "Minimum Font" size?

---

### Post by SeijiSensei on 2014-09-13
I usually just zoom the page to a font-size I prefer by holding down Ctrl and scrolling the mouse button.

---

### Post by uRock on 2014-09-13
> **SeijiSensei said:**
> I usually just zoom the page to a font-size I prefer by holding down Ctrl and scrolling the mouse button.

I use Ctrl and the + or - keys. Either way gets it done.

---

### Post by mcduck on 2014-09-13
Minimum font size helps, and you can also use the NoSquint extension to set default zoom levels for each site...

---

### Post by kostkon on 2014-09-13
The Electron font is definitely not the default setting. It's true that most pages define their own fonts so that font is not used that often, but I'm just saying.

---

### Post by buzzingrobot on 2014-09-13
Try setting the minimum font size at 12.

The key factors are the dimensions of the display you are using and its resolution.  Text displayed in the same font size will look smaller as resolution increases and display size remains the same; it will also look larger as resolution remains the same and display size increases.  And, vice versa.

That said, you are likely using a 1920x1080 display on a laptop.  Font size would be visibly smaller than on a Macbook with slightly less resolution, but not to the point of being difficult to read.

Playing with fonts in Firefox really won't affect much because, as you note, sites typically set the fonts used in their display in their CSS, including use of downloadable fonts. Also note that "Sans" and "Sans Serif" are generic labels mapped to a specific font family.  E.g., if memory serves, Sans maps to DejaVu Sans on Ubuntu. Typically, Sans will be the last, catch-all, font-family specification in a site's CSS.  E.g., "Arial, Helvetica, sans-serif" is a very common specification. Text would default to display in Arial on any machine with Arial installed, i.e. Windows.  On Macs without Arial installed, it would be Helvetica, and then the catch-all of Sans-Serif for anything else.

---

