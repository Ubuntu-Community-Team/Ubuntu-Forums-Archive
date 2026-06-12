---
title: "[SOLVED] I need a program/script to reboot my ADSL modem!!"
date: 2008-07-02
forum: Programming Talk
---

### Post by LinuX-M@n1@k on 2008-07-02
Hi!

First, I want to say that I don't know any kind of programming language, and I need someone to write me a program or a script to ping to a stable server (google.com for example) and if there's no reply to connect to my ADSL Modem (with telnet session) and reboot it.

It looks **impossible** for me, but I hope that I'll find a good friend here who can do this for me...

The problem is that I have 3 PCs behind my ADSL Modem and because of the many connections - the modem freezes... It's not with USB interface, it's over the LAN

Thank you VERY much for reading this, and hopefully helping me...
(Yes, English is not my first language :oops:)

---

### Post by CptPicard on 2008-07-02
Do a firmware upgrade of your modem or replace the modem, they should not freeze on some kind of connection table overflow :)

---

### Post by LinuX-M@n1@k on 2008-07-02
Thank you for the reply!
Upgrading the firmware is not an option for me.

I got the modem from my ISP and their settings must not be removed... I'm afraid that when I upgrade the firmware their settings will be replaced. I even should not have the login and the password for the modem.

Model: ZTE ZXDSL 831
Memory: 8MB (only ?!?)

When it freezes, I connect to it and ping google.com. I get an error "Memory fault". Maybe I'll change it, but it won't be soon.

Anyone else ? Thanks!

---

### Post by CptPicard on 2008-07-02
Complain to the ISP? Ask tech support if they are using factory default settings? If not, ask for the settings, and do the firmware upgrade, and then reset the settings to what they need.

If they hold you hostage it is their problem completely :)

---

### Post by thschiavo on 2008-07-02
You want a script that pings a stable server and, if not get the response from this server, it reboots the modem? It shouldn`t be easy at all...

---

### Post by LinuX-M@n1@k on 2008-07-02
> **thschiavo said:**
> You want a script that pings a stable server and, if not get the response from this server, it reboots the modem? It shouldn`t be easy at all...

Yes, I know :)

> **CptPicard said:**
> Complain to the ISP? Ask tech support if they are using factory default settings? If not, ask for the settings, and do the firmware upgrade, and then reset the settings to what they need.

If they hold you hostage it is their problem completely :)

I have stolen the password to get in the modem :D They won't be very happy to hear me asking if I can make a firmware upgrade :lol:

---

### Post by LinuX-M@n1@k on 2008-07-02
*bump*

---

### Post by henchman on 2008-07-02
what about exporting the settings and importing them after the update... on some routers there is such an option :)

if it won't work just send it to them complaining it won't work anymore and they think the firmware got crashed ;)

---

### Post by Psykotik on 2008-07-02
This script could be very easy to do... if your modem has a function to be rebooted. 

Here is mine :

```
#!/bin/bash

linkreboot="http://user:password@192.168.1.1/rebootinfo.cgi"

# ping google
ping="ping -c 1 -w 3 -q www.google.ch"

if $ping | grep -E "min/avg/max/mdev" > /dev/null 
	then
		# ping is ok
		echo 'connection is ok'
	else
		# ping is down, reboot
		/usr/bin/wget -O /dev/null $linkreboot
		# if no web reboot is allowed
		sudo reboot
		echo 'No valid ping, reboot'
fi
```

modify $linkreboot according your modem option available.

---

### Post by LinuX-M@n1@k on 2008-07-03
> **Psykotik said:**
> 
```

	else
		# ping is down, reboot
		/usr/bin/wget -O /dev/null $linkreboot
		[b]# if no web reboot is allowed
		sudo reboot
		echo 'No valid ping, reboot'[/b]
fi
```

Isn't that going to reboot your PC? I don't get that part...

Yep, my PC just rebooted! :lol:
The idea is to connect to the modem and reboot it, not to reboot my PC. Or maybe I'm not doing it right?

---

### Post by Archmage on 2008-07-03
Just a stupid idea: How about reducing the number of connections? I know that many people even use P2P with such a faulty modem, after they reduce the numbers of connections?

---

### Post by LinuX-M@n1@k on 2008-07-03
I already did that, but it crashed again with the error "Memory fault"... I reduced them again yesterday and I'll wait to see what will happen.

---

### Post by LinuX-M@n1@k on 2008-07-03
> **henchman said:**
> what about exporting the settings and importing them after the update... on some routers there is such an option :)

if it won't work just send it to them complaining it won't work anymore and they think the firmware got crashed ;)

If I find a firmware for my modem I'll try it. It has a backup option.

The bad thing is that when the modem connects to my ISP's server it downloads their limitation (I dont know if there's such a word :)) settings.
(1000 connections only; about 330 connection per PC in my case)

---

