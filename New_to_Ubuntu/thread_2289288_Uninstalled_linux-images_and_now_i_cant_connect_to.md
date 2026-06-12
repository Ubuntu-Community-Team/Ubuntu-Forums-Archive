---
title: "Uninstalled linux-images and now i cant connect to wifi or insert a usb"
date: 2015-08-02
forum: New to Ubuntu
---

### Post by chmod7772 on 2015-08-02
I uninstalled a bunch of linux images with a wildcard command like `sudo apt-get remove linux-image-3.16-3*`
Now i can only boot my computer but can't connect to the internet or plug in a usb to my lenovo yoga 2 13 computer.

How do i fix this?

---

### Post by oneindelijk on 2015-08-02
download the .deb files and reinstall them with dpkg -i

---

### Post by oneindelijk on 2015-08-02
I suppose you need these :
[URL="http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.16.3-utopic/"]http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.16.3-utopic/
[/URL]Are you on Ubuntu 14.10 ?

---

### Post by Vladlenin5000 on 2015-08-03
> **oneindelijk said:**
> Are you on Ubuntu 14.10 ?

^^^^
This... If you are then you should be aware that's an EoL, unsupported, release. Instead of trying to fix what you broke, do your backups and install from scratch 14.04 LTS or 15.04.

---

