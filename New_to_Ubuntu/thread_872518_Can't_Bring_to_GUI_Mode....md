---
title: "Can't Bring to GUI Mode..."
date: 2008-07-28
forum: New to Ubuntu
---

### Post by SAMEERACEB on 2008-07-28
:(...I Have Already Installed the Server in Easy Way. But Can't Bring to GUI Mode..Can Anyone Help Me Please...?

---

### Post by eightmillion on 2008-07-28
Do you have the package, "ubuntu-desktop" installed. Try installing it with
> sudo apt-get install ubuntu-desktop

---

### Post by mcduck on 2008-07-28
There is no "GUI mode" on the server install. Most server users wouldn't want one.. ;)

You'll have to install X & some desktop environment yourself if you want them. The "ubuntu-desktop"-package witll install Gnome & all default Ubuntu applications, "kubuntu-desktop" will give KDE, and "xubuntu-desktop" XFCE4.

---

### Post by SAMEERACEB on 2008-07-28
***Eightmillion >>> Error Came Like This "E: Couldn't Find Package ubuntu-desktop" What Do I Do Now...?:( ***

---

### Post by eightmillion on 2008-07-28
Try this first...
> sudo apt-get update && sudo apt-get install ubuntu-desktop
If that doesn't work, you'll probably have to take a look at your apt sources file with...
> sudo nano /etc/apt/sources.list
and make sure these lines
> 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

don't have a # in front of them. I assume you have a working internet connection on the box?

---

### Post by SAMEERACEB on 2008-07-28
***mcduck >>> Oopps...!!! There is no GUI Mode...I didn't Know It...***

---

