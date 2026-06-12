---
title: "Updating/Installing the latest flash player"
date: 2011-12-30
forum: New to Ubuntu
---

### Post by Barry1 on 2011-12-30
hi all,
I currently have problem with installing the latest flash player (which I think think in Adobe is 11.1.102.55). I have tried to do it several times through the software centre, but when I got to upload photos in facebook or watching tv episodes online it still says that I need to install the latest flash player.
I have tried doing it through the terminal part which supposedly installs it, but still doesn't work. Also directly downloading from the adobe website, but it downloads and then comes up in file manager.

Just wondering if there is any trick to it?
Do I need to update my version of firefox to make it function? (How do i do that if i need to ?)
i have Ubuntu 11.10 and i think the latest version of flash player is 11.1.102.55
I hope people might have some ideas

---

### Post by Paddy Landau on 2011-12-30
It should work straight from the repository; perhaps the very latest version, but close to it (I'm on 11.04 and my Flash is version 11.1 r02).

Uninstall Flash; log out and in again; and from your repository (whether Ubuntu Software Centre, Synaptic Package Manager or apt-get), install:
[ubuntu-restricted-extras]("apt:ubuntu-restricted-extras")
[flashplugin-nonfree]("apt:flashplugin-nonfree")

Run Update Manager; press Check; Install Updates (if any).

Close Firefox; open it again; and check.

---

