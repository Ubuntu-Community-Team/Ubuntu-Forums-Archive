---
title: "Setting up home server + other things?"
date: 2012-11-04
forum: New to Ubuntu
---

### Post by burgergetsbored on 2012-11-04
Hey, not sure if this is the correct place to put this but here goes. 

I'm looking to make a home server from an old desktop I have lying around. I'd like to make it so it has a sorta dropbox way of accessing it so I can access it over the web anywhere but also to be able to access it through windows so I can have my laptop continuously back up to it. The only problem is my laptop hard drive is fully encrypted with truecrypt so the data that's backed up to the server would also need to be encrypted otherwise there is no point in backing it up, but I have no idea how to go about doing this, is it best encrypt the data before backing it up or just encrypt the servers HDD?

On top of this it be nice if I could use it just as a web server to play around on and I've been thinking about setting up "motion" on it so I can link up a webcam and use it for security purposes. 

The question I'm asking is, is all this possible and what distribution would be best suited for these tasks? And should it be GUI based or command line? Thanks for any help!

---

### Post by sandyd on 2012-11-04
> **burgergetsbored said:**
> Hey, not sure if this is the correct place to put this but here goes. 

I'm looking to make a home server from an old desktop I have lying around. I'd like to make it so it has a sorta dropbox way of accessing it so I can access it over the web anywhere but also to be able to access it through windows so I can have my laptop continuously back up to it. The only problem is my laptop hard drive is fully encrypted with truecrypt so the data that's backed up to the server would also need to be encrypted otherwise there is no point in backing it up, but I have no idea how to go about doing this, is it best encrypt the data before backing it up or just encrypt the servers HDD?

On top of this it be nice if I could use it just as a web server to play around on and I've been thinking about setting up "motion" on it so I can link up a webcam and use it for security purposes. 

The question I'm asking is, is all this possible and what distribution would be best suited for these tasks? And should it be GUI based or command line? Thanks for any help!

a) The alternative install/ server install cds have encryption options during partitioning. You just have to do a 'manual partition' instead of the default partition setups. You will then be able to create 'encrypted partitions' in the partitioner. 

b) There are a lot of web servers available, you probably want either nginx or apache

c) Yep :)
This is a Ubuntu Forum, most of us would recommend ubuntu :P
Mostly, Servers are command line based for security reasons, and the fact that Ubuntu does not have gui configuration tools for server software.

---

### Post by burgergetsbored on 2012-11-04
ah thanks, would you recommend I install a server version of ubuntu then? I was thinking about using something such as opencloud which I believe I can install and run from command line, the same as motion for the webcam. 

Just wanted to check before I ran a distro that wasn't suited to this!

---

### Post by newb85 on 2012-11-04
The advantage of server edition is that it doesn't require the resources for a graphical desktop environment, which is especially helpful if you're using an older/weaker machine as your server.

And the good news is that if you set the server up with Ubuntu Server Edition and find yourself wishing you had a graphical desktop environment, you can simply install the desktop environment.

---

### Post by burgergetsbored on 2012-11-13
Got everything up and running well. One question, I set up the encryption but the only downside I'm having now is I can't wake on LAN and login via SSH as none of that loads before the encryption stage. Which also annoyingly means I have to constantly have a keyboard connected. It's in my bedroom too so it's turned off every night. I'm guessing there is nothing that can be done about this and it's either one or the other? 


On a side note to anyone who uses a virgin super hub: Every 3 or so days mine decides to reset itself thus losing all the port forwarding settings?!? Is there anyway to save the information when it does reset or do I have to keep restoring it?

---

### Post by DuckHook on 2012-11-14
...which is the reason that I don't encrypt the whole drive, but only the data partitions. In fact, I believe that it is best to not even encrypt the whole /home partition, but only certain directories containing the sensitive data. You can also set aside one whole partition (not /home) for encryption and dump all of your sensitive data there.  That way, you have the best of both worlds: encryption for your private stuff and system access for the base OS, including wake-on-lan, SSH, and headless operation.

BTW, if your server is in your bedroom and gets turned off every night, are you not defeating its role as a server? My servers are on 24/7, which is sorta the whole point in having them as servers. But perhaps I'm missing something here about your unique needs.

---

### Post by burgergetsbored on 2012-11-14
> **DuckHook said:**
> ...which is the reason that I don't encrypt the whole drive, but only the data partitions. In fact, I believe that it is best to not even encrypt the whole /home partition, but only certain directories containing the sensitive data. You can also set aside one whole partition (not /home) for encryption and dump all of your sensitive data there.  That way, you have the best of both worlds: encryption for your private stuff and system access for the base OS, including wake-on-lan, SSH, and headless operation.

BTW, if your server is in your bedroom and gets turned off every night, are you not defeating its role as a server? My servers are on 24/7, which is sorta the whole point in having them as servers. But perhaps I'm missing something here about your unique needs.


that would be a much better option! I just followed the encryption setup on install which just did the whole drive. I'll look into encrypting a certain partition. 

I mentioned in the first post it was mainly for just backing up data continuously from my wireless devices and access from other out of house places, since I obviously don't need this going on while I'm asleep I might as well have it turned off over night and just turned on in the morning/when I'm out!

---

