---
title: "Starting KDE"
date: 2008-10-14
forum: New to Ubuntu
---

### Post by VorlonShadow on 2008-10-14
I have Ubuntu 8.04 Server installed.  I didn't think initially that I'd want a GUI, but I find that working with MySQL strictly through a command line interface is a bit too much work. So, I installed the KDE GUI using the "apt-get install kde" command.  It went through all the motions, then dumped me back to the command prompt.  Now, I'm wondering how I start KDE.  I tried startkde and several other things that I found on Google, but nothing seems to be working.  I think it may be because X is not started, but I'm not sure that it's even installed.  Where do I go from here?

If it's easier to install gnome (or whatever Ubuntu's default GUI is), I'm definitely willing to do that.  I only tried KDE, because I'm a little more familiar with it.

Thanks,
Jesse

---

### Post by SunnyRabbiera on 2008-10-14
you may wish to try sudo apt-get install kubuntu-desktop, that should give you the packages you will need to get a working GUI on your system.
But since this is a server you might wish to go lighter and try xfce.

---

### Post by VorlonShadow on 2008-10-15
This is kind of a "play server", it's not really used for "serious serving".  Basically, I have one PHP web site that I develop on it, and other than that, I really don't use it for anything else.

I'm in the process of installing kubuntu-desktop now.  Once I get that installed, how do I start the GUI?

Thanks,
Jesse

---

### Post by mtausig on 2008-10-15
I think it comes up automatically.
If not, you can either reboot or type "sudo init 5" in the command line.

---

### Post by stephanvaningen on 2008-10-15
I don't know if the 'kde' will install enough.

Wouldn't you want to do this:
```
sudo apt-get install kubuntu-desktop
```
Anyway, I'ld suggest to install Gnome, since I think it is less resource-consuming (or even: XFCE: less consuming)

---

### Post by VorlonShadow on 2008-10-15
Yup, that's what I wanted to do, and did, and after a reboot, I now have a GUI.  Thanks for the help guys!

Jesse

---

