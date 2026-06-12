---
title: "Tightvnc Server"
date: 2013-05-11
forum: New to Ubuntu
---

### Post by apedance on 2013-05-11
Hello!

Installed version: 12.04

I am new to ubuntu. I do like it very much so far.
Nevertheless i can't get my VNC server to work properly.

I am running an old PC (p4, 1gb ram, plenty of harddrives) as a "Server".
What I need: VNC server should be ready before I even log in.

Is there a solution?

Help would be greatly appreciated!

Cheers!

---

### Post by cariboo on 2013-05-12
The problem with logging into a system using one of the gui vnc clients, is that you have to have a desktop environment of some sort installed, and be logged in on the system you want to control remotely. If you are using your server, stuck in a corner with only power  and network cables connected, as intended,  the system will be sitting at the login prompt. so you need to log in.

If you need gui apps to manage your server, I'd suggest you use X-forwarding. To use it, you need to have openssh-server installed on the server, for a howto, have a look [here]("https://help.ubuntu.com/community/SSH/OpenSSH/Configuring"). once you have installed and configured ssh, just open a terminal and type the following command, adding the gui app you want to run at the end, for example:

```
ssh -X user@server
```

then once logged on to the server, just type the name of the app you want to run at the prompt.

---

### Post by apedance on 2013-05-12
Thank you for the answer!

I think I got you with the necessity to have a desktop environment.

What I forgot to mention is that a Mac is used to control the ubuntu server.

Fine. I installed VNCServer on my machine and tried the ssh -X command.

This is what i get. (XQuartz on my Mac starts up doing nothing, when I execute the command)
```
/usr/bin/xauth:  error in locking authority file /home/alex/.Xauthorityperl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = "en_US:en",
	LC_ALL = (unset),
	LC_CTYPE = "UTF-8",
	LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
xauth:  error in locking authority file /home/alex/.Xauthority
xauth:  error in locking authority file /home/alex/.Xauthority


New 'X' desktop is alexubuntu:2


Starting applications specified in /home/alex/.vnc/xstartup
Log file is /home/alex/.vnc/alexubuntu:2.log
```



Besides the autologin function is not working on my system.
I tried several ways to enable it. 

lightdm.conf
gdm.conf
Systemsettings (set to on)

The system does not log in when I boot the machine.

I don't have the standard ubuntu loginscreen. I think I have this -> [http://hackurx.files.wordpress.com/2010/08/gdm.jpg](http://hackurx.files.wordpress.com/2010/08/gdm.jpg)
Really sorry for my non-existing knowledge. ;)


What my goal is:

Wake my ubuntu machine via WOL and remotely control it via VNC or something else. (doesn't matter how)
I just need my machine to login somehow.


Thank you for your time.

---

### Post by apedance on 2013-05-13
> **apedance said:**
> 


What my goal is:

Wake my ubuntu machine via WOL and remotely control it via VNC or something else. (doesn't matter how)
I just need my machine to login somehow.


Thank you for your time.


I hope this is possible somehow. Please help me.

WOL is working :D

---

### Post by steeldriver on 2013-05-13
Have a look here, maybe something like this might work for you - it uses x11vnc, I'm not sure whether the same is possible with tightvncserver

[http://mlepicki.com/2011/10/remote-vnc-login-to-ubuntu-11-10/](http://mlepicki.com/2011/10/remote-vnc-login-to-ubuntu-11-10/)

---

### Post by apedance on 2013-05-14
I will give it a try. Thanks!

---

