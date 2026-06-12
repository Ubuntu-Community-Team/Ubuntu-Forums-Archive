---
title: "Simple File Server"
date: 2013-04-21
forum: New to Ubuntu
---

### Post by NMarvosh on 2013-04-21
Hey there was given a couple of old pentium 4 computers of witch 1 has Ubuntu 12.04 LTS installed on it, works great, thought that it would be "fun" to make it a simple file server. No luck! I have tried to fallow several (6) examples of how to install samba4 with no luck at all!:confused::confused::confused: I am new to this so I'm sure where they are giving examples of things I should know I am taking it as what I should enter..

Is there something simple I could use instead,  I enjoy learning new stuff but don't want to spend the whole weekend doing it!

Is there a video out there in English I seen to do the best fallowing those.

Thanks

---

### Post by bab1 on 2013-04-21
You don't actually state it but, I assume this is really a Desktop version of Ubuntu and you are just starting out.  I assume you only intend  to use this on a simple LAN environment.  It would be much more simple to start by installing Samba 3 (3.6 now).  It is far less complex than Samba4.  There is plenty information on Samba 3 installation.  For a basic setup you can try [**_[COLOR="#FF8C00"]here[/COLOR]_**]("http://www.jonathanmoeller.com/screed/?p=3608").

---

### Post by siddharth007 on 2013-04-22
Try this [link]("http://rbgeek.wordpress.com/2012/04/25/how-to-install-samba-server-on-ubuntu-12-04/")

---

### Post by 3rdalbum on 2013-04-22
Install the system-config-samba package. It gives you the very simple Samba control panel, and with it anyone can set up a Samba server.

---

### Post by Lars Noodén on 2013-04-22
If you want the simplest possible to set up, then [SSHFS](https://help.ubuntu.com/community/SSHFS) is probably your best option.  You only need openssh-server running on your server.  On the desktop, you need the package sshfs.  With it, you can mount the remote server as a local directory and do the same things to it that you can the local file system.  It uses SFTP on the back end.  You won't see that, but that makes it quite secure and will even work securely over the Internet, not just the LAN.

You can still run Samba4 along side it.

---

