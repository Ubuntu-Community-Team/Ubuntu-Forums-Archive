---
title: "Please Help solve the following with Nvidia X Server..."
date: 2008-06-12
forum: New to Ubuntu
---

### Post by Foghornleghorn on 2008-06-12
When I select Nvidia X Server Settings from System Administration,the following box appears on the screen.

You Do not appear to be using the Nvidia X Driver.Please Edit your X configuration file (just run Nvidia-xconfig as root) and restart the X server.
How do i proceed in order to have this rectified?
BTW i'm not having any problems running Compiz/Awn or the Cube effects.

Thanks in Anticipation...
regards,
Foghornleghorn.

---

### Post by aktiwers on 2008-06-12
Try go to terminal and type:
```
sudo nvidia-xconfig

```

Then restart X
CTRL+ALT+BACKSPACE

---

### Post by Foghornleghorn on 2008-06-12
Thanks aktiwers,
No joy still getting....You Do not appear to be using the Nvidia X Driver.Please Edit your X configuration file (just run Nvidia-xconfig as root) and restart the X server.

---

### Post by bodhi.zazen on 2008-06-12
You have to install the nvidia drivers first.

```
sudo apt-get install nvidia-glx-new
```

use "apt-get install nvidia-glx" for older cards.

Then enable the driver under restricted drivers.

Then reboot.

Then:

```
gksu nvidia-settings
```

If you like the changes you make with nvidia-settings hit the "Save" button.

---

### Post by Foghornleghorn on 2008-06-12
> **bodhi.zazen said:**
> You have to install the nvidia drivers first.

```
sudo apt-get install nvidia-glx-new
```

use "apt-get install nvidia-glx" for older cards.

Then enable the driver under restricted drivers.

Then reboot.

Then:

```
gksu nvidia-settings
```

If you like the changes you make with nvidia-settings hit the "Save" button.

Thanks bodhi.zazen for the reply...I have no problems with my screen resolutions, just can't access the Nvidia Server Settings from Administration.I prefer not to install the Nvidia drivers if not needed,due to the fact that it has taken me quite a few weeks to get the card working.

---

### Post by Biggy on 2008-06-12
go to System >Administration >Hardware Drivers 

and check Nvidia accelerated graphics driver ( latest cards )

restart ubuntu

---

### Post by forestpixie on 2008-06-12
My understanding is that the nvidia-settings works with the restricted driver, so to use nvidia-settings you will need to install as bodhi and biggy have said you'll need to install the driver.

Nvidia-settings does make a backup afaik when you check anything with it, you could always do so yourself just to make sure.

---

### Post by Foghornleghorn on 2008-06-12
> **Biggy said:**
> go to System >Administration >Hardware Drivers 

and check Nvidia accelerated graphics driver ( latest cards )

restart ubuntu

Thanks Biggy and others for your suggestions, 
Biggy i've check via Administration>Hardware Drivers and Nvidia is currently in use.
Ah well... i'll leave it for now don't want to play around and mess everything up.

---

