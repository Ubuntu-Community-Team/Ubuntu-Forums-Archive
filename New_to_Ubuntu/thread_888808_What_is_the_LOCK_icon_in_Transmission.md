---
title: "What is the LOCK icon in Transmission?"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by paker on 2008-08-13
I was downloading a file using Transmission. All of a sudden, speed went up from 50 kBytes/s to 800 kBytes/s. I found the jump was coming from just one person. I noticed he didn't have the LOCK icon. All others had LOCK.

1) What is the LOCK icon?
2) If the speed jump comes from no LOCK, is there a way to remove the LOCK?

According to [www.speed.net](www.speed.net), my cable has 1000 kBytes/s down and 60 kBytes/s up. But I always get less than 100 kBytes/s down in Transmission.

Thanks.

---

### Post by Sinkingships7 on 2008-08-13
This is just a guess, but I'd say the lock has something to do with whether or not their router is forwarding the port their torrent client is using.

---

### Post by Sinkingships7 on 2008-08-13
> **paker said:**
> According to [www.speed.net](www.speed.net), my cable has 1000 kBytes/s down and 60 kBytes/s up. But I always get less than 100 kBytes/s down in Transmission.

Thanks.

When it comes to torrenting, your download speed is completely dependent on your peers uploading speed. if you have a 1 MB connection, but you have 100 people uploading to you at only 1 KB per second, then you're only going to get a max 100 KB download.

---

### Post by paker on 2008-08-13
> **Sinkingships7 said:**
> This is just a guess, but I'd say the lock has something to do with whether or not their router is forwarding the port their torrent client is using.

Thanks for the explanation. I am reading up Port Forwarding posts to see if my paltry downloading speed has anything to do with it. If you have advice, please let me know.

> **Sinkingships7 said:**
> When it comes to torrenting, your download speed is completely dependent on your peers uploading speed. if you have a 1 MB connection, but you have 100 people uploading to you at only 1 KB per second, then you're only going to get a max 100 KB download.

I understand that part. What I am trying to say is I am always capped to <100 kB, typically 50-60 kB/s. For example, I start downloading a file. It gets up to 50 kB/s. I open another one. The first goes down as the second goes up. The sum is still 50 kB/s. 

I lived with it until an hour ago, all of a sudden, 50kB/s went up to 800 kB/s for the first time. By the way I was bumping up and down Incoming TCP Port number, not knowing what I was doing (still don't know). Now I am thinking maybe I don't have to live with 50 kB/s.

---

### Post by Sinkingships7 on 2008-08-13
Yup. It sounds to me like you haven't forwarded your torrent port. It's different for every router, but [this page]("http://portforward.com/routers.htm") should help get you started.

---

### Post by Tom--d on 2008-08-13
> **paker said:**
> I was downloading a file using Transmission. All of a sudden, speed went up from 50 kBytes/s to 800 kBytes/s. I found the jump was coming from just one person. I noticed he didn't have the LOCK icon. All others had LOCK.

1) What is the LOCK icon?
2) If the speed jump comes from no LOCK, is there a way to remove the LOCK?

According to [www.speed.net](www.speed.net), my cable has 1000 kBytes/s down and 60 kBytes/s up. But I always get less than 100 kBytes/s down in Transmission.

Thanks.

I've always thought the lock was encryption.

---

### Post by paker on 2008-08-13
> **Sinkingships7 said:**
> Yup. It sounds to me like you haven't forwarded your torrent port. It's different for every router, but [this page]("http://portforward.com/routers.htm") should help get you started.
Thanks for the link. I have additional questions. Pls help.
1) Which ip address must I use? Default d-link ip address is 192.168.0.1. Also, RIGHT CLICK on WIRED CONNECTION ICON > connection information> 

ip address: 192.168.0.10x
broadcast address: 192.168.x.x.

Which one must I enter?

2) What are PUBLIC PORT and PRIVATE PORT? In Transmission, EDIT > PREFERENCE > "Incoming TCP Port xxxx closed." Does xxxx go to PUBLIC or PRIVATE? 

3) As far as I understand, the goal of this port forwarding is to pass the closed, incoming TCP port number to router. Is this corret?




> **Tom--d said:**
> I've always thought the lock was encryption.

Thanks.

---

### Post by macvr on 2008-08-13
> **paker said:**
> Thanks for the link. I have additional questions. Pls help.
1) Which ip address must I use? Default d-link ip address is 192.168.0.1. Also, RIGHT CLICK on WIRED CONNECTION ICON > connection information> 

ip address: 192.168.0.100
broadcast address: 192.168.x.x.

Which one must I enter?

2) What are PUBLIC PORT and PRIVATE PORT? In Transmission, EDIT > PREFERENCE > "Incoming TCP Port xxxx closed." Does xxxx go to PUBLIC or PRIVATE? 

3) As far as I understand, the goal of this port forwarding is to pass the closed, incoming TCP port number to router. Is this corret?






