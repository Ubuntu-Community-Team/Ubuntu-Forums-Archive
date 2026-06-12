---
title: "Emerald"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by hungryOrb on 2008-05-28
Hi!
I broke emerald :( I changed my exit button graphic, and cant change it back! Does anyone know if there is a restore factory settings option? 
EEEK!

---

### Post by mevets on 2008-05-28
If you change the theme then change back to your broken theme you lose any changes you made. This could restore the graphic you changed.

---

### Post by sayakb on 2008-05-28
Did you save the new theme? Do you have some other emerald theme. What is the theme that you are using?

---

### Post by iaculallad on 2008-05-28
To reset the settings you could try this: exit emerald first then input this on your terminal.:

Code:

```
sudo rm .emerald/settings.ini
```

---

### Post by hungryOrb on 2008-05-28
Thankyou guys and Guardian Iacu,
Iacu, unfortunetly I don't think that solution restored the buttons that I may have destroyed (.png's). When first messing with emerald, I hastened to click 'clear' which seems to have truly cleared the button from the list.. Not just currently used graphic ;D
Tried a complete removal and reinstall, but it keeps the old settings :/ and doesn't seem to restore the button .png's to their rightful place.. 
Hmm.. I wonder why the clear button is so devastating :(

---

### Post by sayakb on 2008-05-28
Reinstalling emerald won't do. I guess you need to download and install the theme you are using again. The theme should be in .emerald format and you can press Import at emerald and install it.

---

### Post by iaculallad on 2008-05-28
Ok :) I thought of resetting the settings to keep emerald on track :confused:

---

### Post by hungryOrb on 2008-05-28
> **LinuxIsInnovation said:**
> Reinstalling emerald won't do. I guess you need to download and install the theme you are using again. The theme should be in .emerald format and you can press Import at emerald and install it.

Thanks, although, there was no theme as such.. There was no theme in the list, but the basic emerald additions were visible. And they looked nice, but then I went and pressed clear, and the .png's went bb.

---

### Post by sayakb on 2008-05-28
> **hungryOrb said:**
> Thanks, although, there was no theme as such.. There was no theme in the list, but the basic emerald additions were visible. And they looked nice, but then I went and pressed clear, and the .png's went bb.

In that case, maybe reinstalling emerald might work for you.
Do:
```
sudo apt-get purge emerald
sudo apt-get install emerald
```

---

### Post by hungryOrb on 2008-05-28
> **LinuxIsInnovation said:**
> In that case, maybe reinstalling emerald might work for you.
Do:
```
sudo apt-get purge emerald
sudo apt-get install emerald
```

Thanks for help ;] doesn't seem to work though :(

---

### Post by sayakb on 2008-05-28
Download more good looking emerald themes from [here]("http://gnome-look.org/index.php?xsortmode=high&page=0&xcontentmode=103").

---

