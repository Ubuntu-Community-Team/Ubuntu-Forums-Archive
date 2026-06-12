---
title: "USB wireless problems"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by linuxinireland on 2008-07-05
please help me, I had to write this message on my iPod touch. I bought a generic wireless USB stick but I don't know how to get it to work. USB stick has cd. Please help me.Thank you in advance, this forum has never let me down before

---

### Post by Growbag on 2008-07-05
You need to tell us what type and model of network adapter you have, and what you have already tried to do.

If you need to use ndiswrapper, you need to load the windows driver.

Open a terminal and type:

ndiswrapper --help

for a list of commands.

The first one you will need is the -i (I think, I'm working from memory here!), that takes the Windows driver from your Windows driver CD (or wherever you have it).

An easier way would be to connect your system temporarily to the router by a cable if that is possible, so that you can get help a bit easier.

Good luck.

---

### Post by Dutch70 on 2008-07-05
Not to be rude...:) see I'm smileing, but the info that you gave to help you with is...

"generic wireless USB stick & and has cd.- not working." 

 Although very polite, thats always appreciated. I just wanted to help you see what it looks like from here. 
 You will have to give some well thought out info before some of the more knowledgeable people will be able to help you. 

good luck!
Dutch

---

### Post by linuxinireland on 2008-07-05
Well my battery was running low so I was just trying to be brief. I purchased a trendnet 54 Mbps 802.11g wireless USB 2.0 adapter model # TEW-42ub

---

### Post by linuxinireland on 2008-07-05
and right now I do not have a way of connecting directly to the internet. And apparently I don't have ndiswrapper. What should I do?

---

### Post by Growbag on 2008-07-06
Hmm, I thought the newer versions of Ubuntu came with ndiswrapper!

Oh well, put your Ubuntu CD in the drive, then open a terminal and type this:

```
sudo apt-get install ndiswrapper
```

Best to copy and paste that lot so you don't make any mistakes.

It should then install it for you, test it by typing:

```
ndiswrapper --help
```

when it has finished to make sure.

Then plug the network dongle into the computer and type:

```
lsusb
```

..and copy what it says, then paste it here so we can see it.

---

### Post by stalkingwolf on 2008-07-06
before you go the ndiswrapper route lets fall back to mark1 mod0.
go to system > administration > Network    are you showing a wireless
option?  If so is it enabled, (marked with a check mark)?

If you have a wireless connection showing clickit and click properties.
If it isnt enabled click the enable box, select auto configure (dhcp),
then try with roaming. if that doesnt work try without. Im running about
50/50 some work with it some with out.

You may also have to enter the connection name ( mine at home is linksys)
manually.

If you aren't seeing a wireless connection you will have to go the driver route. I guess Im lucky I have never had to mess with that, my usb devices
have always just been there.

---

### Post by linuxinireland on 2008-07-06
well I appreciate the help guys, I unfortunateley don't have my ubuntu cd available, , but I will soon. I will respond once I have tried your steps. Thanks for everything thus far.

---

### Post by linuxinireland on 2008-07-06
Bus 002 Device 003: ID 046d:c041 Logitech, Inc. 
Bus 002 Device 002: ID 046e:5542 Behavior Tech. Computer Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 005: ID 0bda:8189 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 1058:0901 Western Digital Technologies, Inc. 
Bus 001 Device 001: ID 0000:0000  
 my USB stick is the one from Realtek Semiconductor Corp. 
what do i do now?

---

### Post by linuxinireland on 2008-07-06
what does this mean?
 sudo apt-get install ndiswrapper
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ndiswrapper
 if i type ndiswrapper --help
Error: no ndiswrapper utils found!
 what do i do

---

### Post by cariboo on 2008-07-06
The message you're getting is sayinng that it can't find ndiswrapper. Have you got you LiveCD  in the CD-Rom drive?

Jim

---

### Post by linuxinireland on 2008-07-08
now i have this output i dont know what to do
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
what should i do

---

### Post by chetan.89 on 2008-07-08
Hi there !

I don't know if you have tried this.

Go to System-->Help and Support and check out articles on 'connecting to the internet'.

I did it that way and it worked. Anyway, I'm using a wireless network and not a USB wireless one. So, I don't know if it will work but it is worth a try if you haven't tried !

Good luck !
Chetan.

---

