---
title: "Wrong Settings For Keyboard"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by BennyHill on 2008-05-12
Hi, I just installed Ubuntu for my uncle, on his PC, but I must have selected the wrong Keyboard settings as its coming up with the wrong symobls and the @ key at the wrong button for us UK users. 

So I changed the settings for the keyboard and scim input method which had USA there, to UK but they work then, but everytime I restart the PC and it loses its settings though UK is still in the keyboard settings as the only layout.

Is there anything I can do to remove the US settings for once and for good, many thanks in advance.

---

### Post by philinux on 2008-05-12
So you've been into system Prefs Keyboard and selected and tested the one you want?

---

### Post by BennyHill on 2008-05-12
yep, but it just never saves right.

---

### Post by Inxsible on 2008-05-12
> **BennyHill said:**
> yep, but it just never saves right.you may have to use gksudo on the application to save the settings.

Create a launcher for the app, by right clicking on it and then selecting Create Launcher (I think -- forgive me if i am wrong, I am currently @ work on XP) But it should be obvious.

Once you have the launcher, right click and select properties and see the exact command for the app. Use ```
gksudo <command-name>
``` in a terminal and see if that works and saves the appropriate keyboard layout for you.

---

### Post by Het Irv on 2008-05-12
If you are only going to change it once, wouldn't it be easier to just type that command into the terminal.  You will just have to remember to use that everytime.

---

### Post by okey666 on 2008-05-12
I had the same problem. What I did was go system>>preferences>>Keyboard>>Layouts>>add

after I had added the UK one I deleted the USA one.

You may have done this I could just not make it out from the text above.

---

### Post by Timpotten on 2008-05-15
The reason to join this forum was that my cheap USB wireless keyboard, which had worked fine the session before, was not recognized on startup. 
(I have "Hardy Heron" with latest updates). 
I tried an old PS2 keyboard (round plug) which works, but only as a USA layout (mine is Spanish) Keyboard preference sets to other languages but is always USA despite other language indicated on Preferences>Keyboard tag. 
I think this may be an old problem come back to haunt Ubuntu?

---

### Post by Timpotten on 2008-05-15
OK, Deleting USA works but it is a fix, not a cure.

---

### Post by Timpotten on 2008-05-16
Well, it worked yesterday! Today we are back with no USB keyboard and a USA layout, plus, the keyboard selection changes colour OK, but the radio selector/indicator buttons do not work (they were all blank). By deleting everything and installing just the Spanish keyboard, both the Spanish layout and the USB keyboard now work correctly. But must this be a daily chore? :(

---

### Post by Timpotten on 2008-05-19
Every day now it finds the USB keyboard, but the Spain preference radio/button is not lit (all others are deleted), and will not light up. 

Delete Spain and reselect Spain works to change the keyboard, but the radio button still does not work under any trick I can think of. 

I am so fed up I am going to reinstall the entire system! This minor irritation put me off Ubuntu completely if it persists after a whole system reload.

---

### Post by GavinZac on 2008-05-19
i'm having the same problem, my keyboard layout - English (Ireland) - won't stick. I have to remove and re-add it every time the computer restarts. The layouts arent that much different but I miss my &#8364; sign.

---

### Post by Het Irv on 2008-05-19
Check your xorg file to see if it is saving the keyboard settings there.
```
gksudo gedit /etc/X11/xorg.conf
```

On mine the first uncommented block of code is the keyboard, which the last line being the keyboard's layout.  If you can find the two character code for the setting you want you should be able to change it there and it would stick.

---

### Post by BennyHill on 2008-05-25
Many Thanks Hat Irv, the code seems to do the trick for him though he still has no £ key, but @ etc is all back where it should be.

Btw, you mis-spelt etc so it should be:-

```
gksudo gedit /etc/X11/xorg.conf
```

Thanks very much

---

### Post by Het Irv on 2008-05-26
> **BennyHill said:**
> Many Thanks Hat Irv, the code seems to do the trick for him though he still has no £ key, but @ etc is all back where it should be.

Btw, you mis-spelt etc so it should be:-

```
gksudo gedit /etc/X11/xorg.conf
```

Thanks very much

argggablargablargablarg

Thanks for the typo catch.  I do that every single time I have to type ect.... etc.

---

