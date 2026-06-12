---
title: "Wine and Mathtype"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by mwf on 2008-04-27
OK, 8.04 is working well and I got the wireless problem sorted out by reinstalling everything. No one knew what was happening! Anyway...

I am so close, just one more problem. I installed Mathtype 6 using Wine. I was very surprised as I know nothing about Wine! So, that went very well. It starts up and runs fine except... it can't find the fonts it needs so most of the symbols are unavailable!

I got desperate and copied all my XP fonts (MathType is installed on XP as well) to the existing /usr/share/fonts/truetype folder. I even did a chmod 777 on all the fonts. But MathType can't see them.

If I can get MathType to run, then Ubuntu will replace a Windows Vista machine. This latest 8.04 version runs like a charm, much much faster than Vista. I can move XP to my Vista laptop and run Ubuntu full time on this desktop.

Please don't suggest Latex, I teach physics and need something better than the stunningly primitive OO Math product yet still a fast point and shoot. MathType fits the bill perfectly.

Thanks for any help.

---

### Post by mwf on 2008-04-27
Good grief, it hit me like a pile of bricks! I solved the problem myself. I noticed, while aimlessly browsing, that Wine has it's own fonts folder in the Wine c_drive folder. I moved all the fonts there, did a chmod 777 for all of them (the only way they work for this) and then "reset to factory settings" under the fonts choice in MathType. Now, it works as expected!

Wine for Ubuntu, now some wine for me.

MathType 6 downloaded from web site, Ubuntu 8.04, Wine downloaded using Synaptic PM. 

Ubuntu may have come of age, for me at least.

---

### Post by forrestcupp on 2008-04-27
Good job.  It's good to keep those fonts in your /usr/share directory for native Linux apps, too.

---

### Post by correaa on 2009-08-31
If you need only the Mathtype fonts and not Mathtype you can download them from [http://www.dessci.com/en/dl/DS_Fonts_6.5c_(TT).exe](http://www.dessci.com/en/dl/DS_Fonts_6.5c_(TT).exe) and use 'cabextract' to get them.

Then put the fonts files in ~/.fonts/

---

