---
title: "Transmisson: enabled port forwarding, but it says port is still closed."
date: 2008-08-03
forum: New to Ubuntu
---

### Post by deathvalleyjoker on 2008-08-03
i did some searching and found this thread:

[http://ubuntuforums.org/showthread.php?t=844034&highlight=bittorrent+slow](http://ubuntuforums.org/showthread.php?t=844034&highlight=bittorrent+slow)

however, i enabled my portforwarding by using this page:

[http://portforward.com/english/routers/port_forwarding/Linksys/WRT54G/BitTorrent.htm](http://portforward.com/english/routers/port_forwarding/Linksys/WRT54G/BitTorrent.htm)

 and use a static ip on my router, so i know it should be going to my computer. but in transmission, on the Incoming TCP Port, it always says that the port is closed. any thoughts on what i am missing? these 36KiB/s downloads speeds are killing me.

---

### Post by Vivaldi Gloria on 2008-08-03
Transmission uses a different port number. See its settings.

---

### Post by adult swim on 2008-08-03
also if your router doesnt support UPnP it wont automatically forward your port.
EDIT: i totally misread your post!
have you made an exception in your firewall for the port?

---

### Post by deathvalleyjoker on 2008-08-03
> **adult swim said:**
> also if your router doesnt support UPnP it wont automatically forward your port.
EDIT: i totally misread your post!
have you made an exception in your firewall for the port?

No, good point. what is the name of that firewall-manger?

---

### Post by adult swim on 2008-08-03
firestarter

---

### Post by Vivaldi Gloria on 2008-08-03
> **adult swim said:**
> firestarter

Not good advice.

The default ubuntu comes with all ports open. No need to make any changes in ubuntu to use p2p programs. It's all about router port and router firewall settings.

Besides, firestarter is dead and ubuntu comes with ufw. See

```
man ufw
```

and especially the examples section for more info on it.

But I repeat again, in the default ubuntu install, firewall is not working and all ports are open.

---

### Post by deathvalleyjoker on 2008-08-03
ok i have firestarter installed, could you tell me the quick and dirty way i can add the port to it?

---

### Post by Vivaldi Gloria on 2008-08-03
> **deathvalleyjoker said:**
> ok i have firestarter installed, could you tell me the quick and dirty way i can add the port to it?

Open a terminal (Apps. > Access. > Term.) and give the command

```
sudo ufw status
```

If it comes back as

```
Firewall not loaded
```

then all ports are already open. No need to add port to firewall. 

Start transmission, look into its settings, learn the port number it uses. Then forward that port it in router nat and router firewall. No need to do anything in ubuntu.

---

### Post by deathvalleyjoker on 2008-08-03
ill try that.

---

### Post by deathvalleyjoker on 2008-08-03
ok so back to the router settings. i must be missing something

---

### Post by Vivaldi Gloria on 2008-08-03
> **deathvalleyjoker said:**
> ok so back to the router settings. i must be missing something

You're missing the fact that transmission uses a different port number. See its settings to learn it. Then forward that port.

---

### Post by dhughes on 2008-08-03
I was going to say what my setup was but I realized I got a new router recently and Transmission wasn't port forwarded, it seems that 10000 TCP is default. 

 Opening 10000 TCP under my Linksys WRT54GL router's Applications & Gaming> Port Range Forward then setting my IP 192.168.1.100 didn't work.

 I don't use any firewall, just the router. I'll get back to you if I get it working.
[B]
edit:[/B] that wasn't hard I had it set to 192.168.1.100 instead of .200

---

### Post by Vivaldi Gloria on 2008-08-03
I just checked and my transmission uses the TCP 51413 port. It may change from computer to computer, that's why I suggest to start transmission and look at its settings. Or change the default port.

---

### Post by dhughes on 2008-08-03
> **Vivaldi Gloria said:**
> I just checked and my transmission uses the TCP 51413 port. It may change from computer to computer, that's why I suggest to start transmission and look at its settings. Or change the default port.

 I was going to mention that but I restarted it to test it and the port didn't change, Transmission doesn't seem to have the option to randomize the port number, which I guess is a good thing in this situation.

 Anyway it's open on my system, but as I said I don't use any firewall, I never even heard of ufw until you mentioned it deathvalleyjoker.

 What kind of router do you use deathvalleyjoker?

 Pretty much just do this:

[LIST]
[*] Start Transmission, under Edit>Preferences look to see the port number next to 'Incoming TCP Port', mine is 10000 

[*] In the router's 'Port Range Forward' or 'Virtual Server' put in that number, e.g. 10000, Transmission uses TCP (not UDP or Both).

[*] Make sure it's forwarded to your IP for example mine is 192.168.1.200 make sure the check mark is there (for Linksys)

[*] Remember to Save, and possibly restart Transmission. Test it by going to Edit>Preferences to see if the port next to 'Incoming TCP Port' says **open**
[/LIST]

---

### Post by deathvalleyjoker on 2008-08-05
> **dhughes said:**
> 
 What kind of router do you use deathvalleyjoker?

 Pretty much just do this:

[LIST]
[*] Start Transmission, under Edit>Preferences look to see the port number next to 'Incoming TCP Port', mine is 10000 

[*] In the router's 'Port Range Forward' or 'Virtual Server' put in that number, e.g. 10000, Transmission uses TCP (not UDP or Both).

[*] Make sure it's forwarded to your IP for example mine is 192.168.1.200 make sure the check mark is there (for Linksys)

[*] Remember to Save, and possibly restart Transmission. Test it by going to Edit>Preferences to see if the port next to 'Incoming TCP Port' says **open**
[/LIST]

Router: linksys wrt54g

I followed your steps above, with the new port.(and i have tried a few ports now, each time changing them respectively in the port forward page of my router.) and still nothing. 

I have included some pics to show you what i am looking at.

EDIT: also thanks for working with me on this one guys. I would hate to have to log back into my windows partition just to so some bittorrenting. 

Also sidenote: i am not self-incriminating; The naruto torrent file i am downloading is hosted by the Japanese company that makes it. it is the jap language with eng subs. the english dub is the illegal one since cartoon network or someone like owns thoes rights.

---

### Post by roquefilipe on 2008-08-05
some routers have to be restarted. 

Also make sure that your pc has the specified IP address: 192.168.2.136

---

### Post by Vivaldi Gloria on 2008-08-06
I looked at the port forward guide you gave the link to above. It looks stupid. This is my howto port forward.

**1)** Enter the router settings. Every decent router has a setting or table where you can fix the adresses of particular computer (ethernet card). Find that setting which fixes your computer's adress. It can be something of the sorts "Always use the ip 192.168.XX.XX for the computer with the mac adres XX:XX:...". I choose a number like 192.168.1.35. Restart router.

**2)** In a terminal give the command ifconfig. Here is the top lines of its output from my box:

