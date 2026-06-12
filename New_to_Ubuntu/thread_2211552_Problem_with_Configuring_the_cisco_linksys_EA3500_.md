---
title: "Problem with Configuring the cisco linksys EA3500 router"
date: 2014-03-16
forum: New to Ubuntu
---

### Post by sram180990 on 2014-03-16
hello guys 
I have a cisco linksys EA3500 router dont know how to configure it. 
So please help me to configure it. And I am using Ubuntu 13.04 
Thank you

---

### Post by Vladlenin5000 on 2014-03-16
How to configure what exactly?

---

### Post by sram180990 on 2014-03-16
I want to connect my PC through it
so pls help me

---

### Post by Vladlenin5000 on 2014-03-16
Connect how exactly? Ethernet (cable) or WiFi?
You see, there's a problem with this topic you opened from the start. With a title such as 
***[SIZE=1]Problem with Configuring the cisco linksys EA3500 router[/SIZE]***

one has to wonder, at first glance, what does that have to do with Ubuntu?!? Then, at the request of clarification... Moving on...

Is the router already configured with internet access and so on? It should work for any device regardless of the operating system. If your Ubuntu computer isn't connecting whether by cable or wireless a troubleshooting of that computer is required and it has nothing to do with the router.
If the router isn't properly configured then it isn't a Ubuntu issue (or Android, MacOS, Windows, etc.). We *probably* can help you that too... 

Either way, it's important to describe the problem correctly and accurately and provide relevant information.

---

### Post by Bashing-om on 2014-03-16
sram180990; Hi !

Wired connection ? 
Does your ISP dynamically assign the IP adress ?

Access your router from your browser's address bar; -> type 192.168.0.1
default username is left blank. and the default password is "admin" - no quotes. 
Best I recall ( I also run the Cisco router) , all I had to do was insure DHCP was enabled and to clone the MAC address of the PC.

Getting wireless to work is another different thing - not been there,

"save" the settings in the router, close the browser out, and reboot.

Can you now connect ?

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by sram180990 on 2014-04-02
I have tried that 
It gives me the reply 
Host Unreachable

---

### Post by Bashing-om on 2014-04-02
sram180990; Humm,

Let's do some poken' :
Post back the outputs -between code tags - of terminal commands:
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
# denotes a comment, not to be entered -

1. Hardware ?
```

##network card detected ?##
sudo lshw -C network
##else:##
lspci | grep Ethernet

```
2. IP address assigned ?
```

ipconfig eth0 ##(or whichever the network is,eth1)?##

```
3. Check /etc/network/interfaces
```

cat /etc/network/interfaces

```
Can you even see your router ?
```

netstat -r

```

Let's see where these lead us.
[INDENT][INDENT]where there a re solutions there are no problems
[/INDENT][/INDENT]

---

