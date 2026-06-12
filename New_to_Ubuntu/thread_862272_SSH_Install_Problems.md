---
title: "SSH Install Problems"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by yeuker on 2008-07-17
Hi Everyone,

I recently rebuilt my linux machine as I do sometimes with Ubuntu 8.04.  First thing I did was install ssh:

sudo aptitude install ssh

Next, I tried logging in to my computer through ssh but I get 

ssh: connect to host [my ip] port 22: Connection refused

I have ran ssh on this computer before but don't know where to troubleshoot.  How can I tell if it is running, or installed? Can someone please help?

Also, what is the difference between ssh and openssh-server?  Many install posts say to sudo aptitude install ssh openssh-server, but I only ever have installed ssh?  Some clarification would be greatly appreciated.

Also, what is the difference between ssh and open-ssh-server?

Thanks everyone!

---

### Post by benfindlay on 2008-07-17
Try ```
sudo aptitude install openssh-server
```

Hope this helps!

---

### Post by roquefilipe on 2008-07-17
ssh is a client program that connects to a ssh server. Ubuntu comes with the client but not the server. To connect to that machine ssh server must be installed, but not to connect from that machine.

---

### Post by OffAxis on 2008-07-17
ssh is the metapackage consisting of the two openssh packages for client and server
[http://packages.ubuntu.com/hardy/ssh](http://packages.ubuntu.com/hardy/ssh)

You could be getting blocked at the router or have mis-typed your ssh logon somehow.

---

### Post by OffAxis on 2008-07-17
> How can I tell if it is running, or installed?

```
ps -e | grep sshd
```
This'll search the currently running processes for the ssh server daemon.

There's a graphical equivalent somewhere in the System Administration Panel that'll show all running processes.

---

### Post by roquefilipe on 2008-07-17
> **OffAxis said:**
> ```
ps -e | grep sshd
```
This'll search the currently running processes for the ssh server daemon.

```
pgrep ssh -l
```
this will do the same

---

### Post by Vivaldi Gloria on 2008-07-17
To test whether the ssh-sever works try sshing itself:

```
ssh localhost
```

---

