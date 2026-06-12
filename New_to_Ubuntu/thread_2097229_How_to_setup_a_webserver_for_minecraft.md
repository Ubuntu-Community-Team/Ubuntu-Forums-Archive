---
title: "How to setup a webserver for minecraft"
date: 2012-12-22
forum: New to Ubuntu
---

### Post by rguz10 on 2012-12-22
Ok guys. I have an issue when trying to SSH into localhost.
ryan@ubuntu:~$ ssh localhost
ryan@localhost's password: 
Welcome to Ubuntu 12.10 (GNU/Linux 3.5.0-17-generic x86_64)

 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)

230 packages can be updated.
58 updates are security updates.

Last login: Sat Dec 22 11:19:05 2012 from localhost
ryan@ubuntu:~$ 

So what is going wrong.

---

### Post by Cheesemill on 2012-12-22
> **rguz10 said:**
> Ok guys. I have an issue when trying to SSH into localhost.
ryan@ubuntu:~$ ssh localhost
ryan@localhost's password: 
Welcome to Ubuntu 12.10 (GNU/Linux 3.5.0-17-generic x86_64)

 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)

230 packages can be updated.
58 updates are security updates.

Last login: Sat Dec 22 11:19:05 2012 from localhost
ryan@ubuntu:~$ 

So what is going wrong.
Nothings wrong, that's what is meant to happen.

What were you expecting?

---

### Post by rguz10 on 2012-12-22
I was thinking something like this would come up.
ryan@localhost:
So I could then install spacebukkit.

---

### Post by rguz10 on 2012-12-22
This is what i'm trying to install. I think it might help.
[http://home.xereo.net/documentation/cat1/installing-the-panel](http://home.xereo.net/documentation/cat1/installing-the-panel)

---

### Post by sandyd on 2012-12-22
**moved to new thread**

---

### Post by rguz10 on 2012-12-22
No I have minecraft setup. I just dont know how to install something to the webserver

---

### Post by ubudog on 2012-12-22
To run commands on localhost you don't need to ssh to it, just open a terminal.

To install and run SpaceBukkit you need to have the [required]("http://173.237.196.252/documentation/cat1/requirements") software installed.

Here's how to do that:

```
sudo apt-get install apache2 php5 mysql-server
```

Press 'Y' when it asks if you want to continue installing.

Now we have to enable the things SpaceBukkit needs (mod_rewrite):

```
sudo a2enmod rewrite
```

For security, I'd recommend disabling some other things in Apache:
```
sudo a2dismod status
```
```
sudo a2dismod autoindex
```

Then follow the instructions [here]("http://home.xereo.net/documentation/cat1/installing-the-panel") (for Linux) and you should be set.

Hope this helps,
ubudog

---

### Post by sandyd on 2012-12-22
**fixed title - my bad**

---

