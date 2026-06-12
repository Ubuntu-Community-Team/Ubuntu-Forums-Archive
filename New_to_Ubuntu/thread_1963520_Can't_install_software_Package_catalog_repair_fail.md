---
title: "Can't install software Package catalog repair failing"
date: 2012-04-22
forum: New to Ubuntu
---

### Post by ljt3759 on 2012-04-22
I'm running a fresh 64bit installation of 11.10 only installed today (I decided to move on from wubi to a proper installation after getting a few problems). I was just downloading all my previous applications and got an error, I am always getting asked to repair the Package catalog.

It tells me to enter the command:
```
sudo apt-get install -f
```

When I do this I get another error:
```
dpkg-deb (subprocess): data: internal gzip read error: '<fd:0>: data error'
dpkg-deb: error: subprocess <decompress> returned error exit status 2
dpkg: error processing /var/cache/apt/archives/openarena-081-textures_0.8.5split-1ubuntu1_all.deb (--unpack):
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2
No apport report written because the error message indicates an issue on the local system
         Errors were encountered while processing:
 /var/cache/apt/archives/openarena-081-textures_0.8.5split-1ubuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Does anyone know how I could fix this? It's not allowing me to install or delete any software. (Via terminal or the ubuntu software center)

---

### Post by Krytarik on 2012-04-22
The cached deb package is corrupt, either clear the cache completely:
```
sudo apt-get clean
```Or just remove the concerning file:
```
sudo rm /var/cache/apt/archives/openarena-081-textures_0.8.5split-1ubuntu1_all.deb
```Then run again:
```
sudo apt-get install -f
```If you keep on getting this kind of issues, you have a failing disk.

Regards.

---

