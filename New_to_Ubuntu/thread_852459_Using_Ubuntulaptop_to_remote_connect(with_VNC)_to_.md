---
title: "Using Ubuntulaptop to remote connect(with VNC) to Vistapc"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by zelluz on 2008-07-07
Hello people of the internets!

I love Ubuntu so far, but I have one little problem. This is how it looks like:

I have one laptop with Ubuntu on it. 
I have on Vista stationary PC.

With the laptop I want to remote control my Vista machine.

I have installed freeSSHD on my Vista machine, and putty on my ubuntu. (Port forwarded port 22 to my router for SSH...) 
The SSH part is fine. At the moment I can open up Putty and connect to the vistamachine, over the internet. (Through port 22)

And now for the hard(?) part:

I have also installed TightVNC server on my vista pc. Ive checked the "allow loopback connections" box. Port 5900 is also port forwarded in my router.

In Putty, under the SSH-> tunnels menu, I have entered in 5900 in the source port, and 127.0.0.1:5900 in the destination.

I have installed xtightvncviewer, and I'm currently trying to log on to my vistapc, over the internet by using Terminal Server Client.

Here I use 127.0.0.1:5900 in the computer-field
Protocol is vnc
username is the same as the username on the vistapc
In the password field I can not type anything into it.
In the Domain field I have typed in the domain my vistapc is on

If I try to connect, all I'm getting is this:
vncviewer: ConnectToTcpAddr: connect: Connection refused
Unable to connect to VNC server.

Now, do you have any idea what I'm doing wrong here? I appreciate all the help I can get in advance. Thanks!

The SSH part seems to be working properly, however not the VNC part...

---

### Post by someonestolemyname on 2008-07-18
Have you tried with just VNC? It's not secure, but it would be better for testing. Forget any tunnels and just [IP address of Vista]:5900.

If that works then there must be something wrong with your SSH setup

---

### Post by cmittle on 2008-11-15
Have you been able to setup vnc from your laptop to vista machine yet?  I am hoping to be able to do this to remotely help my dad on his home machine.


cory

---

### Post by nhasian on 2008-11-15
vista broke VNC

[http://www.tightvnc.com/faq.html](http://www.tightvnc.com/faq.html)

Does TightVNC work on Windows Vista?

Unfortunately, TightVNC has known issues with Windows Vista operating system, just like all other versions and free distributions of VNC-derived software. Vista's new security features broke the way VNC service was implemented. And it's not clear yet how much effort would be required to workaround the problems. Unfortunately, that does not look very simple. 

I tried getting it to work with UltraVNC but i was not successful either.

---

### Post by Peter09 on 2008-11-15
use FreeNX if you want a desktop.

[http://freenx.berlios.de/download.php](http://freenx.berlios.de/download.php)

Windows does support RDP as does Linux. So if you can enable RDP on your vista machine thats the way to go. (RDP capable apps are already installed in Ubuntu)

---

