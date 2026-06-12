---
title: "ubuntu vncviewer --&gt; Fedora 9 realvncserver"
date: 2008-10-07
forum: New to Ubuntu
---

### Post by prt7u on 2008-10-07
Howdy!

I hope that y'all can help me solve this problem.  Typically, what I was doing in Fedora9 to other Fedora machines was this:

Logging in to the remote machine, firing up the realvnc server and back on my desktop machine fire up the vncviewer and do what I want on the machine where the server resides.  Everything works just fine.

Skip ahead.  I installed ubuntu linux 8.04.1 on my desktop and have it configured just the way I want it.  Very nice, I must say.  I want to do the same as above.  Login to the remote machine Fedora machine, fire up realvnc server and then back on my ubuntu 8.04.1 desktop machine I want to point vncviewer at it and do what I want on the machine running the server.

Does anyone have any ideas how I can get this to work?  I haven't had a lot of luck poking around here.  Are the two compatible?

Thanks,

Pete

---

### Post by superprash2003 on 2008-10-07
well.. through vnc yes.. to connect go to the terminal and type vncviewer x.x.x.x where x.x.x.x is the ip of the fedora machine you want to connect to.. to remotely connect, you need to enable remote desktop in ubuntu . go to system->preferences->remote desktop

---

### Post by HermanAB on 2008-10-07
Well, on Linux, VNC is almost always the wrong answer.  The purpose of VNC is to control Windows machines that don't have RDP (the Home version) or for training, where the user needs to see what the help desk guy is doing.

Linux to Linux, SSH is better:
$ ssh -C -c blowfish -X user@server "gedit /etc/fstab"

or if you are click happy:
$ ssh -C -c blowfish -X user@server gnome-panel

Cheers,

Herman

---

