---
title: "[SOLVED] cant change resolution"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by browny254 on 2008-05-20
Hi, I have just been playing around trying to get Compiz working and had to install the restricted drivers by going to Kmenu -> System -> Hardware Drivers Manager. Compiz is now working but my resolution has been set to 640x480 (i usually have 1280x800) and when i access the Monitor & Display section in the System settings to change my resolution I get a wierd screen shown in my attachment here.

Any advice or links to tell me how to fix this?

Also, it could have something to do with me trying to set up a second monitor as a clone, which i did by ticking the box on the same screen to set the resolution on. My second monitor isnt working though even after a restart.

---

### Post by Golem XIV on 2008-05-20
I just replied to your previous post but you didn't mention you wanted 2 monitor support.

Check out [this article]("http://www.ubuntugeek.com/dual-monitors-with-nvidia.html") and see if it helps.

good luck!

---

### Post by browny254 on 2008-05-20
2 monitor support isnt essential, i just have my old pc on the desk here so i plugged the monitor in to see if it would work with the changes i have made because i couldnt get it to before.

but with that error that has come up i dont know what it means so i dont know what to even really look for to fix it. i did what you said in the thread i have about getting compiz working, but not really sure what to do to change the resolution there, i tried changing 640x480 in the xorg.conf file to 1280x800, but it made my resolution worse, well it kind of stretched the 640x480 out assuming my monitor was square so i wasnt able to see the bottom of my display, ie, the logout button in the Kmenu was below my visible screen and i just had to blindly click to get it.

---

### Post by bumanie on 2008-05-20
I didn't get any like message, but my resolution went to those same settings today (a friend's ubuntu did it yesterday). Suspect it is a disagreeable update. I just uninstalled restricted driver - reboot. Then reinstall restricted driver - rebooted and everything worked again.

---

### Post by browny254 on 2008-05-20
ok im not sure what I did but that error message has disappeared from the Display & Monitor setting screen and it has the normal screen there now, except my resolution is still fixed at 640x480 and the slider used to select the reolution has no other possible values.

I would prefer not having to uninstall drivers and reinstall as my internet is really slow and it takes ages...i would prefer to keep that as a last resort.

---

### Post by maybeway36 on 2008-05-20
Try manually editing the xorg.conf - add this between the beginning and end of the "Screen" section:
```
SubSection "Display"
	Depth     24
	Modes "1280x800"
EndSubSection
```

---

### Post by browny254 on 2008-05-20
ok, i had tried that before and it didnt work and did it again and it has, but now that everything is the right resolution that error which i have in the attachment to the first post is occuring again, and also i have no title bars on any of my windows, plus I cant resize any of them...

---

