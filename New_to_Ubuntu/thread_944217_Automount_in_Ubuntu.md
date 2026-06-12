---
title: "Automount in Ubuntu"
date: 2008-10-11
forum: New to Ubuntu
---

### Post by graphicmist on 2008-10-11
Where is the entry for mounted drives in ubuntu...as i can see my fstab file none...that means there must be some other file for it...what is it???

---

### Post by Nepherte on 2008-10-11
To see the currently mounted devices, you can use:
```
mount
```

Though the drives mounted on startup should be listed in /etc/fstab. Besides that one, there is no other file.

---

### Post by sokopok on 2008-10-11
filesystems mounted at boot time go in /etc/fstab , use ```
mount
``` to view mounted filesystems.
automounted drives usually end up under /media/XXX , use ```
ls /media
``` or your file manager to view drives mounted there

---

### Post by graphicmist on 2008-10-12
actually u dont understand my ques.
i dont want to see the mounted partitions...
i want to see the file containing the script to mount these partitions..

---

### Post by sokopok on 2008-10-12
the filesystems mounted at boot time go in /etc/fstab

---

### Post by kansasnoob on 2008-10-12
> **graphicmist said:**
> Where is the entry for mounted drives in ubuntu...as i can see my fstab file none...that means there must be some other file for it...what is it???

Would you please be more specific about what drives you're trying to mount. If you mean mounting external drives I use "pmount" which is in synaptic. another option is "usbmount", also in synaptic.

I'm just not sure what type(s) of drive(s) you're trying to "automount".

---

### Post by bumanie on 2008-10-12
The file is /etc/fstab. In terminal type > cat /etc/fstab and you will get a read only copy of the file to look at.

---

### Post by graphicmist on 2008-10-15
u guys are not getting my ques.
when i installed ubuntu the other windows partiton get automatically mounted and there entries are not in fstab file that means there must be some other file which contains the mount entry for them...
where is that file???

---

### Post by sokopok on 2008-10-15
No need to get frustrated ;)
That will be the automounter. It detects when filesystems that are not in fstab are connected to the system and mounts them automatically, or let you mount them just by opening them in your filemanager or even cd'ing in the shell I suppose. How this works exactly, ... beats me. It just works. If you want to know more, search for automount or autofs (here or in google).
eg. [http://tldp.org/HOWTO/Automount.html](http://tldp.org/HOWTO/Automount.html) or [http://www.autofs.org/](http://www.autofs.org/)

---

