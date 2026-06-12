---
title: "using the ftp"
date: 2013-06-16
forum: New to Ubuntu
---

### Post by kom333 on 2013-06-16
Hello dear Ubuntu users!

 I've got PC (12.04 on it) and laptop (10.04 on it). My multimedia files  are on my laptop and I was wondering how to copy them on my PC. I've  heard that bast way to do it is ftp but I dont know how to use it. Is it  similar to ssh where I must enter user@hostname or its completely  different? 
Plz someone help me :D

---

### Post by MidnightGrey on 2013-06-16
You can try using samba to share folders, simply right click on the folder > Properties > Share. It will ask you to install samba if you haven't already.

---

### Post by Iowan on 2013-06-16
> **kom333 said:**
> Hello dear Ubuntu users!MUCH better than:  > **kom333 said:**
> Hello lowly GNU/Linux users! If you were worried about SSH, you really won't like FTP for it's lack of security. If you are familiar with SSH, you can use SCP (secure copy). **man scp** should provide basic instructions.

---

### Post by Lars Noodén on 2013-06-16
Just to give a little more detail to what Iowan writes about ssh, you can use the built-in SFTP support to copy files if you have the package [openssh-server](http://packages.ubuntu.com/precise/openssh-server) installed on one machine.  

Put openssh-server on one machine and if you have a firewall, open port 22 for SSH.

Then on the other machine, open your file manager, press ctrl-L, and then enter *sftp://kom333@xx.yy.zz.aa/* where *xx.yy.zz.aa* is the ip number of the machine which is running openssh-server.

FTP is insecure and difficult to set up.  Best to forget about FTP and use SFTP instead.

---

### Post by kom333 on 2013-06-17
Thank you all for your awesome advices. And lowen, i am not worried about SSH. ;)

---

