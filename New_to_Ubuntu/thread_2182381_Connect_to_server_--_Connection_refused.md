---
title: "Connect to server -- Connection refused"
date: 2013-10-21
forum: New to Ubuntu
---

### Post by r3bol on 2013-10-21
Hi, I would like to transfer some files between PCs on my lan (over encrypted wifi). My PC is ubuntu and the other PC has ElementaryOS (based on ubuntu). I tried to use ubuntu's "Connect to server" feature in the nautilus window, but I'm getting a connection refused. 
The method I was trying was FTP, with the address of the ElementaryOS - 192.168.10.109, and targeting the folder /home/asdf. The error is connection refused. 

Do I need to setup anything of the ElementaryOS PC to get the connection working?

---

### Post by perseus.cool on 2013-10-21
Are you running a FTP server on elementaryOS? 
The best way that I know to do this is to use Samba.
Have a look here. [https://help.ubuntu.com/community/Samba/SambaServerGuide](https://help.ubuntu.com/community/Samba/SambaServerGuide)
This should work fine in elementaryOS as well, and when you are done setting up the server you can use this command in ubuntu (alt+f2 - run the command below)

nautilus smb://ip-address-of-elementaryos/sharedfolder

---

### Post by r3bol on 2013-10-21
Ah, ok. I thought there might have been some automatic thing to connect them. I'll try the samba then. Thanks.

---

### Post by Johan De Cauwer on 2013-10-21
But safest is to use the ssh. something like scp to copy from one machine to the other but like with ftp it's not standard activated, you have to install it. But that's easy: In the ubuntu software center search for openssh en in the middle of the screen there is a 'metapackage' called ssh. Install it. scp is a command line, you might want to use a GUI, then: Next install gFTP from the software center. It also provides ssh support. Run it with the address of the remote computer (where you also installed ssh) and the username and the password of that user. The first time it asks you a confirmation, and there it is: just copy between computers.

---

