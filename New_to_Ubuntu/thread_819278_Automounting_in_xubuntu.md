---
title: "Automounting in xubuntu"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by hebebl on 2008-06-05
xubuntu fails to recognize my windows partition and each time i have to enter the code manually to get it working. Where do i set the automount settings for the partition? Thanks in advance.

---

### Post by bumanie on 2008-06-05
Generally one would manually edit /etc/fstab, however with ntfs-3g one can enable that via synaptic. Mark ntfs-3g and ntfs-config for installation. The go Applications --> System Tools and set up your ntfs hard drive the changes are automatically registered in /etc/fstab

---

### Post by rraj.be on 2008-06-05
You can set it in

```
NTFS CONFIGURATION TOOL.
```


select your mount point and hard disk and click apply.

It will show you a pop up window and in that check
```

Enable write access to internal device.
```

Next time when you reboot all your windows drives will be auto mounted

---

