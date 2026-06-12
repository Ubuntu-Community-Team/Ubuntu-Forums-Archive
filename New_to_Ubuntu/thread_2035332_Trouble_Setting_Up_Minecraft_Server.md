---
title: "Trouble Setting Up Minecraft Server"
date: 2012-07-30
forum: New to Ubuntu
---

### Post by doppel.ganger on 2012-07-30
I'm tring to set up a Minecraft Server for my family on Ubuntu. I downloaded the minecraft_server.jar file from the Minecraft website and put it in its own folder on the desktop. I ran:
```
java -Xmx1024M -Xms1024M -jar minecraft_server.jar nogui.
```
and everthing went smoothly. I then gave my username ops. Also no trouble. Then when I went to test it on another computer. I went to "Add Server", put in the the server name and my ip address, but I get the "Can't Reach Server" message. Can anyone help me?

Thanks,
DG

---

### Post by androssofer on 2012-07-30
> **doppel.ganger said:**
> I'm tring to set up a Minecraft Server for my family on Ubuntu. I downloaded the minecraft_server.jar file from the Minecraft website and put it in its own folder on the desktop. I ran:
```
java -Xmx1024M -Xms1024M -jar minecraft_server.jar nogui.
```
and everthing went smoothly. I then gave my username ops. Also no trouble. Then when I went to test it on another computer. I went to "Add Server", put in the the server name and my ip address, but I get the "Can't Reach Server" message. Can anyone help me?

Thanks,
DG

is it on ubuntu server or ubuntu desktop?

most likely cause is the firewall is blocking the connections.

or you need to forward the ports on your router..

or both...

if your on ubuntu desktop, download 'firestarter', and it should allow you to open up the ports in the firewall..

---

### Post by androssofer on 2012-07-30
this should open up the port if you have ubuntu server:

```
sudo iptables -A INPUT -p tcp --dport 25565 -j ACCEPT
```

as for port forwarding on your router.. it varies but a simple search should tell you how.

ps: port 25565 is the standard Minecraft port. 

pps running the command as:

```
 java -Xmx1024M -Xms1024M -server -jar minecraft_server.jar nogui
```

might give you marginal performance improvements

---

### Post by mlentink on 2012-07-30
Hmm.

Maybe I misunderstood, but I think the OP is running the server only internally (LAN), so why would all this port-forwarding be necessary?  Maybe input the IP-adress of the server rather than the name??

---

### Post by doppel.ganger on 2012-07-30
I am using the Ubuntu Desktop.

---

### Post by doppel.ganger on 2012-07-30
I have a Linksys WiFi router, model # WRT54G. Does anybody know how to open the ports needed with this router?

---

### Post by levlaz on 2012-07-30
> **doppel.ganger said:**
> I have a Linksys WiFi router, model # WRT54G. Does anybody know how to open the ports needed with this router?

To access the port options plug an ethernet cord into the router and go to the admin panel. 

Should be 192.168.2.1 or 192.168.1.1 

The default password and username is 

username: admin 
password: admin 

This will allow you to set up rules for ports and whatnot. 

Best, 

Lev

---

### Post by anewguy on 2012-07-30
Are you trying to access this from within your own network, or are you trying to let access across the internet?

Also - you may want to ask to have this moved to the leisure and gaming forum.  A lot of stuff on Minecraft there, and you may find someone either has had the same problem or can help you more.

---

### Post by mlentink on 2012-07-31
@doppel.ganger: As per my earlier question, and anewguy's, could you please speify whether you want to reach the minecraft server by computers within your own private LAN only, or if it should be reachable by others on the internet?

---

### Post by doppel.ganger on 2012-07-31
> **mlentink said:**
> @doppel.ganger: As per my earlier question, and anewguy's, could you please speify whether you want to reach the minecraft server by computers within your own private LAN only, or if it should be reachable by others on the internet?

Can I have both?

---

### Post by mlentink on 2012-07-31
You should be able to do both, but in that case you really should forward the necessary ports on your router to your server, and make sure the firewall does not block those ports. See the earlier comments.

Even though you should be easily able to connect to such a server from within your own network, I understand from my son you can only really connect it to play through the Minecraft site (Connect to server). This means you should know your external IP (see whatismyip.com or somesuch).

---

### Post by collisionystm on 2012-07-31
I just set one up recently, so I am sure I can point you in the right direction.

You need to do 3 things.

1. Make yourself 'OP' so you can execute server commands from in-game.
2. Setup your minecraft as a Service on your server.
3. Setup port forwarding in your router so your friends can connect


So first make yourself OP so you dont have to later on.
Just start the minecraft server like you did before.
Open a terminal
```
java -Xms1024M -Xmx1024M -jar minecraft_server.jar nogui
```

Now you should be at the MC server console. Connect with your PC to it.
Once you have joined just type on the server

op YOURUSERNAME

I.E. op drakesilverfall    < drakesilverfall being me

Now you can close out and move on.


To make minecraft run as a service and auto-start with your machine, here are 2 links. I used the 2nd one... cant remember why at this moment, but they both will work. I think.

