---
title: "Install script for software"
date: 2009-11-05
forum: Programming Talk
---

### Post by Paul dH on 2009-11-05
Hi there,
 
I've made a script for autoinstallation of my standard software, it is'nt working yet and I've searched google for solutions but could not find one.
 
This is what I have this far:
 
```

#!/bin/bash
clear
echo "Kubuntu Install Software script"
: <<'END'
 
Kubuntu Install Software script
--------------------------------------------------------------------
 Run the script as root: (sudo ...)
--------------------------------------------------------------------
 For testing in Virtualbox:
 Preform:
 apt-get update
 apt-get upgrade
 apt-get install gksu
 Make sure you connected the Virtualbox additions cd in your VM.
 Navigate to cd:
 cd /cdrom
 ./autorun.sh
--------------------------------------------------------------------
 Save this file as install-software.sh
 Preform: chmod +x install-software.sh
 This it to make the file exacutable.
--------------------------------------------------------------------
  Install packages
--------------------------------------------------------------------
 Part 1:
 build-essential
 automake
 gimp
 firefox
 wine
 kubuntu-restricted-extras
 xine-ui
 totem-xine
 msttcorefonts
 sox
 autoconf
 Filezilla
 libdvdread4
When preforming a normal install, add gksu to the line of aps
--------------------------------------------------------------------
END
apt-get update
echo "Part 1 ..."
apt-get install build-essential automake gimp firefox wine kubuntu-restricted-extras xine-ui 
totem-xine msttcorefonts sox autoconf filezilla libdvdread4
echo "Finished installing software"
read -n 1 -p "Done installing"
fi # Script is done

```
 
What I want to add in the script is that it makes a backup of my sources.list and I must be able to add sources. This is needed for the installation of some software.
 
I know there is a link for managing apt trough the commandline, so that will be added later.
 
[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)
 
I thought it was useful to post and maybe fun for someone else to use it, specialy becouse I'm a noob and was searching for this for long.
 
Sorry for the crappy english, I'm dutch thats my excuse :P
Greetings, Paul dH

---

### Post by Paul dH on 2009-11-05
Just made another .sh for updating apt and adding Wine to sources.list:
 
```

#!/bin/bash
clear
echo "This will backup sources.list and uncomment all repositories in apt"
cp /etc/apt/sources.list /etc/apt/sources.list.backup
sed -i -e "s/# deb/deb/g" /etc/apt/sources.list
apt-get update
echo "Instert wine repository..."
cp /etc/apt/sources.list /etc/apt/sources.list.backup2
wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O-
apt-key add -
wget [http://wine.budgetdedicated.com/apt/sources.list.d/karmic.list](http://wine.budgetdedicated.com/apt/sources.list.d/karmic.list) -O 
/etc/apt/sources.list.d/winehq.list
apt-get update
echo "Apt is updated and Wine repository is added."
echo "There are 2 backup files, .backup is the original."
echo ".backup2 is the updated version without Wine."
read -n 1 -p "Done updating Apt and adding Wine to repositories."
fi #Script end

```
 
Be carefull, I have'nt tested the scripts yet. I will setup a test system when I'm home.
 
I got the info from: [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)
 
Greetings, Paul

---

