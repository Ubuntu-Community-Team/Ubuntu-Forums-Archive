---
title: "Problem with Samba &quot;I think&quot;"
date: 2018-11-28
forum: New to Ubuntu
---

### Post by phobos84 on 2018-11-28
Hello all, 
I want to apologize before hand for being new to terminal and for the fact that I have no idea what I'm doing.  Anyway with that being said,  I have 3 computers with some form of Linux.  Laptop1 with Mint, Laptop2 is dual boot win 8.1 and Lubuntu, and I have an old Pentium 4 tower with Linux Lite.  I use the old P4 tower as a media server.  I set all this up by having absolutely no idea of what I was doing.  I just followed tutorials and cut and paste samba config files until it "kind of" worked.  After at least 20 or so attempts I finally got a large hard drive on the tower to be seen by the other PC's and Roku's in the house "with Kodi".  Anyway everything was fine until I got laptop2 and tried dual boot.  Windows on laptop2 can see the old P4 tower no problem.  But when I flip over to Lubuntu It can't see anything.  I tried copying the samba config text from the other laptop and pasting it into the other but this didn't work. 

Can anyone point me in the right direction?

---

### Post by mitesh.agrwl on 2018-11-29
> **phobos84 said:**
> Hello all, 
I want to apologize before hand for being new to terminal and for the fact that I have no idea what I'm doing.  Anyway with that being said,  I have 3 computers with some form of Linux.  Laptop1 with Mint, Laptop2 is dual boot win 8.1 and Lubuntu, and I have an old Pentium 4 tower with Linux Lite.  I use the old P4 tower as a media server.  I set all this up by having absolutely no idea of what I was doing.  I just followed tutorials and cut and paste samba config files until it "kind of" worked.  After at least 20 or so attempts I finally got a large hard drive on the tower to be seen by the other PC's and Roku's in the house "with Kodi".  Anyway everything was fine until I got laptop2 and tried dual boot.  Windows on laptop2 can see the old P4 tower no problem.  But when I flip over to Lubuntu It can't see anything.  I tried copying the samba config text from the other laptop and pasting it into the other but this didn't work. 

Can anyone point me in the right direction?

If you are using the file server for media sharing, it is better to set up a FTP server which is relatively easy to install, maintain and access from any OS! Using Kodi with FTP is easy, check this [guide]("https://kodi.wiki/view/FTP").

---

### Post by TheFu on 2018-11-29
Linux to Linux file sharing should use NFS, not CIFS.  NFS supports native file and directory permissions, as needed by Unix systems.

The "server" needs to have a static IP. It is best if all the clients also have static IPs.

Before starting everything, make certain that every client can 'ping' the server using the name and that the server can 'ping' the clients using their names.

Since you have a mixed environment, I cannot say how to setup these things.

For Windows, you'll probably still want CIFS/Samba, but CIFS is a little slower than NFS.  Kodi has built-in support to access NFS storage.
Some guides:
* [https://help.ubuntu.com/lts/serverguide/network-configuration.html.en](https://help.ubuntu.com/lts/serverguide/network-configuration.html.en)  - Static IP
or
* [http://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management](http://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management) managing a network using DHCP reservations

* [https://help.ubuntu.com/stable/serverguide/network-file-system.html](https://help.ubuntu.com/stable/serverguide/network-file-system.html) - NFS Server
* [https://wiki.ubuntu.com/systemd#Remote_filesystem_mounts](https://wiki.ubuntu.com/systemd#Remote_filesystem_mounts) - NFS clients

BTW, "terminal" is a type of program. There isn't one "terminal", there are 20 different programs which provide a terminal.  I suspect you mean to say "shell interface" or "CLI".  The "shell" is one of many programs you run, usually bash, but there are 20 other possible choices.  "CLI" means *Command Line Interface* and covers local terminals, remote terminals, remote shells, and local consoles.  The real power from Unix systems comes from automation and that means **not** using a GUI, hence why the real power in Unix systems is by shell scripting and automation.

[http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) is a free PDF you can grab (or buy in any bookstore) to learn the Linux CLI.  If you start from the beginning and work through a chapter a week, you'll get the background in an organized way to bring your knowledge up in the shortest possible manner.  Googling for answers when you are really new is dangerous. Some background is needed as a foundation.

If you are really new, there are a few other well-written blog articles which will prevent lots of misunderstandings common from Windows-centric people. Just ask.

---

