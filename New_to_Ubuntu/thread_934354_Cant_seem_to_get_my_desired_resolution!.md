---
title: "Cant seem to get my desired resolution!?"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by thetimer on 2008-09-30
Hello friends, 

I have installed ubuntu a few weeks ago, but seem to be stuck in 800x600 resolution for GNOME.   I have tried numerous things, I have verified it is using the correct Nvidia drivers, however when I try to setup my "monitor" it does not have any option for my monitor, so I am left with a generic list of resolutions, 800x600 being the highest, which I know this video card is capable of farrrr better resolutions.       My monitor is an old IBM P260, but that does not appear to be on the list when trying to setup my display.   

Any ideas how I can change my resolution? I have tried everything I can think of and I am only able to set it to 800x600 or 640x480

Any help would be great. 

thanks!

---

### Post by Ryadt on 2008-09-30
Try ```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by thetimer on 2008-09-30
Well I tried that, as well as using the Screens and Graphics utility, neither of which seem to work.. I am wondering if its something else?   I dont quite understand!   

Any other ideas?

---

### Post by waspbr on 2008-09-30
yep

go to terminal and type

```
sudo displayconfig-gtk
```

this should open a dialog about your screens, try to choose the screen that you have (make and model), then see if the choice for the resolution you want is available.

if choosing your model and make doesn't solve it, just select a generic screen of the resolution you want, this will definitely enable the resolution you want.

on the event that you may need to configure your GDM resolution as well, check out this howto

[https://help.ubuntu.com/community/FixVideoResolutionHowto]("https://help.ubuntu.com/community/FixVideoResolutionHowto")

---

### Post by thetimer on 2008-10-28
Welp I am back, and i still cannot get the correct resolution, this really stinks. 

I tried pretty much everything that applied to my situation here with no success: 
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

I tried manually editing my xorg.conf with the correct horizontal and vertical refresh rates, and resolutions i desired, still no luck.. 


what else could be wrong?? I am getting so frustrated!! :(

---

### Post by SunnyRabbiera on 2008-10-28
what version are you running?

---

### Post by thetimer on 2008-10-28
Ubuntu 8.04

I dont get it, i've never had a resolution problem with any other distro im quite stumped at this point.

---

### Post by SunnyRabbiera on 2008-10-28
well some video cards are demons with Ubuntu.
But did you try envy yet?
Its worth a shot.

---

