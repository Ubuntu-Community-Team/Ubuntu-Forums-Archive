---
title: "[SOLVED] Resolution Restricted by NVIDIA driver"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by sevansbr on 2008-06-14
Hi there, I wasn't sure where to post this, as it is a display problem, but I have a very hard time understanding the answers elsewhere because I've got about one day's worth of Linux experience.

I'm Running:
Ubuntu 8.04 (hardy)
Kernel Linux 2.6.24-18-generic
GNOME 2.22.2

The Machine is:
Pentium 4 2.4 GHz
757.1 MiB Memory

And the graphics card is:
Gefore 6200

I've now installed the card's drivers two ways, the first was through System->Hardware Drivers and enabling the restricted driver. The second was to download and run EnvyNG.

After the first install the highest resolution that Ubuntu would allow me to select was 640x480 which was completely unworkable (nothing fit in the screen any more!). After running EnvyNG things were a little better. I could set the screen to 800X600. This is still very small (or big as it were), I'd like to be able to get up to at least 1024x768.

Any suggestions?

---

### Post by Rhubarb on 2008-06-14
Try running this:
```
gksu displayconfig-gtk
```
This will give you a nice easy to configure app to setup your display resolution.
If you can't open up a terminal, press Alt + F2, then enter in the command above.

Once set, you need to log off / restart X.  (Restarting X can be done by pressing Ctrl + Alt + Backspace - please save any work before doing this).

---

### Post by sevansbr on 2008-06-14
Hmmm... In the configuration app at first it would still only allow me to go up to 800x600. However, when I selected a monitor other than PlugandPlay Monitor it let me go higher. It asked me to logout for the changes to take place. When I logged back in it remained in 1024x768 for about 2 seconds before bumping back down to 800xz600. 

Does this mean that the monitor is the problem? It *is[I]*[/I] a decidedly crappy monitor. However, this doesn't explain why I was allowed to display in 1024x768 before installing the card's driver.

Any other ideas?

---

### Post by Rhubarb on 2008-06-14
Hmm, that should've worked.
Try some different monitor types, like generic 1024x768 and make sure nvidia is the graphics card type.

There's a chance that Xorg is detecting that the monitor doesn't like going above 800x600.  In which case I'm not sure how to fix this.
Have you got access to a better monitor that you could try out?

---

### Post by housam on 2008-06-14
Try this :
```
sudo nano /etc/usplash.conf
```

you will got something like that
> 
# Usplash configuration file
# These parameters will only apply after running update-initramfs.


add the required resolution like that as an example :

> 
# Usplash configuration file
# These parameters will only apply after running update-initramfs.

xres=[COLOR="Red"]1280[/COLOR]
yres=[COLOR="Red"]800[/COLOR]

then reboot and type :

```
sudo dpkg-reconfigure usplash
```

then check for the new settings -- System > Preferences > Screen Resolution and select the new one.
__________________> [QUOTE][/QUOTE]

---

### Post by sevansbr on 2008-06-14
AHA!
In the graphics card tab I changed the driver from NVIDIA 6800 (generic) to NVIDIA 6 series and now it is running fine in the higher resolution. Thanks a lot!

---

### Post by jasontu on 2008-06-14
I have a similar issue, but when I use gksu displayconfig-gtk I don't how to save the settings.  I hit save and it asks for a save location.  If I hit okay it just bring me back to where I started.

---

### Post by EwanB on 2008-06-14
I'm a ten year windows veteran with MCSE etc to boot, but thought I'd switch to Ubuntu since vista sucks slightly.

Spent the last 2 hours trying to fix the resolution on my Shuttle XPC box with no luck until I read this post!!

Thank you v much for the fix - worked a treat.

Ewan fae Scotland!

---

### Post by luapekralc on 2008-06-14
I too add my thanks. I managed to get the resolution to stay after the proposed fix, by re-setting the values in preferences.

---

