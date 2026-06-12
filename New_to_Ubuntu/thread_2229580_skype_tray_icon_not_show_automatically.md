---
title: "skype tray icon not show automatically"
date: 2014-06-13
forum: New to Ubuntu
---

### Post by monkeybrain20122 on 2014-06-13
Hi,

As the title says, skype tray icon is missing when login. It does show up if I move the cursor to a hot corner to activate the scale addon of switch to a different workplace and switch back. Ubuntu 14.04 with unity 7.2.0+14.04.20140423-0ubuntu1.2.

I tested on two machines with completely different specs so I don't think it is hardware or driver related.

P.S. It is not the same problem that some people reported where the tray icon doesn't show at all. It just doesn't show automatically. The fix for this problem is to install sni-qt:i386 but that is already installed.

**Edited:** The icon would also show up if I tab the wheel icon on the top right of the panel (where the drop down shows About this computer, system settings etc)

---

### Post by kostkon on 2014-06-13
A better option is to forget about the tray icon and use [skype-wrapper]("https://launchpad.net/~skype-wrapper/+archive/ppa") that will fully integrate Skype into the messaging menu (unread messages, pop-up notifications, etc.)

You can then close the Skype window (or minimise it), while it is running, and bring it up whenever you want by clicking on its entry in that menu (you can start it when it is not running by doing the same.) Also, every time you receive a new message it will appear in the messaging menu and you can then click on it to bring up the message window.

To get rid of the tray icon remove the package sni-qt:i386.

Hope that helps.

EDIT: you can access skype-wrapper's settings from your system settings (may not be there in 14.04). Alternatively, you can search for "skype" in the dash.

---

### Post by monkeybrain20122 on 2014-06-14
Thanks for the advice. but I would see if there is another solution before installing an additional package, it is mostly for someone I install Ubuntu for so maintenance is a consideration, I can deal with the present situation. 

> To get rid of the tray icon remove the package sni-qt:i386.

But would that affect other tray icons?

---

### Post by kostkon on 2014-06-14
> **monkeybrain20122 said:**
> But would that affect other tray icons?
Only old Qt apps that don't support indicators. Especially, If your installation is 64bit, only if you happen to install the 32bit version of an old Qt app; thus, in my opinion, the chances that you'll install an app that really needs a tray icon to work properly, but doesn't support indicators, are slim.

---

### Post by monkeybrain20122 on 2014-08-23
I am still experiencing this. Any suggestion or update?

---

### Post by mc4man on 2014-08-23
I'd think the 'best' solution would be to enable (in source) a global  systray in unity & get rid of sni-qt. I haven't seen any qt4 app that doesn't offer a systray option as good or better (vlc) than the sni-qt created indicator
In the scenario of this thread this may not be the best option.

---

