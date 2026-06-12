---
title: "ubuntu gnome with kde"
date: 2012-10-15
forum: New to Ubuntu
---

### Post by Xyler on 2012-10-15
Is it possible to install and run both gnome and kde on Ubuntu and enjoy the best of both worlds without having to switch between them? :guitar:

---

### Post by audiomick on 2012-10-15
Not as such. You have to choose a desktop environment when you boot, and only on can run at any one time. You don't have to completely re-boot to change. You can simply log out and log back in with another DE.

However:
You can have as many desktops as you want installed, and choose which one you want at any given time. 

You can install KDE applications in a Gnome environment and vice versa. Installing the application via the software centre will bring in any dependencies, and the application should run without a problem.

Doing this will make your install "heavier", i.e. use more space on the drive. It may possibly make it marginally slower too. It is up to you to decide if that is a problem.

I am not aware of any problems using programs that were intended for one desktop environment in a different DE. Having said that, I could imagine it is possible that using kde applications in Unity may result in some odd behaviour. I do not know this for sure, though, It is just a guess.

---

### Post by Xyler on 2012-10-15
I see. I just like the mac-like gnome feature and the windows-startbutton-like kde feature. I thought that it is possible to merge them ;)

---

### Post by Xyler on 2012-10-16
I finally got what I wanted.  After installing gnome, I logged on to it and performed the following:

1. open terminal by pressing ctrl+alt+t
2. type:  sudo apt-get install plasma-desktop plasma-scriptengine-python
3. press alt+f2 and type: plasma-desktop

Now, I have both gnome and kde :D

source: [http://www.webupd8.org/2010/01/use-kde-plasma-in-gnome-ubuntu-linux.html](http://www.webupd8.org/2010/01/use-kde-plasma-in-gnome-ubuntu-linux.html)

---

