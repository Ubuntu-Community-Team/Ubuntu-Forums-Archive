---
title: "ghdl in 12.04"
date: 2012-05-15
forum: New to Ubuntu
---

### Post by idom on 2012-05-15
Hi 

I am trying to install ghdl in 12.04 by 

modi@modiultrabook:~$ sudo apt-get install ghdl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ghdl is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'ghdl' has no installation candidate

on google search it confirmed that it is figured it is removed because of gnat version problem.

Can anybody help if there is any solution for this.

Samarth

---

### Post by josephmills on 2012-05-15
You have read though this ? 
[http://ghdl.free.fr/download.html](http://ghdl.free.fr/download.html)
Hope that it helps in some sorta way but I do not have installed my self sorry. Good luck

---

### Post by idom on 2012-05-16
> **josephmills said:**
> You have read though this ? 
[http://ghdl.free.fr/download.html](http://ghdl.free.fr/download.html)
Hope that it helps in some sorta way but I do not have installed my self sorry. Good luck

Thanks I am looking for any known issues in this. I have not tried to install just google search says that gna new version might be a problem.

idom.

will try out shortly and update here in day or two

---

### Post by g000 on 2012-11-14
To install the .deb package of ghdl from the previous Ubuntu version:

1) Get the following deb packages (click on each link to download):

[LIST]
[*][ghdl_0.29+gcc4.3.4+dfsg-1+b2_amd64.deb]("http://ftp.acc.umu.se/mirror/cdimage/snapshot/Debian/pool/main/g/ghdl/ghdl_0.29+gcc4.3.4+dfsg-1+b2_amd64.deb")
[*][gnat-4.4-base_4.4.6-1ubuntu3_amd64.deb]("http://launchpadlibrarian.net/80193767/gnat-4.4-base_4.4.6-1ubuntu3_amd64.deb")
[*][libgnatprj4.4_4.4.6-1ubuntu3_amd64.deb]("http://launchpadlibrarian.net/80193773/libgnatprj4.4_4.4.6-1ubuntu3_amd64.deb")
[*][gnat-4.4_4.4.6-1ubuntu3_amd64.deb]("http://launchpadlibrarian.net/80193777/gnat-4.4_4.4.6-1ubuntu3_amd64.deb")
[*][libgnat-4.4_4.4.6-1ubuntu3_amd64.deb]("http://launchpadlibrarian.net/80193768/libgnat-4.4_4.4.6-1ubuntu3_amd64.deb")
[*][libgnatvsn4.4_4.4.6-1ubuntu3_amd64.deb]("http://launchpadlibrarian.net/80193773/libgnatprj4.4_4.4.6-1ubuntu3_amd64.deb")
[/LIST]
2) Install gcc-4.4:
```
sudo apt-get install gcc-4.4
```
3) Install the downloaded .deb packages:
```
sudo dpkg -i ghdl_0.29+gcc4.3.4+dfsg-1+b2_amd64.deb gnat-4.4_4.4.6-1ubuntu3_amd64.deb gnat-4.4-base_4.4.6-1ubuntu3_amd64.deb libgnat-4.4_4.4.6-1ubuntu3_amd64.deb libgnatprj4.4_4.4.6-1ubuntu3_amd64.deb libgnatvsn4.4_4.4.6-1ubuntu3_amd64.deb
```

---

