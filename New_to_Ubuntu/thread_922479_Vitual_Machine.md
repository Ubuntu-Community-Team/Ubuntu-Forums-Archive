---
title: "Vitual Machine"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by georgem1234 on 2008-09-17
I am using vmware and i installed ubuntu on it and it cannot pick up and of my usb's or anything.

---

### Post by aeiah on 2008-09-17
have you added usb ports to your virtual machine? does adding a usb device from the vmware menu do anything?

if not then maybe when a usb device is plugged into a socked, it probably gets auto-mounted by windows (the host) and is thus locked from the vm. you'll probably have to unmount it in windows before ubuntu will see it. you can check if anything is being detected in ubuntu regarding usb devices by using the list usb command in a terminal like so:

```
lsusb
```

ps - i dont know if unmounting a usb device in windows is as simple as selecting 'safely remove hardware' or whatever from the taskbar but you could try it.

---

### Post by georgem1234 on 2008-09-17
Ok how can i make vmware reconise a usb?

---

### Post by howefield on 2008-09-17
what operating system are you using as host ?

---

### Post by georgem1234 on 2008-09-17
xp

---

### Post by bomanizer on 2008-09-17
Have you installed vmware tools in the guest OS? I think in a Ubuntu guest the installation files appear on the desktop when you select "install vmware tools" from the vmware menu. It's under "vm", I think...

Look for a readme-file when you have managed to get the installation files into the guest OS.

BR

---

