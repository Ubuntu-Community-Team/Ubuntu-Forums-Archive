---
title: "pls help me..&gt;"
date: 2008-10-22
forum: New to Ubuntu
---

### Post by saki.star on 2008-10-22
how to disable and enable the usb in ubuntu linus in os level not in bios settings

---

### Post by saki.star on 2008-10-22
> **saki.star said:**
> how to disable and enable the usb in ubuntu linus in os level not in bios settings
how to disable and enable the usb in ubuntu linux in os level not in bios settings

---

### Post by Hexagoon on 2008-10-22
To disable the usb controller (bad idea if you have usb keyboard or mouse), you use the following commands:

```
sudo sh -c 'echo blacklist ehci_hcd > /etc/modprobe.d/blacklist-ehci'
sudo sh -c 'echo blacklist uhci_hcd > /etc/modprobe.d/blacklist-uhci'
sudo sh -c 'echo blacklist ohci_hcd > /etc/modprobe.d/blacklist-ohci'
sudo update-initramfs -u
```

to enable usb controller again you remove the files you create in the previous commands (/etc/modprobe.d/blacklist-ehci etc), and run this command again:

```
sudo update-initramfs -u
```

---

### Post by hyper_ch on 2008-10-22
It is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;) 

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse brackets around (each) output. That makes it also easier to read.

---

### Post by billgoldberg on 2008-10-22
The answer has been given.

In case you meant, how to correctly eject a usb device, open nautilus (places -> home) and right click the usb device and select unmount.

---

