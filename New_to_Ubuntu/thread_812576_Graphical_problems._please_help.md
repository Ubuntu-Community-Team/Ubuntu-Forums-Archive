---
title: "Graphical problems. please help"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by Shaun440 on 2008-05-30
hi all

I'm fairly new to ubuntu. I recently installed it and got it running and all, but when i go to system>administration>Hardware drivers and check "enabled" on NVIDIA accelerated graphics driver I get problems. It seems to work fine after I enable it, but when i restart the computer, once it gets to the login screen, everything goes blurry and i get weird colours and vertical lines on the screen.

I can get ubuntu working fine again if i reboot and start it in recovery mode and "fix X server".

Any idea's?

Cheers
Shaun

---

### Post by powerpleb on 2008-05-30
> **Shaun440 said:**
> hi all

I'm fairly new to ubuntu. I recently installed it and got it running and all, but when i go to system>administration>Hardware drivers and check "enabled" on NVIDIA accelerated graphics driver I get problems. It seems to work fine after I enable it, but when i restart the computer, once it gets to the login screen, everything goes blurry and i get weird colours and vertical lines on the screen.

I can get ubuntu working fine again if i reboot and start it in recovery mode and "fix X server".

Any idea's?

Cheers
Shaun

How did you install the drivers?

Have you tried removing them and re-installing them?

---

### Post by Shaun440 on 2008-05-30
I haven't installed the driver. I thought that was how you install it :S

---

### Post by powerpleb on 2008-05-30
> **Shaun440 said:**
> I haven't installed the driver. I thought that was how you install it :S

Hmmm, I hope I'm right here.

Deselect the driver in 'Hardware drivers' if it's selected, reboot.

Go to Add/Remove in the menu.
In search type 'nvidia', there should be a few NVidia drivers available. 

Depending on your chipset you probably want the 'new' driver. But have a look at the text, it should say which chipsets each driver supports.
Select the appropriate one and 'Apply Changes'

---

### Post by Shaun440 on 2008-05-30
ok I did that, but it still wont let me select "extra" in the visual effects tab, and it still wont let me use 3D applications like the chess game that comes with ubuntu.

---

### Post by powerpleb on 2008-05-30
> **Shaun440 said:**
> ok I did that, but it still wont let me select "extra" in the visual effects tab, and it still wont let me use 3D applications like the chess game that comes with ubuntu.

Sounds like it's not working still...

You can use Envy which is basically a program that should auto-detect all your hardware and install/configure the appropriate drivers.
Firstly you *must* have Hardy for this...

Open up a terminal and type this to update the package list:
```

sudo aptitude update
```
Install the envy package:
```
sudo aptitude install envyng-gtk

```
Wait till it's done then type this to run envy:
```
sudo envyng -t
```

The envy FAQ is:
[http://albertomilone.com/envyngfaq.html](http://albertomilone.com/envyngfaq.html)

---

### Post by Shaun440 on 2008-05-30
ok tried that, and it seemed to install the drivers properly, then it asked to reboot, so i did, and i get the same graphic problems as before :(

If it helps at all, im using a dell m1530, with an 8600M GT graphics card

---

### Post by powerpleb on 2008-05-30
> **Shaun440 said:**
> ok tried that, and it seemed to install the drivers properly, then it asked to reboot, so i did, and i get the same graphic problems as before :(

If it helps at all, im using a dell m1530, with an 8600M GT graphics card

OK, I'm not really that knowledgeable about this sort of thing as mine worked out of the box. But my last suggestion would be to:

in the terminal again
Get rid of Jockey (It's called 'Hardware Drivers' in the menu)
```
sudo aptitude purge jockey-gtk
``` 

Get rid of currently installed drivers:
```
sudo aptitude purge nvidia-glx-new
```

run envy again
```
sudo envyng -t
```



If this doesn't work...
You could open up synaptic:
Search for NVidia
This will give you a list of what drivers are available. You could try getting rid of any you see installed by unchecking them.

Then run envy.
```
sudo envyng -t
```

---

### Post by Shaun440 on 2008-05-30
should i exit the X server before running envy?

---

### Post by powerpleb on 2008-05-30
> **Shaun440 said:**
> should i exit the X server before running envy?

No, it's a GTK app, it needs the X server to run.
You will have to reboot to restart the X server with the new config.

---

### Post by Shaun440 on 2008-05-30
still no luck :(

---

### Post by powerpleb on 2008-05-30
> **Shaun440 said:**
> still no luck :(

Sorry I don't know then...

Here are some links to other pages that may be of use:
[http://www.funnestra.org/ubuntu/hardy/#nvidia-driver](http://www.funnestra.org/ubuntu/hardy/#nvidia-driver)
[http://ubuntuforums.org/showthread.php?t=797270](http://ubuntuforums.org/showthread.php?t=797270)

---

