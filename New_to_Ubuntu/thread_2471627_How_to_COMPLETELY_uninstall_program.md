---
title: "How to COMPLETELY uninstall program?"
date: 2022-02-04
forum: New to Ubuntu
---

### Post by ra-white on 2022-02-04
So I totally messed up settings etc in a program.

Upon a "successfull" "removal" through the Ubuntu Software-app I "reinstalled" the same program again, only to find out that ALL my settings etc was still there.
Obviously the button "remove" didn't do anything at all other than removing the icon!

 I also did the "sudo apt-get remove <program>" and "sudo apt-get --purge remove <program>".
Still, after re-installation all settings and files everything is still there.

One of the main reasons I switched over from Windows to Linux was that I wanted to be in control of my machine.

So, how do I acutally uninstall a program in Ubuntu 20.04??

---

### Post by deadflowr on 2022-02-04
User's personal settings are never removed when programs are uninstalled.
For that you need to search your home folder's hidden folders for any related name folders and delete them.
Usually those are inside the .config directory, but sometimes they might have their own directory.

---

### Post by ra-white on 2022-02-05
Alright I found it. Thanks!

---

### Post by linux-sysop on 2022-02-05
May I add, for people who "tinker" with the system a lot - as I do - you may wish to install a program called Timeshift.

I suggest you back up to another partition or drive, I use a 32 GB USB thumb drive myself.

There is a  script program called Bodhibuilder that worked well with version 18.04, making a bootable iso for USB. I have no idea if it is still compatible beyond that version today.  

Timeshift takes less time making a snapshot, in my opinion, can save hours trying to sort out what went wrong in your installation.

---

