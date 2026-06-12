---
title: "Howto: Gimp 2.3.10 on Ubuntu Edgy"
date: 2006-09-17
forum: Outdated Tutorials &amp; Tips
---

### Post by picpak on 2006-09-17
Please note: it says **Edgy**. This won't work on Dapper. At all. Unless you want to upgrade half your system. In that case, get Debian.

I know 2.3.11 is released, but there are no packages for it yet.

1) Download gimp, gimp-data, libgimp2.0 2.3.10, and libwmf0.2-7 0.2.8.4:

```
wget http://sadleder.de/debian/gimp_2.3.10-1.1_i386.deb
wget http://sadleder.de/debian/gimp-data_2.3.10-1.1_all.deb
wget http://sadleder.de/debian/libgimp2.0_2.3.10-1.1_i386.deb
wget http://ftp.debian.org/debian/pool/main/libw/libwmf/libwmf0.2-7_0.2.8.4-2_i386.deb
```

2) Install them:

```
sudo dpkg -i gimp_2.3.10-1.1_i386.deb gimp-data_2.3.10-1.1_all.deb libgimp2.0_2.3.10-1.1_i386.deb libwmf0.2-7_0.2.8.4-2_i386.deb
```


3) Try it out:

```
gimp
```


*Note: Your shortcuts may still point to /usr/bin/gimp-remote-2.2. In that case:

```
sudo ln -s /usr/bin/gimp-2.3 /usr/bin/gimp-remote-2.2
```

Enjoy!

---

