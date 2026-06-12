---
title: "Can't login"
date: 2011-07-27
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by vikktor91 on 2011-07-27
Hi, 
After todays upgrade i cannot login into my desktop(unity and unity-2d).When i type my username and password the login screen disappears and i have only moving cursor and background.I'm using gdm, lightdm can't even load.Is this bug in ubuntu or in my pc ?

---

### Post by Harry33 on 2011-07-27
> **vikktor91 said:**
> Hi, 
After todays upgrade i cannot login into my desktop(unity and unity-2d).When i type my username and password the login screen disappears and i have only moving cursor and background.I'm using gdm, lightdm can't even load.Is this bug in ubuntu or in my pc ?

Do you have both gdm and lightdm installed?
Also see, that you have these packages installed:
lightdm
liblightdm-gobject-1-0
lightdm-gtk-greeter

Did you configure lightdm before rebooting?

```

sudo dpkg-reconfigure lightdm

```

---

### Post by iClouseau88 on 2011-07-27
Hi,

I got more or less the same problem.  Upon logging in, I did not see the username & password boxes, but just a blinking hyphen at the top left corner of the screen.  Tried "nomodeset" boot option in Grub menu but that didn't work.  After looking at a few threads in this forum, here's how I solved my problem:

```

CTRL ALT F1
login with userid and password

```

```

sudo apt-get remove lightdm-greeter-example-gtk
sudo apt-get remove lightdm-gobject-0-0 (not found)
sudo apt-get install lightdm-gtk-greeter
sudo apt-get install lightdm-gobject-1-0
sudo dpkg-reconfigure lightdm

```

```

sudo stop lightdm
sudo start lightdm

```

Afer this, the screen boots directly into lightdm. After updating, I got the latest versions:

lightdm 0.9.2-0ubuntu3
lightdm-gtk-greeter 0.9.2-0ubuntu3
lightdm-gobject-1-0 0.9.2-0ubuntu3

Hope this is helpful to someone.

:D

---

