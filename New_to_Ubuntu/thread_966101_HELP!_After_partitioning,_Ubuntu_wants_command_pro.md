---
title: "HELP! After partitioning, Ubuntu wants command prompt"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by gerhardcbad on 2008-11-01
After I partitioning during installation, and after I've put in my username and password, I'm asked for a command prompt next to this: gerhard@ubuntu$:  I've tried boot. Having no background on command prompts I'm lost. I'm using Ubuntu 8.04.1 on a Toshiba Satelliet pro with Windows XP. Did I use the wrong CD? and what is the alternative CD that people mention om the forums? What is also confusing is that it says Ubuntu 8.04.1_**server**. The server part looks wrong. Last question for now (I promise!). If I decide to solve this problem by downloading the Ubuntu 8.10, do I have to uninstall 8.04.1 first or will it write over it?
Come on good people help a brother out here!

---

### Post by lH)4~mK0e on 2008-11-01
Sounds like you got the wrong disc.  If you go to the website and download it, there is a tab that says Desktop and another that says Server.  Make sure you are using the Desktop section and try to download again.  I would suggest 8.04 for the time being.  You shouldn't have to modify much on the reinstall, just do NOT use Guided: Use Entire Disk during the partition phase of the install or you may lose windows.

---

### Post by PocketDog on 2008-11-01
The server edition doesn't come with a GUI. To get one, look [here](http://ubuntuforums.org/showthread.php?t=37713) (Installing gnome with server edition)

---

### Post by ugm6hr on 2008-11-01
> **gerhardcbad said:**
> What is also confusing is that it says Ubuntu 8.04.1_**server**. The server part looks wrong.
The server part is wrong (for you). As mentioned - sounds like you want the "desktop" version - which is for regular computing use.  The server version is for servers (if you don't know what that is - don't worry), and has no GUI.  It is possible to add a GUI desktop to the server edition if you have ethernet connection to the internet.

>  If I decide to solve this problem by downloading the Ubuntu 8.10, do I have to uninstall 8.04.1 first or will it write over it?
Come on good people help a brother out here!
If you install 8.10, you will have to use the "manual" installation option and tell it which partition to use (and format it).  Otherwise - just delete the 8.04 partitions and tell it to use the "Largest free space" option.  Remember - you want 8.10 desktop (i.e. not server!)

> and what is the alternative CD that people mention om the forums? 
The alternative CD is an install only CD which does not have a GUI during the install process.  It is easy enough to follow (like the server CD you used), but does not give you the advantage of knowing whether your hardware is compatible before installation, and will not let you try it out like the LiveCD (desktop).

---

### Post by gerhardcbad on 2008-11-05
Thanks everyone!):P

---

