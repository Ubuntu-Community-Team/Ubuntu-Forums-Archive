---
title: "How to set up a Thin Client?"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by mohenjo on 2008-07-11
Awhile back I posted this question in the Networking forum but didn't find the answer I was looking for, so I'll try here.

I've got a fresh install of Ubuntu 8.04 and I'm looking to try to get it set up in such a way that when the machine starts up, it automatically connects to a pre-configured terminal server via RDP.  

I want users to enter the username/password to get onto the terminal server, but I'd like Ubuntu to skip any local logon (or configure a heavily restricted user to automatically logon to get the RDP session started.

Does anyone know of a method either via scripts or GUI that this could be accomplished?

---

### Post by Neobuntu on 2008-07-11
I'm not sure I know enough to advise you properly and so I state that up front. I have been contemplating the same type of thing. So far I thought RDP (nope I'm thinking RDC) was an application that just runs after an installed (Thick client) is already up and so it can act as if it is the other remote computer; sharing it's control. Kind of a Go-to-my-PC thing. 

On the other hand, I thought terminal serving was where one system is the server and the other client computers with zero OS, log in using the network searching PXE type connection from it's BIOS (or floppy or CD or whatever) and actually boots from the server (the latest upgraded OS.)

What I see; as the overall pros and cons are: Only one system needs upgrades and once upgraded, all the clients benefit automatically and time can be saved. Saving time is the biggest of deals.

Then there's the down side. The server must me up, all the time and you have one single point of failure (which perhaps you can plan for with fail over.) For home use, there may be issues of power usage, on not so efficient computers. The question becomes, is a low power appliance like server (NAS) better? Mainly, what about graphics? If you want to use your faster GPU (and there are some reasons besides games) then you may be out of luck with a client server model. Gigabit LAN devices may help but that's not a dirt cheap like 100BT NICs and routers.

I don't know, perhaps with PXE boot and no software on the client idea, a boot from the server could be made to utilize the fancy GPU on each client. It's kinda like the server is just the hard drive; for the client(s). 

On the other hand, if you wanted (or needed) off-line; thick client use without the Server (non-Internet, local user needs) as well, then using something like RDC in a window to control the server would be great, but restricted to limited graphics, through the LAN (or slower Internet). This (I think) is why most people use independent thick clients (regular computers), just share Internet on their LAN and then setup file and printer sharing, per seat.

Lately though, I've been meaning to set up the Squid proxy server or something, so that each of my home/office computers do not have to download the SAME darn upgrades. That's perhaps a step one. Where, hard-drive-less (or drive not used) regular computers on the other hand; used as just "thin clients" would obviously, be a much further step; in that direction.   

Someone who has tested all these, please help us.

---

### Post by bab1 on 2008-07-11
I would search on the terms "diskless linux install", if you are truly looking to create a "thin client".  I believe Sun's Sunray model is a diskless thin client.

That being said, a brief description of your project (not how you would connect it) might help.

For clarity:  RDP is a Windows terminal server thing.  See: [http://searchservervirtualization.techtarget.com/general/0,295582,sid94_gci1226989,00.html]("http://searchservervirtualization.techtarget.com/general/0,295582,sid94_gci1226989,00.html")  

There are other ways of addressing your data.

---

### Post by avtolle on 2008-07-11
I'm hoping this will help you: [https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall](https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall) 

There seems to be some links there which might also prove beneficial.

---

### Post by bab1 on 2008-07-11
Yes!  LTSP.  That will work.

See:
 [https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall]("https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall")

and
[https://help.ubuntu.com/community/ThinClientHowto]("https://help.ubuntu.com/community/ThinClientHowto")

---

### Post by cariboo on 2008-07-11
You should also have a look here:

[http://www.ltsp.org/](http://www.ltsp.org/)

The documentation is well written. I had success the first time I tried it, This was several years ago when the client side was a lot harder to set up.

Jim

---

### Post by mohenjo on 2008-07-14
Thanks for the replies everyone.  I'll have to do a little more looking into LTSP to see if that's what I'm looking for.

To give a little more detail into what I'm trying to do:

I've already got a Windows Server running that currently hosts Windows XP computers through RDP.  The computers that are running Windows XP however are starting to get sluggish, so users have to log into a slow Windows XP session first, then log onto the terminal server.

What I'd like to do is save those computers by formatting them with Ubuntu and set them up so that when they boot up, they connect to our terminal server (at the login screen for the server of course).

---

### Post by austinderrick2 on 2008-07-24
Just a thought, I'm by no means knowledgeable in thin client setup:


1. I know that you can modify the startup programs
(Via the graphical "System\Preferences\Sessions\Startup Programs"

2. tsclients can be run via the command line to connect to an RDP file, so add this command to the startup programs.

3. To auto login go to the System\Administration\Login Window under Security you can enable automatic login.



I would also trim down the startup items, as most of these are probably not needed to connect to RDP/VNC and it will speed up the boot time.

---

