---
title: "RPM to DEB"
date: 2008-07-31
forum: New to Ubuntu
---

### Post by ozbolt on 2008-07-31
So there is the picture:
[[img]http://shrani.si/t/2C/7I/2825J73O/snapshot1.jpg[/img]](http://shrani.si/?2C/7I/2825J73O/snapshot1.png)
What to do?

---

### Post by jualin on 2008-07-31
so what's the question?

---

### Post by Technoviking on 2008-07-31
You can install alien to convert a rpm to deb, but I would not suggest it. The file structure between the rpm's distro  maybe different the Ubuntu's and cause problems of files being put in the wrong area.

With VMware, I suggest using the .bin installer. It works great, and should install files properly.

If you want to install alien
```
sudo apt-get install alien
```

---

### Post by gjoellee on 2008-07-31
NOTE: Alien does not work every time or with all software...
if you need help installing vmware try one of those links:
[http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto](http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto)
[http://ubuntu-tutorials.com/2007/09/26/how-to-install-vmware-server-on-ubuntu-710/](http://ubuntu-tutorials.com/2007/09/26/how-to-install-vmware-server-on-ubuntu-710/)
[http://www.bauer-power.net/2008/04/installing-vmware-server-on-ubuntu-804.html](http://www.bauer-power.net/2008/04/installing-vmware-server-on-ubuntu-804.html)
[http://www.google.com/search?hl=en&q=how+to+install+vmware+in+ubuntu+8.04&btnG=Search](http://www.google.com/search?hl=en&q=how+to+install+vmware+in+ubuntu+8.04&btnG=Search)

---

### Post by jualin on 2008-07-31
I think that [this website]("http://www.howtoforge.com/converting_rpm_to_deb_with_alien") will help you.

---

### Post by neurostu on 2008-07-31
Alien does an alright job converting SIMPLE rpm's to debs.

Debs in and of them selves are relatively simple packages, however, building and maintaining a package takes some effort. Many of the ways that RPMs & debs work are similar enough for simple packages to be converted fine.

But when faced with a complex RPM like VM Ware I would be very surprised if you could get Alien to convert it properly.

You should look read up on how to install VMWare from source... there are literally hundreds of tutorials on how to do it...

---

### Post by Oldsoldier2003 on 2008-07-31
> **neurostu said:**
> Alien does an alright job converting SIMPLE rpm's to debs.

Debs in and of them selves are relatively simple packages, however, building and maintaining a package takes some effort. Many of the ways that RPMs & debs work are similar enough for simple packages to be converted fine.

But when faced with a complex RPM like VM Ware I would be very surprised if you could get Alien to convert it properly.

You should look read up on how to install VMWare from source... there are literally hundreds of tutorials on how to do it...

Agreed. My personal stance on alien is this:
Don't use it except as a last resort. Compile form source or get a binary from the developer or a reputable source.

---

### Post by bodhi.zazen on 2008-07-31
If you want to install vmware server , see this thread :

[How to VMWare in Ubuntu 8.04 - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=779934") 

In general it is better to install from source rather then convert a .rpm

---

### Post by ryanhaigh on 2008-07-31
Or the ubuntu documentation:
[https://help.ubuntu.com/community/VMware/Server](https://help.ubuntu.com/community/VMware/Server)

---

### Post by ozbolt on 2008-08-01
Thanks to everyone. I'll use alien for smaller packages if neccesary. BTW, I went your way, bodhi.zazen

---

