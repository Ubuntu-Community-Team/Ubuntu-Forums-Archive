---
title: "different server software set up"
date: 2008-11-30
forum: New to Ubuntu
---

### Post by 007casper on 2008-11-30
what is the difference between these?  I can figure that mail server is for mx mail server but is there any information regarding these different server set ups

DNS server
LAMP server
Mail server
OpenSSH server
PostgreSQL server
Print server
Samba file server
Tomcat Java server
Virtual Machine host

I followed the instructions here...
[http://howtoforge.com/perfect-server-ubuntu-8.10-p2](http://howtoforge.com/perfect-server-ubuntu-8.10-p2)

I am not sure if I did something wrong. It seems like OpenSSH server doesnt have graphic interface. I know OpenSSH is supposed to extremely secure but how does that compare to DNS and LAMP server

thank you

---

### Post by halitech on 2008-11-30
> **007casper said:**
> what is the difference between these?  I can figure that mail server is for mx mail server but is there any information regarding these different server set ups
actually a mail server is for incoming and outgoing mail, mx actually refers to the record with a DNS server so it knows where to send email

> DNS server
Dynamic Name Service (or Server) - translates domain names into IPs so the internet works
> LAMP serverLinux Apache MySQL Php - the 4 basics of a webserver
> Mail serverfor sending and delivering mail
> OpenSSH servera protocal for connecting to a remote machine using the command line
> PostgreSQL servera database server
> Print servera machine that looks after all print jobs
> Samba file serverused to share (serve) files over a Local Area Network
> Tomcat Java servera type of webserver, not too sure on exactly the difference between it and Apache
> Virtual Machine hosta way of running different Operating Systems on a single machine

> I followed the instructions here...
[http://howtoforge.com/perfect-server-ubuntu-8.10-p2](http://howtoforge.com/perfect-server-ubuntu-8.10-p2)

I am not sure if I did something wrong. It seems like OpenSSH server doesnt have graphic interface. I know OpenSSH is supposed to extremely secure but how does that compare to DNS and LAMP server

thank you

SSH is command line only, if you want a GUI then you need something like VNC or RDP.

HTH

---

### Post by 007casper on 2008-11-30
thank you so much halitech!

I am a designer, and extremely visual.  Usually I check everything I do on the terminal on the gui desktop.  I know it is silly.  But thats what I am used.

I would like to use the server to host myself and a few friends.  I know I need to use VNC eventually.  How can I get a desktop graphic interface environment?

so all the rest of these set ups are graphical except OpenSSH... 
so LAMP is a more common choice for graphical interface hosting server than DNS server?

before I did a sample test on a slow computer with DNS server set up and it worked like charm... but it seems like people choose LAMP.

trying to decide on the right choice that handles gui

thank you

---

### Post by jamesstansell on 2008-12-01
The Apache Tomcat server allows you to run jsp pages, java servlets, etc.  It can serve webpages directly, or can serve as a backend processor for an Apache Httpd web server.

---

### Post by halitech on 2008-12-01
> **007casper said:**
> thank you so much halitech!

I would like to use the server to host myself and a few friends.  I know I need to use VNC eventually.  How can I get a desktop graphic interface environment?

```
sudo apt-get install ubuntu-desktop
```replace ubuntu with kubuntu/xubuntu depending on which desktop you want. this will also install all the extras that go along with it so you may want to research a little more on just which apps you want/need and just install them.

> so all the rest of these set ups are graphical except OpenSSH... 
so LAMP is a more common choice for graphical interface hosting server than DNS server?

before I did a sample test on a slow computer with DNS server set up and it worked like charm... but it seems like people choose LAMP.

trying to decide on the right choice that handles gui

thank you

actually, other then the Virtual Machine host and VNC, they are all administered by editing config files. Some may have a GUI that you can install to administer the settings but not all (webmin comes to mind)

Not sure how you installed a DNS server to have it serve web pages but if you say so. LAMP is the most common although some servers replace Linux with BSD as it is just as secure (just not as desktop ready yet)

Each type of server is different (other then Apache and Tomcat) so if you want to serve webpages, you pick a web server, if you want to share files with windows computers on a LAN you would use SAMBA, etc.

---

### Post by 007casper on 2008-12-03
oh man! Thank you so much! :D

I love it... you dont know how much having the desktop speed up my process. 

I guess I have a bad habit of using terminal with desktop 

Thank you. Thank you.

Gotta try samba ;)

---

### Post by hyper_ch on 2008-12-03
I think you are quite confused about servers and stuff.

what do you want to achieve?

---

### Post by 007casper on 2008-12-04
hyper_ch as stated above
>>I am a designer, and extremely visual. Usually I check everything I do on >>the terminal on the gui desktop. I know it is silly. But thats what I am >>used.
>>
>>I would like to use the server to host myself and a few friends.

I am doing great. So far so good.... unless, you have suggestions.

yeah, I am too green on the server set up... I am pretty sure you can smell it a mile a way.  Thats okay.  Having a blast over here.

---

### Post by hyper_ch on 2008-12-04
so you want to operate a web-server?

---

### Post by 007casper on 2008-12-05
yes, I want to operate a web server

---

### Post by hyper_ch on 2008-12-05
and you want to host multiple domains or just one?

---

### Post by 007casper on 2008-12-06
multiple

---

### Post by rev0lv3r on 2008-12-06
Multiple will require the use of vhosts (virtual hosts)

I would just do the following (either find the packages in synaptic, or just do this line in terminal"

sudo apt-get install apache2 mysql5 php5

That will get apache2 (a web server), mysql5 (a sql database server) and php5 (i guess the language you use for everything... it's pretty neat)

I would also ... perhaps... suggest installing "phpmyadmin" and "webmin"

phpmyadmin allows you to administrate the mysql db using a web browser
and webmin allows you to administrate the machine through a web browser.

Good luck, you're going to have a lot of headaches, but you're also going to have a lot of fun :)

---

### Post by hyper_ch on 2008-12-06
In that case I'd recommend you a perfect setup iwth ISPConfig install... have a look here: [http://www.howtoforge.com](http://www.howtoforge.com)

---

### Post by 007casper on 2008-12-06
hyper_ch I am already following that set up for perfect server from howtoforge

which is good for cluster servers webmin, virtualmin, ispconfig?

---

### Post by hyper_ch on 2008-12-06
no clue about cluster servers...

---

### Post by theozzlives on 2008-12-06
```
sudo apt-get install apache2
```
```
sudo apt-get install mysql
```
```
sudo apt-get install php5
```

---

### Post by 007casper on 2008-12-28
>>which is good for cluster servers webmin, virtualmin, ispconfig?

does anyone know which is the best suitable application for cluster servers?

thank you ~ have a wonderful new year!

---

### Post by hyper_ch on 2008-12-28
ispconfig 3 will support cluster servers... I think it's beta this far.

---

