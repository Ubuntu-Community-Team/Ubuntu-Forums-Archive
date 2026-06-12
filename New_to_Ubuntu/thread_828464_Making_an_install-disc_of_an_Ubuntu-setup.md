---
title: "Making an install-disc of an Ubuntu-setup"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by ArnsteinK on 2008-06-13
A friend of me who is a total noob wants to try Ubuntu. He don't know anything about linux(and barely anything about windows), so I got the idea that I can install it on my computer, and customise stuff(install the programs I know he wants to use etc.) and then make an install-disc of it, so that he installs it like a normal Ubuntu. Can this be done?

---

### Post by drs305 on 2008-06-13
I think there are applications that can make a distribution cd but it is probably more complicated than what you are looking for. One thing you can do is make a list of all the installed apps on your machine and then put it on his machine. Then he runs the command and it will install all the same apps.

To save the list of apps (on Desktop named installed-pkgs):
```
sudo dpkg --get-selections >~/Desktop/installed-pkgs
```

To put on new computer, copy file installed-pkgs to Desktop, then:
```
sudo dpkg --clear-selections
dpkg --set-selections <~/Desktop/installed-pkgs 	
sudo apt-get dselect-upgrade 

```

---

### Post by dnairb on 2008-06-13
Found this page: [http://sudan.ubuntuforums.com/showthread.php?t=688872](http://sudan.ubuntuforums.com/showthread.php?t=688872)

I haven't tried this, so I don't know how easy/difficult it is to do.

---

### Post by ArnsteinK on 2008-06-13
Thanks! I'll check it out!

---

### Post by Joeb454 on 2008-06-13
I'm not 100% sure, but I think you can use "RemasterSys" for this :) You may want to do some research on that

---

### Post by alienexplorers on 2008-06-13
I use a program called remastersys.  It creates a .iso file that can be burnt to a DVD.  You can either make a backup copy or distribution copy.  It can be found at:
> [http://www.remastersys.klikit-linux.com/](http://www.remastersys.klikit-linux.com/)

---

### Post by nkri on 2008-06-13
If I were you, I would try PartImage.  It is a GUI program run from the terminal and it makes an ISO file of entire hard disk partitions.  You can then burn the ISO to a CD and put it on another computer (I have not actually tried putting an image on another computer, it's just what I've heard from the forums and such).  Good luck!

---

### Post by expatCM on 2008-10-07
This link may help if you are wishing to replicate your setup including your settings 
[http://ubuntuforums.org/showthread.php?t=688872](http://ubuntuforums.org/showthread.php?t=688872)

---

### Post by cj2003 on 2008-10-07
There's a couple of guides to remastersys on Ubuntu here:

[Best Way To Create Your Own Ubuntu]("http://ubuntu-news.net/modules/news/article.php?storyid=4276")

[Make your own Ubuntu! ]("http://ubuntu-news.net/modules/news/article.php?storyid=4928")

---

### Post by expatCM on 2008-10-07
There is a short tutorial on the forums at this link
[http://ubuntuforums.org/showthread.php?p=5917726#post5917726](http://ubuntuforums.org/showthread.php?p=5917726#post5917726)

---

