---
title: "Broke OS right away! XD"
date: 2022-05-04
forum: New to Ubuntu
---

### Post by hugepants on 2022-05-04
Hey all,

Recently received my Ras Pi 4 8g, weeks after acquiring my first Ras Pi (4 mb 4g). 

Got cocky and began research just to learn snap's weren't preferential... anyway, not sure if the snap uninstall or something else was to blame (recalled snapd to no avail). I seem to have broken the OS... Ubuntu is handsdown the most pretty of the desktop experiences... I really don't want to touch the thing til i figure it all out. Uninstalling Snaps was not the only command I presented to my nice new single board computer but either way, I feel I messed it up pretty good! 

I would like some feed back yet don't have much of an idea of what exactly ya'll are looking for... again, I'm new to all this!

Please help as I would love to carry on with my Ubuntu experience! XD

Thanks, 
Garrett

---

### Post by issh on 2022-05-04
Did you completely remove Snapd? If not, can you list what is currently installed in snap with the ***snap list*** command? Fyi, removing snap apps and snapd service shouldn't break your system. It would be possible to fix whatever is broken by using ***chroot***, but it might be easier to just format the micro sd card and reinstall the OS if you didn't have any important data on it. If you want to learn, go the ***chroot*** way and try to fix it!

---

### Post by hugepants on 2022-05-04
Thank you for the reply... I do want to learn so I am looking in to the chroot route now.
As it is, most commands that I've read to be part of the fix are 'missing operand' or, feedback some error or another.
I've saved some of the communication to text editor and will send it as soon as I find a way to send it to myself with out a browser. &#129318;*&#9794;&#65039;
Firefox snap was SUPER slow so removed it, same time, as I was working to acquire chromium.

---

### Post by grahammechanical on 2022-05-06
Which version of Ubuntu did you install on that Raspberry Pi? Ubuntu Desktop, Ubuntu Server or Ubuntu Core? In what way is the OS broken? Firefox is not a snap in Ubuntu 20.04 desktop but it would be a snap in Ubuntu 22.04 desktop. Which version did you install? 

Regards

---

### Post by Paddy Landau on 2022-05-07
> **hugepants said:**
> … learn snap's weren't preferential
That depends entirely on what you're after. If you don't want to use snaps, just don't use them; but you don't have to uninstall the snap system. For Ubuntu 22.04, you probably shouldn't uninstall it.

Firefox is known to be a problem with the *first* load after a reboot (thereafter it's fine). You can uninstall the snap version of Firefox and replace it with the flatpak version, which works fine. If you don't know how to go about installing flatpak, I'll tell you, but you haven't told us which version of Ubuntu you're using.

---

