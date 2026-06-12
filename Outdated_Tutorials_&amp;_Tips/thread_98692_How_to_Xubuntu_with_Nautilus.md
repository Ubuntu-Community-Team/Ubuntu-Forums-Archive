---
title: "How to: Xubuntu with Nautilus"
date: 2005-12-03
forum: Outdated Tutorials &amp; Tips
---

### Post by linuxnomad on 2005-12-03
This is my first attempt at a how to. I tried just about everything to get my Xubuntu running with as much functionality as I had in Gnome, I am running a lot of gnome as you will see.

Incert the Ubuntu install CD into the CD-drive
when the boot screen comes up type "server" and press enter
after the server install is complete the fun begins

open up the source-list with the nano editor

     "sudo nano /etc/apt/sources.list"
uncomment the universe repositories and save&exit (ctrl-x)

     "apt-get update"
     "apt-get dist-upgrade"
     "apt-get install Xubuntu-desktop gdm"

installing gdm because a display manager makes logging in nicer

next I wanted to use Nautilus because it has a lot of functionality that you just can't get from rox, thunar, and xffm. The only drawback I see using Nautilus is its slower, but I don't really see the difference on my system. 

Ok first you need to apt-get nautilus, another drawback is it brings a lot of gnome with it.

open a terminal:

      "apt-get install nautilus"

Once its installed to get it to not draw the desktop the best way I have found is a method psychicdragon mentioned in another post.

open a terminal and enter:

      "gconftool-2 -s /apps/nautilus/preferences/show_desktop -t bool false"

this stopped nautilus from drawing my desktop everytime I logged in. To change the file manager in the Xfce menu right click the Xfce menu button select properties and copy the menu file:

      "/etc/xdg/xfce4/desktop/menu.xml"

open a terminal:

      "sudo mousepad /etc/xdg/xfce4/desktop/menu.xml"

scroll down to <xfdesktop-menu> and change <app name="File Manager" cmd="rox" icon="file-manager"/> to <app name="File Manager" cmd="nautilus" icon="file-manager"/> here is what is should look like:

<xfdesktop-menu>

	<app name="Run Program..." cmd="xfrun4" icon="gnome-fs-executable"/>

	<separator/>

	<app name="Terminal" cmd="xfterm4" tip="Terminal emulator" icon="gnome-terminal"/>
	<app name="File Manager" cmd="nautilus" icon="file-manager"/>
	<app name="Web Browser" cmd="sensible-browser" icon="gnome-globe"/>

	<separator/>

next you need to go into the file manager in the Xfce4-MenuEditor

left click Xfce-menu go up to settings and select XFCE4-MenuEditor
right click File Manager select edit and change command from rox to nautilus save and close

next I used arniboy's Automatix to install most of the video and auto codec and a few other things like j2re-1.5, firefox pluggins, and acrobatreader

Automatix will change you sources.list file

to get Automatix to run in Xubuntu you need to install gnome-terminal

open a terminal:

       "apt-get gnome-terminal"

get Automatix from "http://ubuntuforums.org/showthread.php?t=66563" arnieboy is a genius, saved me hours of install time.
With gnome-terminal installed just follow arnieboy's install instruction. 

to set up a network printer you will need gnome-cups-manager. The cups manager was disabled for some reason. 

      "apt-get install gnome-cups-manager"

This is the easiest way to get a printer working, at least for me.

I used  vnbuddy2002 How to ([http://www.ubuntuforums.org/showthread.php?t=26438&highlight=printing+linux](http://www.ubuntuforums.org/showthread.php?t=26438&highlight=printing+linux))
to set up samba and connect my two computers.

I really didn't like using so much of gnome in XFCE, but I really wanted a more complete system. A hybrid system isn't that bad is it. 

Using Nautilus my usb drives automount without gnome-volume-manager. Just  plug in the usb drive and open nautilus and click on the computer icon in the task bar. 

Hope this helps someone. Also if anyone has a better way of doing any of what I have done please let me know. I'm just a noob, only been using Ubuntu 6 months.

Matt

---

### Post by deepspring on 2006-08-04
Thanks mate, works perfectly.

Thunar is a great filemanager, but it lacks many of the features nautilus show cases, like network browsing.

---

### Post by trondhuso on 2006-11-20
Hi list,
After working a while with Ubunut 6.06 (which crached a lot) I went for Xubuntu - and (knock on wood) the computer is still running without a crash.

I am also a big fan of Nautilus, and therefor I am very grateful for this how to. Since I from time to time connect to a WinXP-machine, I needed Samba-extentions, and so I contribute with the apt-get you need to run in order to connect with smb://... in nautilus.

sudo apt-get install smbfs libsmbclient libgnomevfs2-extra
(thanks to this link I found that out: [http://cremerieprod.fr/~cmaussan/dotclear/index.php/post/2006/10/11/Nautilus-et-Samba-sous-Xubuntu](http://cremerieprod.fr/~cmaussan/dotclear/index.php/post/2006/10/11/Nautilus-et-Samba-sous-Xubuntu))

I still haven't found out how you make nautilus work as default filemanager since I would like to use it in all programs in Xubuntu. And I pretty much want to remove Thunar...

Trond

---

