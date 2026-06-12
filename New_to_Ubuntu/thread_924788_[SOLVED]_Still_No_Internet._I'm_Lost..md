---
title: "[SOLVED] Still No Internet. I'm Lost."
date: 2008-09-19
forum: New to Ubuntu
---

### Post by SarahMarieNC2 on 2008-09-19
Okay, I had posted maybe a week ago about needing help with internet but I can't find the thread now. I am on my mother in laws laptop but can only use it on weekends. So, I really need to figure this out by Sunday if at all possible. Would help so much just to have internet on my computer again.

I have a HP Media Center PC (M8100N) with Ubuntu 8.04 LTS. Totally new to Linux and Ubuntu. My PC has a Linksys WMP 54 G PCI card. It does not have a router because I've just never needed one to get a connection. We use wi-fi. If having one would make this easier to set up I suppose I could go get one. 

Can someone walk me through this process. I'm so lost reading all the help stuff. I've never had to be "so involved" in this. Okay, so on my desktop for Ubuntu (my computer doesn't have any other OS on it) it shows in the right corner that wireless networking is enabled but some setting or some file is missing because it says that it's manually configured but that it's at 0% connectivity. 

I don't know if this will help or not but my ESSID="" That's   where the troubleshooting offline comes to a dead end. It says something about wpa_supplicant and network manager and needing to download something...

I've read countless and varying degrees of "setup" guides but I'm lost the minute they talk about copying and pasting this or downloading that. Unfortunately my time is limited to late nights on the weekends after my children are in bed. Anyone who can put this in simple terms for me ... I'd really appreciate it so much.

Sarah

---

### Post by Paqman on 2008-09-20
> **SarahMarieNC2 said:**
> It says something about wpa_supplicant and network manager and needing to download something...


Without knowing too much about the exact specifics of this error message, i'd say the system wants to download a driver to get the wifi up and running.

You say you don't have a router, but that you have wifi. The box your ISP gave you that plugs into the wall and acts as your wifi access point is the router. It should have sockets in it that you can plug your laptop into and obtain a wired internet connection. You'll need an ethernet cable, they look like this:
[img]http://www.tvcables.co.uk/images/items/10m-ethernet-cable-cat6-utp.jpg[/img]

You might have got one with the router, or else somebody will have one you can borrow (corporate IT departments normally have piles of them lying about). Once you've got a wired connection it'll be easier to get help and download anything you need to sort out your wifi.

---

### Post by SarahMarieNC2 on 2008-09-20
> **Paqman said:**
> Without knowing too much about the exact specifics of this error message, i'd say the system wants to download a driver to get the wifi up and running.

You say you don't have a router, but that you have wifi. The box your ISP gave you that plugs into the wall and acts as your wifi access point is the router. It should have sockets in it that you can plug your laptop into and obtain a wired internet connection. You'll need an ethernet cable, they look like this:
[img]http://www.tvcables.co.uk/images/items/10m-ethernet-cable-cat6-utp.jpg[/img]

You might have got one with the router, or else somebody will have one you can borrow (corporate IT departments normally have piles of them lying about). Once you've got a wired connection it'll be easier to get help and download anything you need to sort out your wifi.

Well then maybe I dont have wifi. I don't have an ISP. Basically I bought a wireless card (Linksys WMP54G) and put it in my computer (back before the big Vista crash) and voila, instant internet connection. I never really thought about it much just knew I could get online via my linksys card. 

Then the crash happened. Now I'm new to linux and so lost it's not even funny. I just know that I really would like to have internet again. 

I can take a computer apart but when it comes to all these commands and things that I see people are using to get their internet working, or anything else for that matter, it's overwhelming. But putting Vista back on my computer isn't an option. I already tried that. So, I've got to learn to use this linux stuff or be computerless. What a thought!

---

### Post by egalvan on 2008-09-20
> **SarahMarieNC2 said:**
> Well then maybe I dont have wifi. **I don't have an ISP**. Basically I bought a wireless card (Linksys WMP54G) and put it in my computer (back before the big Vista crash) and voila, instant internet connection. I never really thought about it much just knew I could get online via my linksys card.

Sounds like you are surfing on a neighbor's open wifi.
Could be OK, could be not OK.

Is your computer at a different location from your mother's computer?

> Then the crash happened. Now I'm new to linux and so lost it's not even funny. I just know that I really would like to have internet again. 

I can take a computer apart but when it comes to all these commands and things that I see people are using to get their internet working, or anything else for that matter, it's overwhelming.** But putting Vista back on my computer isn't an option. I already tried that**. So, I've got to learn to use this linux stuff or be computerless. What a thought!

Why is Vista "not an option"? Not that I would recommend it, I don't use it myself, I'm just curious.

Did you buy your HP new or used? 
Did it come loaded with Vista or XP?

I ask because HP will (almopst always) sell you the original XP install media for your computer.

I just bought a used Media Center M7690n and bought the XP recovery set for approx $17.00

Similar for a laptop Media Center.

Don't know about Vista.

And please note that I am not recommending Windows, I think Ubuntu is nicer.

Setting up wireless is usually not that difficult.
Lots of help from this forum.

ErnestG

---

### Post by SarahMarieNC2 on 2008-09-20
> **egalvan said:**
> Sounds like you are surfing on a neighbor's open wifi.
Could be OK, could be not OK.

--Yah, I dunno how it all works.

Is your computer at a different location from your mother's computer?

--Right now my mother in laws laptop  is at my house with my computer. During the week she keeps it with her. 


Why is Vista "not an option"? Not that I would recommend it, I don't use it myself, I'm just curious.
--I had Vista up until about 2 months ago when the SP1 update crashed my computer. It has a NVIDIA chipset and lots of them are being recalled because of not working right with Vista. Mine hasn't been recalled but it may not be able to run Vista because when I tried to re-install Vista with the SP1 update it crashed the computer again. So, I called a computer-friend from church and he said that it probably has to do with my chipset and thats why linux will run on it but Vista won't (too graphics intensive or something like that)


Did you buy your HP new or used? 
--I bought it refurbished from newegg.com back in February 2008.

Did it come loaded with Vista or XP?
--It came loaded with Vista premium on the 500 GB 7200 RPM Harddrive with 3 GB Ram and it has an AMD 64 bit dual-core processor.

I ask because HP will (almopst always) sell you the original XP install media for your computer.

I just bought a used Media Center M7690n and bought the XP recovery set for approx $17.00
--I bought the recovery cd's specific to my build of computer and they had errors. HP says the errors are built in and that if I leave them alone that it will complete. It gets to 99% restarts, and then says my boot mgr is missing. HP says that they will fix my computer if I send it to them and pay for  the service. It's about $250.00. 


Similar for a laptop Media Center.

Don't know about Vista.

And please note that I am not recommending Windows, I think Ubuntu is nicer.

Setting up wireless is usually not that difficult.
Lots of help from this forum.

ErnestG

---Thanks so much for all your help :)

