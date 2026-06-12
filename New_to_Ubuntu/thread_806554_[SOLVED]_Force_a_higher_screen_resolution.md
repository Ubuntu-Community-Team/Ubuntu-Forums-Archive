---
title: "[SOLVED] Force a higher screen resolution"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by Twizzle on 2008-05-25
I setup 8.04 on an old computer to use as a server and set the screen resolution to 800x640. I have since disconnected it from a monitor and plugged it in elsewhere.

When I VNC to it, the screen is set to 640 x 480. If I go to System > Preferences > Screen Resolution, the max setting is 640 x 480.

Its not the end of the world, but is it possible to increase the resolution a bit?

---

### Post by housam on 2008-05-25
Try this :
```
sudo dpkg-reconfigure usplash
```
and set the correct resolutions

---

### Post by Twizzle on 2008-05-25
I tried that and got > update-initramfs: Generating /boot/initrd.img-2.6.24-16-generic

It seemed to pause for a while then gave me the command prompt again.

If I go back to System > Preferences > Screen Resolution it remains then same.

---

### Post by housam on 2008-05-25
Try this 
```
sudo nano /etc/usplash.conf
```
you will got something like that 

> # Usplash configuration file
# These parameters will only apply after running update-initramfs.  


add the required resolution 
> # Usplash configuration file
# These parameters will only apply after running update-initramfs.

xres=860
yres=640 

then reboot and type :
```
sudo dpkg-reconfigure usplash
```

---

### Post by Twizzle on 2008-05-25
Thankyou

Fixed it :)

---

### Post by housam on 2008-05-25
Glad to hear you did it. cheers

---

### Post by vashwood on 2008-05-31
I'm in the same situation.  I tried updating my usplash.conf but it still doesn't show up under screen resolution when I VNC into the computer.  Any other suggestions?

---

### Post by Twizzle on 2008-06-01
Im not sure how it all ties in but have you tried 'Screens and Graphics' Under Applications > Other. I messed around with this and it was a combination of both that worked.

If it's not in the menu (I don't think it is by default on Hardy), right click on Applications > Edit Menus and tick the box for it under Other.

---

