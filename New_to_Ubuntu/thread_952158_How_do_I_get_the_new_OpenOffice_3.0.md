---
title: "How do I get the new OpenOffice 3.0?"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by andrewwg94 on 2008-10-18
^

---

### Post by SunnyRabbiera on 2008-10-18
well if you insist, just keep in mind this isnt a chatroom:
This guide mainly applys to recent versions of Ubuntu (Versions 7.10 through 8.10) as I am unsure if Open office 3 will work in older versions of Ubuntu.
Anyhow I will keep this simple:
Step 1: Download open office 3 for debian
2: Extract the zip file
3: In the debs folder move everything you have into the desktop integration folder by selecting as many of the debian insallers you can at a time but there are a whole crap load of them so this might take a while.
4: For normal Ubuntu users install the package nautilus-open-terminal, for Kubuntu and xubuntu users skip this
5: For normal Ubuntu users, restart your computer, for Kubuntu and xubuntu users skip this.
6: Remove as much of open office 2 as you can
7: go into that desktop integration directory and open up a terminal, now how to open your terminal in Ubuntu is by right clicking in the folder and selecting Open terminal.
Kubuntu and xubuntu users should have the open terminal command in the main menu of both Thunar and Dolphin/Konqueror
8: put in the command: sudo dpkg -i *.deb
9: after dpkg is done you may wish to try to install the package openoffice.org3.0-debian-menus_3.0-9354_all located in your desktop integration folder.
10: done

---

### Post by waldo_phill on 2008-10-18
If you haven't already downloaded it. You can find the package here: [http://download.openoffice.org/other.html#en-US](http://download.openoffice.org/other.html#en-US)

---

### Post by andrewwg94 on 2008-10-18
> **SunnyRabbiera said:**
> well if you insist, just keep in mind this isnt a chatroom:
This guide mainly applys to recent versions of Ubuntu (Versions 7.10 through 8.10) as I am unsure if Open office 3 will work in older versions of Ubuntu.
Anyhow I will keep this simple:
Step 1: Download open office 3 for debian
2: Extract the zip file
3: In the debs folder move everything you have into the desktop integration folder by selecting as many of the debian insallers you can at a time but there are a whole crap load of them so this might take a while.
4: For normal Ubuntu users install the package nautilus-open-terminal, for Kubuntu and xubuntu users skip this
5: For normal Ubuntu users, restart your computer, for Kubuntu and xubuntu users skip this.
6: Remove as much of open office 2 as you can
7: go into that desktop integration directory and open up a terminal, now how to open your terminal in Ubuntu is by right clicking in the folder and selecting Open terminal.
Kubuntu and xubuntu users should have the open terminal command in the main menu of both Thunar and Dolphin/Konqueror
8: put in the command: sudo dpkg -i *.deb
9: after dpkg is done you may wish to try to install the package openoffice.org3.0-debian-menus_3.0-9354_all located in your desktop integration folder.
10: done

why is there no .deb package?

---

### Post by stmiller on 2008-10-18
Just download and install the 'deb' version from openoffice.org . It's a huge folder of debs- there is not just 'one' deb.

It installs in /opt and does not interfere with any Ubuntu packages. :)

Edit: check out this page I just ran across

[http://openofficedocs.wordpress.com/2008/10/14/install-openoffice-30-on-ubuntu/](http://openofficedocs.wordpress.com/2008/10/14/install-openoffice-30-on-ubuntu/)

---

### Post by andrewwg94 on 2008-10-18
It doesn't install as nicely as i would have expected. for example, i have to assciate the file formats with ooo3

---

