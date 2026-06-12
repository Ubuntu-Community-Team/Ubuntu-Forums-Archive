---
title: "Shortcuts to Unity taskbar"
date: 2011-05-11
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Kevbert on 2011-05-11
Using Oneiric with Unity Desktop. If I go to Applications on the left taskbar and drag an application to that taskbar (for example Aisleriot Solitaire) I can open the application via the new icon. If I close the Application the new icon stays on the left taskbar, but when I reboot the icon is not displayed. How do I make the new icon stay on the taskbar so that it is permanent ?
With the old gnome desktop it was possible to edit the menus via a right-click. How would I do this with Unity ?

---

### Post by Peter09 on 2011-05-11
Should be able to right click on the icon and select keep in launcher

---

### Post by Kevbert on 2011-05-13
Thanks for the reply. When I right-click on the icon 'Keep in Launcher' is ticked (as per default icons) but it does not stay permanent as a reboot no longer displays the new icon in the left taskbar.
I've raised a [COLOR="Red"][bug report]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/782053")[/COLOR] on this.

---

### Post by coffeecat on 2011-05-13
> **Kevbert said:**
> Thanks for the reply. When I right-click on the icon 'Keep in Launcher' is ticked (as per default icons) but it does not stay permanent as a reboot no longer displays the new icon in the left taskbar.
I've raised a [COLOR=Red][bug report]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/782053")[/COLOR] on this.

Could your problem be this bug?

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/778950](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/778950)

If so, you need to install dconf-gsettings-backend.

Also mentioned in this thread (from post #27 onwards):

[http://ubuntuforums.org/showthread.php?t=1751438](http://ubuntuforums.org/showthread.php?t=1751438)

---

### Post by Kevbert on 2011-05-16
> **coffeecat said:**
> Could your problem be this bug?

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/778950](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/778950)

If so, you need to install dconf-gsettings-backend.

Also mentioned in this thread (from post #27 onwards):

[http://ubuntuforums.org/showthread.php?t=1751438](http://ubuntuforums.org/showthread.php?t=1751438)

Thanks. Installed as required.
I can confirm that this is a duplicate of bug #778950 and has been marked accordingly.

---

