---
title: "Can't mount WD WhiteLight Network drive"
date: 2013-09-05
forum: New to Ubuntu
---

### Post by dod1mcb1 on 2013-09-05
Hello
After switching from ubuntu to lubuntu i can't acces my WD white Light network drive. There was no problem on ubuntu there is with lubuntu 
when i'm going to File manager PCManFM>Go>Network Drives>MYBookWorld
I got message: "the specified location is not mounted"
Although i can acces disk management through web browser
Please help

---

### Post by Jonathan Precise on 2013-09-05
> **dod1mcb1 said:**
> Hello
After switching from ubuntu to lubuntu i can't acces my WD white Light network drive. There was no problem on ubuntu there is with lubuntu 
when i'm going to File manager PCManFM>Go>Network Drives>MYBookWorld
I got message: "the specified location is not mounted"
Although i can acces disk management through web browser
Please help

Install nautilus, the file-manager used with ubuntu. In network, choose your drive. That should mount it. (Did I mention that nautilus also sets the background!?. If you want to change the background that nautilus sets, install gnome-control-center. Then run it, and choose background. Then change it to your liking. To always use the nautilus background, add this to autostart: Command: "nautilus -n". (without quotes).).

---

### Post by Dennis N on 2013-09-05
Try Gigolo:

[http://www.maketecheasier.com/manage-remote-filesystems-with-gigolo/2013/04/06](http://www.maketecheasier.com/manage-remote-filesystems-with-gigolo/2013/04/06)

It's in the Ubuntu repositories.

---