### Post by Psykotik on 2008-07-03
Sorry, I should have specified:

```
		# if no web reboot is allowed
		sudo reboot

```

is only meant to reboot the PC whenever the modem doesn't allow a web reboot.

If it's not the case, and the modem allows the web reboot, get rid of this part.

---

### Post by LinuX-M@n1@k on 2008-07-03
> **Psykotik said:**
> Sorry, I should have specified:

```
		# if no web reboot is allowed
		sudo reboot

```

is only meant to reboot the PC whenever the modem doesn't allow a web reboot.

If it's not the case, and the modem allows the web reboot, get rid of this part.

Sorry if I'm rude, but what's the point? In my case this script is useless... Here's how I see it:

If there's ping to google.com -> `echo "connection is ok"`
If not -> `do nothing? (or reboot my PC, not the modem)`

Other ideas?

PS: I'm still looking for a firmware to upgrade mine.

---

### Post by Psykotik on 2008-07-03
> **LinuX-M@n1@k said:**
> Sorry if I'm rude, but what's the point? In my case this script is useless... Here's how I see it:

If there's ping to google.com -> `echo "connection is ok"`
If not -> `do nothing? (or reboot my PC, not the modem)`

Other ideas?

PS: I'm still looking for a firmware to upgrade mine.

This script launch this link if there is no ping:

```
/usr/bin/wget -O /dev/null $linkreboot
```

where $linkreboot is a link to reboot the modem... mine is 

[http://user:password@192.168.1.1/rebootinfo.cgi](http://user:password@192.168.1.1/rebootinfo.cgi)

Not all modems allow a direct link to reboot, check if yours do.

---

### Post by Zugzwang on 2008-07-03
> **Psykotik said:**
> This script launch this link if there is no ping:

```
/usr/bin/wget -O /dev/null $linkreboot
```


The problem with this is that the OP has only telnet access to the modem. However, there's a Python module for interacting with the telnet client (and other interactive CLI-programs): [http://www.noah.org/wiki/Pexpect#Overview]("http://www.noah.org/wiki/Pexpect")

---

### Post by Psykotik on 2008-07-03
> **Zugzwang said:**
> The problem with this is that the OP has only telnet access to the modem. However, there's a Python module for interacting with the telnet client (and other interactive CLI-programs): [http://www.noah.org/wiki/Pexpect#Overview]("http://www.noah.org/wiki/Pexpect")

Where did you read about having only telnet access ? He said

> I have stolen the password to get in the modem They won't be very happy to hear me asking if I can make a firmware upgrade 

I assume he has a direct access to the modem...

---

### Post by LinuX-M@n1@k on 2008-07-03
> **Psykotik said:**
> This script launch this link if there is no ping:

```
/usr/bin/wget -O /dev/null $linkreboot
```

where $linkreboot is a link to reboot the modem... mine is 

[http://user:password@192.168.1.1/rebootinfo.cgi](http://user:password@192.168.1.1/rebootinfo.cgi)

Not all modems allow a direct link to reboot, check if yours do.

My link is the same, but it's not a link to reboot the modem... It's only a text file:

[http://192.168.1.1/rebootinfo.cgi](http://192.168.1.1/rebootinfo.cgi)
> Reboot DSL Router

The DSL Router has been configured and is rebooting.

Close the DSL Router Configuration window and wait for 2 minutes before reopening your web browser. If necessary, reconfigure your PC's IP address to match your new configuration. 

----
> **Zugzwang said:**
> The problem with this is that the OP has only telnet access to the modem. However, there's a Python module for interacting with the telnet client (and other interactive CLI-programs): [http://www.noah.org/wiki/Pexpect#Overview](http://www.noah.org/wiki/Pexpect#Overview)
I had to say earlier that I have both telnet and web access to it. Sorry for that.
And thanks for the link! I'll check it in a minute.

---

### Post by LinuX-M@n1@k on 2008-07-03
I've done the script! :D

Here it is: [http://ubuntuforums.org/showpost.php?p=5314667&postcount=11](http://ubuntuforums.org/showpost.php?p=5314667&postcount=11)

And I've attached it too, so I can download it whenever I want :D. Thank you all for the help!

---

### Post by sokhi on 2011-06-15
Hi Psykotik
Thanks for script
working with Beetal 220bx adsl2+modem on CentOS 5.6 
+Scheduled Cron Jobs
```
#!/bin/bash

linkreboot="http://admin:password@192.168.1.1/rebootinfo.cgi"

# ping google
ping="ping -c 3 -w 3 -q google.co.in"

if $ping | grep -E "min/avg/max/mdev" > /dev/null 
	then
		# ping is ok
		echo 'connection is ok'
	else
		# ping is down, reboot
		/usr/bin/wget -O /dev/null $linkreboot
fi
```

Regards
sukhdev sokhi
[http://www.sokhi.net](http://www.sokhi.net)

---

