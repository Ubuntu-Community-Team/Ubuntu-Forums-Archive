---
title: "Changing startup sound"
date: 2012-06-17
forum: New to Ubuntu
---

### Post by Melvyn Gattinoni on 2012-06-17
Hi all,
I'm using Ubuntu 12.04 and I want to change the startup sound. I copied the new ogg file to  usr/share/sounds/ubuntu/stereo.  I also changed the path in Gnome login sound in startup applications to "paplay /usr/share/sounds/ubuntu/stereo/debout.ogg". The original startup sound works fine but the new sound, for some reason, doesn't. 
Note: I tried the default path in startup applications for Gnome login sound (/usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login"), but that doesn't work either. I also changed the name of the new file to "desktop login". That didn't work either.
Help on this will be greatly appreciated!
Cheers,

Melvyn

---

### Post by daslinkard on 2012-06-17
This [link  ]("http://www.upubuntu.com/2011/12/how-to-change-startup-sound-for-ubuntu.html")is what I used to change my start up sound in 11.10....and it should work the same way in 12.04.....the one suggestion that I would recommend (if you didn't do so) would be to rename your new sound as [COLOR=#660000]desktop-login.ogg[/COLOR]

Hope this helps!

---

