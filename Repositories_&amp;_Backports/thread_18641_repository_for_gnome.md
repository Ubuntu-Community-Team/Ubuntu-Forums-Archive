---
title: "repository for gnome"
date: 2005-03-07
forum: Repositories &amp; Backports
---

### Post by jhands on 2005-03-07
I am trying to install gnome from the repository. I have hoary installed without x or a desktop environment. so i work from the command line. i need to installl gnome but it gives an error saying dependencies not met and some thing like gnome-office and gnome-desktop-environment. E: Packages broken.

im have this link in my sources.link file to install gnome:
[http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) hoary universe

it updates properly. but when i do apt-get install gnome it gives the above mentioned error.

i found out that this repository doesnt have the gnome-desktop folder and others needed to install gnome. is there any other link i can use to install gnome?

---

### Post by bored2k on 2005-03-07
[QUOTE=jhands]I am trying to install gnome from the repository. I have hoary installed without x or a desktop environment. so i work from the command line. i need to installl gnome but it gives an error saying dependencies not met and some thing like gnome-office and gnome-desktop-environment. E: Packages broken.

im have this link in my sources.link file to install gnome:
[http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) hoary universe

it updates properly. but when i do apt-get install gnome it gives the above mentioned error.

i found out that this repository doesnt have the gnome-desktop folder and others needed to install gnome. is there any other link i can use to install gnome?[/QUOTE]
 Add this to you're /etc/apt/sources.list

> 
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted

this should work

---

