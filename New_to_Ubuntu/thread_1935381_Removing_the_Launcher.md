---
title: "Removing the Launcher"
date: 2012-03-04
forum: New to Ubuntu
---

### Post by gstoilov on 2012-03-04
Hallo,

will anybody tell me how can I remove the launcher. Whenever I reach for the edge of the screen I have problems with doing my job. Even if I can make starting of Launcher in another way not only with touching the edge will be great.

---

### Post by mcduck on 2012-03-04
> **gstoilov said:**
> Hallo,

will anybody tell me how can I remove the launcher. Whenever I reach for the edge of the screen I have problems with doing my job. Even if I can make starting of Launcher in another way not only with touching the edge will be great.

In the login screen, choose some other session to use than Unity. Install one (or some desktop environment) if you don't have any available.

You can't use Unity session without the Unity launcher, you'd have no way to start programs and switching between them would only be possible through keyboard shortcuts.

...and yes, the launcher can be configured to be always visible, or always hidden and only shown by a keyboard shortcut instead of by moving the mouse cursor to screen edge. Or you could configure it to only react to top left corner instead of the whole left edge. The tool that allows you to configure such settings is [CompizConfig Settings Manager]("apt:compizconfig-settings-manager"), but be careful with it as it will allow making changes that do break your desktop. Pay close attention to any warning/error messages about conflicting plugins or keyboard shortcuts, and make sure you actually want to proceed before clicking any other button than "cancel" if you get such warnings...

---

### Post by MG&amp;TL on 2012-03-04
Removing the launcher and still using Ubuntu's default interface would be a very bad idea. You wouldn't be able to launch anything.

You have two options, as I see it.

1. Configure the launcher to always stay open, so that you don't 'awaken' it when you use firefox or whatever. Apps just moves out of the way. To do this, install *compizconfig-settings-manager *from the repositories. Launch CCSM, then click on the Ubuntu Unity Plugin (not the checkbox next to it). DO NOT enable/disable anything else unless you know what you are doing. Then set the launcher hide to "Never".

2. Install a different DE. There's lots to choose from, I recommend LXDE or KDE myself, but there's also XFCE, GNOME shell, GNOME fallback, enlightenment, and many more.

---

### Post by yetiman64 on 2012-03-04
> **MG&TL said:**
> ..You have two options, as I see it.

1. Configure the launcher to always stay open, so that you don't 'awaken' it when you use firefox or whatever. Apps just moves out of the way. To do this, install *compizconfig-settings-manager *from the repositories. Launch CCSM, then click on the Ubuntu Unity Plugin (not the checkbox next to it). DO NOT enable/disable anything else unless you know what you are doing. Then set the launcher hide to "Never".....

Another Option:

I use ccsm and set the Hide Launcher to "autohide" and the Reveal Mode to "none". This keeps the launcher off the screen at all times when using apps or open windows. It will occasionally pop up if a file is being dragged (if the file has an associated application on the Launcher).

Apart from the freeing up of my desk space, this also has the advantage that dash and the launcher itself can be called up with the keyboard combinations ALT + F2 and ALT +F1 respectively, both can be turned off with the esc key.

@ OP, whichever way you decide on, pay heed to > DO NOT enable/disable anything else unless you know what you are doing.as Unity can be very nasty when the wrong settings are played with. All too tempting to do at times, :), take care with ccsm.

---

### Post by NikTh on 2012-03-04
> **mcduck said:**
>  Or you could configure it to only react to top  left corner instead of the whole left edge. The tool that allows you to  configure such settings is [CompizConfig Settings Manager]("apt:compizconfig-settings-manager"), but be careful with it as it will allow making changes that do break your desktop
+1  
for be careful . Nice tool , but if you don't know how to use it = disaster 

> **MG&TL said:**
> 
2. Install a different DE. There's lots to choose from, I recommend LXDE or KDE myself, but there's also XFCE, GNOME shell, GNOME fallback, enlightenment, and many more.
+1 +1

i prefer gnome-session-fallback . Like the old gnome 2 , but not the same

---

### Post by Carterclan on 2012-03-04
> **mcduck said:**
>  The tool that allows you to configure such settings is [CompizConfig Settings Manager]("apt:compizconfig-settings-manager"), but be careful with it as it will allow making changes that do break your desktop. Pay close attention to any warning/error messages about conflicting plugins or keyboard shortcuts, and make sure you actually want to proceed before clicking any other button than "cancel" if you get such warnings...

A much safer way of tweaking Unity is via Ubuntu Tweak found in USC

---

### Post by mcduck on 2012-03-04
> **NikTh said:**
> +1  
for be careful . Nice tool , but if you don't know how to use it = disaster 

Actually it's perfectly safe to use even if you don't know what each setting does, as long as you follow the basic rule of *"if you get a warning message, and you don't fully understand it, blindly clicking OK is always a bad idea"*. 

The same rule of course applies to all programs. :D

---

### Post by gstoilov on 2012-03-04
Thank you to anybody for the valuable advises.

Problem is solved

Best Regards
Georgi

---

