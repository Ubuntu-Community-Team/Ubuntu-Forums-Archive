---
title: "Problems with Ubuntu- many errors while removing KDE and Gnome"
date: 2018-06-29
forum: New to Ubuntu
---

### Post by chandramauli2 on 2018-06-29
Sorry, askubuntu is not accepting any more questions. Let me begin what did I do first,
At first, I install gnome desktop environment in my Ubuntu 16.04, but then I install KDE plasma using 


    sudo add-apt-repository ppa:kubuntu-ppa/backports
    sudo apt-get update && sudo apt-get dist-upgrade
    sudo apt-get install kubuntu-desktop
And then removed gnome using [this site]([https://askubuntu.com/questions/767577/how-can-i-remove-gnome-desktop-environment-without-messing-unity-de-ubuntu-16](https://askubuntu.com/questions/767577/how-can-i-remove-gnome-desktop-environment-without-messing-unity-de-ubuntu-16))  the first answer from the above site, but I cannot reinstall:
ubuntu unity with the command;


    sudo apt-get install ubuntu-desktop
    sudo apt-get install unity
The error showing by the terminal is this:


    Some packages could not be installed. This may mean that you have
    requested an impossible situation or if you are using the unstable
    distribution that some required packages have not yet been created
    or been moved out of Incoming.
    The following information may help to resolve the situation:
    
    The following packages have unmet dependencies:
     ubuntu-desktop : Depends: checkbox-gui but it is not going to be installed
                      Recommends: python3-aptdaemon.pkcompat but it is not going to be installed
                      Recommends: qt-at-spi but it is not going to be installed
                      Recommends: sni-qt but it is not going to be installed
                      Recommends: unity-webapps-common but it is not going to be installed
    E: Unable to correct problems, you have held broken packages.


I have removed KDE using synaptic and also tried [this]([https://askubuntu.com/questions/140246/how-do-i-resolve-unmet-dependencies-after-adding-a-ppa](https://askubuntu.com/questions/140246/how-do-i-resolve-unmet-dependencies-after-adding-a-ppa)), both the solutions. But still the font are not like the previous, and while opening the Ubuntu I do not get the typical Ubuntu symbol, but the Gnome symbol.


Edit:
While installing checkbox-gui;


    sudo apt-get install checkbox-gui
    E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
    E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


N.B.:I have a dual boot with Windows 7

---

### Post by chandramauli2 on 2018-06-29
Please help me!!

---

### Post by ajgreeny on 2018-06-29
This may or may not work, and you could have complicated things even more by using a ppa for the kubuntu-desktop installation.  It also shows the inadvisability of installing multiple DEs in your system which can make things very cumbersome and give you a variety of some basic applications available, ie duplicate text-editor, terminal, file-manager, etc etc, and cause some instability.

However, run command ```
grep -i " install " /var/log/dpkg.log.1 /var/log/dpkg.log | grep kubuntu-desktop
``` which will show you the date and time that you installed the new DE.
You can now run the same command again without the final **grep** section, ie ```
grep -i " install " /var/log/dpkg.log.1 /var/log/dpkg.log
``` and from the full listing output you should be able to see all the packages that were installed at the same time as kubuntu-desktop.

Make a note of all these packages and now try removing them using ```
sudo apt remove *packages*
``` but listing them all where I show *packages* with a space between each package name. Do not use the package version number unless it is really part of the name.
This can be quite a time consuming activity as I know from experience having first added and then removed mate DE from a xubuntu installation, but it did what was necessary.

If that works well enough for you try the same but for **gnome-desktop**, or whatever the main package was that you installed to get gnome.

Good luck!

---

