---
title: "[SOLVED] Very confused about web server setup??"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by rhcm123 on 2008-11-29
I have some skills in web design, and consider myself to be moderatley skilled in linux. I love ubuntu and it's debian-based counterparts (mostly for their use of APT), and have been generally satisfied with the systems i've built.

However, there would be something that I would like to do soon: host a home server page. I would like to setup a small home web site so I can access my server on the road, along with my files and Jinzora shares.

I have read so much information on the net that I am now very confused. I have read about needing to know my ip, getting a static ip from my ISP, getting multiple IP's, needing DYNDNS, etc. I have no clue what to do?

Can anybody explain to me in a simple way how to setup an easy to remember way to access my web server (which I have setup myself, and can confirm works) from the internet?:confused: :(

---

### Post by rev0lv3r on 2008-11-29
Apache2 is the web server most people use

"sudo apt-get install apache2"

As for your IPs, you should just get some kinda dynanic dns server
Check dyndns, zoneedit, or many many others

---

### Post by rhcm123 on 2008-11-29
> **rev0lv3r said:**
> Apache2 is the web server most people use

"sudo apt-get install apache2"

As for your IPs, you should just get some kinda dynanic dns server
Check dyndns, zoneedit, or many many others

i have apache (my web server is also hosting my jinzora collection, which nessicated a LAMP)
I have a dyndns, but I have no clue how to use it

---

### Post by Yuki_Nagato on 2008-11-29
Start small.  Do you have a dynamic IP?  Does it change from day to day?  You will need to set up a DYNDNS account to tell the world where your server is today.  That will require "ddclient."

You will need to install the apache server within your computer.

Then you need to forward the HTTP (80) port on your router to allow the world access to the files.

That is about it.  Those three steps for a basic server.

"ddclient" is in the repositories.  

Install it and then the wizard should run automatically.  If not, here is a working config file:

```

pid=/var/run/ddclient.pid
protocol=dyndns2
#use=if, if=eth0
use=web
server=members.dyndns.org
login=FroSho &
password='Junkser' &
tehwired.ohnoes.com &

```

The '&'s are what you need to personalize.

---

### Post by rhcm123 on 2008-11-29
> **Yuki_Nagato said:**
> Start small.  Do you have a dynamic IP?  Does it change from day to day?  You will need to set up a DYNDNS account to tell the world where your server is today.  That will require "ddclient."

You will need to install the apache server within your computer.

Then you need to forward the HTTP (80) port on your router to allow the world access to the files.

That is about it.  Those three steps for a basic server.

"ddclient" is in the repositories.  

Install it and then the wizard should run automatically.  If not, here is a working config file:

```

pid=/var/run/ddclient.pid
protocol=dyndns2
#use=if, if=eth0
use=web
server=members.dyndns.org
login=FroSho &
password='Junkser' &
tehwired.ohnoes.com &

```

The '&'s are what you need to personalize.

Ok, answers to your questions:
-Dynamic IP
     Yes, it changes... lets say weekly. (It varies)
-DYNDNS account
     I've got one, but I don't know how to use it :(
-ddclient
     What does that do?
-apache
     Apache is installed and I just updated all my packages.
-forwarding http
     Let me check somthing... i setup forwarding, but everytime i go to my dyndns address it sends me to my modem's control panel.

---

### Post by rhcm123 on 2008-11-29
Nevermind!!!! I just setup ddclient onto mah server and it works! I can get to my server from the interwho!!! Thank you so much... now... to build my website!!!

---

