---
title: "maintenance of computer remotely"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by marquee moon on 2008-05-21
I'm setting up my parents with ubuntu & would like to maintain their computer remotely. Which packages do I need to do this & how do I go about it?

---

### Post by shifty_powers on 2008-05-21
[http://ubuntuforums.org/showthread.php?t=122402&highlight=vpn](http://ubuntuforums.org/showthread.php?t=122402&highlight=vpn)

;)

---

### Post by bodhi.zazen on 2008-05-21
The only thing you need is ssh :

[uwiki]SSHHowto[/uwiki]

You can VNC or FreeNX in if you wish.

[uwiki]VNCOverSSH[/uwiki]

The only other issue is with routing ? Is the remote computer diretctly connected to the internet or via a router ? If via a router you need to forward the port(s). SSH uses port 22 and VNC 5900 , although both can be changed.

---

### Post by neurostu on 2008-05-21
I would echo the SSH comment. 

You need to install openssh-server. This will allow you to connect to their computer via their ip address.  I would also recommend disabling password based authentication over ssh and use rsa_id keys. 

Most of what you will need to do can be done from the shell, but if you need some sort of GUI you can add the -X or -Y command line argument to your ssh connection and X will automatically forward any windows you open to your remote station.

---

