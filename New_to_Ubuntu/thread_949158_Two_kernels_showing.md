---
title: "Two kernels showing?"
date: 2008-10-15
forum: New to Ubuntu
---

### Post by GameGuru on 2008-10-15
At bootup I used to just have one kernel, memtest and Windows, now I have:

Ubuntu 8.04.1, 2.6.24-21
Ubuntu 8.04.1, 2.6.24-21 (Recovery Mode)
Ubuntu 8.04.1, 2.6.24-19
Ubuntu 8.04.1, 2.6.24-19 (Recovery Mode)
Ubuntu 8.04.1 memtest86+
Other Operating Systems
Microsoft Windows XP Professional

Why?

---

### Post by Frak on 2008-10-15
That's normal. If your system doesn't boot with the new kernels, it allows you to boot back into one that did work.

---

### Post by drs305 on 2008-10-15
This happens each time a new kernel is introduced and is normal. To tweak grub's menu list to  display only one or change the default, the simplest method is to install Startup-Manager. 

```
sudo apt-get install startupmanager
```

To Run:
System, Administration, StartUp-Manager.

Startup-Manager is a simple gui tool which will let you change a variety of grub menu options, including menu display time, default OS and kernel, colors, number of kernels to display, etc.

There is a lot of information about SUM and kernel displays in the link in my signature line. It will also tell you if and how to remove older kernels which you may no longer need.

---

