---
title: "[SOLVED] Ubuntu Tweak upgrade-How do I install?"
date: 2008-10-11
forum: New to Ubuntu
---

### Post by Don1947 on 2008-10-11
I went to use my Ubuntu Tweak and was notified of an upgrade. I have downloaded it to desktop and followed the instructions[ here]("http://ubuntu-tweak.com/downloads") precisely as given -to no effect it seems.:confused:](*,)
If I open Ubuntu Tweak I still get notification of the download
I am running Ubuntu 8.04.01
Can someone explain what I am doing wrong, please?

---

### Post by Elfy on 2008-10-11
The instructions are a bit vague - have you downloaded the source or added the lines to your sources list - the second is easiest

> open your terminal, type the command to run gedit(or other editor in your opinion) to modify the sources.list:

sudo gedit /etc/apt/sources.list

And put the two line into it(If you are using Ubuntu 8.04 Hardy or early) :

deb [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) hardy main

sudo apt-get update

```
sudo apt-get install ubuntu-tweak
``` should install the newest version

---

### Post by Don1947 on 2008-10-11
Actually I did both-downloaded AND added to source list! Will try your advice. Thanks for the help

---

### Post by Don1947 on 2008-10-11
Houston, we have a problem.

Have followed your advice:

don@don-desktop:~$ sudo apt-get install ubuntu-tweak
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-tweak is already the newest version.
The following packages were automatically installed and are no longer required:
  libexif-gtk5
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
don@don-desktop:~$ 

Then I go to Ubuntu Tweak-it is still asking me if I want to upgrade and stuck at version 3-so I have now tried


don@don-desktop:~$ apt-get autoremove libexif-gtk5
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
don@don-desktop:~$ 


?????????????? Help?!!

---

### Post by Elfy on 2008-10-12
You'll need to use sudo for apt-get commands - and any that affect the system.

---

### Post by Don1947 on 2008-10-12
Thanks-but I am none the wiser! I have been using Ubuntu for only a week. However the problem has solved itself as the update in question was flagged up on Ubuntu's own updates this morning and self installed-Also I have just returned from "Ottakers" where I bought "Beginning Ubuntu Linux"-hopefully it will help! :)

---

