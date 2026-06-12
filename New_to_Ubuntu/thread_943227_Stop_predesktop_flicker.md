---
title: "Stop predesktop flicker"
date: 2008-10-10
forum: New to Ubuntu
---

### Post by poordamnedfool on 2008-10-10
In between the login screen and the desktop there is a flicker of the dull orange (plain) background, where is this located?  Thanks

---

### Post by lovinglinux on 2008-10-10
I don't know if there is an option to avoid that screen but you can at least change it's color. Go to "System > Administration > Login Window"  and then open the "Local" tab and change the "Background color" option.

---

### Post by robert shearer on 2008-10-10
> **poordamnedfool said:**
> In between the login screen and the desktop there is a flicker of the dull orange (plain) background, where is this located?  Thanks

This is before your xorg configuration for your graphics card kicks in so the screen refresh rate is probably at the default 60Hz.
So it flickers, but only for a moment or two!

You could look at System=>Preferences=.Splash screen  and see if there is a way to alter this.

---

