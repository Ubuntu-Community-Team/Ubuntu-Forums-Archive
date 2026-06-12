---
title: "Ubuntu server software and Dell Poweredge 1800"
date: 2012-01-31
forum: New to Ubuntu
---

### Post by raxhunter on 2012-01-31
Hi all, 
I am new to Ubuntu and I have a few questions about the Ubuntu server software. Currently I have a Dell Poweredge 1800 server running Raid.  I have also installed the latest Umbuntu server software.  The installation seemed to be fairly quick and easy, but when I go to boot the server up I get to ubuntu@$ login and password screen. I log in and get into a suedo screen. I am unsure if this is where my server is supposed to boot too? I was kinda hoping it would boot to a windows type screen as I don't know anything about suedo commands or how to really navigate thru suedo.  I want to use my server to serve picture, music, videos and files to my home network and abroad. My question is is the ubuntu server software stand alone or do I need another piece of software to run with the sever software?

---

### Post by Cheesemill on 2012-01-31
That's how it should be, Ubuntu Server installs without a GUI (Graphical User Interface) as standard for performance and security reasons. If you don't want to learn how to do everything via the command line then you could just install the desktop version of Ubuntu instead.

All of the same applications are available on the Desktop version as the Server version, for example you can install Samba to share files between computers on both versions.

---

### Post by raxhunter on 2012-01-31
> **Cheesemill said:**
> That's how it should be, Ubuntu Server installs without a GUI (Graphical User Interface) as standard for performance and security reasons. If you don't want to learn how to do everything via the command line then you could just install the desktop version of Ubuntu instead.

All of the same applications are available on the Desktop version as the Server version, for example you can install Samba to share files between computers on both versions.

Thank u for the info... ill go download the desktop version on my 1800 and play with this version on my 1900... thanks again!!:p

---

### Post by dolphin194 on 2012-01-31
[COLOR=Green]**You can actually install a GUI in Ubuntu Server**[/COLOR]

I recommend the Xfce environment for a server if you're going to use a GUI. You can install it with this command:
```
sudo apt-get install xubuntu-desktop
```You can also use the normal Ubuntu Unity
```
sudo apt-get install ubuntu-desktop
```Or KDE...
```
sudo apt-get install kubuntu-desktop
```

---

### Post by raxhunter on 2012-01-31
> **dolphin194 said:**
> [COLOR=Green]**You can actually install a GUI in Ubuntu Server**[/COLOR]

I recommend the Xfce environment for a server if you're going to use a GUI. You can install it with this command:
```
sudo apt-get install xubuntu-desktop
```You can also use the normal Ubuntu Unity
```
sudo apt-get install ubuntu-desktop
```Or KDE...
```
sudo apt-get install kubuntu-desktop
```

I am unsure if im even connected to the net with my server... I know when I loaded the software that the internet portion went thru with out any problems, but when I went to ping the server ip on my laptop the ping errored out.

I should of stated that I do have a network cable connected to my cable modem, but the light blinks orange on the server nic.

---

### Post by rgreener25 on 2012-01-31
You can also use lxde which is really lightweight ```
sudo apt-get install lubuntu-desktop
```

---

### Post by raxhunter on 2012-01-31
> **rgreener25 said:**
> You can also use lxde which is really lightweight ```
sudo apt-get install lubuntu-desktop
```

Thanks guys for your help!!! Rest azure ill probably have more.questions lol

---

### Post by raxhunter on 2012-01-31
Okay I loaded the GUI as noted. . The load went well, but now when I rebooted a different screen poops up with a bunch of [OK]  while doing this the screen blinks with mouse pointer in the back ground then stops at checking battery state...... that's where it is currently staying... I had 1 [fail] at stoping automatic crash report generation... ?????

---

