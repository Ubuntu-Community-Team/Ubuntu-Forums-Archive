---
title: "Unable to start the GUI"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by Google Spider on 2008-05-04
whoa! I've been using Hardy since when it was released and today when I start my computer it says:

> 

Frequency out of range


Please lower the resolution or read your monitor's manual](*,)


I wonder how this happened all of a sudden :(

I have ATI radeon xpress 200 card and had been using compiz fusion pretty well :guitar:

what do i do now? ( I don't think I have the monitor's manual so don't tell me to RTFM :biggrin: )

I don't know how to change my resolution from CLI..

Thanks for your time

---

### Post by seshomaru samma on 2008-05-04
to reconfigure the Xserver (the GUI) run this command:
```
sudo dpkg-reconfigure xserver-xorg
```

I would suspect there is some problem with the ATI driver , hopefully lowering the resolution will give you access to the GUI so you can fix it from there

---

### Post by Google Spider on 2008-05-04
> **seshomaru samma said:**
> to reconfigure the Xserver (the GUI) run this command:
```
sudo dpkg-reconfigure xserver-xorg
```

I would suspect there is some problem with the ATI driver , hopefully lowering the resolution will give you access to the GUI so you can fix it from there

That command gave me some options to change settings related to my keyboard, not the resolution or anything. I can get into the GUI using "failsafe Gnome". 

All I could do here was to change the refresh frequency from 85 Hz to 75 Hz...resolution was already 1024 x 768, which I had been using with Ubuntu and other OSs ( mint and xp). Looks like I cannot login with normal Gnome to enable the 3D effects. It gives me a white screen.

---

### Post by philinux on 2008-05-04
You cannot use the reconfigure xorg command in hardy for display problems it does not work.

In failsafe mode I would disable all desktop effects and then reboot.

There is a command from recovery called xfix but I've never used it so can't comment on it's use.

---

### Post by seshomaru samma on 2008-05-05
> You cannot use the reconfigure xorg command in hardy for display problems it does not work.
really? that's unusual (still on Gutsy here)
there must be some alternative
i guess the failsafe mode is the option i would go for it

---

