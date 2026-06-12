---
title: "How can I easily switch between Xubuntu and Ubuntu (having both installed)?"
date: 2008-09-21
forum: New to Ubuntu
---

### Post by inktri on 2008-09-21
I'm currently using regular Ubuntu; however for some school work I need to work with OpenGL and glut. Unfortunately glut is really buggy under gnome (windowless borders, you need a idle function to keep the window showing). I'd like to install Xubuntu just for working with Eclipse/glut. 

Is there a possibility of having both the Xfce desktop environment and the gnome desktop environment installed with the ability to easily switch between the two? 

THanks for the help

---

### Post by MegaJim on 2008-09-21
Yes, if you are currently using gnome (ubuntu) just install the xubuntu-desktop meta package:

```
sudo apt-get install xubuntu-desktop
```

To switch between the two, just logout and change session then login again.

---

### Post by 73ckn797 on 2008-09-21
You can have them all available and only have to log out and switch desktops (via Sessions).

You will need to use terminal and type these commands:

For Kubuntu:
sudo apt-get install kubuntu-desktop

For Xubuntu:
sudo apt-get install xubuntu-desktop

If you decide that you do not want those after installation you enter the following commands:

sudo apt-get remove kubuntu-desktop
sudo apt-get remove xubuntu-desktop

There would also be more stuff to remove to fully clean everything out.

You can also use Synaptic Package Manager to install/remove either desktop.

You could also load each variation independently but would have to restart the computer to load each one.

---

