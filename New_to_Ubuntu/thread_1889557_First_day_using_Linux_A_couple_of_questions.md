---
title: "First day using Linux: A couple of questions"
date: 2011-12-01
forum: New to Ubuntu
---

### Post by powerchord84 on 2011-12-01
Hi all. I just got done installing Ubuntu to a virtual machine. This is my first serious attempt at trying to use Linux so here goes...
 
The first problem I have run into is no network access. I have the VM set up in bridged mode and I can ping the Ubuntu VM from my main machine (and others on the network) but I can't ping outside of my own box within Ubuntu. Does anyone have any suggestions with this?
 
 
 
Also, I was reading about some of the first things you should do when you do a fresh install...one that was mentioned:
 
*sudo apt-get update && sudo apt-get upgrade*
 
Apparently this updates your repositories...I was just wondering if someone could explain to me exactly what those are. If I'm not mistaken it has something to do with getting new software, right?
 
Thanks in advance!
pc

---

### Post by androssofer on 2011-12-01
> **powerchord84 said:**
> Hi all. I just got done installing Ubuntu to a virtual machine. This is my first serious attempt at trying to use Linux so here goes...
 
The first problem I have run into is no network access. I have the VM set up in bridged mode and I can ping the Ubuntu VM from my main machine (and others on the network) but I can't ping outside of my own box within Ubuntu. Does anyone have any suggestions with this?
 
 
 
Also, I was reading about some of the first things you should do when you do a fresh install...one that was mentioned:
 
*sudo apt-get update && sudo apt-get upgrade*
 
Apparently this updates your repositories...I was just wondering if someone could explain to me exactly what those are. If I'm not mistaken it has something to do with getting new software, right?
 
Thanks in advance!
pc

what vm software u using?

try openning a terminal window and typing

```
ifconfig
```

to get a terminal, click the ubuntu icon on the top left and search terminal (assuming ur on the new ubuntu with the unity UI)


repositories are hard to explain. so i will try my best. wont b 100% true, but will be enuf for you to get the general idea.

the easiest way to think of repositories is like the app store. in ubuntu u have an app store called 'software center' and in it is a list of almost all the software available for ubuntu. when u update ur repositories u update the list software center shows. so it updates which version is available, a new stuff thats out. and it also lets the software center know if their are updates for the software already installed. 

alot of this is done automatically for u, but its gd practice to run it urself on the first boot. 

also if u add new software sources to the repositories (some 3rd party sources arent in by default), the doing it updates the list to include their stuff.

thats how i understand it anyway...

---

### Post by techvish81 on 2011-12-01
> **powerchord84 said:**
> Hi all. I just got done installing Ubuntu to a virtual machine. This is my first serious attempt at trying to use Linux so here goes...
 
The first problem I have run into is no network access. I have the VM set up in bridged mode and I can ping the Ubuntu VM from my main machine (and others on the network) but I can't ping outside of my own box within Ubuntu. Does anyone have any suggestions with this?
 
 
 
Also, I was reading about some of the first things you should do when you do a fresh install...one that was mentioned:
 
*sudo apt-get update && sudo apt-get upgrade*
 
Apparently this updates your repositories...I was just wondering if someone could explain to me exactly what those are. If I'm not mistaken it has something to do with getting new software, right?
 
Thanks in advance!
pc

welcome to ubuntu forums and the exciting world of linux ¡¡;-)

if you really want to try ubuntu , vm installation will not give you exact idea or introduction of linux or ubuntu .

i suggest you to make a live usb or cd dvd of  ubuntu and try it (you will find the 'how to' at download page of ubuntu ). if you are interested and your hardware is supported , you can install it on your harddrive as dual boot with windows , it Will give you ample time to decide , whether to keep it , ditch it , ditch windows etc ... 
good luck .

---

### Post by MG&amp;TL on 2011-12-01
although a vm is fine for now., while you test. :)

You don't need to do the apt-get update bit, it's done automatically for you by update-manager, but it's *just* faster to do it by terminal, and it makes us look nerdy. Besides, I use my terminal more than my desktop.

Welcome. :)

