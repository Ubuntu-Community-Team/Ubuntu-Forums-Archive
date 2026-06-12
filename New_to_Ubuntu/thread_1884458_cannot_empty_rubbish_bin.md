---
title: "cannot empty rubbish bin"
date: 2011-11-21
forum: New to Ubuntu
---

### Post by al.adab on 2011-11-21
all of a sudden I cannot empty the rubbish bin in Xubuntu 11.10. 

I installed Xubuntu 11.10 on one of my machines through my USB memory stick. After that, I deleted all the installation files from the memory stick, and tried to put back my documents folders. I realized I should have emptied the rubbish bin first as an error message saying (something like) "not enough space" came up. 

I then first deleted the files I'd copied on the memory stick, and proceeded to empty the rubbish bin. An error message popped up "could not delete file XY - fail to delete - do you want to skip". 

I tried *sudo rm -rf /home/username/.local/share/Trash/** to no avail (no message given in terminal). I also tried to unmount the usb stick + re-boot the machine, with no result. 

Please have a look at the attached screenshot. Any idea?

---

### Post by drs305 on 2011-11-21
These files may be owned by root but not in your normal user's trash bin - especially if they are located in a non-linux trash bin (such as .Trash-1000).

Do a search as root for all existing Trash bins:

```
sudo find / -type d -name .Trash* 
```
If you don't find the folder, try expanding it to:
```
sudo find / -type d -name *Trash* 
```

Once you find the offending folder, open nautilus as root (gksu nautilus), navigate to the Trash folder, and use SHIFT-DEL to remove it.

---

### Post by al.adab on 2011-11-21
thank you!

---

