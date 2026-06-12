---
title: "GeForce drivers and messed up resolution"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by tone33 on 2008-07-27
I seemed to have messed up my video.  I have a fresh install of 8.04 and when trying to install the nvidia drivers for my GeForce 6600 the screen resolution somehow was set to 640x480.  I was able to get the drivers installed, but when I go to the NVidia XServer settings I don't see where i can change the resolution.  I have also stopped and started the xserver from terminal with this:

sudo /etc/init.d/gdm stop
sudo /etc/init.d/gmd start

any ideas?

---

### Post by northern lights on 2008-07-27
System > Preferences > Screen Resolution

---

### Post by tone33 on 2008-07-27
the highest option i have is 640x480.

---

### Post by northern lights on 2008-07-27
stop the gdm/X

run ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

start X again

now what?

---

### Post by tone33 on 2008-07-27
ok great that worked.  Now when I go to System->Admin->Nvidia X Server Settings I get this message:

You do not appear to be using the Nvidia X driver.  Please edit your X configuration file (just run 'nvidia-xconfig' as root), and restart the X server.

I did this last time and that's how I ended up with the small screen resolution.  I'm trying to configure my desktop for dual monitors.

---

### Post by northern lights on 2008-07-28
It didn't keep the 'nvidia' dirver? Crap.

Reenable the driver under "System > Administartion > Hardware Drivers".

Then navigate to "System > Administartion > NVIDIA X Server Settings" (alternatively 'gksu nvidia-settings') and under "X Server Display Confoguration" (second in lefthand menu) click on the "Confogure" button and select "Twinview" for dual monitors. X is going to treat them as one device actually and span the desktop across both.

Should the resolution get messsed up in the process, please post the outputs of ```
cat /etc/X11/xorg.conf
``` and ```
sudo lshw -C display
```

Thank you.

---

### Post by tone33 on 2008-07-30
Thanks.  I got this worked out.  Can't remember exactly what I did at this point...  just messed with it enough and finally i did something correct.  Even got my Twinview setup and saved to config so it keeps settings on reboot.

---

### Post by northern lights on 2008-07-30
Sorted. I wasn't thinking too clearly either. The error message gave a solution:

> **tone33 said:**
> Please edit your X configuration file (just run 'nvidia-xconfig' as root), and restart the X server

i.e. ```
sudo nvidia-xconfig
```would (and probably did --> did you run that?) have solved it.

---

### Post by tone33 on 2008-07-30
yea i think that may have been what i did.  And it makes sense as i would have to run as root to save to the configs.  The root terminal window in debian had me spoiled for a minute.

---

