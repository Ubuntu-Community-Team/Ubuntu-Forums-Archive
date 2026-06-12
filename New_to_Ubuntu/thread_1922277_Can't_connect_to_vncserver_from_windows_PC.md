---
title: "Can't connect to vncserver from windows PC"
date: 2012-02-08
forum: New to Ubuntu
---

### Post by zulasmum on 2012-02-08
I am currently installing and configuring a headless ubuntu 10.04 server. I am mostly there and now have a functioning system. However I want to access the server from my windows desktop machine using tightvnc client. I have installed vnc4server on the server machine and tightvnc on the windows machine following [this]("http://www.havetheknowhow.com/Configure-the-server/Install-VNC.html") tutorial but am unable to connect. I can access the server using putty.
I'm sure that it is something simple that I have done incorrectly.
Thanks

---

### Post by ikt on 2012-02-08
> **zulasmum said:**
> I am currently installing and configuring a headless ubuntu 10.04 server. I am mostly there and now have a functioning system. However I want to access the server from my windows desktop machine using tightvnc client. I have installed vnc4server on the server machine and tightvnc on the windows machine following [this]("http://www.havetheknowhow.com/Configure-the-server/Install-VNC.html") tutorial but am unable to connect. I can access the server using putty.
I'm sure that it is something simple that I have done incorrectly.
Thanks

Why not use putty instead of tightvnc?

My mistake, just saw the link, you've intalled gnome and would now like to access that via VNC.

---

### Post by zulasmum on 2012-02-08
yes, I thought it would make life a bit easier to have a virtual desktop. I can use putty and use the command line but it is a slow learning process.

---

### Post by CharlesA on 2012-02-08
FreeNX > VNC.

Works over SSH too, so it's more secure.

---

### Post by zulasmum on 2012-02-08
Thanks, have managed to install freenx and am now connected!

---

### Post by CharlesA on 2012-02-08
Outstanding. Don't forget to mark the thread as [SOLVED] from thread tools. :)

---

