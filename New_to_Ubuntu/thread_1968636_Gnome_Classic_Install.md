---
title: "Gnome Classic Install"
date: 2012-04-29
forum: New to Ubuntu
---

### Post by cdo on 2012-04-29
Unable to install Gnome Classic from terminal . Installed 12.04 through a series of upgrades from 10.04 and wondering if that's why i am having some of the problems i am having . Slow page loads , desktop freezing , etc. Or perhaps i am not using proper command ?

alan@alan-desktop:~$ sudo apt-get install gnome classic
[sudo] password for alan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package classic
alan@alan-desktop:~$ 

Suggestions welcome...

---

### Post by Cavsfan on 2012-04-29
> **cdo said:**
> Unable to install Gnome Classic from terminal . Installed 12.04 through a series of upgrades from 10.04 and wondering if that's why i am having some of the problems i am having . Slow page loads , desktop freezing , etc. Or perhaps i am not using proper command ?

alan@alan-desktop:~$ sudo apt-get install gnome classic
[sudo] password for alan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package classic
alan@alan-desktop:~$ 

Suggestions welcome...

I believe it is gnome-classic.

---

### Post by Cavsfan on 2012-04-29
This might help.

[[COLOR=blue]_http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed/_[/COLOR]]("http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed/")

---

### Post by kohoutek1 on 2012-04-29
> **Cavsfan said:**
> I believe it is gnome-classic.

Yeah. What Cavsfan means is, check the syntax of your command. You're missing a hyphen.

---

### Post by cdo on 2012-04-29
Tried gnome-classic , same result . Softwear center says gnome panel  already installed installed but i can't find it and neither can terminal .Maybe indicative of not getting a clean upgrade ?

---

### Post by Frogs Hair on 2012-04-29
Try the following. ```
sudo apt-get install gnome-session-fallback
```

---

### Post by cdo on 2012-04-29
Just did that one as well and still no panel . The only thing the reboot seems to do is prevent Firefox from loading the precious session . I t take the panel should be seen in the top right hand corner or is it on the log in screen ?

---

### Post by Cavsfan on 2012-04-29
Open the Ubuntu Software Center and search for ‘gnome-panel’, hit install and log out.

---

### Post by cdo on 2012-04-29
Softwear center said it was already installed , i just went back there again and now the installed softwear will not display .  Geez , do i have a ghost..   :-)

---

### Post by Frogs Hair on 2012-04-29
If you can get a terminal open using Ctrl + Alt + t  try starting or restarting the panel with the following . ```
gnome-panel
``` or ```
killall gnome-panel
```

---

### Post by Cavsfan on 2012-04-29
Did you logout and back in?

---

### Post by Cheesemill on 2012-04-29
You need to select a Gnome classic session on the log in screen.

---

### Post by Cavsfan on 2012-04-29
> **Cheesemill said:**
> You need to select a Gnome classic session on the log in screen.

Correct. It needed to be installed and for it to take effect, you have to logout and log back in...

---

### Post by cdo on 2012-04-29
Just woke up.. tried ctrl+alt+t . Terminal loads , just nothing happens within terminal..

I will try the various terminal commands again today . If nothing works thinking i need to back up data , burn iso and install from disk .

---

### Post by cdo on 2012-04-29
Have loge out and back in after terminal commands . Log in screen does not give the option for classic . Any chance issue could be related to how user accounts are set up ? I am root .

---

### Post by cdo on 2012-04-29
Problem Solved . Not sure if a single action or series of actions solved it but classic does display now . Went to softwear center and installed pretty much everything that had gnome panel in the description as some were not checked as installed . Monkeyed around in bios then rebooted and options emblem was displayed at start up . So far good . 

Thanks for all the suggestions guys... you are a great bunch..

---

