---
title: "installers used by Ubuntu"
date: 2015-05-05
forum: New to Ubuntu
---

### Post by Guy_Rich on 2015-05-05
Does Ubuntu use yum to install packages ?

Thanks

Guy

---

### Post by yancek on 2015-05-05
No.  That would be Red Hat, CentOS and Fedora.  Ubuntu is derived from Debian and in a terminal you would use the apt-get command.

---

### Post by dino99 on 2015-05-05
As Ubuntu is based on Debian, which use deb package format, yum is not the installer, even if you can find it into the archive.

Yum (Yellow dog Updater, Modified) is an automatic updater and package
installer/remover for rpm systems.

Ubuntu use apt for the commandline, and some frontend like synaptic (not installed by default as update-manager (buggy) and software-center (buggy) are installed)

---

### Post by Guy_Rich on 2015-05-05
> **yancek said:**
> No.  That would be Red Hat, CentOS and Fedora.  Ubuntu is derived from Debian and in a terminal you would use the apt-get command.

Thank You Yancek. 
So How do I start a terminal session?  (I'm using Ubuntu 14.04 LTS) I tried the alt-f2 I got a "command-line" (not a full terminal session) and issued a ping...it didn't do anything. except display a 3 gear icon and the ip address I pinged. 
What's that supposed to mean? 

Thanks 

Guy

---

### Post by sammiev on 2015-05-05
> **Guy_Rich said:**
> Thank You Yancek. 
So How do I start a terminal session?  (I'm using Ubuntu 14.04 LTS) I tried the alt-f2 I got a "command-line" (not a full terminal session) and issued a ping...it didn't do anything. except display a 3 gear icon and the ip address I pinged. 
What's that supposed to mean? 

Thanks 

Guy

Ctrl + Alt + T

---

### Post by deadflowr on 2015-05-05
> **Guy_Rich said:**
> Thank You Yancek. 
So How do I start a terminal session?  (I'm using Ubuntu 14.04 LTS) I tried the alt-f2 I got a "command-line" (not a full terminal session) and issued a ping...it didn't do anything. except display a 3 gear icon and the ip address I pinged. 
What's that supposed to mean? 

Thanks 

Guy

alt+f2 opens the run dialog, which you can use to run various commands, though no terminal output will be seen as to what happens.
You can actually use that function to open a terminal, just type *gnome-terminal* and hit enter.
The gears icons represent the previous commands you tried in the run dialog.

Alternatively, in Ubuntu, to get a terminal, press the super(windows) key on your key board and start typing terminal. You only need to actually type the first three letters, ter, and the terminal application should show up.
Select it with a mouse click or simply hit the enter button. When selected the terminal will launch.
Also, note that when an app is launched an icon for it will appear in the sidebar.
You can right click on that icon and select the option lock to launcher and the terminal will forever be launch onto the sidebar, even after you close it.


Aside from that though, Ubuntu can use several easier to understand frontends for package management like the software center(installed by default) or synaptic(not installed by default)
Synaptic is widely recommended though. As it has an abundant more features and abilities than the software center.

Hope that helps.

---

### Post by grahammechanical on 2015-05-05
If you are curious about using the command line to update/upgrade the system and to install and remove packages, then you will need this

[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

Regards

---

