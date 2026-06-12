---
title: "braodband connection problems"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by stephendexter on 2008-07-30
i have recently bought a dell inspiron 1525 laptop that came with the ubuntu 8.04 system, when putting in the installation cd i recieved from TISCALLI, nothing happens and i cant get my connection up and running, it came with a wired siemens speedstreem router but nothing is happening. so as of yet i have had no joy from tiscalli, i really need help in getting the settings or configuration to get my broadband up and running. any help would be greatly appreciated, many thanks,

steve

---

### Post by Bucky Ball on 2008-07-30
The machine was preinstalled with Ubuntu? If so, why do you need to run the install cd? Just after a bit of clarification ...

---

### Post by northern lights on 2008-07-30
> **Bucky Ball said:**
> The machine was preinstalled with Ubuntu? If so, why do you need to run the install cd?

> **stephendexter said:**
> when putting in the installation cd i recieved from [COLOR="Red"]TISCALLI[/COLOR]

@Bucky: Tiscali is an ISP.

@stephen: The CD you got is beyond the shadow of a doubt designed for Windows only.
No need to despair, everything you need to do can be done manually also.

If both the comp and the router are new, we first got to figure out where the problem(s) lie.

Most probably, the router needs configuration.

A few question to get a better idea of your setup:
Do you eventually want to surf via a wireless connection or can you connect PC and router with an ethernet cable?
Can you post the output of ```
sudo lshw -C network
```
Can you check for the factory set IP of the router in the manual it hopefully came with (most likely 192.168.0.1)?
What kind of broadband is this? (A)DSL, Cable, PPPoE, static IP, etc?
Finally, find your Tiscali username and password.

Eventually we'll have to access the router's config interface by typing the IP you're supposed to look for in your browser's address bar. There you'll set the (W)LAN to dhcp and on the WAN config page you'll enter the info you got from Tiscali.

---

### Post by Bucky Ball on 2008-07-30
Ah, thanks for that Northern Lights. In Aus and never heard of them, thought it was computer retailer! lol

Agreed, cd no doubt for windoze. :)

---

### Post by northern lights on 2008-07-30
> **Bucky Ball said:**
> Ah, thanks for that Northern Lights. In Aus and never heard of them, thought it was computer retailer!
Mkey. Makes sense. I doubt people know 3 Mobile in Europe either - unless they watch Cricket, that is...
:D

---

### Post by Bucky Ball on 2008-07-30
You are not insinuating Australia is in Europe I hope! lol :p But maybe you thought Aus meant Austria. Fair call.

We are aware of 3 mobile here; how can we not be when the media crams it down our throat day and night! Cheers.

---

### Post by northern lights on 2008-08-01
> **Bucky Ball said:**
> You are not insinuating Australia is in Europe I hope! lol :p But maybe you thought Aus meant Austria. Fair call.
Neither.

Since Tiscali is a European ISP it ain't too well heard of in Australia and you didn't know it. 3mobile being and Aussie company, Europeans haven't heard of it. Unless they watch cricket, cause it's one of the baggy greens main sponsors. That's what I meant.

--> I'm currently residing in Germany, it'd be pretty daft to think Australia were in Europe...
:)

---

### Post by Bucky Ball on 2008-08-01
Agreed, but you'd be surprised ...

---

