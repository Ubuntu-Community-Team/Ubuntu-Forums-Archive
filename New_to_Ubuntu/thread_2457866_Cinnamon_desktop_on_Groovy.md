---
title: "Cinnamon desktop on Groovy"
date: 2021-02-11
forum: New to Ubuntu
---

### Post by wingarmac on 2021-02-11
Hi,

I have a setted in "Disks" to show/hide some drives. But it seems this doesn't apply to Cinnamon I installed on it.
The same problem occurs for other settings, like the permission of Clementine to access other drives as the one where the system is installed (personal folders only available).
how can I fix this without lag of security by enabling everything ?

Can somebody help ?

---

### Post by grahammechanical on 2021-02-11
If you installed Clementine from Ubuntu Software then it is possible that you installed a Snap packaged version of Clementine. Snap package applications are designed to be very secure. They are not allowed access to the folders on the operating system or on other drives. Only the folders in the Home directory. A music player might only be allowed to access the Music folder. It is reasoned that a music player has no need to look anywhere else for music files. It is part of the security strategy of the snap package format.

If you have the Universe repository enabled then Ubuntu Software should show you Clementine Music Player. Uninstall the snap version of Clementine and install Clementine Music player and that application should have the freedom to access any folder on any drive.

I do not have the Clementine snap installed so this advice is May Be. If you look up Clementine in Ubuntu Software you may have access to some settings (permissions) that will allow you to change things.

Regards

---

