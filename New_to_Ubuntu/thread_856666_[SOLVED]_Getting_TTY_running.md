---
title: "[SOLVED] Getting TTY running?"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by VorlonShadow on 2008-07-11
I use Windows primarily, but have a couple of Linux Servers.  I would like to access my new Ubuntu 8.04 server via my "putty" utility.  However, when I try to go to that server, I'm told "Network error: Connection refused".

I'm assuming that the TTY service is not running on the Linux box, but I have no idea how to ensure that it's either installed or running, or accepting connections. Could someone point me in the right direction?

Thanks,
Jesse

---

### Post by finer recliner on 2008-07-11
make sure you have ssh installed and running on your ubuntu server: 

```
 sudo /etc/init.d/ssh start 
```

and if its behind a router, make sure you have port forwarding set up for port 22 correctly

---

### Post by neurostu on 2008-07-11
Make sure you even have the ssh-server installed.  when you have access to the server run:
```

sudo apt-get install openssh-server

```
Besides intalling the openssh-Server this will also open port 22 on the server and start the ssh deamon.

---

### Post by VorlonShadow on 2008-07-11
Cool.  That was it.  Being new, I didn't equate ssh to tty.  ssh actually wan't installed, so I did an apt-get install and got it, then started it, and it seems to be working fine now.

Thanks for the help!

Jesse

---

