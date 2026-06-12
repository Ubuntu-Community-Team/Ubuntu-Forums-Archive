---
title: "Remoe connect to ubuntu server?"
date: 2016-01-12
forum: New to Ubuntu
---

### Post by thexnightmare on 2016-01-12
Dear,
After testing ubuntu on y desktop and switched from widnwos it it, I want to try ubuntu server.
THa'ts why Ive regsistered a VPS ubuntu 14, and I am connecting to it through ssh.
Andone can help me to manage how can I remote connect to it;s desktop?

---

### Post by nerdtron on 2016-01-12
You mean your VPS Ubuntu server has a GUI?

SSH and the command line are all you need to configure an Ubuntu server. But if you really want to remotely access the Ubuntu desktop GUI, you ca have several options such as:
Team viewer: [https://www.teamviewer.com/en-us/download/linux/](https://www.teamviewer.com/en-us/download/linux/)
VNC: [https://www.youtube.com/watch?v=gemAacoe78U](https://www.youtube.com/watch?v=gemAacoe78U)
XRDP: [http://www.ubuntugeek.com/xrdp-remote-desktop-protocol-rdp-server.html](http://www.ubuntugeek.com/xrdp-remote-desktop-protocol-rdp-server.html)

---

### Post by thexnightmare on 2016-01-12
no it dont, the server provider jsut send me ssh login access with root usrname and password. I want to install a the GUI and remotely connect to it.

---

### Post by QIII on 2016-01-12
Just a minor point to remember here:  Ubuntu Server installs without a desktop.  Adding one detracts from its duties as a server and adds more attack surface if it is facing the web.

There is little to be gained and much to be lost by adding a desktop and all of the associated services.  

Is there a compelling reason for you to have a desktop?

---

### Post by thexnightmare on 2016-01-12
Oh i see, but how come windows server is strong and have dekstop?

---

### Post by nerdtron on 2016-01-12
> **thexnightmare said:**
> Oh i see, but how come windows server is strong and have dekstop?

Because on windows, the GUI is integrated it to the OS itself. you can't (much so) use it windows without a GUI.

On linux the GUI is just another program running on the OS, you can turn it off anytime you want and you will not lose any feature of the OS.

EDIT: ahhh, it's tempting to start the linux vs windows wars here :) Anyway, that's just the way it is, a GUI is not a requirement on using Linux as a server.

---

### Post by thexnightmare on 2016-01-12
This is another point counting to linux, and that why i will go for it, but canu or anybody tell me how to install and run GUI on it? at least at the first time and when need to i, then will shut it down for security issues

---

### Post by nerdtron on 2016-01-12
The links I've given on my first reply installs a GUI. It's XFCE since it consumes lower resources and doesn't require 3D acceleration.
You can have lots of choices for GUI, not just XFCE

From [URL="http://askubuntu.com/questions/53822/how-do-you-run-ubuntu-server-with-a-guiYou"]http://askubuntu.com/questions/53822/how-do-you-run-ubuntu-server-with-a-gui
[/URL] You can install the default Ubuntu desktop by executing the following:
  sudo apt-get install ubuntu-desktop
  There are many desktop alternatives which you may install and use, like:
  
[LIST]
[*][Gnome 3]("http://www.gnome.org/gnome-3/") installation: sudo apt-get install gnome-shell 
[*][KDE]("http://www.kde.org/") see [Kubuntu]("http://www.kubuntu.org/") installation: sudo apt-get install kubuntu-desktop 
[*][XFCE]("http://www.xfce.org/") installation: sudo apt-get install xfce4 
[*][LXDE]("http://lxde.org/") installation: sudo apt-get install lxde 
[*][Openbox]("http://openbox.org/") installation: sudo apt-get install openbox 
[*]Gnome Classic a Gnome 3 desktop that looks like Gnome 2 installation: sudo apt-get install gnome-session-fallback 
[/LIST]

Or try this link: [http://www.htpcbeginner.com/install-gui-on-ubuntu-server-14-04-gnome/](http://www.htpcbeginner.com/install-gui-on-ubuntu-server-14-04-gnome/)

---

### Post by thexnightmare on 2016-01-12
ok, ive installed apt-get install xubuntu-desktop, and now it is done, but still in terminal, what to do?

---

### Post by nerdtron on 2016-01-13
> **thexnightmare said:**
> ok, ive installed apt-get install xubuntu-desktop, and now it is done, but still in terminal, what to do?

What VPS provider are you using? because I think Amazon can give you a remote desktop via a Java applet from the web browser.
Command to start the GUI:
```
 sudo startx 
```

If you are on an SSH connection, the startx command will not do anything.

---

### Post by HermanAB on 2016-01-13
It is perhaps a little confusing, but a 'desktop' is only needed on your local computer.  From your local machine, you can run any program you want on any other UNIX computer, anywhere on the planet, be they graphical, or command line over SSH.

For example, if the graphical editor 'gedit' is installed on a remote machine, then you can run it from your local machine like this:
$ ssh -X -C -c blowfish username@serveripaddress 'gedit filename'

and then the remote instance of gedit will pop up transparently on your local machine.

It literally makes no sense to have a graphical desktop on a remote machine.  Your local machine already has a desktop, so there is no point in overwriting the whole thing with a desktop from another machine - doing so just makes it slow, due to all the useless network traffic required to shuffle the desktop graphics back and forth.

---

### Post by thexnightmare on 2016-01-13
I see,
I am on windows, how to run the gedit from ssh?

---

### Post by HermanAB on 2016-01-14
To run X programs on Windows, you need to install and X server (Xming) and a ssh client (PuTTY).

Run Xming first, then PuTTY and then log into the Ubuntu machine.

---

### Post by thexnightmare on 2016-01-14
ok, now i have both software.
i run putty it opens GUI, how to run [COLOR=#000000]$ ssh -X -C -c blowfish username@serveripaddress 'gedit filename'[/COLOR]

---

