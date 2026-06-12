---
title: "[SOLVED] If I installed Ubuntu using Wubi......."
date: 2008-05-14
forum: New to Ubuntu
---

### Post by josh995 on 2008-05-14
Well, I want to start over with Ubuntu. I have messed it up beyond repair for my new Ubuntu knowledge. I love the fast performance of Ubuntu, but I have no idea how to work it. I've installed way too many programs, and I have no idea how to delete them. Windows has the simple "uninstall a program" but Ubuntu has... well, I don't know!!!!

I just want to uninstall Ubuntu, and start all over.

But, when I installed ubuntu with Wubi, i did 30GB's for Ubuntu.

If I go to "uninstall a program" on Windows, will it delete everything, and take my hard drive back to normal, as if I never partitioned it? Or, will I have to wipe my hard drive and re-install windows or something?

Please respond using the simplest terms, I know none of the Linux terms I see on here...

---

### Post by PinkFloyd102489 on 2008-05-14
If you want to get rid of Ubuntu completely, just remove Wubi from inside of Windows. FYI, Wubi doesnt partition. It drops a file the size that you specify for the HD space and stores everything Ubuntu related in that file, similar to how VMWare works.

You can remove programs in Ubuntu using the Add/Remove program. If you want to get a bit more technical, you can see all of the packages installed on your system by opening a terminal and executing this command: 

```
sudo dpkg --get-selections > installed-software
```

And then open the file called "installed-software" to see everything installed.

---

### Post by SunnyRabbiera on 2008-05-14
also there is synaptic, a advanced tool to install/uninstall software in ubuntu.

---

### Post by dnns123 on 2008-05-14
Wait wait wait... you have Ubuntu as your system? or just the Wubi?
If its the system, you can uninstall the certain programs you dont like using the Synaptic Package Manager in System->Administration->Synaptic
It's messy at first, but its complete

---

