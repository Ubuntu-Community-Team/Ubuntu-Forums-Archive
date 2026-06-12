---
title: "Removing Shared folders from samba"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by modman27 on 2008-09-24
I shared out some directories with samba and now i dont want them to be shared anymore. For some reason I cannot get them to unshare. Is there some terminal command, or other way that I can accomplish this?

---

### Post by bab1 on 2008-09-25
How did you "share" the directories?  If you did it using Nautilus you can just rightt click and select remove.  I believe Gnome is the same way.  This will take a few minutes to happen.  If you browse reight after you remve the shares it is possible that you may see the shares.

Using the GUI to create shares is different from the command line configuring them in /etc/samba.smb.conf.  The GUI method stores the config as a binary in /var/lib/samba.

---

