---
title: "Cant update avant window nav"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by personal-data-removed on 2008-04-30
In the update manager, i cant update the following:

avant-window-navigator-bzr
awn-core-applets-bzr
awn-manager-bzr
libawn-bzr
pythin-libawn-bzr

In the terminal when i type sudo apt-get upgrade, i get the following message:

The following package will be kept in is actual version:
avant-window-navigator-bzr 
awn-core-applets-bzr 
awn-manager-bzr 
libawn-bzr
python-libawn-bzr

What should i do to update this ?

---

### Post by RealPSL on 2008-04-30
From what I remember those packages  are not standard ubuntu packages. You can see this from the linked article

[]("http://linuxhelp.blogspot.com/2008/02/cool-awn-applets-to-adorn-your-ubuntu.html")

It explains the setup. If the author updates those packages and you configured your repository as shown in the article then you will be notified of the updatees just like other packages. Otherwise there is no need to be concerned. 

Hardy has an AWN package but I do not believe the pluginsn made the cut.

---

