---
title: "how to uninstall kioworker"
date: 2024-06-21
forum: New to Ubuntu
---

### Post by firesdhgsht on 2024-06-21
A program called kioworker on my Kubunut 22.04 causes all sorts of problems, one of them is that it prevents downloading files from Signal desktop. 

How do I uninstall kioworker?

Thanks

---

### Post by psychohermit on 2024-06-21
sudo apt purge kioworker

-glenn

---

### Post by Holger_Gehrke on 2024-06-21
Kio is part of the base framework of KDE. It abstracts all resource accesses so they are all handled in a similar way as far as an application is concerned. kioworker is an abstract base-class for a lot of different classes for accessing specific resources (a file, a unix domain socket, various kinds of network connections). An application asks for access to a resource and gets handed an object of a specific class but that object is treated as if it was an object of the (abstract) base class. Removing kioworkers would break the whole of KDE.

Did you install signal-desktop as a snap ? If you did, then that's probably the reason for the problems. snaps are confined in various ways to protect the system from buggy or malevolent programs (note: to protect the system, not you or your data; snaps still have enough access to your stuff to ruin your day). Try installing it from [https://signal.org](https://signal.org) , they have a repository of their own from which you can install a .deb-package through apt.

Holger

---

