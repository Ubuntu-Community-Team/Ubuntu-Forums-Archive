---
title: "removing 8.04 upgrade"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by Papa-san on 2008-08-28
I went through the process to upgrade my Ubuntu install, and when it was finished, I had problems with firefox. (I had 2, and the upgrade included the Firefox 3. 5 beta) I need to either remove the first Ubuntu 8.04 in my boot list (That's the new 'upgrade') or to revert to the older install of firefox. I'll need to know how to get the outdated versions removed anyways, so I don't end up with a list of 18 Ubuntu versions in my boot menu...

---

### Post by Vadi on 2008-08-28
I'd recommend simply installing Firefox 2. You can do so by clicking [here]("apt:firefox-2").

---

### Post by OffAxis on 2008-08-28
firefox 2 and 3 can coexist on the same system, so you don't have to uninstall 3 when you revert back to version 2.

As for the grub menu, you can directly edit the menu.lst file with any text editor and remove any entries that you consider excessive. (you may just want to comment them out instead of erasing them; just in case)

**/boot/grub/menu.lst**

---

### Post by Vadi on 2008-08-28
I'd recommend against using a text editor to edit menu.lst, you might mess up and render your system unbootable.

Instead use StartUp Manager ([click to install]("apt:startupmanager")) to remove the entries.

---

### Post by Papa-san on 2008-08-29
This is why I love this community! I've asked questions to the Microsoft people, and almost never get usable information... I recommend this OS to everyone I meet, and have 'converted' at least half a dozen ex-windows users...

---

### Post by Papa-san on 2008-08-29
> **Vadi said:**
> I'd recommend simply installing Firefox 2. You can do so by clicking [here]("apt:firefox-2").

I did it (Nice, easy script I might add!), but the menu item "Firefox 2 Web Browser" still opens the Firefox 3 Beta 5 program... (Applications > Internet > Firefox 2) I know I'll probably have to modify a file somewhere, but a walkthrough would be nice! :rolleyes:

Thanks!

---

### Post by Vadi on 2008-08-30
Try doing alt+f2, and "firefox-2". It should open the 2nd version...

---

### Post by MasterSander on 2008-08-30
> **Vadi said:**
> Try doing alt+f2, and "firefox-2". It should open the 2nd version...

if it does, you can edit the menu entry and change it to firefox-2 as well.

---

### Post by Papa-san on 2008-09-20
This has gone way beyond firefox...
I have lost most of my functionality, and cannot work my way through it all. I used to be able to use my mp3 player to copy files and stuff to, but now even that is gone. 

Is there any way to go back to the way it was before the 'upgrade'? I tried to load the earlier one in my boot list, but it comes up the same way. evidently, whatever broke my system is included in the earlier versions as well. Does this OS do any kind of backing up? how do I restore it to a date previous to my 'upgrade' and then get rid of the 'improved' version? 

Trying to install off of my original disc doesn't even want to work, because there is nothing regarding my other partitions included in it when I try to re-install. I cannot format the whole HD as I have Vista on another partition...

---

