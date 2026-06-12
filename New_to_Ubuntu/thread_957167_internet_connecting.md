---
title: "internet connecting"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by anubhav2k on 2008-10-24
I connected to internet via ethernet ASDL pppoe as given in help

by typin in terminal

sudo pppoeconf and did all that

it connected to internet 

but i have to do all that procedure every time ......... 
is there any way so that i get connected when i turn on my laptop

i m usin dell 1525 and ubuntu 8.04

and i m unable to connect usin my wireless .............. i have a wifi modem provided by bsnl ZXDSL 531B....

---

### Post by melojo on 2008-10-24
you should be able to add the commands to /etc/rc.local

open up a terminal and type

sudo gedit /etc/rc.local

ad the info above the exit line.

We may be able to help you get your wireless working.

open a terminal and post the output of

lspci

---

### Post by dineshs on 2008-10-24
Install gpppon . Select dsl-provider and click pon.

---

