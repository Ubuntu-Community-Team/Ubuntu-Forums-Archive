---
title: "Ubuntu - ncview display error"
date: 2020-08-21
forum: New to Ubuntu
---

### Post by kdl0013 on 2020-08-21
I was working with ncview last week in Ubuntu and I had to enter export DISPLAY=:0 before it would load the .nc files.   But as of 2 days ago, I now receive this error message :" Error: Can't open display: :0".  I have read through a bunch of forums, but nothing is specific to this issue about the display suddenly not working.

Has anyone experienced this situation?

I am running on a Windows machine and have the latest version of Ubuntu Desktop app.

---

### Post by wildmanne39 on 2020-08-21
Moved to New to Ubuntu Forum.

---

### Post by Holger_Gehrke on 2020-08-22
If I understand your situation right, you're running Ubuntu in the Windows Subsystem for Linux. WSL is meant mainly for running command line tools. If you want / need to run graphical Linux applications, you need to run an X-server on Windows to do the actual displaying. Setting and exporting the DISPLAY variable tells programs where to send their output. Do you have an X-server running and is it configures to offer a display ':0' and will it accept connections from programs running on your machine ?

Holger

---

### Post by TheFu on 2020-08-23
ncview isn't sufficient to figure out what you are trying to accomplish. Google returned 3+ different things, each in different industries. I've never used ncview - or heard of it before today. I have used xming as an X11/server on Windows alone with a few expensive commercial X11/Servers. In the end, I found it more efficient to just load a Linux desktop into a virtual machine and use that X/Server rather than fight with Windows limitations.

If you can't/won't to that, assuming this is some sort of X11 thing, [https://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications](https://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications) has multiple methods to accomplish that.  Most will require an X11 server running on the OS you sit behind, as Holger_Gehrke says.  

For Linux desktops, remote X11 through ssh tunnels is really, really easy.  So, if you can wipe that proprietary OS and install Linux, I bet we can get you working with remote X11 in just a few minutes, securely. This is best on a LAN.

If you need a full desktop or need to traverse lower bandwidth connections, then there's x2go, which also works using ssh tunnels. The NX protocol that x2go uses includes ssh tunnels. x2go has Windows, OSX, and Linux clients. I used the Windows client every day for years. It was fairly stable, but not for GPU/image/video stuff.

---

