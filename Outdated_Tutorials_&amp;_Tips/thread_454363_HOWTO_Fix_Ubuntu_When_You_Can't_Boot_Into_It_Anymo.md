---
title: "HOWTO: Fix Ubuntu When You Can't Boot Into It Anymore"
date: 2007-05-25
forum: Outdated Tutorials &amp; Tips
---

### Post by syalam on 2007-05-25
Entry from my blog [**sheehantu**]("http://sheehantu.wordpress.com/2007/05/24/what-to-do-when-you-can-no-longer-start-ubuntu/")

Lets face it, if you like to edit system configuration files keeping your sudo finger happy - you just might screw up your operating system. Before you go reformatting your drive just remember not all hope is lost. In fact its really easy to get your system back in action with Linux.

Option 1 - Reinstall the Ubuntu Desktop

The ubuntu-desktop is a metapackage that links together a lot of core applications in Ubuntu. If you reinstall it, the system will add all of the original software and packages that were bundled when you first installed it.

“sudo apt-get reinstall ubuntu-desktop”

Once this is complete, your system should be good to go! In most cases, this will do the trick. If this does not fix the problem, you could have an issue with your desktop manager….

Option 2 - Purge GNOME (or KDE, XFCE, etc.)

One time I could no longer boot into my window manager. All I had was my trusty shell and an internet connection - and thats all I needed. If you have somehow messed up your desktop manager such as GNOME, re-installing it might not work because a lot of settings are still present. Even if you did a remove and then a clean install of the package you may have some lingering config files around.

“sudo apt-get purge gnome”

“sudo apt-get install gnome”

If you perform a purge all settings WILL be removed cleanly. After that, do an install and you should be set! Try this in conjunction with an ubuntu-desktop reinstall if the problem isn’t solely GNOME.

These two options have saved me a lot of headache. Fortunately I haven’t witnessed any problems more serious than these cases. If I ever have a more severe problem and manage to fix it, I’ll be sure to update this post!

---

### Post by ReaLitaliano on 2007-06-01
i still cant boot to linux or windows. i had to install windows on a new partition just so i can get help and download things to help but i am still stuck.

---

