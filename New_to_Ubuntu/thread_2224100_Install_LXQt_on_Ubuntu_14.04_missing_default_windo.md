---
title: "Install LXQt on Ubuntu 14.04 missing default window manager"
date: 2014-05-14
forum: New to Ubuntu
---

### Post by parker-hugh on 2014-05-14
I intalled LxQt on Ubuntu 14.04 using following commands in terminal window ...

sudo apt-get install software-properties-common
sudo add-apt-repository ppa:lubuntu-dev/lubuntu-daily
sudo add-apt-repository ppa:gilir/q-project
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install lxqt-metapackage
sudo apt-get install lxqt-panel

reboot and click small circle to chose LXQt login option

message displayed:
[B]please select your default window manager
other...       chose your favourite one.
you will be able to change this at any time through
Preferences > Session settings > Basic Settings[/B]

I am unable to select window manager, so I had a look on google and wonder is system looking for openbox  or PCManFM-Qt ? not sure what to do here.

I  am completely_** new**_ to linux so if someone could explain how to fix this I  would be grateful. is there an easy command line I can use in the  terminal?

any help would be appreciated

Hugh

---

### Post by kansasnoob on 2014-05-14
It was buggy the last time I tried, but this did work:

[http://xpressubuntu.wordpress.com/2014/03/01/installing-the-lightweight-lxde-qt-desktop/](http://xpressubuntu.wordpress.com/2014/03/01/installing-the-lightweight-lxde-qt-desktop/)

---

### Post by parker-hugh on 2014-05-14
thanks [**[COLOR=#000000]kansasnoob[/COLOR]**]("http://ubuntuforums.org/member.php?u=554595&") for your prompt reply, I also got a reply from [http://forum.lxde.org](http://forum.lxde.org) where Rex suggested  install the default Window Manager for Lubuntu  (which is Openbox) by following command line....

**sudo apt-get install openbox obconf**

after restart I was able to select LxQt from the login screen.

cheers, Hugh

---

### Post by vasa1 on 2014-05-14
Well, I'm using LXQt full-time for the last couple of days.

As for bugs, even relatively mature software churned out by huge corporates can have bugs. So that's neither here nor there.

All the best with your Linux adventure.

---