[http://www.minecraftwiki.net/wiki/Tutorials/Ubuntu_startup_script](http://www.minecraftwiki.net/wiki/Tutorials/Ubuntu_startup_script)

[http://www.minecraftwiki.net/wiki/Tutorials/Server_startup_script](http://www.minecraftwiki.net/wiki/Tutorials/Server_startup_script)

Now you wont have to work about starting/stopping or accidentally closing out your minecraft server. It will just run until you explicitly say, ```
/etc/init.d/minecraft stop/start
```


The next thing to do is setup your port forward in the router.
Find out what the local ip of your "server" is.

```
ifconfig
```

Setup your internet router to forward port 25565 to your servers local IP.

You can go to, [www.whatismyip.com](www.whatismyip.com) to get your external address that your friends will punch in to connect.


Now... you can play.


Oh and you shouldnt have to do any sort of firewall changes on your machine internally unless you turned on a firewall. There really is no point in enabling it internally when you are behind one anyways (your router).

---

### Post by doppel.ganger on 2012-07-31
Thanks so much, collisionystm! I had done step 1, but I needed to do the others. Thank you so much again! I'll make another post if I run into any problems or if it works.

---

### Post by doppel.ganger on 2012-07-31
I'm pretty sure I did something wrong with Port Forwarding. The server is still not working. See screenshot.

---

### Post by ubudog on 2012-07-31
> **doppel.ganger said:**
> I'm pretty sure I did something wrong with Port Forwarding. The server is still not working. See screenshot.

Hi doppel.ganger -- from the screenshot it seems you put '192.168.1.1' as your IP in the port forwarding control panel.  Be sure you have the IP of the server set (run ifconfig on the server to get it).

I'd suggest setting up a [Static IP]("http://www.howtoforge.com/linux-basics-set-a-static-ip-on-ubuntu") so that when you reconnect, DHCP doesn't reassign you a different IP.

Hope that helps!

---

### Post by doppel.ganger on 2012-07-31
Sorry, ubudog. Those Static IP instructions were way over my head. I rarely disconnect, so that shouldn't be too much of an issue. Can you tell me how to read the output of ifconfig?

---

### Post by anewguy on 2012-08-01
> **ubudog said:**
> Hi doppel.ganger -- from the screenshot it seems you put '192.168.1.1' as your IP in the port forwarding control panel.  Be sure you have the IP of the server set (run ifconfig on the server to get it).

I'd suggest setting up a [Static IP]("http://www.howtoforge.com/linux-basics-set-a-static-ip-on-ubuntu") so that when you reconnect, DHCP doesn't reassign you a different IP.

Hope that helps!

I'm no geniuos here, so forgive me if I've got it wrong - wouldn't the 192.168.1.1 be stepping on the access to the router control panel on several routers - and if so, could this be part of the OP's problem?

---

### Post by collisionystm on 2012-08-01
> **doppel.ganger said:**
> Sorry, ubudog. Those Static IP instructions were way over my head. I rarely disconnect, so that shouldn't be too much of an issue. Can you tell me how to read the output of ifconfig?


Post the output of your ifconfig

---

### Post by doppel.ganger on 2012-08-01
```
thomas@Thomas-HP-Mini-5101:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:21:00:ff:2f:ed  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:ff:feff:2fed/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:614 errors:0 dropped:0 overruns:0 frame:5543
          TX packets:675 errors:21 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:171394 (171.3 KB)  TX bytes:113206 (113.2 KB)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:25:b3:6d:1d:98  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:168 errors:0 dropped:0 overruns:0 frame:0
          TX packets:168 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9706 (9.7 KB)  TX bytes:9706 (9.7 KB)

thomas@Thomas-HP-Mini-5101:~$ 

```

---

### Post by collisionystm on 2012-08-02
> 


eth0      Link encap:Ethernet  HWaddr 00:21:00:ff:2f:ed             inet addr:**[COLOR=Red]192.168.1.100[/COLOR]**  Bcast:192.168.1.255  Mask:255.255.255.0           inet6 addr: fe80::221:ff:feff:2fed/64 Scope:Link           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1           RX packets:614 errors:0 dropped:0 overruns:0 frame:5543           TX packets:675 errors:21 dropped:0 overruns:0 carrier:0           collisions:0 txqueuelen:1000            RX bytes:171394 (171.3 KB)  TX bytes:113206 (113.2 KB)           Interrupt:16 




Theres your address... Marked in Red. Thats what you port forward to.

---

### Post by doppel.ganger on 2012-08-03
That didn't work. Computer still can't reach server.

---

### Post by doppel.ganger on 2012-08-04
*bump*

---

### Post by anewguy on 2012-08-04
You know, at this point you might be better off:

(1) removing everything you've done.  If it was a fresh install or if otherwise possible, just reinstall ubuntu.

(2) before doing anything else, I personally would go to the gaming and leisure forum and ask for advice on setting up the minecraft server and being able to connect from multiple computers. 

Obviously, you are by far not the first person to do this.  Posting in that forum before doing anything you may find someone who can give you step-by-step instructions for doing it so you don't run into the same problems.

Remember, patience, especially when it's something like this that just HAS to work now, is a great friend in dealing with these things.  Ask the simplest of questions, and work into the rest, instead of trying to do everything at once.

Best of luck

---

### Post by doppel.ganger on 2012-08-04
Thanks, anewguy. I'll take your advice.

---

