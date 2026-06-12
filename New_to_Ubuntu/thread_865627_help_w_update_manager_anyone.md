---
title: "help w update manager anyone ??"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by essequamvideri on 2008-07-20
when i run update manager to check for updates...i get these errors in the info box after the search has completed....


GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423)]/dists/hardy/main/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423)]/dists/hardy/restricted/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

that's all i know...have tried looking for solutions but so far no luck...
any help would be great  :)

---

### Post by ejpyle on 2008-07-20
> **essequamvideri said:**
> when i run update manager to check for updates...i get these errors in the info box after the search has completed....


GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423)]/dists/hardy/main/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423)]/dists/hardy/restricted/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

that's all i know...have tried looking for solutions but so far no luck...
any help would be great  :)


you need to go SYSTEM - ADMIN  - SOFTWARE SOURCES and uncheck the CD / DVD rom options.,.....

---

### Post by dfreer on 2008-07-20
> **essequamvideri said:**
> 
GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783


This happens when you add a third party repository, and don't add their public key (which is there to prove that they are who they say they are). No harm here, but if you want to add their Public Key check out their website.

> **essequamvideri said:**
> Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423)]/dists/hardy/main/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423)]/dists/hardy/restricted/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

Both of these are referring to the repository located on your installation CD/DVD. Unless you are planning on using the CD/DVD to install packages instead of downloading them, it's safe to disable these repositories.

To disable them, follow the above advice or simply edit /etc/apt/sources.list

---

### Post by essequamvideri on 2008-07-20
thanks... will do that now ....you rock  :guitar:    ....

---

### Post by zvacet on 2008-07-21
For medibuntu type in terminal

gpg --keyserver hkp://subkeys.pgp.net --recv-keys 2EBC26B60C5A2783
gpg --export --armor 2EBC26B60C5A2783 | sudo apt-key add -

---

