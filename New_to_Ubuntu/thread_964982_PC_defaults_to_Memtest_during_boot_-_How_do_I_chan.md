---
title: "PC defaults to Memtest during boot - How do I change the default to Windows or Ubuntu"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by RichTJ99 on 2008-10-31
Hi,

Ever since I upgraded from 7.10 to 8.04 (8.10 is coming soon, my PC has been defaulting to Memtest instead of XP or Ubuntu.  Is there a way (graphically) to change the boot setting to something else (other than Memtest)?

Thanks,
Rich

---

### Post by reg4c on 2008-10-31
Hey, 

```
sudo apt-get install startupmanager
```

It will appear in System > Administration > Startup Manager.
When you start it in the first screen there will be an option saying Default OS.

Choose the one you want, click close and you're done

Cheers

---

### Post by drs305 on 2008-10-31
Here is a link to a StartUp-Manager tutorial, an app which will allow you to tweak many aspects of the grub boot loader.

[StartUp-Manager]("http://ubuntuforums.org/showthread.php?t=818177")

---

