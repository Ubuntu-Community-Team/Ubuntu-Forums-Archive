---
title: "[SOLVED] Orphaned Package Problem -"
date: 2008-08-07
forum: New to Ubuntu
---

### Post by diego898 on 2008-08-07
I installed the gtkorphan and when I click on it in system admin there is an option to 
"show all orphaned packages, not just the ones in libs section"

with that clicked I have 112 packages

with that unclicked I have 15 packages

I was told:
> You could delete all 112, and be ok.
I thought by ok it was meant my system would remain in the same state it currently was in.

I deleted all 112, and now the remove orphaned packages option is gone from my admin menu, and so is the confiz settings manager. Now, when I go to view trailers in apple, it sais "get the latest quick time". The only thing left of open office is word, my entire system was trimmed down completely. I have no calculator, no games, whats going on?! I think i saw it remove alot of important things like "fglrx" and "gecko media player", etc!

For example, as a simple test I went to synaptic and tried to install the restricted extras package and I was able to install it! Meaning of course that it got uninstalled somehow! Im assuming there is no way to "undo" what I just did? If so, then why was I told that I would be ok?

---

### Post by Aetherius on 2008-08-07
I'm sorry to tell you but you will have to reinstall what you have just uninstalled, and be a little more wary of automated package management


*From GtkOrphan's Homepage:*
> At GtkOrphan's first run, you should initialize your system in order to keep track of needed packages, even if they are reported as orphaned.
In the main window, expand the "Options" section and check the "Show all orphan packages, not only those in the libs section" checkbox. Note: with this option, GtkOrphan will report as "orphaned" all those installed packages that are not dependencies for any other. In this way, for instance, packages such as gparted, ubuntu-desktop, wine will be listed too, as they are "top-level" packages and no other package depends on them.

Regards,

Aeth

Note: by "be ok" GtkOrphan meant that you would not "break" any installed packages, ie you wouldn't be removing anything that was depended upon by other applications.

---

### Post by diego898 on 2008-08-07
> **Aetherius said:**
> I'm sorry to tell you but you will have to reinstall what you have just uninstalled, and be a little more wary of automated package management


*From GtkOrphan's Homepage:*


Regards,

Aeth

So what do I have to reinstall? Ubutu-desktop?

---

### Post by Norm24 on 2008-08-07
Very good advice:

 Originally Posted by oldsoundguy  
Linux is a much better housekeeper than Windows by thousands of miles!

CCLeaner gets the stuff in Windows that any activity leaves behind, but it is not 100% even if you set it up with the added stuff to remove.

Windows has amnesia, and the majority of the time re-booting will NOT clean it.
Linux, on the other hand, does not save the garbage to look over it again and to fill up your drive .. in most instances just control/alt/backspace will reset. BUT sometimes, you MAY have to re-boot. Either way, you are not starting out with a tractor-trailer full of garbage to remove, just the junk bag you have hanging in your car!

Linux is NOT Windows. Things you have to do in Windows to keep it running are no longer needed in any form of Linux.

---

### Post by diego898 on 2008-08-07
What about the driver for my ATI graphics card? How come I dont see a "Hardware" option in either one of the submenus of system tab?

---

### Post by Norm24 on 2008-08-07
If you feel the need to "clean" just use these commands:

      ```
sudo apt-get clean

sudo apt-get autoclean
      
sudo apt-get autoremove
```

Messing with other stuff in unnecessary and as you've found can be dangerous.

---

### Post by Aetherius on 2008-08-07
@Norm24: Shouldn't that be in the CCLeaner thread norm? although its still relevant here.


@diego898: Yes, ubuntu-desktop should install some of what you seem to have lost, however stand-alone things like the compiz-settings manager etc, will have to be reinstalled manually.

---

### Post by diego898 on 2008-08-07
How exactly would I just get back to a default FRESH installation of ubuntu? Would I have to perform a reinstalltion?

---

### Post by Aetherius on 2008-08-07
ubuntu-desktop will pretty much return you to a fresh installation

ubuntu-desktop is a dummy file, which causes all the desktop software to be installed. If you first remove ubuntu-desktop

```
sudo apt-get remove ubuntu-desktop
```

and then reinstall it

```
sudo apt-get install ubuntu-desktop
```

it will install all missing "children" applications too

---

### Post by ace007 on 2008-08-07
You could move your /home directory to a different partition and then just reinstall ubuntu, but there is really no need.  Imagine that now you have a totally blank ubuntu.  Just install things you need as you go along!

---

