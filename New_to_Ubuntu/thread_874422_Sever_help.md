---
title: "Sever help"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by moose4204l on 2008-07-29
I just installed the Sever edition and installed everything. I am confused though, since I am a NEWB, how do I use it as a server now. Where can I get help on finding out how to use it to save stuff on and ssh into my laptop and all that jazz. I am completely lost!!!!!!!!!!!!!!!

NEED INFO BIG TIME!!!!!!

---

### Post by kool_kat_os on 2008-07-29
[https://help.ubuntu.com/community/Servers](https://help.ubuntu.com/community/Servers)

it may help

here's a better one:
[https://help.ubuntu.com/8.04/serverguide/C/index.html](https://help.ubuntu.com/8.04/serverguide/C/index.html)

---

### Post by hyper_ch on 2008-07-30
what do you want to do?

---

### Post by moose4204l on 2008-07-30
for starters i just installed the server cd. do i need to download apache? if so what should i download with it?

---

### Post by eightmillion on 2008-07-30
The server install cd gives you an option to set up apache mysql and php along with the install.

---

### Post by moose4204l on 2008-07-30
i didnt see the apache thing, it was lamp, samba, openssh, dns server, and some other things

---

### Post by hyper_ch on 2008-07-30
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by eightmillion on 2008-07-30
> **moose4204l said:**
> i didnt see the apache thing, it was lamp, samba, openssh, dns server, and some other things

Lamp stands for **L**inux **A**pache **M**ySQL and **P**HP

---

### Post by Iowan on 2008-07-30
There are some great server setups on [howtoforge.com]("http://www.howtoforge.com/howtos/linux/ubuntu"), but the LAMP option does a good portion of the work for you.  I've also set up a LAMP server to play with - local library has some books on Apache, PHP and MySQL (although not necessarily on Ubuntu). You might also set up your server as DHCP server.  The server is usually more a candidate to SSH *into* (from your laptop) than *from*.

---

### Post by moose4204l on 2008-07-31
how do i start using the lamp server. I typed apache2 and it gave me bad user name ${APACHE_RUN_USER}

i typed in /etc/inti.d/apache2 start 
and it gave me 

apache2: could not reliable determine the server's fully qualified domain name, using <IP ADDRESS> for ServerName
two permission denied for make_sock
no listening sockets available and then a fail in red

scratch that...i got it working with  a sudo. BUT HOW DO I USE IT??? what do i do?

---

### Post by cariboo on 2008-07-31
If you are on the server point Firefox to [http://localhost](http://localhost) and you should see a page that says **It Works!**. If you are on another computer http://<ip of server>

Jim

---

### Post by MasterXandrex on 2008-07-31
> **moose4204l said:**
> apache2: could not reliable determine the server's fully qualified domain name, using <IP ADDRESS> for ServerName
two permission denied for make_sock
no listening sockets available and then a fail in red

You'll need to be superuser or user superuser permissions to start apache try:

```
sudo /etc/init.d/apache2 start
```

However, this is probably done at boot if you installed the lamp. Also, the Fully qualified domain name error is because the servername isn't set in the CONF and it can't autodetec it... it's pretty safe to ignore.
 

If you want to SSH in the server then you will need to install the SSH server daemon thusly:

```
sudo apt-get install openssh-server
```

It will then start at boot.

To begin populating apache, place files in /var/www -- you will need root permissions -- to get these try:

```
sudo -s
```

This will temporarily make you root.


Xan

---

### Post by hrod beraht on 2008-07-31
> **moose4204l said:**
> how do i start using the lamp server. I typed apache2 and it gave me bad user name ${APACHE_RUN_USER}

Apache starts automatically in daemon mode (i.e. sitting in memory waiting for something to happen mode) when you boot the server, so it's already running.

Have you  got another machine one your local LAN with a web browser? Go to it and type the local LAN address of your server (probably something like [http://192.168.1.102](http://192.168.1.102)) and you should see the default Apache **It works!** page.

Note: you will have to forward the http port on your router to the server in order for it to be seen from outside your local LAN.

Bob

P.S. Did you set up a static ip address for your server?

---

### Post by Potatoj316 on 2008-07-31
if your behind a router and you want to access anything from outside your LAN you will need to set up port forwarding on your router.  Forward ports 20-22, and 80.  this will let http, ssh, and ftp traffic through.  

If you installed everything the CD let you install you already have apache, PHP, MySQL, SSH, and a few more things.  to ssh into your server type 
```
ssh USER@IPOFSERVER
```

---

### Post by moose4204l on 2008-07-31
> **hrod beraht said:**
> Note: you will have to forward the http port on your router to the server in order for it to be seen from outside your local LAN.

Bob

P.S. Did you set up a static ip address for your server?

how do i set up the port forwarding and i dont believe i did the static ip address how do i know and how should i if i didnt.

---

### Post by Potatoj316 on 2008-07-31
to set up static IP you have to look for "internal lan" or something like that in your router config.  then you tell it the MAC address and the IP you want that MAC address to have.  

to set up port forwarding look for "port forwarding" and then specify the port that you want people to be able to access your computer on and then specify the internal IP of the computer to send it to.  (the one you set up with static IP)

---

### Post by moose4204l on 2008-07-31
> **Potatoj316 said:**
> 

to set up port forwarding look for "port forwarding" and then specify the port that you want people to be able to access your computer on and then specify the internal IP of the computer to send it to.  (the one you set up with static IP)

need more specifics man, not to good hear with that stuff

---

### Post by cariboo on 2008-07-31
This should get you started:

[http://tldp.org/HOWTO/NET3-4-HOWTO.html](http://tldp.org/HOWTO/NET3-4-HOWTO.html)

Jim

---

### Post by moose4204l on 2008-08-03
ok, i will check that out now. 

next thing is, what do i do and how do i get the php and mysql thing going. basically, i just installed the lamp server, now what?

---

