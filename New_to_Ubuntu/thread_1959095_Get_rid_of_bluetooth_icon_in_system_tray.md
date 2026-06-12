---
title: "Get rid of bluetooth icon in system tray?"
date: 2012-04-15
forum: New to Ubuntu
---

### Post by josephellengar on 2012-04-15
Hi. I just upgraded to 12.04, and suddenly my long-functioning system tray is messed up. There is a large, ugly bluetooth icon sitting there. I used to be able to uncheck a box in bluetooth options to get rid of it, but that option is no longer available, and if I remove the gnome-bluetooth package, I also lose gnome-tweak-tool. Is there any other way to get rid of this now?

Thanks!

---

### Post by Frogs Hair on 2012-04-15
I have no Bluetooth adapters so, the icon has never appeared . There is a visibility on-off in the Bluetooth settings , but it is not available because I am not using Bluetooth.

---

### Post by josephellengar on 2012-04-15
> **Frogs Hair said:**
> I have no Bluetooth adapters so, the icon has never appeared . There is a visibility on-off in the Bluetooth settings , but it is not available because I am not using Bluetooth.

My visibility is set to off and it's still showing up.

---

### Post by Frogs Hair on 2012-04-15
> **josephellengar said:**
> My visibility is set to off and it's still showing up.

Have you logged out and in since changing the setting ?

---

### Post by josephellengar on 2012-04-15
> **Frogs Hair said:**
> Have you logged out since changing the setting ?

Yeah, I've logged out/restarted. I'm also working on fixing a few other warts, so I've done a number of restarts.

(If you know anything about it, one that I'm working on right now is that I can't get the lightdm background to read its config file background variable)

---

### Post by josephellengar on 2012-04-15
Hmm. The "visibility" option is only for whether the device is visible over bluetooth, not for whether the bluetooth button is visible.

---

### Post by Frogs Hair on 2012-04-15
You can see if Bluetooth is one of your startup programs , but since you use it removing it from the list may only work temporarily. If an adapter is detected it may be automatically started.

---

### Post by josephellengar on 2012-04-15
> **Frogs Hair said:**
> You can see if Bluetooth is one of your startup programs , but since you use it removing it from the list may only work temporarily. If an adapter is detected it may be automatically started.

It's not. And actually I don't use it, if that matters.

---

### Post by Frogs Hair on 2012-04-15
> **josephellengar said:**
> It's not. And actually I don't use it, if that matters.

The icon should not appear or at least it didn't  on my clean installation and that includes all desktop environments  .  If you are using Classic Gnome you can add or remove panel  items with Alt+Right +Click or Super + Alt + Right Click. The shell  of course, has no right click option. There are some extension for removing panel items , but I don't think it is supposed to be there to begin with.  I didn't see it in 11.10 either .

---

### Post by josephellengar on 2012-04-15
> **Frogs Hair said:**
> The icon should not appear or at least it didn't  on my clean installation and that includes all desktop environments  .  If you are using Classic Gnome you can add or remove panel  items with Alt+Right +Click or Super + Alt + Right Click. The shell  of course, has no right click option. There are some extension for removing panel items , but I don't think it is supposed to be there to begin with.  I didn't see it in 11.10 either .

It's showing up in the system tray, so to remove that I'd have to remove the other items in my system tray as well, such as the wifi, volume, battery, etc. And actually, this is a clean installation as well. I am using gnome classic.

---

