---
title: "Cannot find installed ubuntu using wubi"
date: 2012-03-29
forum: New to Ubuntu
---

### Post by shmparvez on 2012-03-29
I installed a new ubuntu (as app option) using wubi on my win 2008 R2 box. It asked me to reboot.
After rebooting I dont see any option to run that. its not in start programs or my desktop, no shortcut whatsoever. If I start wubi it says do you want to uninstall and I said no and closed it.

What do I do now?

---

### Post by Frogs Hair on 2012-03-29
Hello and Welcome

Ubuntu , when installed in Windows is selected from the Windows boot loader . It does not start after Windows is booted . See the guide at the link .If Ubuntu is not selected Windows will boot by default after a given time.   
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by shmparvez on 2012-03-29
The option I chose from ubuntu.com web site was to install it as an app.

"This Windows installer (Wubi) will help you to run Ubuntu within your current system. Wubi is an officially supported Ubuntu installer for Windows users. It can install and uninstall Ubuntu in the same way as any other Windows application. It's simple and safe."

Doesn't this mean, it runs like an app. Similar to what Virtual PC app is to be?

---

### Post by Mark Phelps on 2012-03-29
From the (linked) Wubi Guide:

[https://wiki.ubuntu.com/WubiGuide]("https://wiki.ubuntu.com/WubiGuide")

> Which Operating Systems are supported?

Windows 7, Vista, XP, and 2000 are known to work with Wubi. Windows 98 should also work, but has not been thoroughly tested. Windows ME is not supported. Linux is supported through Lubi. 

I see no mention of Windows Server 2008 in the list.  It simply may not work on that platform.  Perhaps someone else who HAS been able to get this to work on Win Srvr 2008 will see this thread and respond ...

---

### Post by Gleichsnerd on 2012-03-29
> **shmparvez said:**
> 
Doesn't this mean, it runs like an app. Similar to what Virtual PC app is to be?

Unfortunately no. If you want to run Ubuntu within windows (an operating system within an operating system), you'll need a program like VirtualBox. Just install it within that.

Wubi is essentially a shortcut method of installing Ubuntu; instead of changing up partitions, the Ubuntu files are stored within Windows.

---

### Post by Frogs Hair on 2012-03-29
Select Ubuntu from the Windows boot screen per the guide . Wubi .exe is the application used to download and install Ubuntu inside the Windows partition .

---

