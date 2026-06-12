---
title: "Python Deamon's Inter-process communication"
date: 2009-08-02
forum: Programming Talk
---

### Post by OpenFish on 2009-08-02
Hi All

i have a virtual server like iptable setup and clients on one side and some services on the other, eg network printers, intranet 

i want remote clients with a web browser to be able to log in via https and a strong password. then i wish for these clients to be able to access some services. this should work a little like a radius server but less complicated

i plan to use php as apaches scripting engine
and a daemon running as root to change iptables

the clients that are active will be on a mysql database and the daemon will check this and if any need removing due to timing out or left. but i would like the php to tell the daemon that it needs to check the mysql so that it doesn't need to have to wast loads of resources checkin the mysql
every 2 seconds and update are almost instant

i have a lot of practice with python thus i would like to write the daemon and a program that php can run to update the daemon in python

i would then like to rewrite in c or something more efficient than python but have little experience and would like a working solution asap 

any and all comments and advice welcome but am most unsure about weather to use dbus, sockets or .. for inter python communication!!

thank u all for feed back, have googled this but cant tell witch method is best!

---

