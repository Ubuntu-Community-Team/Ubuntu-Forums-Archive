---
title: "Need help syncing an usb external memory with a folder in my pc"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by Josep CA on 2008-09-24
Hi, 
I'm a begginer in Ubuntu and I would like to know how to sync a folder in my pc with an usb external memory.
I want my usb memory to, if possible, get automatically updated every time I plug it to my machine.
Thanks in advance.

---

### Post by uidb4056 on 2008-09-24
> **Josep CA said:**
> Hi, 
I'm a begginer in Ubuntu and I would like to know how to sync a folder in my pc with an usb external memory.
I want my usb memory to, if possible, get automatically updated every time I plug it to my machine.
Thanks in advance.

You can try to install Unison, it is in the repository and you can install using Synaptic Package Manager under System->Administration menu.

See this link for more information [http://www.cis.upenn.edu/~bcpierce/unison/]("http://www.cis.upenn.edu/%7Ebcpierce/unison/")

---

### Post by Josep CA on 2008-09-24
> You can try to install Unison, it is in the repository and you can install using Synaptic Package Manager under System->Administration menu.
Thanks!
I've installed it and it seems to work fine. I am able to select a folder to sync in my machine. However in the second step Unison ask me for a second directory to sync (which is my usb external memory). In order to do this Unison asks me to use SSH, RSH or socket protocol and, later, it asks me for a host when I select SSH and RSH and asks me both for a host and a port when I select socket.
I have no idea what all this is.
Can you give me some help?

---

### Post by uidb4056 on 2008-09-24
You can set the second directory using the mount point of your USB drive (normally /media/disk/), you can add to the path a specific folder in your USB if you want.

---

