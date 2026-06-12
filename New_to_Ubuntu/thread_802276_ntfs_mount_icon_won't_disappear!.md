---
title: "ntfs mount icon won't disappear!"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by chchandler on 2008-05-21
Well, I've been experimenting with dual-booting with XP.  I then installed ntfs-config to be able to see XP files.  Worked fine, but I have a bigger HD on the way and wasn't sure if I wanted to use ntfs-config or create a /home partition for both OS's to access.  

So, I removed ntfs-config.  But, the desktop icon for IBM_PRELOAD can't be deleted.  Even tho ntfs-config is removed from my apps, I can still browse the file system.

Suggestions?

---

### Post by Inxsible on 2008-05-21
Once you kill this session, you will not be able to. In Linux you can remove programs even if they are running (with the exception of the kernel specific packages) After you kill the X or reboot, you will not be able to use the uninstalled packages. Try hitting Ctrl + Alt + Backspace and then login again.

---

### Post by chchandler on 2008-05-21
Re-booted the laptop and I can still browse the IBM_PRELOAD and still cannot unmount it.  Odd...

---

### Post by Inxsible on 2008-05-21
how did you uninstall it ?

---

### Post by asysma on 2008-05-21
hmm..

maybe you can try this..

```

press ALT+F2 and then type "gconf-editor"

and then go to

"apps > nautilus > desktop"

then,,untick the "volumes_visible"

```

hope this working...
thanks before.. :KS

---

### Post by chchandler on 2008-05-21
> **Inxsible said:**
> how did you uninstall it ?

Applications|Add/Remove

---

### Post by chchandler on 2008-05-21
> **asysma said:**
> hmm..

maybe you can try this..

```

press ALT+F2 and then type "gconf-editor"

and then go to

"apps > nautilus > desktop"

then,,untick the "volumes_visible"

```


hope this working...
thanks before.. :KS


That did work.  I hope it's really uninstalled and un-mounted, though...

Thanks!!

---

### Post by asysma on 2008-05-21
ummm..sorry

as i know,,is not unistalled and un-mounted..

is just made the partition invisible...

thanks before.. :KS

---

