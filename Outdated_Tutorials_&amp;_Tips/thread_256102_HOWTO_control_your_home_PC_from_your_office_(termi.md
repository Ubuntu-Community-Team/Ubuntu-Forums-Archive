---
title: "HOWTO control your home PC from your office (terminal, putty, ddclient &amp; sshd)"
date: 2006-09-12
forum: Outdated Tutorials &amp; Tips
---

### Post by Nano on 2006-09-12
This guide is mainly thought for people who have a computer home and want to controll it from their office, passing through the company firewall restrictions using ssh.

Usually certain ports are always open, such 80, 443 and 21, so we will use one of this to connect home.
First of all, make sure you have the ssh server installed on your computer at home:

```

sudo apt-get install ssh

```

and once it's installed we'll make it listen the right port
```

sudo vi /etc/ssh/sshd_config

```
look for the line 
```

Port 22

```
and change it to
```

Port 443

```

*The port 443 is generally used by https, which is, in basic words, the encrypted web browser flow. 

Let's restart it sshd:
```

sudo /etc/init.d/ssh restart

```

and check if it works properly:

```

ssh your_user_name@127.0.0.1 -p 443

```

Good!

Now, next problem comes up since most ISP give you dynamic IPs and you don't know what's your home's ip.
To solve this we'll use ddclient.

First go to [www.dyndns.com](www.dyndns.com), create an account and read their HOWTO to create a host name: [https://www.dyndns.com/services/dns/dyndns/howto.html](https://www.dyndns.com/services/dns/dyndns/howto.html)
Once it's done we'll work on ddclient, the dyndns client software.

```

sudo apt-get install ddclient

```

then let's edit the configuration file
```

sudo vi /etc/ddclient.conf

```

and make it look like this:

```

pid=/var/run/ddclient.pid
protocol=dyndns2
use=web
server=members.dyndns.org
login=your_username
password='your_password'
your_hostname.your_domain.com

```

Once it's edited let's restart it:
```

sudo /etc/init.d/ddclient restart

```

and check if it works with:
```

dig your_hostname.your_domain.com

```

Now check if the ip matches yours.

Now, install firestarter and allow TCP connections to port 443. I won't describe this point because most users know about it.
Don't forget to forward the 443 traffic from your router to the computer you want to control. If you're connected using a USB modem you don't need do to it.


Now, when you're at office simply download Putty, which is a windows ssh client or use the terminal in MacOSx or Linux to connect home.
To connect just type:
```

ssh your_username@your_hostname.your_domain.com -p 443

```
or from Putty fill the connection form and you'll be in.

I mainly use this to control mldonkey from my office.

If some point isn't clear enough I'll be glad to explain it in details.

---

### Post by mherring0209 on 2006-09-30
how do i set it up to control my home computer from the internet?  the directions are quite unclear for a newbie like myself.  I am not sure of most of the settings

---

### Post by Bosonator on 2007-05-30
¡muy bueno! Agradece, nano.

---

### Post by kinemagician on 2007-11-20
I am using nx  ([www.nomachine.com](www.nomachine.com)) to connect from the office PC my home PC.  However, you must
a) configure your router;
b) subscribe for your domain name such as yourname.dyndns.org at [www.dyndns.org](www.dyndns.org)

---

### Post by SuperMike on 2007-11-20
Thank you SOOOOO much for figuring this out Nano. I badly needed this.

---

### Post by mellowd on 2007-11-20
Putty is a great little app. My setup is similar but I go through a firewall before I get access to my box

---

### Post by maww on 2007-11-20
Thank you nano!

---

### Post by myharshdesigner on 2007-11-21
thanks Dear :)

---

### Post by lowebb on 2008-01-15
This doesn't work for users whose company sits behind a proxy server

---

