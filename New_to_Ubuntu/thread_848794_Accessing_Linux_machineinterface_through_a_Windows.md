---
title: "Accessing Linux machine/interface through a Windows machine"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by JustGus on 2008-07-03
Is there a good freeware app that I can load up on my Windows laptop, that allows me to access my Ubuntu desktop and change configurations?  Essentially something that allows me to use the screen of my Windows laptop as though its running my Linux machine (rather than simply being able to see my Linux machine and access the files, but using the Windows interface)?

I currently have monitor connected to the Linux machine but will lose it soon and it will be connected in to the network in a cabinet, so being able to use the laptop's screen and keyboard to act as though it's connected to the Linux machine would be great.

Am running Hardy Heron on one machine and Vista SP1 on the other.

Any suggestions gratefully received!

G

---

### Post by skylinedna on 2008-07-03
Not too sure if this will be any help but i used samba to connect my gutsy to xp. i assume you can do the same??

---

### Post by goexplode on 2008-07-03
This sounds like a perfect situation to make use of VNC. You can set up your Ubuntu machine as a VNC server, see [here]("http://maketecheasier.com/set-up-a-vnc-server-in-ubuntu-hardy-heron/2008/05/30") for one example, then install a VNC client such as TightVNC on your Windows machine. VNC will allow you to connect to your Ubuntu machine as if you were sitting right in front of it.

I'd suggest googling VNC, there are plenty of resources out there.

[Here]("http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html") is another good resource.

---

### Post by JustGus on 2008-07-04
Perfect!  Will have a look and thanks for the advice.

Gus

---

### Post by JudgeFudge on 2008-07-04
VNC is a good solution - it is basically the same as remote desktop in windows. It does involve running a VNC server on your linux machine.

An alternative is to run cygwin on windows which is essentially a cut-down linux environment. You can run an X-server on your PC and then create a session on your remote linux box. No changes re required on linux for this to work.

A similar solution to cygwin is using putty (SSH) and mingw (for the X server).

---

### Post by wdaniels on 2008-07-04
VNC will probably be the easiest for you to setup and start using, so if it works well enough for you then just stick with that. However, if you find VNC frustratingly slow (as I do) you could take a look at the NX protocol instead. There is a free NX server available from [NoMachine]("http://www.nomachine.com/products.php") which is limited to 2 concurrent connections, but there is also a the [FreeNX Project]("http://freenx.berlios.de/") which is building an open source implementation of the NX server. I believe all the client-side stuff from NoMachine is already GPL'd.

---

