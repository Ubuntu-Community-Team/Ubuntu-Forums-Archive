---
title: "Is it possible changing the Desktop Environment of Ubuntu?"
date: 2014-07-16
forum: New to Ubuntu
---

### Post by Jonathan_Vazquez on 2014-07-16
Hi, im sorry if this has been posted elsewhere, i'm new here so i'm a bit confused as well as been new to Linux Ubuntu itself! 
I'm a bit excited to be part of the linux community. I believe linux in its own is more capable than what OS X and Windows has to offer!
Anyways, my question is this, can i change the look of the desktop? I'm not a big fan of having the Icon on the left side since my computer (laptop) screen is a tad small (13"), it takes more room and that is really a bother with me. Is there anyway to make like windows style (i think its Kfc)? All opinion and helps will be 100% appreciate ! Thanks !

---

### Post by Dennis N on 2014-07-16
You can install an additional desktop environment such as xfce4 or lxde and have that option at login.

---

### Post by slickymaster on 2014-07-16
Like Dennis N mentioned, you can install additional desktop environments in your Ubuntu installation.

**Xfce**
Xfce is a lightweight desktop environment. It aims to be fast and low on system resources, while still being visually appealing and user friendly. It comes with various [additional apps and panel plug-ins]("http://goodies.xfce.org/") which greatly enhance the functionality of the DE.
To install it just run the following command in a terminal window:```
sudo apt-get install xubuntu-desktop
```

**LXDE**
LXDE is an extremely light desktop environment that focuses on high performance and low resource usage. It is currently the default desktop environment used by Lubuntu.
To install it just run the following command in a terminal window:```
sudo apt-get install lubuntu-desktop
```

Besides the ones you asked, you also have [GNOME]("http://www.gnome.org/gnome-3/"), [KDE]("http://www.kde.com/") and a few others.

---

### Post by Dennis N on 2014-07-16
Before making any changes, you should be aware that reversing the installation of an additional DE or (even worse) an entire desktop (such as lubuntu-desktop) is difficult to do. Read this thread:

[http://ubuntuforums.org/showthread.php?t=2231923](http://ubuntuforums.org/showthread.php?t=2231923)

---

### Post by vasa1 on 2014-07-16
And this thread too: [http://ubuntuforums.org/showthread.php?t=2234646](http://ubuntuforums.org/showthread.php?t=2234646)

---

### Post by grahammechanical on 2014-07-16
I do not understand what you mean by "icon on the left." Do you mean the Launcher? That panel on the left side of the screen that holds icons for the File Manager, Firefox and System Settings and other applications?

We can reduce the size of the Launcher. Open System Settings and go to Appearance>Behaviour tab and there is a slider that will reduce to size of the Launcher. We can also Autohide the Launcher so that it only appears when we move the mouse pointer to the left side of the screen.

If you like Microsoft Windows then use Microsoft Windows but do not expect the developers of Free and Open Source Software (FOSS) to agree with you. Making free clones of a Microsoft operating system is not their reason for writing computer code.

Regards.

---

### Post by ibjsb4 on 2014-07-16
```
sudo apt-get install gnome-session-flashback
```

Will give you the old school look.

[https://www.google.com/search?q=gnome+flashback+pics&client=ubuntu&hs=dFs&channel=fs&tbm=isch&tbo=u&source=univ&sa=X&ei=cODGU_-YJcLTiwL8zYDIDA&ved=0CB4QsAQ&biw=1280&bih=655](https://www.google.com/search?q=gnome+flashback+pics&client=ubuntu&hs=dFs&channel=fs&tbm=isch&tbo=u&source=univ&sa=X&ei=cODGU_-YJcLTiwL8zYDIDA&ved=0CB4QsAQ&biw=1280&bih=655)

---

