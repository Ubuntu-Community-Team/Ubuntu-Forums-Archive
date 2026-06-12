---
title: "Bluetooth Trouble"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by a.campbell.tx on 2008-09-17
Howdy guys- This is my first post, and I suppose it fits in the beginner talk forum. I've been using Linux for a while now, but have just jumped to Ubuntu, and enjoy it thoroughly. I was curious about KDE 4 so I downloaded and installed it alongside Gnome. By the way, Im Using Ubuntu 8.04. My problem comes from the boot screen which runs beautifully until it gets to "Starting Bluetooth" and apparently stops booting. I don't have Bluetooth, and also didn't have this problem before KDE. I am having to use my windows partition. What do I do? Thanks in advance.

Alex

---

### Post by karlr42 on 2008-09-17
If you don't need bluetooth, try this:
You have to edit a file in linux from Windows, install [fs-driver](http://www.fs-driver.org/), then navigate to
```

/etc/modprobe.d/blacklist
```
Basically, a file that's a list of modules NOT to use.

Enter this at the end of the file:
```

blacklist hci_usb
```
Reboot and see what happens!

---

### Post by a.campbell.tx on 2008-09-17
thanx karlr42, now i can get into the recovery command line mode, but during normal boot, it still hangs up on me. Do you have any other ideas?

---

