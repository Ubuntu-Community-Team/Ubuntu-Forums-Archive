---
title: "[SOLVED] Connect to other computers via command line?"
date: 2008-11-30
forum: New to Ubuntu
---

### Post by baruch60610 on 2008-11-30
I've got some computers (all Ubuntu) on a LAN.  I installed Ubuntu Server edition on one of them, which is going to be used as a server.  The server has no GUI, just the command line.

I am stymied as to how to connect to other computers using the command line (or how to connect to the server, using the command line).

I assume I have to use the server name somehow (Server1 - not very original), but I can't seem to find what the exact syntax is or should be.  All the sources I find seem to assume you're using a GUI-based program, but I'm not.

Where can I find info on how to connect the old-fashioned way?  I am perplexed...

---

### Post by b0b138 on 2008-11-30
check this out [https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

---

### Post by blackened on 2008-11-30
On the server use
```
sudo apt-get install openssh-server
```

Then connect to it using
```
ssh **insert.server's.lan.ip.address.here**
```

---

### Post by baruch60610 on 2008-11-30
Thanks to both of you for your quick replies.  I already have SSH installed and running, with sshd on the server.  It's working correctly, as far as I can tell.  When I enter 'ssh localhost' I am asked for my password and logged into localhost.  I'm assuming that means both the client and server parts of ssh are working correctly.

I think perhaps my problem is that I don't know what my computer's network name is.  I named it "Server1" when I was installing Ubuntu.  I was under the impression that this would be enough.

This may sound like a dumb question, but how do I determine what the computer's IP number is?  If all I need is that IP number, I may be able to figure out the rest.  But... I haven't found a way to get that number.  Anything that I do tells me the number is 127.0.0.1, but that isn't very helpful.

---

### Post by blackened on 2008-11-30
On the server
```
ifconfig
```
will display your network card's configuration info including IP address (look at the inet addr: xxx.xxx.xxx.xxx entry returned by ifconfig).

You should seriously consider making the server's ip static so that you don't have to run this command physically from the server every time you want to connect remotely.

---

### Post by baruch60610 on 2008-11-30
Thanks, Blackened.  I got a new error message, which I consider a hopeful sign.  It says "network not reachable", which doesn't make much sense since I can access other computers on the lan.  I'll go track down what this means.  I appreciate your help.  Thanks.

---

### Post by Xiong Chiamiov on 2008-11-30
The IP address you're looking for is one that starts with 192.168.  Any other one will be your WLAN address, which you won't be able to use to access it unless you've got 'net access on the client machine and you've set up port forwarding for port 22 on your router to the server.

---

### Post by baruch60610 on 2008-11-30
Hi, Xiong Chiamiov:

Thanks for your help.  I actually had it almost right, but my eye picked up the *broadcast* IP address (ending in .255).  Using the correct IP address, I was easily able to connect to the server via ssh.

Thanks again everyone for your help.

---

### Post by blackened on 2008-11-30
> **baruch60610 said:**
> Hi, Xiong Chiamiov:

Thanks for your help.  I actually had it almost right, but my eye picked up the *broadcast* IP address (ending in .255).  Using the correct IP address, I was easily able to connect to the server via ssh.

Thanks again everyone for your help.

Hehe, that's why I said to make sure you had the inet addr: xxx.xxx.xxx.xxx :)

Glad you got it sorted out.

---