```
vivaldi@narval:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:07:c4:d2:17:ba  
          inet addr:192.168.1.35 ...
...
...
```

Here eth0 is the my main ethernet card. The ip 192.168.1.35 is the ip fixed by the router for that card. So at this step we verify that you indeed get the ip the router reserved for your computer.

**3)** Now since your computer's ip is fixed to 192.168.1.35 you can forward the ports you want to 192.168.1.35. For example for transmission use

start & end ports: 10000, TCP, ip:192.168.1.35

**4)** Some routers also have a seperate firewall settings in which you may also need to enable ports.

There you go.

---

### Post by deathvalleyjoker on 2008-08-06
```
wlan0     Link encap:Ethernet  HWaddr 00:18:f8:26:c7:02  
          inet addr:192.168.2.136  Bcast:192.168.2.255  Mask:255.255.255.0

```

I already had a thread about how to make my ipaddress static:

[http://ubuntuforums.org/showthread.php?t=877919](http://ubuntuforums.org/showthread.php?t=877919)

I know how to portforward, i did it with my windows install to enable remote desktop through dyndns.com and i followed every step the same way. still the port is closed....

That is why i think i might be missing a step somehow or somewhere. my ip is hardcoded at 2.136, the applications say to point it there, and i followed the steps from that portforward.com to make sure all the other router settigns are set. though i dont they have as much to do with this as it took for remote desktop.

---

### Post by Vivaldi Gloria on 2008-08-06
> **deathvalleyjoker said:**
> I already had a thread about how to make my ipaddress static.

I find it easier to fix ips with the router settings (rather than editing some config file) because router fixes the ip for that computer regardless of the operating systems installed (or you'll install) in that computer.

> **deathvalleyjoker said:**
> That is why i think i might be missing a step somehow or somewhere. my ip is hardcoded at 2.136,

Does your router have a firewall or security settings? In my router it is not enough to port forward, but also I need to make some changes in the router's firewall.

---

### Post by deathvalleyjoker on 2008-08-06
I didnt relize that routers have a firewall. I dont remember seeing any options for firewall anywhere. do u know of any sites or maybe a screenshot to show me what it looks like. also if u could point or show me a way of haveing the router assign my ipaddress, that would be great. i didnt know that was possible either. thanks.

---

### Post by Vivaldi Gloria on 2008-08-06
> **deathvalleyjoker said:**
> I didnt relize that routers have a firewall. I dont remember seeing any options for firewall anywhere. 

Not all have a firewall. I guess yours doesn't have one.

> **deathvalleyjoker said:**
>  if u could point or show me a way of haveing the router assign my ipaddress, that would be great. i didnt know that was possible either. thanks.

I don't know your router so I don't know if you can do it. See my above post 17 for howto do it in a router which has that option.

In my router settings there is a list of client computers connected (actually their mac numbers) and there is a checkbox for each which says "do you want to reserve this ip for this mac adress?" If I check it then the router always assigns the same ip to that computer.

---

### Post by jackson_vkh on 2008-09-19
You're not doing anything wrong... There's something messed up with Ubuntu/Linksys.  

If I plug my computer directly to my DSL it shows my port as being open.  However when I go through my Linksys Router, it tells me my port is closed, even though I know I properly opened it.

Here's how to check.

Open a command prompt and type 

nc -z -v -w2 IPADDRESS PORTNUMBER

The IP should be that of your machine that Transmission is installed on and the port number is the one Transmission is using.

It's not a solution to your problem, but it does prove that you're not crazy.

---

### Post by deathvalleyjoker on 2008-09-21
> **jackson_vkh said:**
> You're not doing anything wrong... There's something messed up with Ubuntu/Linksys.  

If I plug my computer directly to my DSL it shows my port as being open.  However when I go through my Linksys Router, it tells me my port is closed, even though I know I properly opened it.

Here's how to check.

Open a command prompt and type 

nc -z -v -w2 IPADDRESS PORTNUMBER

The IP should be that of your machine that Transmission is installed on and the port number is the one Transmission is using.

It's not a solution to your problem, but it does prove that you're not crazy.

Thank you. I pretty much gave up on it, and blamed it on the the torrent or seeding or something. Really, I shouldn't complain, because i can now download a movie in the time it took to download an mp3 6-8 years ago. 

But you did jump start me to look into remote desktop now. That was how i found out how to port forward before, and i definitly want to do it with Ubuntu.

Cheers!

---

