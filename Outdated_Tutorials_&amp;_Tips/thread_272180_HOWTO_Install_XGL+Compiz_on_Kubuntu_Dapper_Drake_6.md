---
title: "HOWTO: Install XGL+Compiz on Kubuntu Dapper Drake 6.06"
date: 2006-10-05
forum: Outdated Tutorials &amp; Tips
---

### Post by x64Jimbo on 2006-10-05
I've been taking the instructions from this page:
[http://ubuntuforums.org/showthread.php?t=147711](http://ubuntuforums.org/showthread.php?t=147711)
and turning it into a shell script. It's a bit slow going at the moment, and I was wondering if there are any shell scripting experts out there willing to help me out. 
[SIZE=6][COLOR=Red]THIS SCRIPT IS NOT COMPLETE. DO NOT EXECUTE.[/COLOR][/SIZE]
Here's what I have so far:
```

#!/bin/bash
# XGL+Compiz Switcher
# By x64Jimbo
clear
switch=0
start=0
vidcard=0
if [ `id -u` != 0 ] ; then
    echo "You must be root to run this script"
    exit
fi
echo "XGL+Compiz Installer and Switcher"
echo "For Kubuntu Dapper Drake 6.06 ONLY"
echo "USE AT YOUR OWN RISK"
echo "Press any key to continue..."
read KEY
clear
echo "Choose an option..."
echo "-------------------"
echo "0, Setup - Backs up your current working settings and sets up XGL+Compiz on your system"
echo "1. Turn XGL+Compiz On"
echo "2. Turn XGL+Compiz Off"
read switch
if [ $switch -eq 0 ] ; then
    clear
    if [ -e /etc/X11/xorg.conf-NONXGL ] ; then
        echo "This option has already been run. You must run the script with option 1 to enable XGL now."
        exit
    else
        echo "Backing up your current settings..."
        echo "The following files will be backed up:"
        echo "/etc/X11/xorg.conf"
        echo "/etc/kde3/kdm/kdmrc"
        echo "/usr/bin/displayconfig-restore"
        echo "...To these locations:"
        echo "/etc/X11/xorg.conf-NONXGL"
        echo "/etc/kde3/kdm/kdmrc-NONXGL"
        echo "/usr/bin/displayconfig-restore-NONXGL"
        echo "Press any key to continue..."
        read KEY
        cp /etc/X11/xorg.conf /etc/X11/xorg.conf-NONXGL
        cp /etc/kde3/kdm/kdmrc /etc/kde3/kdm/kdmrc-NONXGL
        cp /usr/bin/displayconfig-restore /usr/bin/displayconfig-restore-NONXGL
        clear
        echo "Done. Now, we will backup your /etc/apt/sources.list file to this location:"
        echo "/etc/apt/sources.list-NONXGL"
        echo "Press any key to continue..."
        read KEY
        cp /etc/apt/sources.list /etc/apt/sources.list-NONXGL
        clear
        echo "Select your video card brand"
        echo "----------------------------"
        echo "1.nVidia"
        echo "2.ATI"
        read vidcard
        echo "You have selected..."
        if [ $vidcard -eq 1 ] ; then
            echo "nVidia"
        else
            if [ $vidcard -eq 2 ] ; then
            echo "ATI"
            else
                echo "Invalid Entry."
                exit
            fi
        fi
        echo "Press any key to continue..."
        read KEY
        clear
        echo "Done. Now, we will make the necessary modifications to the files."
        echo "Press any key to continue..."
        read KEY
        echo "functions not implemented yet. you must make the modifications yourself."
        echo "visit http://ubuntuforums.org/showthread.php?p=845077 for details"
        echo "Press any key to continue..."
        read KEY
        clear
        echo "Done. Now, we will add the following entries to the end of your /etc/apt/sources.list file:"
        echo "deb http://xgl.compiz.info/ dapper main"
        echo "deb-src http://xgl.compiz.info/ dapper main"
        echo "deb http://www.beerorkid.com/compiz/ dapper main"
        echo "Press any key to continue..."
        read KEY
        echo "#######################################" >> /etc/apt/sources.list
        echo "########## XGL+Compiz Stuff ###########"  >> /etc/apt/sources.list
        echo "#######################################" >> /etc/apt/sources.list
        echo "deb http://xgl.compiz.info/ dapper main" >> /etc/apt/sources.list
        echo "deb-src http://xgl.compiz.info/ dapper main" >> /etc/apt/sources.list
        echo "deb http://www.beerorkid.com/compiz/ dapper main" >> /etc/apt/sources.list
        clear
        echo "Done. Now, we will fetch and install the GPG key"
        echo "for Quinn's files in the Beerorkid repository."
        echo "Press any key to continue..."
        read KEY
        wget http://www.beerorkid.com/compiz/quinn.key.asc -O - | sudo apt-key add -
        clear
        echo "Done. Now, we will fetch and install all the necessary software."
        echo "Press any key to continue..."
        read KEY
        apt-get update
        apt-get install nvidia-kernel-common nvidia-glx compiz xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 compiz-gnome gconf-editor gset-compiz
        clear
        echo "Done. Installation complete. Run this script again" 
        echo "with the 1 option to turn ON XGL+Compiz."
        exit
    fi    
else
    if [ $switch -eq 1 ] ; then
        echo "Turning ON XGL+Compiz support. Press any key to continue, or Ctrl+C to abort."
        read KEY
        mv  /etc/X11/xorg.conf-NONXGL
        mv /etc/kde3/kdm/kdmrc /etc/kde3/kdm/kdmrc-NONXGL
        
        /etc/init.d/kdm restart
        echo "XGL ON"
    else
        if [ $switch -eq 2 ] ; then
            echo "Turning OFF XGL+Compiz support. Press any key to continue, or Ctrl+C to abort."
            read KEY
            /etc/init.d/kdm restart
            echo "XGL OFF"
        else
            echo "Invalid Option. Please choose either 1 or 2"
            exit
        fi
    fi
fi

```If you think there's something here you can do better, feel free to re-post with your improvements.

---

### Post by Jonas Reiff on 2006-10-06
Dose this also work on ubuntu... With out KDE?

---

### Post by x64Jimbo on 2006-10-06
No. This script will be for Kubuntu only, but there is a possibility that it could be re-written for GNOME.
Also, it is NOT finished yet. I need some assistance with finishing it. Please do not attempt to run this script until a working version is posted.

---

### Post by rebegin on 2006-10-16
hey,
may i ask you what this line would do?
```
mv  /etc/X11/xorg.conf-NONXGL
```
i quess you missed one argument...i'm not sure, but, what are you moving there?
anyway, i'm trying now this and will see

---

### Post by cosmint_1973 on 2006-10-16
Hi there !

so copying the script into a file with, let's say kate and saving it with the .sh extension, then running it from konqueror as root would do all of the job ? ](*,)

---

### Post by x64Jimbo on 2006-10-18
> **rebegin said:**
> hey,
may i ask you what this line would do?
```
mv  /etc/X11/xorg.conf-NONXGL
```i quess you missed one argument...i'm not sure, but, what are you moving there?
anyway, i'm trying now this and will see
I believe I stated very clearly that it was a **work in progress**, and that you should _**not**_ run it. I hope you didn't hose your system.

---

### Post by rebegin on 2006-10-21
> **x64Jimbo said:**
> I believe I stated very clearly that it was a **work in progress**, and that you should _**not**_ run it. I hope you didn't hose your system.
just a little bit, but at the end everything is fine.
my only problem is that i cannot configure very well the compiz plugins...i try to modify those in the compiz settings manager, but everything stays the same.

---

