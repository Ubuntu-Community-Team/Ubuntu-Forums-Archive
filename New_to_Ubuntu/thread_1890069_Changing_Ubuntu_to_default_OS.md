---
title: "Changing Ubuntu to default OS"
date: 2011-12-02
forum: New to Ubuntu
---

### Post by Treyonator56 on 2011-12-02
I installed Ubuntu v11.10 via Wubi (dual boot) and It works fine. I go into Window$even to change Ubuntu to my default OS and ran into a problem.  I went to the administrator tools, as usual, and Ubuntu isn't on the list. I remember doing it via a USB Drive a while ago with Ubuntu v11.04 and it was there. Can anyone inform me on how to change Ubuntu back to my default OS? Do I need to use the terminal? Any tips will greatly be appreciated!

---

### Post by lolpenguin on 2011-12-02
Oops...Wubi...You can't.

---

### Post by fantab on 2011-12-02
> **Treyonator56 said:**
> I installed Ubuntu v11.10 via Wubi (dual boot) and It works fine. I go into Window$even to change Ubuntu to my default OS and ran into a problem.  I went to the administrator tools, as usual, and Ubuntu isn't on the list. I remember doing it via a USB Drive a while ago with Ubuntu v11.04 and it was there. Can anyone inform me on how to change Ubuntu back to my default OS? Do I need to use the terminal? Any tips will greatly be appreciated!

With WUBI you CANNOT. However you can if you DUAL BOOT, you can set Ubuntu as your default OS. [See this]("http://opensource-sidh.blogspot.com/2011/10/install-ubuntu-1110-and-windows-dual.html"). also there plenty of information on dual booting ubuntu with windows, just search.

---

### Post by oldfred on 2011-12-02
What version of Windows?

XP, you should be able to edit boot.ini. And in Vista/7 use BCDedit to change boot around.

In grub (which really is not booting as wubi uses the Windows boot loader) Ubuntu should be first.

If you are using Ubuntu as your primary system, it may be time to upgrade to a full partitioned system. Even the designer of wubi expects you to upgrade.

[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

HOWTO: migrate wubi install to partition - bcbc 
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

---

### Post by lolpenguin on 2011-12-03
> **oldfred said:**
> In grub (which really is not booting as wubi uses the Windows boot loader) Ubuntu should be first.

In current versions of Ubuntu installed using Wubi, GRUB disables the Windows entries.

---

### Post by sadaruwan12 on 2011-12-03
Do a complete install of ubuntu on a free partition then normally ubuntu will be your default OS and the windows will be the selective one this is the easiest way to do it.

---

### Post by Mark Phelps on 2011-12-03
You don't NEED to reintall Ubuntu just to have it the default OS selection.

In Win7, click on the button on the bottom left of the screen and type MSCONFIG in the search box, and press the ENTER key.

Select the boot tab.  There, you have an option to set the default OS.

---

### Post by Treyonator56 on 2011-12-03
Okay. Thanks guys! Time to reinstall Ubuntu...

---

### Post by *^kyfds( on 2011-12-17
if you didn't want to completely erase your windows partition, and use windows as a 'backup' as so to speak, it would be easier just to reduce the size of your windows partition and increase the size of the Ubuntu partition (then just follow the steps above for setting ubuntu as your default OS)

---

### Post by amjjawad on 2011-12-17
> **Treyonator56 said:**
> Okay. Thanks guys! Time to reinstall Ubuntu...
Just in case you are NOT ready yet for installing Ubuntu OR you don't want to mess with your internal HDD, please check this:
[http://ubuntuforums.org/showthread.php?t=1650699](http://ubuntuforums.org/showthread.php?t=1650699)

---

