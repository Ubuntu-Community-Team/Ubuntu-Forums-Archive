---
title: "what is the difference between Qtransmission Bittorrent Client and Transmission?"
date: 2014-03-03
forum: New to Ubuntu
---

### Post by Matrix01 on 2014-03-03
what is the difference between Qtransmission bittorrent client and Transmission?

---

### Post by Vladlenin5000 on 2014-03-03
Not much really, both do the job nice and easy. Transmission is lighter on resources but not by much and qBittorrent - not "Qtransmission bittorrent" - has a couple of features more, namely the integrated search but not something really relevant.

Transmission as default in Ubuntu is the best choice.

---

### Post by pmorch on 2014-09-24
I see one MAJOR difference:

I use the transmission daemon, so I can use the cli client and the web interface, and Qtransmission can interface to that too, so I can see the same torrents in all interfaces. The Transmission client looks nicer, has a launcher icon (Qtransmission for some reason doesn't in 12.10), but cannot interface to the daemon :-(. That is why I'm using Qtransmission.

---

### Post by Rob Sayer on 2014-09-24
Transmission is written using the GTK libraries, which are used in Unity, XFCE, and LXDE as far as ubuntu flavors go.

Qtransmission uses Qt libraries, which is used by KDE.  And also LXQt, which will be the replacement for LXDE when it's finished.

I'd recommend Qtransmission if you're using a Qt based system like Kubuntu.  It will use more resources on a GTK based system as vlad mentioned but that's just because you have to load all those extra libraries.

Otherwise differences are mostly because of the different themes in the libraries.  The underlying program is identical.

---

