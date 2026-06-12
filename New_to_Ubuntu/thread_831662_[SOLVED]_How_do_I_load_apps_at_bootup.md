---
title: "[SOLVED] How do I load apps at bootup?"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by zaivala on 2008-06-17
I have a couple of apps (a clock and a gdesklet app) that I use all the time I'm in Linux.  I have to reload them every time I boot.  Is there some way to have them load at bootup?  Just being lazy...

---

### Post by Ripfox on 2008-06-17
system/preferences/sessions

---

### Post by sdennie on 2008-06-17
You can do this by going to System->Preferences->Sessions and adding applications to the startup list (it's the first tab when you start the Sessions application).

---

### Post by zaivala on 2008-06-17
Thanks for the responses, but it looks like an RTFM moment, not sure what to enter after hitting ADD+.

Moss

---

### Post by sdennie on 2008-06-17
If you aren't sure what the applications are called but they are installed in your menu, you could go to System->Preferences->Main Menu and find the application there.  If you right click on the application and select Properties, it should tell you the command the menu item is using to launch the application.

---

### Post by zaivala on 2008-06-17
> **vor said:**
> If you aren't sure what the applications are called but they are installed in your menu, you could go to System->Preferences->Main Menu and find the application there.  If you right click on the application and select Properties, it should tell you the command the menu item is using to launch the application.

Well, that was bloody easy but... how come, when you click Browse to look for stuff, it takes you to a bunch of folders which appear to have nothing to do with your applications?  I think I got it done, though, will find out as soon as I reboot.

---

### Post by zaivala on 2008-06-17
Worked fine, with a new quirk ... it loaded the first app (gworldclock) against an all-black background, then loaded the second (gDesklets) and the background and status bar, et al... it was a shaky 4-5 seconds seeing just the gworldclock and all black... but everything's cool, and thanks loads.

---

### Post by sdennie on 2008-06-17
> **zaivala said:**
> Well, that was bloody easy but... how come, when you click Browse to look for stuff, it takes you to a bunch of folders which appear to have nothing to do with your applications?  I think I got it done, though, will find out as soon as I reboot.

I'm not sure.  It could be because the most common place to install programs is in /usr/bin and that directory is likely to contain at least 1000 files so, trying to find a program with Browse might not be the most common user operation.

---

