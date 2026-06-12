---
title: "Mac OSX X11 Port Forwarding via SSH"
date: 2014-04-01
forum: New to Ubuntu
---

### Post by thault on 2014-04-01
I'm connecting to my home server via ssh from school on a Mac Book(10.9). I have X11 port forwarding turned on on the server. When I connect and run command firefox i get an display not specified error. What do i need to do? 

```
thault$ ssh -X -p xxxx thault@xxx.xxxx.x.xxx
thault@xxx.xxx.x.xxx's password: 
Welcome to Ubuntu 12.04.4 LTS (GNU/Linux 3.8.0-38-generic x86_64)

 * Documentation:  https://help.ubuntu.com/

  System information as of Tue Apr  1 18:46:07 EDT 2014

  System load:  0.0                Processes:             109
  Usage of /:   22.6% of 10.31GB   Users logged in:       0
  Memory usage: 4%                 IP address for eth0:   192.168.0.131
  Swap usage:   0%                 IP address for virbr0: 192.168.122.1

  Graph this data and manage this system at:
    https://landscape.canonical.com/

thault@ThaultServ:~$ firefox
Error: no display specified
```

---

### Post by 1clue on 2014-04-01
Do you have XQuartz on your mac?

---

### Post by 1clue on 2014-04-01
Addendum:
You'll need an X server on your mac, which generally means XQuartz.

If you don't have some blazing fast network speeds all along the route, you're going to be horribly disappointed with the speed.

---

### Post by thault on 2014-04-02
So an X server is required then? None of the things I was reading was saying Macs an X server was needed.

---

### Post by 1clue on 2014-04-02
I've been using a mac to connect to linux for years now.  You need an X server on the terminal you're sitting at.  it's not automatically installed but it's free.

[https://xquartz.macosforge.org/landing/](https://xquartz.macosforge.org/landing/)

---

