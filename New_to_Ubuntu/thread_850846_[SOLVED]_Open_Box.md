---
title: "[SOLVED] Open Box"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by deadlySniper on 2008-07-06
What Open Box do I use if I want to use it. KDE or GNOME

---

### Post by jw5801 on 2008-07-06
openbox is a window manager, it could be used to replace the native window managers in either KDE or Gnome, or it could be used as it's own desktop environment (completely seperate to KDE or Gnome or Xfce).

---

### Post by akiratheoni on 2008-07-06
You could use it instead of metacity and use it alongside KDE or GNOME, but personally I don't feel you're getting the optimal speed if you're doing that... use it standalone without KDE or GNOME and you'll get incredible speeds out of it.

---

### Post by deadlySniper on 2008-07-06
so it doesnt matter which file I download

---

### Post by jw5801 on 2008-07-06
Please give more detail in your posts. What files are you looking at, and where are you looking at them?

---

### Post by deadlySniper on 2008-07-06
[http://icculus.org/openbox/index.php/Main_Page](http://icculus.org/openbox/index.php/Main_Page) which would I use

---

### Post by akiratheoni on 2008-07-06
> **deadlySniper said:**
> so it doesnt matter which file I download

Why are you looking at files?

Here's a tutorial I made awhile ago, hopefully it'll help, I tried to make it as detailed as possible.

[http://blog.zantherus.com/2008/02/09/how-to-install-openbox-on-ubuntu-710/](http://blog.zantherus.com/2008/02/09/how-to-install-openbox-on-ubuntu-710/)

The directions are for 7.10 but it should work for 8.04.

EDIT: Openbox is already in the repositories, check out my tutorial and it'll help you.

---

### Post by atomkarinca on 2008-07-06
> **deadlySniper said:**
> [http://icculus.org/openbox/index.php/Main_Page](http://icculus.org/openbox/index.php/Main_Page) which would I use

Openbox is in the repositories:

```
sudo apt-get install openbox
```

I suggest also installing the configuration tools:

```
sudo apt-get install obmenu obconf
```

---

### Post by jw5801 on 2008-07-06
> **deadlySniper said:**
> [http://icculus.org/openbox/index.php/Main_Page](http://icculus.org/openbox/index.php/Main_Page) which would I use

Those aren't downloads. Those are guides on running OpenBox inside either Gnome or KDE, as discussed above. You can install it from the repositories:
```
sudo apt-get install openbox
``` If you want to run it standalone, log out and at the login screen click on the 'sessions' button and choose openbox from there. Otherwise take a look at the instructions on that page to match your desktop environment (Gnome if you're in a base install of Ubuntu, KDE for Kubuntu, although you can install both on either).

I'd also suggest you take a look at the 'Getting the best help' link in my signature. One line questions don't help us get to a solution for you particularly quickly. Try and give us some idea of what you've done and what you're trying to achieve.

---

### Post by deadlySniper on 2008-07-06
thanks

---

### Post by sayakb on 2008-07-06
With openbox, you can add custom startup objects by creating a script: ~/.config/openbox/autostart.sh
The script should be like:
```
#!/bin/sh
command1 &
command2 &

```
You may use [fbpanel]("http://fbpanel.sourceforge.net/") or [pypanel]("http://pypanel.sourceforge.net/") for the panel. 
[http://urukrama.wordpress.com/openbox-guide/](http://urukrama.wordpress.com/openbox-guide/) (what i used)
[http://ubuntuforums.org/showthread.php?t=192106](http://ubuntuforums.org/showthread.php?t=192106)

---

### Post by deadlySniper on 2008-07-06
Ya, I'm having problems. I cant get this to work inside terminal
	cp /etc/xdg/openbox/menu.xml ~/.config/openbox/menu.xml 

tar xzvf ~/obmenu-1.0.tar.gz
	cd obmenu-1.0
 and the path is right in my file system

---

### Post by akiratheoni on 2008-07-06
> **deadlySniper said:**
> Ya, I'm having problems. I cant get this to work inside terminal
	cp /etc/xdg/openbox/menu.xml ~/.config/openbox/menu.xml 

tar xzvf ~/obmenu-1.0.tar.gz
	cd obmenu-1.0
 and the path is right in my file system

What are the errors you're getting?

---

### Post by atomkarinca on 2008-07-06
> **deadlySniper said:**
> Ya, I'm having problems. I cant get this to work inside terminal
    cp /etc/xdg/openbox/menu.xml ~/.config/openbox/menu.xml 

Try copying with sudo:

```
sudo cp /etc/xdg/openbox/menu.xml ~/.config/openbox/menu.xml
```


> tar xzvf ~/obmenu-1.0.tar.gz
    cd obmenu-1.0
 and the path is right in my file system

You don't have to compile obmenu, it's in the repos:

```
sudo apt-get install obmenu
```

---

### Post by deadlySniper on 2008-07-07
It says that the files do not exist but they do exist

---

### Post by atomkarinca on 2008-07-07
Can you paste the terminal output here?

---

### Post by dominiquec on 2008-07-07
You can edit the menu files using obmenu.

First, download and install from the repositories.  Open a terminal and:
```
sudo apt-get install obmenu
```

Then, type "obmenu" and enter.

Beats having to edit menu.xml.

---

### Post by deadlySniper on 2008-07-07
i have obmenu working, what do I do next

---

### Post by atomkarinca on 2008-07-07
> **deadlySniper said:**
> i have obmenu working, what do I do next

Now you can enjoy your Openbox :) With obmenu you can edit the right-click menu and if you install obconf you can edit your Openbox configuration:

```
sudo apt-get install obconf
```

---

### Post by urukrama on 2008-07-08
Have you seen my Openbox guide (link in signature)? If you are totally knew to stand-alone window managers, you'll most likely find it useful. I tried to make it as comprehensive as possible.

---

