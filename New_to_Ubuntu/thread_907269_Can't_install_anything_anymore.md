---
title: "Can't install anything anymore"
date: 2008-09-01
forum: New to Ubuntu
---

### Post by badsheriff on 2008-09-01
I recently downloaded Ubuntu Studio 8.04.1 burnt it on a DVD and I tried running the DVD to see what it looks like on the inside and that was when my troubles began. Now, I can neither sudo apt-get anything nor can I use Synaptic Package Manager to install or update my PC. Here's the error message am getting "An error occured please run Package Manager from the right-click menu or apt-get ins a terminal to see what's wrong. The error message was 'Error: opening the cache (E: Type 'niverse' is not known on line 63 in sources list /etc/apt/sources.list, E:The list of sources could not be read.) This usually means that your installed packages have unmet dependencies.

Could anyone please tell me what to do.

Any help would be highly appreciable.

---

### Post by limasierra on 2008-09-01
As I don't know why that happened, I recommed you to burn a live cd of the latest ubuntu and start it (but don't install it yet). Once it started type in the terminal ```
sudo mount /mnt/sda1 /media/sda1
```Go to /media/sda1/home/yourusername and copy your documents to an usb drive. Finally, reinstall ubuntu.

---

### Post by halitech on 2008-09-01
open a terminal (Applications - Accessories - terminal) and type in
```
cat /etc/apt/sources.list
``` and post the output here

---

### Post by halitech on 2008-09-01
> **limasierra said:**
> Finally, reinstall ubuntu.

isn't that an extreme way of fixing 1 line in sources.list?

---

### Post by knattlhuber on 2008-09-01
> **badsheriff said:**
> I recently downloaded Ubuntu Studio 8.04.1 burnt it on a DVD and I tried running the DVD to see what it looks like on the inside and that was when my troubles began. Now, I can neither sudo apt-get anything nor can I use Synaptic Package Manager to install or update my PC. Here's the error message am getting "An error occured please run Package Manager from the right-click menu or apt-get ins a terminal to see what's wrong. The error message was 'Error: opening the cache (E: Type 'niverse' is not known on line 63 in sources list /etc/apt/sources.list, E:The list of sources could not be read.) This usually means that your installed packages have unmet dependencies.

Could anyone please tell me what to do.

Any help would be highly appreciable.

You have a typo in line 63 of '/etc/apt/sources.list'. Once you fix that, everything will be fine. No need for re-installation...

---

### Post by badsheriff on 2008-09-01
Hey, I got it, i just typed this 'sudo gedit /etc/apt/sources.list' and I deleted the corrupt line.

Thanks for all your support.

---

### Post by oldos2er on 2008-09-01
> **badsheriff said:**
> Hey, I got it, i just typed this 'sudo gedit /etc/apt/sources.list' and I deleted the corrupt line.

Thanks for all your support.

 Please use "gksudo" in place of "sudo" when running graphical apps. Here's why:
[http://psychocats.net/ubuntu/graphicalsudo](http://psychocats.net/ubuntu/graphicalsudo)

---

