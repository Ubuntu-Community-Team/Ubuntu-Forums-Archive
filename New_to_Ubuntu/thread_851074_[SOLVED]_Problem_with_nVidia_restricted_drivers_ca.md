---
title: "[SOLVED] Problem with nVidia restricted drivers: can't set screen resolution above 10"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by Flaphal on 2008-07-06
The title says it all really. Without the driver I can set the screen res how I like, with it I can't set it above 1024x768.

Graphics card: nVidia Geforce 8800GTX 
Ubuntu: 8.04, 32bit (wubi)

Every guide I have found that looks like it might fix this has been either years out of date or far too technical (the only thing i can do with the terminal is copy/paste :) ) so I hope you guys have a solution... this res sucks. 

Thanks in advance!


Edit:
One more think that might be useful: my screen is not recognised.

---

### Post by Teber on 2008-07-06
think this might be helpful.

in menu system/preferences/main menu add under other screen and graphics. this should then appear under applications/other

i had a similar issue and resolved it using screen and graphics.

good luck!

---

### Post by ellgor on 2008-07-06
Hi,
 You could try this, open a terminal and type in     gksudo-nvidia-settings  this will bring up a new window for changing the nvidia settings, adjust to suit, hope this helps.

Regards, Ellgor.

---

### Post by Flaphal on 2008-07-06
> **ellgor said:**
> Hi,
 You could try this, open a terminal and type in -  gksudo-nvidia-settings - this will bring up a new window for changing the nvidia settings, adjust to suit, hope this helps.

Regards, Ellgor.

Fantastic! Thanks a lot.

Didn't work at first, but then I installed "nvidia-settings" in the SPM and typed instead "gksudo nvidia-settings" (minus the first - )

[I]
(I think this may have something to do with my screen being recognised... nvidia-settings recognises it, the normal resolution settings thing doesn't, and still cant change the setting)[/I]

---

### Post by calvin6 on 2008-09-04
> **Flaphal said:**
> Fantastic! Thanks a lot.

Didn't work at first, but then I installed "nvidia-settings" in the SPM and typed instead "gksudo nvidia-settings" (minus the first - )

[I]
(I think this may have something to do with my screen being recognised... nvidia-settings recognises it, the normal resolution settings thing doesn't, and still cant change the setting)[/I]

hey i'm having the same problem. i tried the gksudo nvidia-settings in terminal but nothing happens. i get a prompt that asks for password. i enter it but then it just goes back to the terminal and nothing has opened up. maybe it has something to do with where you said you "installed nvidia-settings in the SPM" I didn't do this. what is SPM? and how do i install it? i'm an oober noob with linux. first try so any dumbed down help would be greatly appreciated. thank you

---

### Post by philinux on 2008-09-04
system>admin>synaptic.

or
```
 sudo apt-get install nvidia-settings
```

---

### Post by calvin6 on 2008-09-04
yaaaay i got it. i'm definitely a giddy little school girl at the moment. thank you very much!!  :)

---

