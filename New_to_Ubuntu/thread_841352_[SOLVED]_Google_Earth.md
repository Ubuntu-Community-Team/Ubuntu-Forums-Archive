---
title: "[SOLVED] Google Earth"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by betterthanjordan79 on 2008-06-26
could somebody please give me step by step instructions on how to install google earth...thanks in advance!!

---

### Post by drs305 on 2008-06-26
For Hardy:

Install Medibuntu Repository from [https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu"):
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

```

Install Google Earth (this is a metapackage, no version number required. current version 4.3):
```
sudo apt-get install googleearth
```

---

### Post by cespinal on 2008-06-26
try going to system>administration>synaptic package manager. 

do a search for it and you may able to download it. 

there  A LOTTASTUFF in ubuntu's repositories.. :P

---

### Post by Canis familiaris on 2008-06-26
Fitst go to terminal. Applications->Accessories->Terminal
Cut, copy, and paste the commands one by one:

```
wget http://dl.google.com/earth/client/current/GoogleEarthLinux.bin
```

```
chmod +x GoogleEarthLinux.bin
```

```
./GoogleEarthLinux.bin
```

There you'll get a GUI which will step by step install Google Earth.


If you are using 32bit Ubuntu then you can also install Google Earth by CNR:
[http://www.cnr.com/](http://www.cnr.com/)

EDIT: @OP: Ignore this post. drs305's way is better.

---

### Post by betterthanjordan79 on 2008-06-26
thanks Anurag_panda - you way worked perfect!!

---

### Post by drs305 on 2008-06-26
I am glad you got it installed. For future reference, installing via .bin files does not register the app in synaptic and dpkg, which means that uninstalling becomes a little more difficult and updates will not automatically be available. When possible using the repositories is generally a better way to go. That being said, there are lots of ways of doing the same thing in ubuntu. 

Enjoy Google Earth!

---

### Post by gandaran on 2008-06-26
adding the medibuntu repository to your synaptic package manager  or following drs305 instructions would be a lot better as you could easily install/uninstall and update google earth using synaptic.

---

### Post by BlueSkyNIS on 2008-06-30
Thanks drs305! :popcorn:

---

### Post by rcadby on 2008-12-07
I guess I'll have to learn more about medibuntu, drs305, synaptic and dpkg. Being a newbie sucks!

Anywho, my Google Earth is installed and works, but the danged 'button' on the desktop doesn't work. I've tried changing its properties and making a new one to no avail.

For now, I have to open a terminal, do sudo -i, cd to the directory where the program is and type ./googeearth every time to get it working.

How do you make a 'button' to open this program?

Also, checking the available help, it says I can change a file's properties using System|Preferences|File Management, but I don't have the File Management option on my Ubuntu toolbar for some reason??? Any help on that?

---

### Post by drs305 on 2008-12-07
> **rcadby said:**
> For now, I have to open a terminal, do sudo -i, cd to the directory where the program is and type ./googeearth every time to get it working.

Depending on how you installed it, your only way to run it may be as root. That is abnormal. 
Using sudo to open an app is not the preferred way of doing things since the configuration files won't be specific to you. However, I understand your plight.

You can normally find out the command to run an app by running the following command (substitute any app name):
```
which googleearth
```

> 
How do you make a 'button' to open this program?


Right click on a panel, Add to Panel, Application Launcher and see if your app is listed and select it. 

If it is not listed, the first thing to do is find a command that works to open the app in terminal (without sudo if possible!). Then right click the panel, Add to Panel, Custom  Application Launcher. Enter a name and then put the run command in the Command box. You can add an icon in the upper left or if ubuntu recognizes the command it will automatically enter the app's icon.

If you have to use sudo to start the app, I would consider reinstalling it so this is not necessary. If you decide to always run the app as root, you can search the forums for "sudoers" and see how you can add the googleearth command to the sudoers file to allow you to run it as root without having to type the password.

---

