---
title: "Start Remote Desktop Server"
date: 2008-11-06
forum: New to Ubuntu
---

### Post by SodaveO on 2008-11-06
I am new to Ubuntu and to forums so I trust you will be kind.
I am running XUBUNTU 8.04 Home Server
This is a package distributed by PC User Magazine in Australia.
One of the options in the package is remote server and viewer.
I can click Start remote Desktop Server and then use VNC from another PC and make a connection.
When the XUBUNTU PC does a restart  the Remote server requires starting on every occaision,
My Question is how can I have the Remote Desktop Server started every time the PC boots.
Thank You in advance

---

### Post by talsemgeest on 2008-11-06
If you can make it auto login, all you have to do is add the command to start the remote desktop server (Usually the name) to the sessions. I don't use xubuntu so I'm not sure where the configuration box is, but have a look around under the preferences, and look for "sessions".

---

### Post by Peter09 on 2008-11-06
Hi,
VNC is not very good for what you want to do - it really is designed to view a remote desktop.

There are plenty of other options. What exactly do you want to do? 

login to the server GUI
Issue terminal level commands to the server
Run a true desktop remotely from the server?

etc



Has your server a GUI such as gnome?

---

### Post by SodaveO on 2008-11-06
I can log in to the PC and there is an option in the menu  called Start Remote Desktop Server and it will run everytime I click on it  but what I am after is to force it to run everytime the PC starts automatically.

---

### Post by SodaveO on 2008-11-06
I want the XUBUNTU PC to be a server and log into it from other PC's. VNC is working fine

---

### Post by Peter09 on 2008-11-06
Yes VNC will work if you have already logged in at the server, VNC shows an existing desktop on the server.

The best solution I have found is to install openssh-server on the server and then install Freenx on server and client.

---

### Post by SodaveO on 2008-11-06
My clients are Vista and XP PC's and I wish to view the server from them which is working well all I want now is for the server to load the service every time it restarts

---

### Post by Peter09 on 2008-11-06
Which services? If after login, you can use System->Preferences->Sessions to define what runs automatically after login

---

### Post by SodaveO on 2008-11-06
I do not have System>Preferences>Session

Preferences and Session are no where to be seen.

---

### Post by talsemgeest on 2008-11-06
Is it the same on Xubuntu? I thought they had a different menu system. But yes, like I said, you need to find hte "sessions" configuration.

---

### Post by SodaveO on 2008-11-06
I have looked in every menu option  and it cannot be seen

---

### Post by Peter09 on 2008-11-06
Yes - sorry did not note that you are using Xubuntu, not sure where that particular menu is in the window manager.

---

### Post by SodaveO on 2008-11-06
It is Xubuntu 8.04

---

### Post by SodaveO on 2008-11-06
How do I find out the file name or program name of the process when it is running

---

### Post by Hibbelharry on 2008-11-12
The first hint was right. The vnc server is a program running on an already started session. It's no system service, so you can't do what you want. There are also vnc servers which are able to do what you want but they need to be installed and configured by hand.
Since vnc is aged and really slow and insecure compared to modern methods of remote desktops i would really really recommend you to use freenx instead. There are clients for linux and windows available for free, it's highly secure and also works well on slower connections or on the other side you get less network traffic and more functionality. 

It's not important which version of ubuntu you're running, whether its xubuntu, ubuntu, kubuntu... they just differ in the preinstalled installed desktop environment and offer the same packages. The Version (8.04 or hardy) is important.

You can grab prebuild packages from here:
[https://launchpad.net/~freenx-team/+archive](https://launchpad.net/~freenx-team/+archive)

just use nxsetup to do the needed steps after installation.

nxclient is available from nomachine.com

---

### Post by HuntMike79 on 2008-12-10
> **Hibbelharry said:**
> The first hint was right. The vnc server is a program running on an already started session. It's no system service, so you can't do what you want. There are also vnc servers which are able to do what you want but they need to be installed and configured by hand.
Since vnc is aged and really slow and insecure compared to modern methods of remote desktops i would really really recommend you to use freenx instead. There are clients for linux and windows available for free, it's highly secure and also works well on slower connections or on the other side you get less network traffic and more functionality. 

It's not important which version of ubuntu you're running, whether its xubuntu, ubuntu, kubuntu... they just differ in the preinstalled installed desktop environment and offer the same packages. The Version (8.04 or hardy) is important.

You can grab prebuild packages from here:
[https://launchpad.net/~freenx-team/+archive](https://launchpad.net/~freenx-team/+archive)

just use nxsetup to do the needed steps after installation.

nxclient is available from nomachine.com
Hi, I've tried freeNX but I just cannot get it to work under Xubuntu 8.04... Is there a guide or something to help us newbies?

---

