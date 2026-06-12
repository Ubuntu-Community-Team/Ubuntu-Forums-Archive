---
title: "[SOLVED] Unable to delete a few files - ghost files?"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by Dekafox on 2008-05-23
I'm running Ubuntu 8.04 x64 and just got done installing WoW via Wine to give it a try.  Now I don't have much disk space free at the moment so I deleted the installer stuff off the desktop(where I'd temporarily copied it) then tried emptying the trash.  It deleted everything except several .cab files buried in the DirectX folder under the WoW installer folder.  I tried deleting them but I get Permission Denied, and when I tried "sudo find -name .Trash*" in a terminal, it didn't find any of them.  I tried changing the perms from read only to read and write in the properties box in the trash, but it told me "Operation not supported by backend."  I was able to copy one of the files to the desktop, then change perms and delete it(permanently) just fine.  When I tried moving the files out of Trash, I also got Permission Denied.

Am I dealing with "ghost" files that'll be gone next time I reboot?  If not, is there some way to kill them permanently?

---

### Post by unutbu on 2008-05-23
In version 8.04, Trash is now located in ```
/home/[user]/.local/share/Trash
```

The command
```
sudo rm -r /home/[user]/.local/share/Trash/*
```
will erase all files in Trash.

---

### Post by Dekafox on 2008-05-23
Ah, that got it.  Thanks!

---

### Post by pigphish on 2008-06-20
had same issue in hard x86. fixed the issue. 
thanks, george

---

