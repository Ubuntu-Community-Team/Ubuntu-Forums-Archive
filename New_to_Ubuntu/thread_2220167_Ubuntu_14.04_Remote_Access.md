---
title: "Ubuntu 14.04 Remote Access?"
date: 2014-04-26
forum: New to Ubuntu
---

### Post by hoffman1978 on 2014-04-26
I have installed Ubuntu 14.04 LTS on an AMD64 machine and all has been running fine. I am planning on making this my media server, and again that has worked flawlessly. I also want to run it headless... problem. I can't seem to configure XRDP or Ubuntu for my Win7 laptop to connect. All I get is the blank screen. I have searched the web, and it seems this problem is not yet solved?

---

### Post by monkeybrain20122 on 2014-04-26
It doesn't work on 3d desktops like unity. You need to install an alternate 2d desktop for remote sessions. For example, lxde or xfce. gnome-flashback with no effect should have been ideal but unfortunately it doesn't work in 13.10, not sure about 14.04

I use lxde as an alternative 2d desktop. For remote sessions to default to lxde create a file named .xession in your home with this line in it

```
lxsession -s LXDE -e LXDE
```

---

### Post by hoffman1978 on 2014-04-27
My wife is ripping a dvd when she finishes I will try this. I have indeed installed gnome-flashback, but maybe i have it configured wrong. I am a complete noob at linux but I have been pouring over youtube and forums for a fix.. unfortunately there isn't much yet available for 14.04. I will update after I try this.

---

### Post by hoffman1978 on 2014-04-27
Still no go. I used sudo gedit .xsession and modified the line as you wrote then resaved. I checked "ls -a" and .xsession is there, but it is yellow, does that mean anything? I used "cat .xsession" and the line shows "lxsession -s LXDE -e LXDE"

---

### Post by deadflowr on 2014-04-27
Did you install the lxde desktop?

---

### Post by hoffman1978 on 2014-04-27
lol yes you did not specify that but i just typed "sudo get-apt install lxde" and it did.

---

### Post by stinger30au on 2014-04-27
i dunno if this helps you or not, but i use teamviewer if i need remote access to any ubuntu/windows pc and it has nver let me down yet. use the home edition, its free and works a treat

---

### Post by simon_r2 on 2014-04-28
Thanks, I had the same problem (with Ubuntu 14.04) and I too tried the various gnome .xsession 2d changes mentiponed online and they did not work. However, making the change you started above (and installing lxde) has resolved the problem!

Thanks again!

Simon

> **deadflowr said:**
> Did you install the lxde desktop?

---

### Post by monkeybrain20122 on 2014-04-28
> **hoffman1978 said:**
> Still no go. I used sudo gedit .xsession and modified the line as you wrote then resaved. I checked "ls -a" and .xsession is there, but it is yellow, does that mean anything? I used "cat .xsession" and the line shows "lxsession -s LXDE -e LXDE"

Maybe a permission issue? you should not sudo anything in your /home.  sudo or gksudo should only be used for system tasks.

P.S. I read that xrdp actually works on gnome shell, but only on Fedora..

---

### Post by monkeybrain20122 on 2014-04-28
FYI [https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/1251281](https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/1251281)
There is a proposed fix implemented in a ppa. You may want to try that out too. If it works it would be a better solution than installing lxde or worse xfce4 (too many unnecessary package duplications and xfce moreover destroys the login screen and folders icons don't show up in remote sessions,--only text wih folder names)

---

### Post by blinky-m on 2014-08-04
Hello all,

I've had a similar problem with XRDP and accessing gnome-flashback from a Windows machine to access my Ubuntu 14.04 remotely.  Grey screen.  I've temporarily used the openbox solution that I read somewhere by running "sudo apt-get install openbox" and chaning my .xsession file to "exec openbox".  
 
It's not pretty but it gives me terminal access should I require it.
 
What I'm wondering is what the status is of a fix between XRDP and gnome-flashback on Ubuntu 14.04?  I don't really want to change desktops environments which is why I'm running gnome-flashback (formerly fallback) to begin with.
 
Thanks in advance and apologies if this has been answered elsewhere.

---

### Post by sp40140 on 2014-08-05
Do you have to use RDP protocol? How about VNC? Is there a reason you are not trying VNC?

---

