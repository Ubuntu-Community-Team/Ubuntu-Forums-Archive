---
title: "connecting to internet"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by player4 on 2008-06-28
I have recently read in a computer magazine a article that said Ubuntu 8.04 is a Window Killer with a better upgrade than Vista so being anti Microsoft I decided to go with Ubuntu instead of Vista.  Have installed it somewhat successfully but cannot connect to the internet.  This is the first time I have touched Linus and am a real novice.  I am using Siemens Slipstream 4200 Ethernet and have gone into the network terminal and connected to DHCP configuration and when I fire up Firefox the little wheel comes on that tells me it is trying to connect and then the message "can't connect to server" pops up.  Obviously I have missed something in the configuration .. can you please HELP ME

---

### Post by wormser on 2008-06-28
Welcome to Ubuntu!

Post the results of the following commands.  Applications> Accessories> Terminal.

```
ifconfig
```
```
ping ubuntuforums.org
```
```
ping 91.189.94.12
```

To get an IP address use the command dhclient.  See if it works.

```
sudo dhclient
```

BTW, you will get more responses if you post in the Absolute Beginners forum.

---

### Post by player4 on 2008-06-28
Thought this was posted in Absolute Beginners but apparently not!  Apologies for double up.

I have recently read in a computer magazine a article that said Ubuntu 8.04 is a Window Killer with a better upgrade than Vista so being anti Microsoft I decided to go with Ubuntu instead of Vista. Have installed it somewhat successfully but cannot connect to the internet. This is the first time I have touched Linus and am a real novice. I am using Siemens Slipstream 4200 Ethernet and have gone into the network terminal and connected to DHCP configuration and when I fire up Firefox the little wheel comes on that tells me it is trying to connect and then the message "can't connect to server" pops up. Obviously I have missed something in the configuration .. can you please HELP ME

---

### Post by player4 on 2008-06-28
> **wormser said:**
> Welcome to Ubuntu!

Post the results of the following commands.  Applications> Accessories> Terminal.

```
ifconfig
```
```
ping ubuntuforums.org
```
```
ping 91.189.94.12
```

To get an IP address use the command dhclient.  See if it works.

```
sudo dhclient
```

BTW, you will get more responses if you post in the Absolute Beginners forum.

Wormer, thank you for your reply but I can't do this at the moment as I am on Windows at the moment.  As soon as I get a chance to get back into Ubuntu I'll let you know what happens.  BTW .. sorry, thought had posted in Absolute Beginners so have re-posted.

---

### Post by paul101 on 2008-06-28
1). are you using a wireless card?

2). have you tried resetting the modem (power off for 10 seconds then on again)

---

### Post by dinomite89 on 2008-06-28
> **player4 said:**
> Thought this was posted in Absolute Beginners but apparently not!  Apologies for double up.

I have recently read in a computer magazine a article that said Ubuntu 8.04 is a Window Killer with a better upgrade than Vista so being anti Microsoft I decided to go with Ubuntu instead of Vista. Have installed it somewhat successfully but cannot connect to the internet. This is the first time I have touched Linus and am a real novice. I am using Siemens Slipstream 4200 Ethernet and have gone into the network terminal and connected to DHCP configuration and when I fire up Firefox the little wheel comes on that tells me it is trying to connect and then the message "can't connect to server" pops up. Obviously I have missed something in the configuration .. can you please HELP ME

Clearly We read the magazine and think alike ;)

---

### Post by masterjonny on 2008-06-28
I had the same error, spent ages trying to fix it. Eventually I got it by using a static IP, but after setting the IP it won't go straight away...you have to restart first. After that it went :)

---

### Post by player4 on 2008-06-28
> **paul101 said:**
> 1). are you using a wireless card?

2). have you tried resetting the modem (power off for 10 seconds then on again)


No, not using a wireless card and will give #2 a go and let you know how I get on .. thanks very much for the reply :)

---

### Post by player4 on 2008-06-28
> **dinomite89 said:**
> Clearly We read the magazine and think alike ;)

Great minds think alike :lolflag:

---

### Post by player4 on 2008-06-28
> **masterjonny said:**
> I had the same error, spent ages trying to fix it. Eventually I got it by using a static IP, but after setting the IP it won't go straight away...you have to restart first. After that it went :)

Thanks .. will give it a shot .. ready to try anything at this stage :KS

---

