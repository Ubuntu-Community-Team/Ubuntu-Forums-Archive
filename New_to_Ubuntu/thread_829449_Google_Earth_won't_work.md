---
title: "Google Earth won't work"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by saskatchewan on 2008-06-14
I have tried looking at the links for suggestions on Google Earth but I am still having problems.  I can get it to load but it is jerky.

When I try to zoom in on a location the Google screen turns blue.

Has anyone tried loading the Windows version and running it in Wine?

---

### Post by azurepancake on 2008-06-14
I've been having the same exact problem as mentioned above.

Your curiosity of using Google Earth Windows edition with Wine inspired me to give it a shot. The program appeared to load perfectly, but unfortunately the great blue marble wouldn't appear!

Although I did use the version thats in beta. Perhaps it just needs some tinkering.

---

### Post by sdowney717 on 2008-06-14
It takes a lot of video power and dont run compiz when using it.
What is your video card?
What video driver are you using?

---

### Post by saskatchewan on 2008-06-15
I am not sure what my video card is.

How do I find out?

Also, how do I find out what driver I am using?

---

### Post by bwang on 2008-06-15
Go to a Terminal and type:

```
lspci | grep VGA
```

This will tell you what video card you have.

---

### Post by perce on 2008-06-15
In order to use Googleearth I have to stop compiz first: 

System > Preferences > Appearance > Visual Effects

and choose "none"

---

### Post by IanW on 2008-06-15
Have you tried the version from Medibuntu's repo? It works perfectly for me using 64-bit Hardy & Compiz set to "normal".

---

### Post by saskatchewan on 2008-06-15
I have an AMD Turion 64 chip so that might be the issue.  I have had problems running some graphics before.  There is also a ATI Radio Express 200M.

---

### Post by xdavidx on 2008-06-15
Google earth frezzeess any sugestion?

---

### Post by markbuntu on 2008-06-15
Turning off the desktop visual effects seems to work the easiest for running google earth with ATI cards. You can always turn them back on when you are done.

You can also try running google earth in full screen with desktop effects enabled if you have unredirectfullscreenwindows checked in the Advanced Desktop Effects general settings.

If you are using the ATI resreicted drivers 8.47.3 or 8.5 you can try the tweaks here:

[http://forum.compiz-fusion.org/showthread.php?t=6794](http://forum.compiz-fusion.org/showthread.php?t=6794)

---

### Post by RedRat on 2008-06-15
> **markbuntu said:**
> Turning off the desktop visual effects seems to work the easiest for running google earth with ATI cards. You can always turn them back on when you are done.

You can also try running google earth in full screen with desktop effects enabled if you have unredirectfullscreenwindows checked in the Advanced Desktop Effects general settings.

If you are using the ATI resreicted drivers 8.47.3 or 8.5 you can try the tweaks here:

[http://forum.compiz-fusion.org/showthread.php?t=6794](http://forum.compiz-fusion.org/showthread.php?t=6794)
I am running nVidia card (8600 GT) on a Dell 530n with 2 Gb memory. I have to turn off the customized effects and click on the "Normal" radio button. Then GE works very well.

---

