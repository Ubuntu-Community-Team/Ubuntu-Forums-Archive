---
title: "Unity System Tray"
date: 2012-04-05
forum: New to Ubuntu
---

### Post by expatCM on 2012-04-05
I learn on another thread that you cannot make changes to the system tray with Unity.  So applets cannot be added.

What about Skype, where does the notification icon appear when you install skype?

---

### Post by UnknownFearNG on 2012-04-05
Click on the first icon in the Unity bar. This is called the "Dash". Search for Skype, and it should be listed. Then, just open it and the icon will be in the Unity bar. You can right-click it and choose Keep in Launcher to, keep the icon in the bar even if it is not running.

---

### Post by expatCM on 2012-04-05
ok ...  great ...  so it works, thank you.

Seems that I have a learning curve with Unity.

---

### Post by UnknownFearNG on 2012-04-05
> **expatCM said:**
> ok ...  great ...  so it works, thank you.

Seems that I have a learning curve with Unity.

Glad it worked :)

---

### Post by 3rdalbum on 2012-04-06
> **expatCM said:**
> I learn on another thread that you cannot make changes to the system tray with Unity.  So applets cannot be added.

What about Skype, where does the notification icon appear when you install skype?

You've misread something.

The old Notification Area API is depreciated in Unity, but still present. Skype still uses Notification Area and its icon will appear in Unity's top panel because it has been "whitelisted" to appear.

Other programs that use the Notification Area API will not work unless you whitelist them.

Programs that need some sort of notification area should instead use the Indicator API, which is a much cleaner and more consistent way of putting these sorts of icons and menus into the panel. Programs that use Indicators do not need to be whitelisted.

Short answer: Skype's notification area icon still works by design, most programs these days show indicator icons instead of notification area icons.

---

### Post by expatCM on 2012-04-06
I went from Ubuntu 6.xx upgrading with each release until 10.10 when I decided to stay put until things settled down.

That may have been a mistake.

I am now going to install 12.04 B2 but it looks like my learning curve is going to be painful or I will need to open a terminal and gedit a lot .. 

Thank you for your help.

---

