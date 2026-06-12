---
title: "Easily Manage Wireless Networks (GTKWifi)"
date: 2006-01-07
forum: Outdated Tutorials &amp; Tips
---

### Post by Mr Frosti on 2006-01-07
One of the essential tasks of a laptop user is to be able to quickly and easily connect to different wireless access points. If anyone has used the "Network Monitor" program that starts with Ubuntu by default, you understand what a frustrating task this can be. 

I came across a Project listed on the Ubuntu Forums named "GTKWifi", and figured I would share it with other people in need of a solid wifi app. 

GTKWifi at a glace supports the following features:
[LIST=1]
[*]One click connecting
[*]Access Point scanning
[*]Preferred network list
[*]WEP key memory
[*]Fast and easy interface
[/LIST]

The project page can be found here:

[http://ubuntuforums.org/showthread.php?t=34645&page=1]("http://ubuntuforums.org/showthread.php?t=34645&page=1")

To install GTKWifi follow these instructions:

1) Open up a terminal by clicking "Applications" -> "Accessories" -> "Terminal"

2) Copy the code in the code boxes, and paste it into the terminal: (Updated to 1.09, thanks Moebius)

```
wget http://internap.dl.sourceforge.net/sourceforge/gtkwifi/gtkwifi-1.09.deb
```
This downloads the file to your computer

```
sudo dpkg -i gtkwifi-1.09.deb
```
This will begin to install the file. You will be prompted for the administrator password. This will be your password.

Once the installation is complete, right click on one of the Gnome panels, at either the top or the bottom of the screen. Click on "Add to Panel". At the very bottom of the list, under "Utility" you will see the "Wireless Connection Manager" application. Select this and click "Add"

You have now installed this application to your panel. To start it, click on it, and select the wireless access point, if any, that you wish to connect to. 

That was an easy one. Thanks goes to Brian Cairns.

---

### Post by GQed76 on 2006-02-04
Should you uninstall network manager?

---

### Post by Kieffer87 on 2006-02-04
When I used this my internet would connect, disconnect, etc. forever. I would have to use the manager to get connected and then once I had a signal in the network manager close the gtkwifi and all was fine. Any ideas for this?

---

### Post by Nate53085 on 2006-02-04
[QUOTE=GQed76]Should you uninstall network manager?[/QUOTE]


No you shouldn't.

---

### Post by maxdevis on 2006-02-12
how do i uninstall this?
it totally fucked up my internet/networkconnection.

i even can't delete it from my Gnome-panel.

---

### Post by kaamos on 2006-02-12
```
sudo apt-get remove gtkwifi
```

---

### Post by Moebius on 2006-02-12
GTKWifi 1.09 has been released for quite some time (September 2005), so you could probably update this thread.

[GTKWifi 1.09](http://ubuntuforums.org/showthread.php?t=73563&highlight=GTKWifi+1.09)

---

### Post by Nano on 2006-02-12
Ok, cool, but still I don't understand what's different and/or better than the default network manager.

---

### Post by namit on 2006-02-13
i try to run gtkwifi and i get this

Traceback (most recent call last):
  File "/usr/bin/gtkwifi", line 27, in ?
    import pygtk
ImportError: No module named pygtk


Can anyone help?

---

### Post by Mr Frosti on 2006-02-13
[QUOTE=Nano]Ok, cool, but still I don't understand what's different and/or better than the default network manager.[/QUOTE]

The default Network Monitor for Gnome seems to be more of an overall network manager, than something made with wireless networks in mind. There is a need, imo for a dedicated wifi tool, hence this guide. I wanted something that could manage preferred networks and quickly tell me what is available in the area. Creating profiles to do this in the Network Monitor was a painstaking task that seemed to hang for longer than it should.

---

### Post by Mr Frosti on 2006-02-13
[QUOTE=namit]i try to run gtkwifi and i get this

Traceback (most recent call last):
  File "/usr/bin/gtkwifi", line 27, in ?
    import pygtk
ImportError: No module named pygtk


Can anyone help?[/QUOTE]

Sounds like you have a broken dependency (Something between Python and Gnome bindings). Run Synaptic Package Manager and see if it prompts you about fixing a broken package. To do this, click in "System" -> "Administration" -> "Synaptic Package Manager". Enter in your password. 

If you are not prompted to fix a broken package, then you will have to install it manually. Do a search in Synaptic for "pygtk" and install the "python-gtk2" package. This should resolve the issue.

---

### Post by evilmrt on 2006-02-13
I love this little program. I don't understand why it isnt a part of the Ubuntu distro??? Its essential if you use wifi!

---

### Post by imagine on 2006-02-13
[QUOTE=Mr Frosti]This will begin to install the file. You will be prompted for the administrator password. This will be your password.[/QUOTE]
Just a little nitpicking: sudo does not ask for the administrator password, but for *your* password, ie the password of the user who runs sudo.
At least that's the default behaviour of sudo and also used in all versions of Ubuntu.

---

### Post by MONODA on 2008-02-11
eh... its pretty good but it takes up tooooo much ram 8mb :S. Try out wifi-radar

---

