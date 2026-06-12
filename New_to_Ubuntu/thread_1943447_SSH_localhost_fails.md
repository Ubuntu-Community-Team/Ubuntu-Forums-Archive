---
title: "SSH localhost fails"
date: 2012-03-19
forum: New to Ubuntu
---

### Post by hussainv1 on 2012-03-19
Hello folks,

I'm installing Apache Hadoop on Ubuntu 11.10  following this tutorial [http://www.michael-noll.com/tutorials/running-hadoop-on-ubuntu-linux-single-node-cluster/](http://www.michael-noll.com/tutorials/running-hadoop-on-ubuntu-linux-single-node-cluster/)

But when i run this command "*ssh localhost*" in the terminal, i get the following message **ssh: connect to host localhost port 22: Connection refused**

I tried all the possible solutions in the article, but not much success.

hduser@hussain:~$ ssh -vvv localhost
OpenSSH_5.8p1 Debian-7ubuntu1, OpenSSL 1.0.0e 6 Sep 2011
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to localhost [127.0.0.1] port 22.
debug1: connect to address 127.0.0.1 port 22: Connection refused
ssh: connect to host localhost port 22: Connection refused



Please help me as i'm stuck with this here.

Thank you,

Warm Regards,
Hussain

---

### Post by dolphin194 on 2012-03-19
In order for you to host an SSH server on your machine, you must first install *all* ssh packages. Only the client comes with Ubuntu, so you will need to install the server.

To do this, run:
```
sudo apt-get install ssh
```

---

### Post by hussainv1 on 2012-03-19
> **dolphin194 said:**
> In order for you to host an SSH server on your machine, you must first install *all* ssh packages. Only the client comes with Ubuntu, so you will need to install the server.

To do this, run:
```
sudo apt-get install ssh
```

Hi, thanx for the suggestion. I had got it fixed already by installing ssh package using the same command u had written here :)

Warm Regards,
Hussain

---

### Post by dolphin194 on 2012-03-19
Glad to hear you got it sorted out.

---

### Post by Gwaro on 2012-03-19
I get this when i try to ssh the localhost   

   'Permission denied (publickey).' 

Where did i possibly went wrong?

---

