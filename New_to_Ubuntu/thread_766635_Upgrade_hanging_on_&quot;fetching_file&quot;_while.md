---
title: "Upgrade hanging on &quot;fetching file&quot; while using alternate CD and no network"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by 01000111 on 2008-04-25
I've downloaded the alt-CD via torrent and started the upgrade, but it hangs on "fetching file 981 of 1171".  When the install started, I clicked "NO" on the "do you want to get the latest from the internet?", and this machine currently has no network connection, so it can't be waiting for servers...  

I've tried this from a CD i burned, and from just mounting the .iso file via 

sudo mount -o loop -t iso9660 cd.iso /media/ISO

but it hangs in the same place no matter what.  What can be the problem here?

TIA
01000111

---

### Post by gsmanners on 2008-04-26
You probably should get the MD5SUMS file and check your iso with it:

md5sum -c MD5SUMS

[http://www.mirrorservice.org/sites/cdimage.ubuntu.com/cdimage/xubuntu/releases/8.04/release/MD5SUMS](http://www.mirrorservice.org/sites/cdimage.ubuntu.com/cdimage/xubuntu/releases/8.04/release/MD5SUMS)

---

