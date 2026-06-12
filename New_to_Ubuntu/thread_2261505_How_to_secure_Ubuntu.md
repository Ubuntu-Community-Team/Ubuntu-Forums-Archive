---
title: "How to secure Ubuntu?"
date: 2015-01-19
forum: New to Ubuntu
---

### Post by Sam_Osman on 2015-01-19
What is the best way to secure Ubuntu after a fresh intall?  Are there any anti-virus or firewall programs that I should use? (like you would in a Windows machine?)

Do I need to change anything with the user accounts or file structure to make it more secure?  I am still new to Linux so I would like to know more about how to secure my machine after a fresh install.

- Sam

p.s.  I am not using the encryption option that was offered during installation because I don't think I need it, but also because I did not want to risk messing up the Windows partition.

---

### Post by kpatz on 2015-01-19
Everything you ever needed to know but were afraid to ask can be found here: [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by Sam_Osman on 2015-01-19
Thanks!  I will definitely bookmark and check it out.
 - Sam

---

### Post by fantab on 2015-01-19
There is no Anitvirus and you don't need one, however if you want to scan any Windows files before sharing with someone on Win PC then there are a few. [AV has no real use in GNU/Linux]("http://www.howtogeek.com/135392/htg-explains-why-you-dont-need-an-antivirus-on-linux-and-when-you-do/") ,as of now, .

Firewall, IMO is a must. Ubuntu ships with a default firewall, [UFW ]("https://wiki.ubuntu.com/UncomplicatedFirewall")(UncomplicatedFireWall), which is disabled by default. 
Enabling, starting and configuring UFW is very simple, [this guide]("http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/") (which is part of the above linked forumWiki) shows how to setup a simple firewall.
UFW is a cli front-end to [iptables]("https://help.ubuntu.com/community/IptablesHowTo"). 

I also use browser addons related to security and privacy. 

[Linux is NOT Windows]("http://linux.oneandoneis2.org/LNW.htm").

Edit: lined more info.

---

### Post by Sam_Osman on 2015-01-19
Hi fantab,

Thank you for your response!  I wil definitely check out and use the UFW guide that you had mentioned.  My further questions are:

1. Is the reason Antivirus is not necessary on GNU/Linux because malicious scripts cannot run without the super user password?  I am still new to Linux so I don't yet have a proficient understanding as to why you do not need antivirus on Linux.

2. Wich security and privacy addons do you use and recommen?

Thanks!
  --Sam

Edit: I just realized you included various links within your post that may already have the answers to my questions.  I opened them all in new tabs and bookmarked.  Will read in a few mins!  Thank you!

---

### Post by whitesmith on 2015-01-19
I think it's more an issue of market penetration. I was reading the other day that, of the world's 500 top supercomputers, Linux runs around 70% and Unix 30%. Windows runs exactly 1. On the desktop side, these numbers are turned around. I'd be surprised if Linux has captured much more than 3%. If you were a black-hat dude, would you write a worm for an OS that has so little penetration? 

Don't get me wrong. If you paid the doorman at a Chicago gold coast address to count passing Fords and Lamborghinis, the latter would number even less than 3%...but which would you rather drive?

---

### Post by grahammechanical on 2015-01-19
We also have AppArmor.

> [COLOR=#333333][FONT=Ubuntu Beta]AppArmor is a Mandatory Access Control (MAC) system which is a kernel (LSM) enhancement to confine programs to a limited set of resources. AppArmor's security model is to bind access control attributes to programs rather than to users. AppArmor confinement is provided via profiles loaded into the kernel, typically on boot. AppArmor profiles can be in one of two modes: enforcement and complain. Profiles loaded in enforcement mode will result in enforcement of the policy defined in the profile as well as reporting policy violation attempts (either via syslog or auditd). Profiles in complain mode will not enforce policy but instead report policy violation attempts.[/FONT][/COLOR]

[https://wiki.ubuntu.com/AppArmor](https://wiki.ubuntu.com/AppArmor)

AppArmor profiles have a special use in Ubuntu for phones and tablets. An app developer has to list all the permissions that his app needs. If the app is going to do something malicious then it will not be allowed in the Ubuntu phone app store. If the app is accepted for inclusion in the app store then an AppArmor profile is written for that app and from then on that app will be prevented from doing something bad to the OS.

AppArmor profiles have been used in Ubuntu desktop for more than 7 years. So, we get a degree of security from the use of AppArmor profiles. A lot of the technology being developed to make Ubuntu phones secure will eventually come into Ubuntu. Another example is the way phone apps run in a container and cannot access data on other parts of the system without user authentication. An email app might rightly need access to our contact list but a game should not need that access and will not be given it. 

If you use WiFi use encryption to make the connection to the router. If you are using a laptop then turn WiFi off when you are not using the internet, then Network Manager will not make connections to unsecured WiFi hotspots bringing with it the possibility of it connection a Wifi hotspot that is actually someone trying to sniff the connections that people are making.

Regards.

---

### Post by Frogs Hair on 2015-01-19
The Wiki is linked in my signature.

---

### Post by Sam_Osman on 2015-01-19
> **whitesmith said:**
> I think it's more an issue of market penetration. I was reading the other day that, of the world's 500 top supercomputers, Linux runs around 70% and Unix 30%. Windows runs exactly 1. On the desktop side, these numbers are turned around. I'd be surprised if Linux has captured much more than 3%. If you were a black-hat dude, would you write a worm for an OS that has so little penetration? 

Don't get me wrong. If you paid the doorman at a Chicago gold coast address to count passing Fords and Lamborghinis, the latter would number even less than 3%...but which would you rather drive?

Haha touche my friend!  Excellent analogy.

> **grahammechanical said:**
> We also have AppArmor.



[https://wiki.ubuntu.com/AppArmor](https://wiki.ubuntu.com/AppArmor)

AppArmor profiles have a special use in Ubuntu for phones and tablets.  An app developer has to list all the permissions that his app needs. If  the app is going to do something malicious then it will not be allowed  in the Ubuntu phone app store. If the app is accepted for inclusion in  the app store then an AppArmor profile is written for that app and from  then on that app will be prevented from doing something bad to the OS.

AppArmor profiles have been used in Ubuntu desktop for more than 7  years. So, we get a degree of security from the use of AppArmor  profiles. A lot of the technology being developed to make Ubuntu phones  secure will eventually come into Ubuntu. Another example is the way  phone apps run in a container and cannot access data on other parts of  the system without user authentication. An email app might rightly need  access to our contact list but a game should not need that access and  will not be given it. 

If you use WiFi use encryption to make the connection to the router. If  you are using a laptop then turn WiFi off when you are not using the  internet, then Network Manager will not make connections to unsecured  WiFi hotspots bringing with it the possibility of it connection a Wifi  hotspot that is actually someone trying to sniff the connections that  people are making.

Regards.


Sweet!  Thank you for the suggestion and details!  I will definitely bookmark and read/install when I have time (I'm working on homework atm).  I like the WiFi part a lot.  That sounds important because someone could potentially force a connection and do something malicious.  The details might be beyond the scope of this forum but it sounds like AppArmor would be a great solution in that situation because it sounds like it basically shuts off your NIC when you are not purposely using it.

The only question that comes to mind is:  how does ubuntu phone compare to android?  I've been using android ever since I got my first smart phone (although I do own an ipad), so is it worthwhile to switch to ubuntu phone?  What are the pros and cons?  It sounds like one pro could be the enhanced security.


> **Frogs Hair said:**
> The Wiki is linked in my signature.


Thanks Frogs Hair! I bookmarked all of the link in your sig.

---

### Post by kevdog on 2015-01-20
I definitely start with setting up a firewall first prior to jumping into AppArmor -- which is very complicated.  If you don't plan on running any server applications, you might not even need a firewall.  Firewalls in Linux are much different than Linux.  They don't block on an Application basis rather on a port basis.  The only exception to this is an application in development known as the Duane firewall which is an application based firewall for Linux. I tried compiling and running this about a month ago --- and its definitely in the alpha stage -- which means its definitely ready for prime time.

---

### Post by mastablasta on 2015-01-20
> **Sam_Osman said:**
> 
1. Is the reason Antivirus is not necessary on GNU/Linux because malicious scripts cannot run without the super user password?  I am still new to Linux so I don't yet have a proficient understanding as to why you do not need antivirus on Linux.


there are a couple of reasons. one is the one you mentioned. i.e. file permissions are handled differently in Linux. then there is a multi-layered security approach which is built form the ground up, and third one is that most antivirus scanners scan for windows malware which doesn't work on Linux. there are also no known viruses out in the wild. there were 7 or 8 viruses identified for Linux all can't hurt you as flaws are patched fast. 

which is another thing - super fast security patching. you might remember so called "heartbleed" hole. once confirmed patch came for servers and desktops in a matter of hours. recently windows had a similarly high vulnerability identified. it took them over 90 days to patch it. 

> **whitesmith said:**
> I think it's more an issue of market penetration. I was reading the other day that, of the world's 500 top supercomputers, Linux runs around 70% and Unix 30%. Windows runs exactly 1. On the desktop side, these numbers are turned around. I'd be surprised if Linux has captured much more than 3%. If you were a black-hat dude, would you write a worm for an OS that has so little penetration? 

Don't get me wrong. If you paid the doorman at a Chicago gold coast address to count passing Fords and Lamborghinis, the latter would number even less than 3%...but which would you rather drive?

well that's a stupid comparison. you only had a look at the desktop and complete4lly neglected the server market, the android market (ok this one is not really gnu/Linux,  and though they use kernel & gui is not really secured). so according to you if you were a black-hat dude you wouldn't be interested in hacking into for example googles servers? or I just read US navy uses Linux now. yeah windows drones got hacked... let's not even start with supercomputers. imagine a bot farm on them....

I don't think Linux has a majority in server market but it does have a large chunk of it. most internet does run on Linux. and when things get hacked it's usually the tools on server that are hacked not the OS itself. it hasn't managed to penetrate desktop market that is true. I don't think it will change soon (unless Valve's Steam box takes off). but hackers these days are much more interested getting into servers than individuals desktop. they attack desktop mostly so they can use it as a bot to attack server. 

I opened port 22 to the internet and started logging attacks. 8-10 per day (most coming from China). they tried to access the server.

---

