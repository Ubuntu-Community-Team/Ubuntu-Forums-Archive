---
title: "HOWTO: Tunnel VNC through SSH from a windows machine"
date: 2005-01-19
forum: Outdated Tutorials &amp; Tips
---

### Post by Darrena on 2005-01-19
VNC is a utility that allows you to remotely control your PC from another networked PC.  VNC has been around a long time and works well enough on high bandwidth connections however by default it passes everything in the clear and is not secure.  This HOW TO walks you through tunneling VNC through SSH to secure the traffic.

[COLOR=Red]NOTE[/COLOR] If you need to use your machine remotely FreeNX is _**MUCH**_ better than VNC, however if you need access to your already logged in session VNC works well enough.  If you need help jdong has a great HOW TO for FreeNX located here: [http://www.ubuntuforums.org/showthread.php?t=1968](http://www.ubuntuforums.org/showthread.php?t=1968)
--------------------------------------------------------------------------------------------------------
On your Ubuntu desktop click computer->Desktop Preferences->Remote Desktop to bring up the VNC properties.

check the following boxes:
[list]Allow other users to view your desktop[/list] 
[list]Allow other users to control your desktop[/list] 
[list]Require the user to enter this password *Enter your connection password here, you will be prompted for this when you connect* [/list] 


UNCHECK the following:
[list]Ask you for confirmation[/list]

Click close when you are finished.
-------------------------------------------------------------------------------------------------------
Download Putty: [http://www.chiark.greenend.org.uk/~sgtatham/putty/](http://www.chiark.greenend.org.uk/~sgtatham/putty/) or use cygwin.

Start putty and enter the address you would like to connect to, select SSH as the protocol.

On the left hand side you will see various configuration options, click the category named 
Tunnels and add the following information under add new forwarded port:
Source Port 5900
Destination Port 127.0.0.1:5900

*Optional* Go to the section labeled SSH and check enable compression, with some VNC clients this can cause slower response but with the generic realvnc client it works fine.

Save the session
-------------------------------------------------------------------------------------------------------
Download vncviewer from [http://www.realvnc.com](http://www.realvnc.com) 
(Or any of the various VNC clients out there like tightvnc or ultravnc)

Open the vncviewer and connect to 127.0.0.1

-------------------------------------------------------------------------------------------------------
Notes:
For added security use your hosts.allow to restrict connections from only localhost so that you must use SSH to connect.

If using a router, redirect TCP Port 22 (SSH) from the internet to your PC so you can connect remotely but you may want to use your hosts.allow or a filter on your router to only allow those connections from a trusted source.

If you are going through a firewall that blocks SSH you can redirect 80 or 443 with iptables.

If you have problems when using ULTRAVNC or TightVNC try using different encoding options, I had problems with the session when using ULTRAVNC and ZRLE

---

### Post by fishd on 2005-01-20
Thanks for the document... I've been messing a fair bit with SSH recently on my Ubuntu box and I'm really impressed with it...

You mention using hosts.allow to tie down the security of the Vino-Server...  as an alternative I take it I can add the following line to hosts.deny

*VINO-SERVER: ALL EXCEPT 127.0.0.1 : ALLOW*

The reason I'm looking at this is I run an open wireless network so anyone can connect but obviously I don't want anyone to be able to access my servers desktop, if I'm reading the man files right, this line will deny everyone except the local machine access to the Vino-server daemon ... correct?

Thanks...

---

### Post by Darrena on 2005-01-20
[QUOTE=fishd]Thanks for the document... I've been messing a fair bit with SSH recently on my Ubuntu box and I'm really impressed with it...

You mention using hosts.allow to tie down the security of the Vino-Server...  as an alternative I take it I can add the following line to hosts.deny

*VINO-SERVER: ALL EXCEPT 127.0.0.1 : ALLOW*

The reason I'm looking at this is I run an open wireless network so anyone can connect but obviously I don't want anyone to be able to access my servers desktop, if I'm reading the man files right, this line will deny everyone except the local machine access to the Vino-server daemon ... correct?

Thanks...[/QUOTE]
 That should work, your method is probably better than what I suggested.  Let me know if it works and I will update my post to use your method.

---

### Post by Ukr on 2007-08-28
Hi everyone! thanks for howto. I still have a  problem to connect win/xp to ubunto7.04/gnome/linksys wrt54. Port forvard 22 to 192.168.1.100. Runnig dyndns doman name and there no problem to connect from home LAN using realVNC. Problem from external network. In a putty section ssh/tunnel/destination should i mark radiobotton from local to remote, and any ather ideas what im doing wrong?

---

### Post by DragonRebornUK on 2009-03-25
Great Guide, got it working instantly with it
Many Thanks

Matt:P

---

### Post by Mriswithe on 2009-04-09
Ok I am having a problem with accomplishing this. I have it set up properly with my port forwarding and this works from a windows box from anywhere, but I have an ubuntu linux box that it does NOT work on. 

I downloaded putty for the linux box set it up exactly as for the windows box and open up either remote desktop connection or an actual version of VNC for linux and point it at localhost just like on a windows box and I get connection was closed. Different error messages on each one.

Remote Desktop Viewer: connection to host "localhost:5900" was closed.

VNCViewer: Unable to connect to host: Connection refused (111) 

The error message doesn't change if the putty session is active or not. I am suspecting that something on my linux laptop just is ignoring the attempt to make the connection and keeping it from even considering the tunnel that I have open, but even if this is the case I do not know where I would confirm or try and change this. Also I can run virtualbox and run a copy of windows xp and the same setup that works everywhere else also works there if this helps at all. 

Anyone run into this already? any help is appreciated. 


Mriswithe

---

### Post by Mriswithe on 2009-04-10
Found that if I used the terminal command to SSH through the VNC connection works. Thanks for the help anyway

Mriswithe

---

### Post by Sivaram Nyapathi on 2010-01-04
hi 
i'm newbie to ubuntu i need help configuring VNC through SSH , i have a desktop which  i use it as PHP server and for downloading . i have tried the steps given in the post but no luck , i'm not able to connect using vnc viewer its sowing error message "connection reset by peer ".

I have my laptop on 192.162.1.2 and my ubuntu desktop which i need to accesses on 192.168.1.3 and my dsl router is on 192.168.1.1.

 it will only work if i log in on desktop then connect vcn viewer to 192.168.1.3.
pls help .

---

### Post by Sivaram Nyapathi on 2010-01-04
i use windows 7 on my laptop(192.168.1.2) and ubuntu 9.10 on (192.168.1.3)

---

### Post by Dj TweeX on 2010-01-08
Hey Everyone. happy new year! this is my first post in a long time. i have an issue and im hoping this thread can help me solve it.

so this is the setup.

My server at home is a hackintosh. my laptop is now a linux mint box but used to be a hackintosh as well. anyway. to get vnc working through my schools network i had to do an ssh tunnel as follows;

```
ssh -L 1024:192.168.1.158:5900 67.161.135.xxx
```
then vnc with;
```
localhost:1024
```

which always worked. now that im running linux, im having troubles connecting the vnc. it will connect, ask for my password, then disconnect on input.

any thoughts??

---

