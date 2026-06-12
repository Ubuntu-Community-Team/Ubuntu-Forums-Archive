---
title: "how to work with applications?"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by raymondvillain on 2008-05-26
New to Linux!  Ubuntu 8.04 running on a dual boot desktop.

Is there a guide or tutorial in existence that allows one to learn the ropes?  For instance, where is the application that controls the panels on the desktop?  I deleted mine by mistake and am slowly reconstructing them, but if I know where and what the settings were that existed at installation I might just be able to restore them.

And when someone in a post says "the gnome terminal" is that the terminal that pops up from the desktop panel?

Thanks in advance,
Hank

---

### Post by Sarah L on 2008-05-26
Try the official community documentation at [https://help.ubuntu.com/community/UserDocumentation]("https://help.ubuntu.com/community/UserDocumentation").

---

### Post by tom56 on 2008-05-26
> **raymondvillain said:**
> New to Linux!  Ubuntu 8.04 running on a dual boot desktop.

Is there a guide or tutorial in existence that allows one to learn the ropes?  For instance, where is the application that controls the panels on the desktop?  I deleted mine by mistake and am slowly reconstructing them, but if I know where and what the settings were that existed at installation I might just be able to restore them.

And when someone in a post says "the gnome terminal" is that the terminal that pops up from the desktop panel?

Thanks in advance,
Hank

The GNOME terminal is similar to a DOS prompt in Windows. It is accessed from Applications -> Accessories -> Terminal.

To restore your panel open the file browser (by going to Places -> Home) and remove the folder ~/.gconf/apps/panel. ~ means your home folder, so for example for me I would delete /home/tom/.gconf/apps/panel. Once you've done that log out then log back in. This will reset the panel to its default setup.

EDIT: Folder names that start with dots (like .gconf) are hidden. To view them in the file browser tick View -> Show Hidden Files.

EDIT 2: I told you log out then realised you might not be able to because the panel with the log out button is missing. If this is the case then to log out you should save and close anything you're doing then press Ctrl+Alt+Backspace.

---

### Post by raymondvillain on 2008-05-26
I have used the official Ubuntu user documentation, but I need to know a little more that it has to offer.

For example, if an application on the desktop is used, where is the executable located on the system?  What is the general scheme used by Linux for accessing executables?

---

### Post by tom56 on 2008-05-26
> **raymondvillain said:**
> I have used the official Ubuntu user documentation, but I need to know a little more that it has to offer.

For example, if an application on the desktop is used, where is the executable located on the system?  What is the general scheme used by Linux for accessing executables?

Enter the following command in a terminal and it will give you a list of where executables are stored. You shouldn't ever need to know this though.
```
echo $PATH
```

---

### Post by sisco311 on 2008-05-26
The configuration files of the panel are stored in your home directory. 
Open your file browser and press Ctrl+H to list the hidden files. 

Navigate to **.gconf** -> **apps** directory and delete or rename the **panel** folder. 
Now you need to restart your panel application. 
Applications -> Accessories -> Terminal
and type:
```
pkill gnome-panel
```to close the panel application.
Press Alt+F2 and type:
```
gnome-panel
```to start the panel.

The panel now will start with the default configuration.

---

### Post by raymondvillain on 2008-05-26
Great help!  I did it. Finally.  Re-boot would not restore the default top panel, I had to turn it off and then cold-boot it.  But now it is back, thanks to everyone.

---

### Post by oldos2er on 2008-05-26
> **raymondvillain said:**
> I have used the official Ubuntu user documentation, but I need to know a little more that it has to offer.

For example, if an application on the desktop is used, where is the executable located on the system?  What is the general scheme used by Linux for accessing executables?

You can find a program by using "whereis [program name]" in a terminal. Most program executables are installed to /usr/bin .

 Or, using Synaptic Package Manager, right-click on an installed package, choose Properties, Installed Files, and it will show you where each file in the package was installed.

---