---

### Post by okey666 on 2008-09-20
So you don't pay anyone anything per month at all? Your just using your neighbors connection?

When you buy a new piece of hardware for windows, you usually have to put a cd in and install some stuff (drivers etc).

Linux (well Ubuntu anyway) downloads them off the internet. This works really well apart from when you do not have internet connection.

If you are paying for internet access, (not just using your neighbors) you should be able to easily set up a wired connection. Do you have a box (modem) anywhere in your house that connects to the phone line (excluding telephones)? Also, when it worked under Vista, what did your wireless card connect to? What was the network called?

---

### Post by SarahMarieNC2 on 2008-09-20
> **okey666 said:**
> So you don't pay anyone anything per month at all? Your just using your neighbors connection?

When you buy a new piece of hardware for windows, you usually have to put a cd in and install some stuff (drivers etc).

Linux (well Ubuntu anyway) downloads them off the internet. This works really well apart from when you do not have internet connection.

If you are paying for internet access, (not just using your neighbors) you should be able to easily set up a wired connection. Do you have a box (modem) anywhere in your house that connects to the phone line (excluding telephones)? Also, when it worked under Vista, what did your wireless card connect to? What was the network called? 

Nope we don't pay anyone anything. We used to pay AOL for dial-up before we got my computer. No we don't have a landline phone or a box for eternet cables or any such thing like that. I have an old one floating around somewhere from when we briefly had RoadRunner.

When I installed my card the directions said NOT to use the cd if you were a windows vista user so I just installed it and windows automatically detected it. After that it asked me to set up a location and password. I did so. My location was "sarah" and this is what would show up when I viewed my connection. Occassionaly it would connect to another network called "linksys" which wasn't mine. Never really thought much  about how it worked. I guess I sound like an idiot but oh well.

---

### Post by okey666 on 2008-09-22
Well it seems quite likely that the network you were connected to does not exist anymore. We can't really help you if you don't have a reliable network to test!

---

### Post by SarahMarieNC2 on 2008-09-23
> **okey666 said:**
> Well it seems quite likely that the network you were connected to does not exist anymore. We can't really help you if you don't have a reliable network to test!

It's showing up in my network file. I've got it all worked out. Thanks for all the help. It turns out I didn't need to do anything at all. It works "out of the box" once I did a clean install of ubuntu :) Yay!

---