Errr...repos. Think of the apt-get program as a download manager and record-keeper extroadinaire. It can download and install programs, it can remove them perfectly ( a lot better than the windows uninstaller, which leaves traces), and do a lot of other stuff too. There's a lot of frontends for apt, the most obvious and simple is the ubuntu software centre. I suggest you find your way around graphically first, then maybe have a dig at the terminal to unlock the true power of linux: [linuxcommand.org]("linuxcommand.org")

---

### Post by grahammechanical on 2011-12-01
When you want to, run Update Manager and click on Check and it will update the list of software and also notify you if there are any updates to download. This utility should automatically notify you of any security fixes. The recommendation that you speak of is so that you are running the most up to date Ubuntu.

I do not have a lot of experience in VMs. Just tried it once or twice. I think that you need to alter a setting in the VM itself. I was running the VM on Ubuntu and testing another Ubuntu in it, which is not the same as what you are doing. To get network access I think I had to set the VM to NAT. I cannot remember exactly. So, I most probably am wrong. But I am sure that it is the settings of the VM that will give the access to the Host's network adapter.

Regards.

---

### Post by oldos2er on 2011-12-01
Repositories are servers that contain software you can install. They are accessed through a package manager (or package manager front-end; there are several you can use).

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by powerchord84 on 2011-12-01
> **powerchord84 said:**
> Hi all. I just got done installing Ubuntu to a virtual machine. This is my first serious attempt at trying to use Linux so here goes...
 
The first problem I have run into is no network access. I have the VM set up in bridged mode and I can ping the Ubuntu VM from my main machine (and others on the network) but I can't ping outside of my own box within Ubuntu. Does anyone have any suggestions with this?
 
 
 
Also, I was reading about some of the first things you should do when you do a fresh install...one that was mentioned:
 
*sudo apt-get update && sudo apt-get upgrade*
 
Apparently this updates your repositories...I was just wondering if someone could explain to me exactly what those are. If I'm not mistaken it has something to do with getting new software, right?
 
Thanks in advance!
pc
 
 
I am using VMWare Player.  I did ifconfig, and IP address, net mask, etc are what they are supposed to.
 
To the other person suggesting a live boot:  I'd like to, but I am using my work computer...so right now, this is the only option I have, although I may give it a try on my personal laptop at home.
 
Thanks for all the explanations for the repositories...if only I could get network access now.  :(

---

### Post by powerchord84 on 2011-12-01
OK, I found something weird. If I do an ipconfig on my host machine, the below is the results I get. I see a couple of new adapters called VMnet and they're on the 192.168.x.x network which is odd, because all of our internal stuff is on 172.16.x.x. Maybe this is why I can't ping out of my VM (Ubuntu)?
 
Thanks in advnance.
 
[IMG]http://i1015.photobucket.com/albums/af278/powerchord84/e33c76b1.jpg[/IMG]

---

### Post by rollin77 on 2011-12-01
When you install Virtual box or VMware they add network interfaces to allow your VM machine to get on the internet.  I'm still learning Virtualbox/VMware, but it looks like your network settings for the VM machine is messed up.  If your windows laptop has a 172.16 address so will your virtual machine, unless I'm mistaken.  Did you configure the VMware network settings yourself, or was it done automatically?

Also, no need to cover up your IP addresses, those are all internal private IPs so it doesn't matter :P (just don't give out your public IP).   I would recomend dual booting Ubuntu on your home laptop/PC if you are serious about learning Linux.  VMware is a great way to try it out but then you are running Windows underneath which is a resource hog and pretty much dilutes the benefits of Linux being a much more efficient operating system.

---

### Post by androssofer on 2011-12-02
I would say ur work firewall is blocking it perhaps? its detecting a unknown comp on the network and therefore not allowing access to and from it. 

so as suggested earlier, switch the connection type in VMware from Bridge to NAT, as this will hide the ubuntu vm behind ur work comp and the firewall wont c it to block it. 

Not sure how to go about tht on VMware, more of a Virtual Box kinda guy ;-).

or it could be the ubuntu machine doesnt have the right ip settings for ur work network... 

NAT shud fix tht also...

live booting, dual booting, or using Virtual Box to run a VM on ur home machine might b a better option, as u will hav more control over it. 

ps:

Incase u dont know Virtual Box is free Virtualisation software, much like VMware, made by Sun (now owned by oracle). its awesome for home use as its a breeze to set up and configure and is cross platform

---

