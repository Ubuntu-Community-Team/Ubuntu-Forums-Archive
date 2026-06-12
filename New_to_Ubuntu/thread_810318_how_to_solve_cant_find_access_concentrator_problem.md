---
title: "how to solve cant find access concentrator problem"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by coolnik6 on 2008-05-28
im trying to get internet on ubuntu for last 6 months but its just not happening
i use adsl router which works fine on win xp.Its in bridge mode in win xp and i have to dial a connection to connect to internet coz i have taken a limited package where i cannot execeed beyond 2gb download.
it works very well in win xp
but in ubuntu its not 
it always gives me an msg ** cannot find access concentrators further saying that it might be bcoz my router is having its own pppoe setting**
i tried connecting on 6.10 then 7.10 now 8.04 but same results
plzz ubuntu experts u tell me how can i use ubuntu when there is not internet 
i need internet to learn ubuntu 
y there is not a solution for this
my router is starcom ut300r2u
the router setting page opens at 192.168.1.1
wat shud i do u tell me
the router's LED'S all blink showing evrey is connected
power,phone line, then ethernet everything n still it cannot find these access concentrators??
plzz guys help me out

---

### Post by bangemudha on 2008-05-31
I am having the same problem as well.. i tried entering 'sudo pppoeconf' in the commandline, after the eth0 page, i see the message 'Access concentrator not responding'. I'm using TP-Link router/modem in cable mode, and i have a RealTek's ethernet card. I'm also using a dual boot system with windows xp. The internet line works well with xp but i'm not being able to configure it linux, could anyone help me (as well as the post before me? :) )

---

### Post by bangemudha on 2008-05-31
Okay, i just found a solution to this.. log on to windows, open a browser and log into the router&#347; page 192.168.1.1, type in the admin&#347; username and password. in the device info section, note the static ip and the gateway address. in my case,
static ip = 192.168.1.2
gateway address = 192.168.1.1
now log onto linux. click on the manual connection from the context menu which appears after clicking on the network icon. now click on the wired connection and then click on the properties

THat should load a properties page, there select static ip in the combo box. 
use the above 2 ip&#347; respectively in the box.. (subnet mask appears automatically, thats 255.255.255.0)

Now open up your web browser and you&#341;e good to go!

---