Thanks.


ok
u must do port forwarding in 2 places
1- dlink router> type 192.168.1.1[or 192.168.0.1] in browser it will open up the router configuration page , then check for the option port forwarding> in that set the any port between 10000-65534 as open
also reserve your system IP in Address Reservation.[for address reservation> check the router's attached devices, see what IP your system is connected to> in IP setup option u have to set that IP as the your fixed ip else the ip will be constantly changing and the router port forwarding wont work]

2- to set a port open in ubuntu> install firestarter[easiest way to open ports] then in the policy for inbound traffic set the port u have opened above as open. add the rule in the allow service section
also in the firestarter> edit> preferences> interface> policy> check the option to apply the policy immediately

after this is done enter the port u have chosen into Transmission, then check if port is open

PS:default torrent ports are 6881-6889, but dont choose between these, as most of these ports might be restricted by your ISP, thats why u have to choose anything above 10000

---

### Post by paker on 2008-08-14
It will take a while for me to do all that.:) When done, will post back. Thanks.

---

### Post by paker on 2008-08-14
> **macvr said:**
> ok
u must do port forwarding in 2 places
1- dlink router> type 192.168.1.1[or 192.168.0.1] in browser it will open up the router configuration page , then check for the option port forwarding> in that set the any port between 10000-65534 as open
also reserve your system IP in Address Reservation.[for address reservation> check the router's attached devices, see what IP your system is connected to> in IP setup option u have to set that IP as the your fixed ip else the ip will be constantly changing and the router port forwarding wont work]

**[SIZE="3]I got my ip address by right-clicking on the Wired Network Connection icon at the top panel of screen. Correct?[/SIZE]**

**[SIZE="3"]There were 2 ports to enter, Private and Public. I entered the same number in both. Done correctly?[/SIZE]**

2- to set a port open in ubuntu> install firestarter[easiest way to open ports] then in the policy for inbound traffic set the port u have opened above as open. add the rule in the allow service section
also in the firestarter> edit> preferences> interface> policy> check the option to apply the policy immediately

[B][SIZE="3"]The Policy Section reads:

inbound traffic policy
allow connections from host (this section is empty)
allow service, port, for: unknown, port #, my ip address (same as above)

On the Add Rule panel,
I selected BitTorrent for Name, the # for Port. For "when the source is" I selected "IP, Host, or network" and entered the same ip address . Did I do everything right?[/SIZE][/B]

after this is done enter the port u have chosen into Transmission, then check if port is open

[SIZE="3"]**The port is still closed.**[/SIZE]

PS:default torrent ports are 6881-6889, but dont choose between these, as most of these ports might be restricted by your ISP, thats why u have to choose anything above 10000

My replies are inside the quotes.

---

### Post by macvr on 2008-08-14
> **paker said:**
> My replies are inside the quotes.

for "when source is" u have to select _Anyone_

if u have selected bittorrent in the Allow service and changed the ports, has the allow service changed to _Unknown_?
else if u are using the regular ports u wont get any speed improvements for most ISPs regulate the ports 

make sure your IP address is reserved in ur dlink router else normally the ip address keep changing[even if its the same now, might change anytime later if reservation is not done]

PS: transmission for a torrent client is very basic,lacks lot of functions, its better if u switch over to some other client(deluge, ktorrent)

---

### Post by paker on 2008-08-15
1) Changing to "anyone" is done.
2) IP address reservation: Where do I reserve it? On the d-link router setup page? I think I did that. I had to enter my ip address and port number there.
3) UNKNOWN: Yes, I selected bittorrent from the list. And the program entered "unknown" into the blank "Allow Service" area.
4) If Transmission can handle port forwarding, I would like to stick to it, mainly because Deluge caused me numerous crushed under 7.10. If you know Deluge has become stable, please let me know. Ktorrent I haven't tried. I will look into it.

Thanks.

---

### Post by macvr on 2008-08-15
[COLOR="DarkRed"]is ur port now open?[/COLOR]

yes ip reservation has to be done in router page
.i'v been using deluge for a few days n didnt have any problems[transmission is fine , but i thought it lacked a few basic options, i dont know if its only for me but it didnt even display ETA for me!] but after using auzerus for a long time on XP i need to adjust to lesser options!

---

### Post by paker on 2008-08-15
Port was open for a while, I mean for several hours. Now it's closed. Maybe I have to switch over to Deluge? At least I should try that. Will post back later.

---

### Post by durand on 2008-08-15
I'm pretty sure the lock is for encryption as someone said earlier...

---

### Post by macvr on 2008-08-16
> **paker said:**
> Port was open for a while, I mean for several hours. Now it's closed. Maybe I have to switch over to Deluge? At least I should try that. Will post back later.

if the port has closed again- it is not transmission's fault
so no matter if u shift to deluge u might have same prob
re-check all steps u have taken to open ports[pretty sure that its something u have missed there]

have u rebooted after the port was open? check what ur ip is now

---

