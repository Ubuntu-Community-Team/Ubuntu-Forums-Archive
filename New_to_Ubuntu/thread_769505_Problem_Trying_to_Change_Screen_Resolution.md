---
title: "Problem Trying to Change Screen Resolution"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by jon8105 on 2008-04-26
Hey guys, I am a "fresh meat" Linux user (just installed Ubuntu 8.04 AMD64 last night), and so far everything has been going good.  I got Compiz Fusion cube and advanced effects running, which is fun to play with BTW.

Anyways, the problem I am having is when I go to System->Preferences->Screen Resolution a window pops up that says "The X Server does not support the XRandR extension.  Runtime resolution changes to the display size and are not available."

Is this because of me setting up The Cube?  Is there anyway I can fix this?  Thanks for any help.

---

### Post by jon8105 on 2008-04-26
Ok, I am able to change my Screen Resolution after I reconfigured my X Server:
```
sudo dpkg-reconfigure xserver-xorg
```

However, when I set back up my advanced desktop settings by first running
```
sudo apt-get install xserver-xorg

```
and then by running
```
compiz
```

I am able to get my advanced desktop settings to work again but the pop up window error shows up again when I try and change my resolution size.  I am assuming that because of using the Compiz Fusion advanced settings I have to change my resolution some other way besides going to System->preferences->Screen Resolution?

It is fine the way it is, I am just trying to figure out what is going on.  Any clue?

---

### Post by nicedude on 2008-04-26
right click on the desktop and go to change desktop background then once open click on visual effects now try to choose EXTRA if it says no then something is not right with your card & driver so post the info for that here.

---

### Post by nicedude on 2008-04-26
Also while I have not switched to hardy yet I see that the System->administration->screens&graphics is now under Applications-> System "I think" so try there as well.


Hope that helps

---

### Post by jon8105 on 2008-04-26
Yes, it lets me choose extra.  However, when I do it cancels my advanced settings using the "Desktop cube."  When I check "Desktop Cube" again it goes back to all circles being empty on the "Visual Effects" tab.  I am assuming this is suposed to happen because I am overwriting the "Visual Effects" from the "Appearance Preferences" with the "Advanced Desktop Settings?"

---

### Post by jon8105 on 2008-04-26
Screens & Graphics is now under Applications->Other

Edited:  I forgot to say that by going there (Screens and Graphics) I am able to change the resolution and still keep my Advanced Desktop Settings.  Thanks for your help. (I am still a noob.)

---

