---
title: "Ubuntu Server 16.04 Wireless Issues"
date: 2016-12-16
forum: New to Ubuntu
---

### Post by jballen001 on 2016-12-16
Hello!

I downloaded Ubuntu server 16.04 about two days ago. When I did, I followed all of the installation requirements, although the DHCP connection did not work. 
Now when I start Ubuntu Server, only the terminal comes up. I know how to download a desktop GUI, but do not have wireless privileges.
Because I do not have wireless connection, I cannot download the desktop GUI.
I have found that this is not the only problem, however. I tried to install the wireless package through a USB drive, however I am greeted with a series of error messages.
I tried to turn auto-mount on so that my USB would be able to transfer the wireless package, however while attempting to activate auto-mount, I am greeted with yet another error message about missing packages.
I think you see what my problem is. None of the required packages seem to have installed upon installation of the server.
Is there a solution? I have already tried to reinstall the server and it did not resolve the issue.
Much appreciated if you know how to fix this. I can get any extra information you may need.
-JBAllen

---

### Post by TheFu on 2016-12-17
Welcome to the forums.

The best answer for any server is to use a wired ethernet connection. That is the truth.  Servers don't have GUIs and they don't need wifi because they are plugged into an ethernet port.

Another option is to run a desktop distro and _*use it like a server*_.  Desktops will usually come with wifi drivers.

---

