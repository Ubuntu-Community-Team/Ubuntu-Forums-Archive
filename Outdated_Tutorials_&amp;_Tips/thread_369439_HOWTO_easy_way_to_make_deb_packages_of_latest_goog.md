---
title: "HOWTO: easy way to make deb packages of latest googleearth and flashplugin-nonfree"
date: 2007-02-24
forum: Outdated Tutorials &amp; Tips
---

### Post by ruibernardo on 2007-02-24
Hi everyone,

today I stumbled  in this [page]("http://www.forumdebian.com.br/topico-1702_Como_instalar_google_earth_.html") (in portuguese) in the internet while looking for a way to make a deb package for GoogleEarth. 

To resume, it explains how to make a deb package for GoogleEarth in Debian distro.

Well, I tried it to see if it worked in Ubuntu. Of course I didn't add the debian repository. Instead I've downloaded the deb package and installed it. The I typed "make-googleearth-package" (no sudo) and it made a deb package of GoogleEarth after it downloaded it automaticaly! No redistribution! After it's only a "sudo dpkg -i" and that's it.

How I did it for **GoogleEarth**:

```
wget [http://ftp.debian.org/debian/pool/contrib/g/googleearth-package/googleearth-package_0.0.5_all.deb](http://ftp.debian.org/debian/pool/contrib/g/googleearth-package/googleearth-package_0.0.5_all.deb)

sudo dpkg -i googleearth-package_0.0.5_all.deb

make-googleearth-package

sudo dpkg -i googleearth_4.0.2735.0-1_i386.deb

```[FONT=System] I've searched a little further in [/FONT][http://www.debian.org/distrib/packages](http://www.debian.org/distrib/packages)[FONT=System] and found another deb to make the latest flashplugin-nonfree on a deb file. 

Here it is for **flashplugin-nonfree**:

[/FONT]
```
 wget [http://ftp.debian.org/debian/pool/contrib/f/flashplugin-nonfree/flashplugin-nonfree_9.0.31.0.2_i386.deb](http://ftp.debian.org/debian/pool/contrib/f/flashplugin-nonfree/flashplugin-nonfree_9.0.31.0.2_i386.deb)

sudo dpkg -i flashplugin-nonfree_9.0.31.0.2_i386.deb
```Here is a more debian way to install those programs that still aren't in the repos (and may never be)! 

I think that those packages should be made available in Ubuntu repos.

Worked on Ubuntu 6.10 Edgy Eft.

---

