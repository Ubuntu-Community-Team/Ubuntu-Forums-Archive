---
title: "Connecting to Server"
date: 2008-09-08
forum: New to Ubuntu
---

### Post by sushibilly on 2008-09-08
Hi, I am totally new to Linux & Ubuntu and have been tasked with setting up a basic ftp server.

I have installed the server and vsftp. I need to amend the vsftpd.conf file.

To do this, I have booted my Windows laptop from an Ubuntu CD and connected to the server. When I have edited the conf file, and tried to save it sdays I don't have permission. WHat do I need to do on the server to amend the permission. Also, can I connect to the server in a shell from the Ubuntu laptop if need be?

Many thanks in advance

---

### Post by rlzyoner on 2008-09-08
You should try to access the file as root

i.e 

sudo gedit /path/to/vsftpd.conf

---

