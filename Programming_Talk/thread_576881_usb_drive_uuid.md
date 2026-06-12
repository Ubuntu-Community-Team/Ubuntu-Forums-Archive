---
title: "usb drive uuid"
date: 2007-10-15
forum: Programming Talk
---

### Post by halfsoft on 2007-10-15
Is there a way to see the UUID of given usb drive. So far I can't find any info how to get it from the shell.

---

### Post by Romanmir on 2007-10-15
The best way that I have found is to cd to /dev/disk/ there you have the choice to view by id, by path, or by uuid. (gutsy/feisty)

Hope that helps.

---

### Post by halfsoft on 2007-10-22
hal-find-by-property -–key volume.mount_point --string /media/disk

This way it returns the id of the usb disk which in the end contains it's uuid.

---

### Post by gruslo on 2009-12-03
sudo blkid

---

### Post by digitalb0y on 2010-09-13
> **gruslo said:**
> sudo blkid

Thank you Gruslo! That works great!

---

### Post by psrdotcom on 2011-09-23
Try this one also 

```

$ sudo ls -l /dev/disk/{by-id,by-label,by-uuid,by-path}

```

---

