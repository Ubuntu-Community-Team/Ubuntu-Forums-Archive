---
title: "Dell E1505 with 12.10 Wireless issues"
date: 2012-12-29
forum: New to Ubuntu
---

### Post by appa69 on 2012-12-29
Behold as I resurrect the dead!  Hi, everyone.  I have a recent install of 12.10 on a Dell e1505 and am having the familiar wireless issue with a twist.  After installing with my lan cable plugged in, I was prompted to install updates.  After doing so, my hard wired connection ceased working.  I discovered that this was caused by the installation of an additional driver for my wireless card.  After uninstalling, I came here and found this.  I followed the steps but hung on sudo modprobe- -r b43 b44 b43legacy ssb, which gave me a FATAL: SSB IN USE error.  So I figured it had to do with the "#if the following text blah blah blah" part so I located the file in question, although damned if i know what the "comment out" means, and removed the entry. However, I was told that I didn't have permission to change the read only file, and when I tried to change the properties I was told I couldn't because I wasn't the owner.  So here I sit, waiting for someone to let me off my lan leash.

---

### Post by Dennis N on 2012-12-29
> **appa69 said:**
> Behold as I resurrect the dead!  Hi, everyone.  I have a recent install of 12.10 on a Dell e1505 and am having the familiar wireless issue with a twist.  After installing with my lan cable plugged in, I was prompted to install updates.  After doing so, my hard wired connection ceased working.  I discovered that this was caused by the installation of an additional driver for my wireless card.  After uninstalling, I came here and found this.  I followed the steps but hung on sudo modprobe- -r b43 b44 b43legacy ssb, which gave me a FATAL: SSB IN USE error.  So I figured it had to do with the "#if the following text blah blah blah" part so I located the file in question, although damned if i know what the "comment out" means, and removed the entry. However, I was told that I didn't have permission to change the read only file, and when I tried to change the properties I was told I couldn't because I wasn't the owner.  So here I sit, waiting for someone to let me off my lan leash.

You need to start a new thread for your question since this thread is old and has been marked solved by the person who started it. When others see it marked solved in the list of threads, most of them won't bother to read it.

---

### Post by dwhitney67 on 2012-12-30
> **appa69 said:**
> I was told that I didn't have permission to change the read only file, and when I tried to change the properties I was told I couldn't because I wasn't the owner.  So here I sit, waiting for someone to let me off my lan leash.

Is the usage of "sudo" available to you?  This will grant you admin rights to your linux system such that you can edit files owned by root.

---

### Post by oldos2er on 2012-12-30
Posts moved to their own thread.

---

### Post by Slaygod on 2012-12-30
> **appa69 said:**
> Behold as I resurrect the dead!  Hi, everyone.  I have a recent install of 12.10 on a Dell e1505 and am having the familiar wireless issue with a twist.  After installing with my lan cable plugged in, I was prompted to install updates.  After doing so, my hard wired connection ceased working.  I discovered that this was caused by the installation of an additional driver for my wireless card.  After uninstalling, I came here and found this.  I followed the steps but hung on sudo modprobe- -r b43 b44 b43legacy ssb, which gave me a FATAL: SSB IN USE error.  So I figured it had to do with the "#if the following text blah blah blah" part so I located the file in question, although damned if i know what the "comment out" means, and removed the entry. However, I was told that I didn't have permission to change the read only file, and when I tried to change the properties I was told I couldn't because I wasn't the owner.  So here I sit, waiting for someone to let me off my lan leash.


Try going into terminal, and edit the file with "sudo" in front of the command to open gedit.

For example:
> sudo gedit (file)

---

### Post by squakie on 2012-12-30
See post #7 in [this]("http://ubuntuforums.org/showthread.php?t=2077104") thread to fix your problem.  It worked for me on the same series.

You may also need to follow the 2 modules to blacklist according to the same thread.

---

