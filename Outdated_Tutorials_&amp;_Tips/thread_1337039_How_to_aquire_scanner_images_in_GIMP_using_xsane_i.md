---
title: "How to aquire scanner images in GIMP using xsane in Jaunty"
date: 2009-11-25
forum: Outdated Tutorials &amp; Tips
---

### Post by Jive Turkey on 2009-11-25
This howto describes the steps that worked for me to get my xsane and GIMP working together to aquire images directly from my scanner.  This also resolves the "xsane only works as root" problem which I have had with every Ubuntu release from Edgy to Jaunty.  Users are advised to read the entire thread before proceeding with these steps.

[LIST=1]
[*]In the newer versions of gimp you should be able to start xsane from via: File > Create > xsane > device chooser, if you don't have this option in your version of gimp you can try this, find the version number of your gimp installation and substitute it into this command: ```
ln -s /usr/local/bin/xsane ~/.gimp-*.*/plug-ins/
``` Then look for xsane under File > Aquire.   This may be unneccesary for you if you have the latest version.  
[*]If, like me just starting the device chooser fails because xsane needs to run as root in order to detect my scanner, please proceed:
Before Jaunty we could sometimes get xsane working by adding our user to the scanner user group via the administration gui.  In Jaunty this was not the case for me as there is no group for that and the users and groups gui has no option to allow this.  No problem, run these commands to make the group, add your user to it, and create the permissions file. ```
sudo addgroup scanner 
sudo adduser <username> scanner 
sudo touch /etc/udev/rules.d/40-permissions.rules 
sudo gedit /etc/udev/rules.d/40-permissions.rules
```
[/LIST]
paste the following code into gedit: 
```

# SCSI devices 
SUBSYSTEMS=="scsi", 
GOTO="scsi_start"
GOTO="scsi_end" 
LABEL="scsi_start" 
ATTRS{type}=="0",	                GROUP="disk" 
ATTRS{type}=="1",			GROUP="tape"
ATTRS{type}=="4",			GROUP="cdrom"
ATTRS{type}=="5",			GROUP="cdrom"
ATTRS{type}=="6",			GROUP="scanner"
ATTRS{type}=="8",			GROUP="tape"
ATTRS{type}=="3", ATTRS{vendor}=="HP",	GROUP="scanner"
ATTRS{type}=="3", ATTRS{vendor}=="Epson", GROUP="scanner"
ATTRS{type}=="3", ATTRS{vendor}=="EPSON", GROUP="scanner"
LABEL="scsi_end"
```  
...then save, close, and reboot.  Admittedly, I don't fully understand the udev rules, and how they might conflict with rules and permissions specified elsewhere.  Feedback and discussion are welcome of course.  I'll make efforts to update this OP to be as correct and helpful as possible.

To reverse these steps issue the following commands in the terminal:
To remove the symlink.
```
rm ~/.gimp-*/plug-ins/xsane
```

To remove the scanner group, only do this if you you created it and don't need it an more.
```
sudo delgroup scanner
```

To remove the udev permissions we created (if you had this file to start with don't touch it).
```
sudo rm /etc/udev/rules.d/40-permissions.rules
```

---

