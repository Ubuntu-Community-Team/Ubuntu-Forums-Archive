---
title: "upgrade from feisty to gutsy failed"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by rabbix2 on 2008-08-16
Tried to upgrade from feisty to gutsy using the upgrading function under System. Got the following message:
Failed to fetch [http://se.archive.ubuntu.com/ubuntu/dists/edgy/universe/source/Sources.gz](http://se.archive.ubuntu.com/ubuntu/dists/edgy/universe/source/Sources.gz) 404 Not Found
Failed to fetch [http://se.archive.ubuntu.com/ubuntu/dists/edgy-backports/main/binary-i386/Packages.gz](http://se.archive.ubuntu.com/ubuntu/dists/edgy-backports/main/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://se.archive.ubuntu.com/ubuntu/dists/edgy-backports/restricted/binary-i386/Packages.gz](http://se.archive.ubuntu.com/ubuntu/dists/edgy-backports/restricted/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://se.archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/binary-i386/Packages.gz](http://se.archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://se.archive.ubuntu.com/ubuntu/dists/edgy-backports/multiverse/binary-i386/Packages.gz](http://se.archive.ubuntu.com/ubuntu/dists/edgy-backports/multiverse/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://se.archive.ubuntu.com/ubuntu/dists/edgy-backports/main/source/Sources.gz](http://se.archive.ubuntu.com/ubuntu/dists/edgy-backports/main/source/Sources.gz) 404 Not Found
Failed to fetch [http://se.archive.ubuntu.com/ubuntu/dists/edgy-backports/restricted/source/Sources.gz](http://se.archive.ubuntu.com/ubuntu/dists/edgy-backports/restricted/source/Sources.gz) 404 Not Found
Failed to fetch [http://se.archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/source/Sources.gz](http://se.archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/source/Sources.gz) 404 Not Found
Failed to fetch [http://se.archive.ubuntu.com/ubuntu/dists/edgy-backports/multiverse/source/Sources.gz](http://se.archive.ubuntu.com/ubuntu/dists/edgy-backports/multiverse/source/Sources.gz) 404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/source/Sources.gz) 404 Not Found

What do I do now?

---

### Post by Majorix on 2008-08-16
Try changing your mirror from within Synaptic. If that works, that means the Swedish servers are probably down.

---

### Post by sharks on 2008-08-16
try changing it to main server(system---administration---software sources).

---

### Post by rabbix2 on 2008-08-16
It is main already :(

---

### Post by rabbix2 on 2008-08-16
Can this be of any help?:
When I open Synaptic, I get the following error message:

W: Duplicate sources.list entry cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/main Packages (/var/lib/apt/lists/Ubuntu%207.04%20%5fFeisty%20Fawn%5f%20-%20Release%20i386%20(20070415)_dists_feisty_main_binary-i386_Packages)
W: Duplicate sources.list entry cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/restricted Packages (/var/lib/apt/lists/Ubuntu%207.04%20%5fFeisty%20Fawn%5f%20-%20Release%20i386%20(20070415)_dists_feisty_restricted_binary-i386_Packages)
W: Duplicate sources.list entry cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/main Packages (/var/lib/apt/lists/Ubuntu%207.04%20%5fFeisty%20Fawn%5f%20-%20Release%20i386%20(20070415)_dists_feisty_main_binary-i386_Packages)
W: Duplicate sources.list entry cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/restricted Packages (/var/lib/apt/lists/Ubuntu%207.04%20%5fFeisty%20Fawn%5f%20-%20Release%20i386%20(20070415)_dists_feisty_restricted_binary-i386_Packages)
W: Duplicate sources.list entry cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/main Packages (/var/lib/apt/lists/Ubuntu%207.04%20%5fFeisty%20Fawn%5f%20-%20Release%20i386%20(20070415)_dists_feisty_main_binary-i386_Packages)
W: Duplicate sources.list entry cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/restricted Packages (/var/lib/apt/lists/Ubuntu%207.04%20%5fFeisty%20Fawn%5f%20-%20Release%20i386%20(20070415)_dists_feisty_restricted_binary-i386_Packages)
W: Duplicate sources.list entry cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/main Packages (/var/lib/apt/lists/Ubuntu%207.04%20%5fFeisty%20Fawn%5f%20-%20Release%20i386%20(20070415)_dists_feisty_main_binary-i386_Packages)
W: Duplicate sources.list entry cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/restricted Packages (/var/lib/apt/lists/Ubuntu%207.04%20%5fFeisty%20Fawn%5f%20-%20Release%20i386%20(20070415)_dists_feisty_restricted_binary-i386_Packages)
W: Duplicate sources.list entry cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/main Packages (/var/lib/apt/lists/Ubuntu%207.04%20%5fFeisty%20Fawn%5f%20-%20Release%20i386%20(20070415)_dists_feisty_main_binary-i386_Packages)
W: Duplicate sources.list entry cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/restricted Packages (/var/lib/apt/lists/Ubuntu%207.04%20%5fFeisty%20Fawn%5f%20-%20Release%20i386%20(20070415)_dists_feisty_restricted_binary-i386_Packages)
W: Duplicate sources.list entry cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/main Packages (/var/lib/apt/lists/Ubuntu%207.04%20%5fFeisty%20Fawn%5f%20-%20Release%20i386%20(20070415)_dists_feisty_main_binary-i386_Packages)
W: Duplicate sources.list entry cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/restricted Packages (/var/lib/apt/lists/Ubuntu%207.04%20%5fFeisty%20Fawn%5f%20-%20Release%20i386%20(20070415)_dists_feisty_restricted_binary-i386_Packages)
W: Duplicate sources.list entry cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/main Packages (/var/lib/apt/lists/Ubuntu%207.04%20%5fFeisty%20Fawn%5f%20-%20Release%20i386%20(20070415)_dists_feisty_main_binary-i386_Packages)
W: Duplicate sources.list entry cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/restricted Packages (/var/lib/apt/lists/Ubuntu%207.04%20%5fFeisty%20Fawn%5f%20-%20Release%20i386%20(20070415)_dists_feisty_restricted_binary-i386_Packages)
W: Duplicate sources.list entry cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/main Packages (/var/lib/apt/lists/Ubuntu%207.04%20%5fFeisty%20Fawn%5f%20-%20Release%20i386%20(20070415)_dists_feisty_main_binary-i386_Packages)
W: Duplicate sources.list entry cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/restricted Packages (/var/lib/apt/lists/Ubuntu%207.04%20%5fFeisty%20Fawn%5f%20-%20Release%20i386%20(20070415)_dists_feisty_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_feisty-security_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_feisty-security_restricted_binary-i386_Packages)

---

### Post by rabbix2 on 2008-08-16
Does it help to make a "fresh install" of gutsy instead? If I do, will I loose all the files and programs I have installed since I upgraded to feisty?

---

