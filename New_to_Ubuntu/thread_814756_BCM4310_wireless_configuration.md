---
title: "BCM4310 wireless configuration"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by ratcatcher9292 on 2008-06-01
Hi! I've got the ubuntu live cd, trying to get my wireless internet to work. Have been searching threads but have problems with the apt-get commands because, of course, I have no internet. I downloaded my driver for my wireless ".exe" and ndiswrapper "1.53.tar.gz" to a flash drive. I'm pretty sure I have erased all old attempmts at ndiswrapper off my computer, so we can skip that step. What do I do now?

lspci output: 

09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller(rev12) 
0b:00. Network Controller: Broadcom Corporation BCM4310 USB Controller (rev01)

I've been using this tutorial: [http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)

Thanks!

PS: 

output for tar -xzvf ndiswrapper-1.53.tar.gz

"No such file or directory" 
The darn thing is on my desktop. Is too.

---

### Post by untermensch on 2008-06-01
My first advice would be drop the wireless chip =p

Although this link is very helpfull [http://ubuntuforums.org/showthread.php?t=779754&highlight=bcm4318](http://ubuntuforums.org/showthread.php?t=779754&highlight=bcm4318)

It is in replacement to updating your fwcutter. Some say the connection is flaky, weak, and goes out periodically. But I've not had a problem with it.

---

### Post by Unix_Slayer on 2008-06-01
> **untermensch said:**
> My first advice would be drop the wireless chip =p

Although this link is very helpfull [http://ubuntuforums.org/showthread.php?t=779754&highlight=bcm4318](http://ubuntuforums.org/showthread.php?t=779754&highlight=bcm4318)

It is in replacement to updating your fwcutter. Some say the connection is flaky, weak, and goes out periodically. But I've not had a problem with it.

Linksys adapters are easier to install. But the Broadcom's do work.

---

### Post by ratcatcher9292 on 2008-06-01
I'm so afraid of dropping my current wireless. Is that everybody's opinion, to do that? :-\


Linksys adapter - I want that. Have searched forum, no results....

---

### Post by untermensch on 2008-06-01
I never said they don't work. I'm using one right now. Honestly you just have to wade threw some instructions and messing up. But you'll get it. I'd definitely try the fwcutter first. Then try to update your ndiswrapper.

and if it's on your desktop make sure that your directory is your desktop.

---

### Post by ratcatcher9292 on 2008-06-01
hard to update your ndiswrapper when you have no internet connection...

I just need to know what to do next, here. Anyone know of a tutorial that ISNT based on a working internet connection?

---

### Post by Unix_Slayer on 2008-06-01
> **untermensch said:**
> I never said they don't work. 


No offense taken. I didn't mean that negatively. I know they work, it's just easier with the Linksys. My apologies.

---

### Post by Unix_Slayer on 2008-06-01
> **ratcatcher9292 said:**
> I'm so afraid of dropping my current wireless. Is that everybody's opinion, to do that? :-\


Linksys adapter - I want that. Have searched forum, no results....


Use what you feel you can use. Why knock yourself out when a Linksys USB adapter is easier to install with a WinXP .inf.

---

### Post by Unix_Slayer on 2008-06-01
> **ratcatcher9292 said:**
> hard to update your ndiswrapper when you have no internet connection...

I just need to know what to do next, here. Anyone know of a tutorial that ISNT based on a working internet connection?

Use the following link ==>[http://ubuntuforums.org/showthread.php?t=807979]("http://ubuntuforums.org/showthread.php?t=807979")

---

### Post by ratcatcher9292 on 2008-06-01
so I need a winxp.inf file for BCM3410?

---

### Post by untermensch on 2008-06-01
Sorry. Didn't mean to phrase that wrong. Personally I love linksys. My home router is one. The only reason I have the card I have is the computer was a gift. You could easily download the fwcutter to a jumpdrive, and put it on your computer, then install it.

---

### Post by Unix_Slayer on 2008-06-01
> **ratcatcher9292 said:**
> so I need a winxp.inf file for BCM3410?


No... Just follow what Pioneer states in this post ==>[http://ubuntuforums.org/showthread.php?t=807979]("http://ubuntuforums.org/showthread.php?t=807979")


And make sure you unplug your wired card after reboot, or you'll be scratching your head for hours.

---

### Post by ratcatcher9292 on 2008-06-01
dumb question - 

do you HAVE to start out with the ethernet cable plugged in if you don't have a wireless connection right away? Would like to install ubuntu on my pc upstairs....and router is downstairs. Kindof a pain.

---

### Post by Unix_Slayer on 2008-06-01
> **ratcatcher9292 said:**
> dumb question - 

do you HAVE to start out with the ethernet cable plugged in if you don't have a wireless connection right away? Would like to install ubuntu on my pc upstairs....and router is downstairs. Kindof a pain.


No you don't have to, but you won't get updates until your connected.

---

### Post by ratcatcher9292 on 2008-06-01
don't think i'll get any updates for a loooooong time, jeje

---

### Post by Unix_Slayer on 2008-06-01
> **ratcatcher9292 said:**
> don't think i'll get any updates for a loooooong time, jeje


[IMG]http://www.egameaddiction.com/posticons/mslugshoot.gif[/IMG][IMG]http://www.egameaddiction.com/posticons/bomb.gif[/IMG]

---

### Post by Pioneer5000 on 2008-06-01
Try the following link, look for my last post at bottom of page and try those instructions.
[http://ubuntuforums.org/showthread.php?t=807979](http://ubuntuforums.org/showthread.php?t=807979)

---

### Post by ratcatcher9292 on 2008-06-01
sudo aptitude update = "could not resolve security.ubuntu.com"

---

### Post by Unix_Slayer on 2008-06-01
> **ratcatcher9292 said:**
> sudo aptitude update = "could not resolve security.ubuntu.com"

Welp you hit that spot for the updates my friend. You need to be wire connected to do this.

---

### Post by Unix_Slayer on 2008-06-01
You could try this:

```
sudo apt-cdrom add
```

This will look on the rom for what it needs. But it might need to update headers on the kernel.

---

### Post by ratcatcher9292 on 2008-06-01
sudo aptitude purge b43-fwcutter - couldn't find any package whose name or descriptionn matched b43-fwcutter

---

### Post by Unix_Slayer on 2008-06-01
> **ratcatcher9292 said:**
> sudo aptitude purge b43-fwcutter - couldn't find any package whose name or descriptionn matched b43-fwcutter

You really need to be wire connected dude. One of those commands downloads the drivers for the wireless card. As ridiculous as that sounds.

[IMG]http://www.egameaddiction.com/posticons/frustrated.gif[/IMG]

---

### Post by ratcatcher9292 on 2008-06-01
will do sometime within the next week. Have to lug desktop downstairs, then move the wireless router down from the ceiling. 


Then use those three codes. Then unscrew my wireless antennae. Then reboot?

---

### Post by Unix_Slayer on 2008-06-01
> **ratcatcher9292 said:**
> will do sometime within the next week. Have to lug desktop downstairs, then move the wireless router down from the ceiling. 


Then use those three codes. Then unscrew my wireless antennae. Then reboot?

I know it's crazy. But I had worse. Like moving my Ap repeaters, routers, and hubs.... and moving them from floor to floor.

---

### Post by Pioneer5000 on 2008-06-01
> **ratcatcher9292 said:**
> will do sometime within the next week. Have to lug desktop downstairs, then move the wireless router down from the ceiling. 


Then use those three codes. Then unscrew my wireless antennae. Then reboot?

Sorry don't understand why you need to unscrew wireless antennae or maybe I'm just not picturing what you have to do to move computer downstairs correctly. But plain an simply all you have to do is connect to internet via Ethernet or U.S.B etc just for like 2 min's to run those 3 lines. Then reboot and plug everything (modem/router) back to how it was. Then once you have loaded back into Linux you should be able to detect wireless connection when you click on the top right hand corner icon. Well lets hope so.... Good Luck.

---

### Post by Unix_Slayer on 2008-06-01
> **Pioneer5000 said:**
> Sorry don't understand why you need to unscrew wireless antennae or maybe I'm just not picturing what you have to do to move computer downstairs correctly. But plain an simply all you have to do is connect to internet via Ethernet or U.S.B etc just for like 2 min's to run those 3 lines. Then reboot and plug everything (modem/router) back to how it was. Then once you have loaded back into Linux you should be able to detect wireless connection when you click on the top right hand corner icon. Well lets hope so.... Good Luck.


Maybe it's a whip antenna.  [IMG]http://www.tech-faq.com/emoticons/free-animated-emoticons/smiley_59.gif[/IMG]

---