### Post by drmrgd on 2011-12-02
> **androssofer said:**
> I would say ur work firewall is blocking it perhaps? its detecting a unknown comp on the network and therefore not allowing access to and from it. 

so as suggested earlier, switch the connection type in VMware from Bridge to NAT, as this will hide the ubuntu vm behind ur work comp and the firewall wont c it to block it. 

Not sure how to go about tht on VMware, more of a Virtual Box kinda guy ;-).

or it could be the ubuntu machine doesnt have the right ip settings for ur work network... 

NAT shud fix tht also...

live booting, dual booting, or using Virtual Box to run a VM on ur home machine might b a better option, as u will hav more control over it. 

ps:

Incase u dont know Virtual Box is free Virtualisation software, much like VMware, made by Sun (now owned by oracle). its awesome for home use as its a breeze to set up and configure and is cross platform

+1 for switching it to NAT mode.  I'm running Ubuntu in VM Player at work too.  My work network is extremely restrictive, and I found that using Bridged mode actually kicked me off the net because it was an unrecognized / unauthorized machine on their net.  Running as NAT, though, uses all my host configurations, and I don't have any net problems at all (with a few very specialized exceptions).

---

### Post by powerchord84 on 2011-12-04
Well, as it stands, I am installing Linux on my home laptop as we speak.  I chose the Windows installer option as I'm not sure how to do any of my normal tasks in linux yet.

One of my big concerns is whether or not there is a way to install itunes and use it as my music player, sync iphone, etc.

Also, I use my laptop as a sort of media server to stream content to my Xbox 360...does anyone know if there is a way to do that using Linux?

Thanks in advance guys.

---

### Post by ubuntu27 on 2011-12-04
[Ubuntu Linux Resources]("http://www.psychocats.net/ubuntu/")

[URL="http://www.psychocats.net/ubuntu/itunes"]
iTunes in Ubuntu Linux[/URL]

---

### Post by powerchord84 on 2011-12-04
> **ubuntu27 said:**
> [Ubuntu Linux Resources]("http://www.psychocats.net/ubuntu/")

[URL="http://www.psychocats.net/ubuntu/itunes"]
iTunes in Ubuntu Linux[/URL]


Thanks for the links.

---

### Post by androssofer on 2011-12-05
i too am looking for a solution to xbox streaming, i tried ushare:

[http://www.themanfromdelmonte.co.uk/2010/02/09/stream-video-to-xbox-360-from-ubuntu-with-ushare/](http://www.themanfromdelmonte.co.uk/2010/02/09/stream-video-to-xbox-360-from-ubuntu-with-ushare/)

but it didnt work for me at all. the closest i got was this:

[https://help.ubuntu.com/community/Ps3MediaServer](https://help.ubuntu.com/community/Ps3MediaServer)

[http://code.google.com/p/ps3mediaserver/](http://code.google.com/p/ps3mediaserver/)

its built for ps3, but apparantly works for xbox. in my case i can see the computer on the network, but it wont connect or stream :-(.

maybe you can try them and see if they work for you.

---

### Post by powerchord84 on 2011-12-05
> **androssofer said:**
> i too am looking for a solution to xbox streaming, i tried ushare:
 
[http://www.themanfromdelmonte.co.uk/2010/02/09/stream-video-to-xbox-360-from-ubuntu-with-ushare/](http://www.themanfromdelmonte.co.uk/2010/02/09/stream-video-to-xbox-360-from-ubuntu-with-ushare/)
 
but it didnt work for me at all. the closest i got was this:
 
[https://help.ubuntu.com/community/Ps3MediaServer](https://help.ubuntu.com/community/Ps3MediaServer)
 
[http://code.google.com/p/ps3mediaserver/](http://code.google.com/p/ps3mediaserver/)
 
its built for ps3, but apparantly works for xbox. in my case i can see the computer on the network, but it wont connect or stream :-(.
 
maybe you can try them and see if they work for you.
 
I will definitely give them a shot either tonight or very soon and let you know the results.

---

### Post by androssofer on 2011-12-06
> **powerchord84 said:**
> I will definitely give them a shot either tonight or very soon and let you know the results.

any luck? 

as a side note: the main issues I hit where forwarding the right ports on my network... and firewall permissions on ubuntu. 

firestarter is what i use on ubuntu to manage the firewall.

---

