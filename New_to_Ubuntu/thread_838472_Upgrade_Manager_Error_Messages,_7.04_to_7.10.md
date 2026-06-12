---
title: "Upgrade Manager Error Messages, 7.04 to 7.10"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by Altin on 2008-06-23
Hi

I installed Ubuntu 6.10 from CD-ROM and upgraded to 7.04 by editing /etc/apt/sources.list, as detailed on the Ubuntugeek.com website. I now want to upgrad again to 7.10 (and then 8.04), but am getting error messages from my upgrade manager. Im following the process described again on Ubuntugeek.com, but dont get any further than 'Preparing the Upgrade' when a pop up message says:

'Error during update
A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.

Failed to fetch cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/dists/feisty/main/binary-i386/Packages.gz Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/dists/feisty/restricted/binary-i386/Packages.gz Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs'

I tried typing'apt-cdrom' into the termrminal, but get a menu offering further commands and options, and dont know which to choose. I dont want to try editing /etc/apt/sources.list yet as I havent seen it described anywhere, and dont want to risk it damaging my system in case it doesnt work with this distribution.

Can anyone offer any ideas please.

Thanks

---

### Post by avtolle on 2008-06-23
In Synaptic, uncheck the CD-ROM as a source, reload your sources, and try it again.

---

### Post by Altin on 2008-06-27
Thanks. That worked like a charm.

---

