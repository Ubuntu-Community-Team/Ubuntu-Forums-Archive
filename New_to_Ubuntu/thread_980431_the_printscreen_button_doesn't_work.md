---
title: "the printscreen button doesn't work"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by afeasfaerw23231233 on 2008-11-12
both the printscreen button on the keyboard and the utility Applications -> Take screenshots don't work.
thanks

---

### Post by tuxxy on 2008-11-12
Could you give more info like what happens when you click take screenshot, it should appear allowing you to save and rename.

---

### Post by afeasfaerw23231233 on 2008-11-12
After i clicked the take screenshot button or pressed the printscreen button on the keyboard the cursor changed to a little "clock-like" circle for half a second and then nothing happened.

---

### Post by afeasfaerw23231233 on 2008-11-13
bump

---

### Post by Kellemora on 2008-11-14
Hi af

If you HAVE the Save Screenshot program loaded, you will get the ability to save the screenshot.
If NOT, then PrntScrn saves the screen to your clipboard.

You can test this by copying some text from a program, then from something else on the screen hit the PrtScr button.
Now, go and paste and see whether you get the text you copied first or an image of the screen from print screen.

If you got the text, then save screenshot is loaded and running.
If you got the image pasted, then save screenshot is NOT loaded.

It has a weird name I can't remember off the top of my head right now, something like Rigdon or Reggea, sorry, maybe somebody else can remember the name of it.

You can try ALT PRTSCR also, but this should only save what's in the window box your arrow is sitting in.

There IS a configuration file for Gnome-Screenshot somewhere, you can set it to not bring up the pop-up I think, maybe this has happened?

Good Luck

TTUL
Gary

---

### Post by afeasfaerw23231233 on 2008-11-29
No matter I press the PrtScr button or click Applications -> Accesories -> Take screenshot, it would only paste the text. But right after I press the PrtScr button or click Applications -> Accesories -> Take screenshot, the cursor of the mouse would change to a "busy clock" for 0.5 second. 
My OS is Ubuntu 7.10. Anybody knows what's the problem? I am a linux noob. Thanks!

---

### Post by afeasfaerw23231233 on 2008-12-01
bump

---

### Post by afeasfaerw23231233 on 2008-12-08
bump

---

### Post by Farmer of Bricks on 2008-12-08
Right after hitting PrintScreen, try opening GIMP or another image editor and pasting into a blank document.

---

### Post by afeasfaerw23231233 on 2008-12-08
GIMP said there was no image data in the clipboard to paste.

---

### Post by afeasfaerw23231233 on 2008-12-12
bump again

---

### Post by afeasfaerw23231233 on 2008-12-14
bump

---

### Post by LordIshamael on 2008-12-14
have you tried ksnapshot?i dunno what you need the printscreens of but if its not fullscreen then try it out, might help
just open it, it opens up a window with the snapshot and asks to save just like a regular application, no need for shortcuts or the prntscrn button

---

### Post by Kellemora on 2008-12-14
Hi af

This IS a known bug on some computers!

Ubuntu apparently now looks to console-setup, not console-data like it did previously.
But on some machines I think it gets it's keymaps from xkeyboard-config instead of console-setup.

Most of my computers are built-ups, but one older Compaq I have here, print screen did not work on either.  I tried putting Compiz-fusion on that machine, but it didn't have a powerful enough graphics card so I uninstalled Compiz.  However, in it's wake it must have left behind some file somewhere because after that PrintScreen would open a KDE based program to save the screenshot, not the Gnome screen I get on the rest of the computers.

Hope that explains a little of what's going on!

TTUL
Gary

---

