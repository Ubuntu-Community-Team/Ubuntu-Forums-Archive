---
title: "VNC on Xubuntu"
date: 2015-02-11
forum: New to Ubuntu
---

### Post by maurice9 on 2015-02-11
Hello all

First time with Linux.

I have followed the instructions on the guide here:
[http://robot.wpi.edu/wiki/index.php/Setting_up_an_XUbuntu_VNC_Server](http://robot.wpi.edu/wiki/index.php/Setting_up_an_XUbuntu_VNC_Server)

I am to the line that says "Turbo VNC" after "Automatically Start The Server"
I am unable to log into Xubuntu from either a Mac (10.6.8) using Chicken of the VNC or Windows 7 using TightVNC.
I left the port alone at first then changed it to 5907 since I have another machine on the network using 5901 and thought maybe an issue and still nothing.
This is all being tested internal on the same lan, not from the outside.

On either Mac or Windows clients am usig 10.0.0.10:5907 (and 10.0.0.10:5901 prior to changing the port)

My IPs are:
xUbuntu = 10.0.0.10
Mac = 10.0.0.33
Windows = 10.0.0.201
All are on the same LAN: 10.0.0.0/24

I dont know if I have to setup the TurboVNC part but if do I dont understand how to do that.
All it says on the guide is:

/opt/TurboVNC/bin/vncserver &

I looked in /opt/ and there is no TurboVNC directory so I tried typing that in to the terminal and got:

maurice@DellE5500:~$ /opt/TurboVNC/bin/vncserver &
[1] 3437
bash: /opt/TurboVNC/bin/vncserver: No such file or directory
maurice@DellE5500:~$ 

So am thinking I need to install TurboVNC?????
How do I do that?

My current start up script at /etc/init/x11vnc.conf:
start on login-session-start
script
x11vnc -xkb -noxrecord -noxfixes -noxdamage -display :0 -auth /var/run/lightdm/root/:0 -forever -shared -bg -o /var/log/x11vnc.log -rfbauth /etc/x11vnc.pass -rfbport 5907 -localhost
end script

And right before changing to port 5907:
start on login-session-start
script
x11vnc -xkb -noxrecord  -noxfixes -noxdamage -display :0 -auth /var/run/lightdm/root/:0 -forever  -shared -bg -o /var/log/x11vnc.log -rfbauth /etc/x11vnc.pass -rfbport  5901 -localhost
end script

and I have restarted the computer and let it both log in to the desktop as well as left it at the login screen.

Thanks much in advance

Maurice

---

### Post by steeldriver on 2015-02-11
First of all, x11vnc and the TurboVNC vncserver are different things. Generally, anything identifying itself as vncserver (that also includes things like vnc4server and tightvncserver) are intended for running multiple, independent,  standalone VNC sessions whereas x11vnc (and for example Gnome/Ubuntu's vino-server) are "desktop sharing"  servers intended to (as the x11vncman page says) "allow VNC connections to real X11 displays". If you are using x11vnc then anything in /opt/TurboVNC shouldn't be relevant.

The most obvious thing about your x11vnc command line is the -localhost parameter: that means that the server will only listen on (only accept connections via) the localhost 'loopback'  interface (usually 127.0.0.1). Why would anyone want to do that, for a service that's designed for remote access? In a word: security.  The bare VNC protocol simply is not secure, so the only safe way to run it anywhere outside a strict LAN context is by tunnelling the connection over SSH. 

If you are sure you will never use it outside the LAN (i.e. your router will never open ports from the outside world) then you could remove the -localhost, however a better solution imho would be to keep it and configure the client(s) to use SSH. Many newer ones (such as remmina) make that fairly painless.

---

### Post by maurice9 on 2015-02-11
Ok I see...

Since it was in the guide that is what I did.
I get it now.
Yes this is only on LAN so I can get into from my bedroom as am diabled and cant get around too well but as you mention if I setup an SSH tunnel to the machine then I can run it thru the tunnel and the same for if I ever need it from the outside.
I appreciate your input.

Thanks much

---

### Post by steeldriver on 2015-02-11
Yeah I can see no reason why that guide suddenly started talking about TurboVNC

Post back if you continue to have issues - I have played with x11vnc a little in the past (I have a mythbuntu box that uses it as part of the default installation) and use tightvncserver (the "other" type of VNC) pretty frequently for work

---

### Post by maurice9 on 2015-02-11
Hey Steeldriver

Eveything is up and working now. Thanks mmuch for your help on this.
I am new to this but I can already tell am going to like the customization and learning.
Mind's already working better.

Thanks much again.

---

