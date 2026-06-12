---
title: "Help requested with hacked Ubuntu 20.04 laptop"
date: 2022-07-09
forum: New to Ubuntu
---

### Post by bhubunt on 2022-07-09
Hi All,

I believe my internet Lenovo laptop with Ubuntu 20.04 has been compromised. Emails have disappeared in recent days; my chromium browser started wiggling up and down for several minutes, not vibrating, but moving up and down. And just half an hour ago, a rectangle appeared in the middle of the screen, somewhat similar to the rectangle in the picture below (i.e. the rectangle next to the terminal in the picture, except that it was solid and in the colors of my Ubuntu 20.04 OS, i.e. orange and purple. The terminal itself did not appear.) I could not take a screenshot of the rectangle as it flashed on the screen very briefly, but I immediately logged off and will reinstall Ubuntu on the Lenovo. In the meantime, I am using this windows laptop that I have sitting around as a back-up.

I am by no means an IT or hacking expert, so I can only guess how I was hacked based on the rectangle, which I believe may indicate that a remote connection was established, in other words, that I was hacked through remote desktop access. 

My question to you all: how can I prevent remote desktop access to my Lenovo laptop in the future? Are there any features I need to remove from the OS through the terminal? Could my laptop be hooked up to a server, even though I have no server set up myself? Can I check via the terminal if that is the case? 

Just in case you wonder: I periodically check my settings through the settings button on the top right side to make sure that the sharing button and sharing features are set to off and they always are. So whatever is going on is going on in the background and not visible to me, except for that strange rectangle that flashed up in the middle of my screen.

I connect to the internet via an ethernet cable. There are no no wifi or bluetooth modules in my Lenovo laptop. 

I hope I will get some serious suggestions and would like to thank you for your time.


P.S. Just to clarify: the picture below is *not* from my laptop. I just plucked it off the internet to give you an idea of the type of rectangle that appeared in the middle of my screen.


[https://c-nergy.be/blog/wp-content/gallery/u20-04/ssh-xrdp-23.png](https://c-nergy.be/blog/wp-content/gallery/u20-04/ssh-xrdp-23.png)

---

### Post by TheFu on 2022-07-09
It is much more likely that you have a failing GPU.
What I'd do is boot from an ubuntu install ISO flash drive and run in the Try Ubuntu mode for a few days. If you don't see graphics issues, then it is likely the GPU isn't the issue.
There could be data/program corruption due to other failing hardware like the disk controller or the storage device(s).  You can look at the SMART data on the storage device(s) for errors.
Those are the most likely issues.

If it truly has been cracked, then your entire network has probably been taken over and needs to be reworked with security as the main goal. Chances are that you aren't really prepared to do this properly and should hire some local people to address network design and to provide advice about keeping it secure and keeping smartphones and IoT stuff on other networks, never the same one used by your laptop/desktops.  This is an FBI recommendation.
Never trust a tablet or smartphone.
Never trust any IoT devices ... that includes household items that have networking, like streaming sticks, TVs, BluRay players, security cams, and the appliances with convenience apps.  They are all security risks for your laptop/desktops.

If your home router isn't updated monthly, I see that as a problem.  In the last week, some very important cryptography libraries which would be used by all routers and nearly every Unix desktop were updated.  Did your router get those patched?  Mine did.  I try to patch my router every week, but usually only see updated every 2 weeks.

If you are famous or a target by someone really interested in accessing your smartphone, there are many, many, more steps.  Hacking Android and iOS isn't nearly as hard as people think. At least it is getting a bit harder, but if they can get you to install an app that has been compromised, game over.

There is a "Basic Security" list with links in my signature. Go and read those.

---

### Post by bhubunt on 2022-07-10
Hi,
Thanks for the info. 

I will look into your recommendations and perhaps my modem might be compromised, but for now that's an unknown. I do not have a smartphone, don't use USB sticks etc. 

However, I would still like to get some practical advice from someone on the forum about how to set up OS Ubuntu 20.04 for better security. How can I prevent remote desktop access to my Lenovo laptop in the future? Are there any features I need to remove from the OS through the terminal to block screen sharing or data sharing for good? Can I check in the terminal to see if I am hooked up to a server? Or whether I am sharing data, a screen? I'd still appreciate some recommended code lines or links, as I look into the other issues over the next few weeks. 

I did sign in to livepatch, but believe I did so after the computer was compromised, so will do so again immediately after I reinstall Ubuntu 20.04.  For some reason, my laptop slowed down phenomenally whenever livepatch was on, so that it almost became unworkable. Not sure if that's to be expected.

Thanks again, folks.

---

### Post by TheFu on 2022-07-10
There are links in my signature above.  Read those.

There are lots and lots of ways to look for network connections on Unix/Linux systems.  But if you don't know what they mean/display, it isn't intuitively obvious what each is, so I suspect it is a waste of time to say use netstat or one of the five other tools for that purpose.  And network connections can be spun up at any time. They can even check whether netstat is being used and not make any connection, so what use is it to an average or new user?

Read the already provided links.  If this is really important, take a few online classes.

BTW, I did some work for an organization that has been actively targeted by one of the world's most prolific cracking govts.  While I could secure my home network by hiding, I was never able to secure the client's network, mainly because they were infiltrated by agents of that govt and nearly all of the users refused to keep their systems secure. Some were giving out wifi credentials to anyone who asked.  We'd change the wifi passphrase for different groups on the network and within 12 hours, the attackers would have returned.  But at least they were limited to the end-user network, not the admin or office staff network, so I'm calling that a "win".

---

### Post by bhubunt on 2022-07-12
Hi the Fu,
I reinstalled the OS Ubuntu 20.04 at a friend's house but now that I am back home, using my own modem, the Ubuntu rectangle reappeared, indicating continued remote access to my laptop over my lan connection. I could tell for days from disappearing emails and a mysterious public file in my file manager named "Documents" that my OS was compromised. I actually transferred some docs into that public file before I even noticed it was public and not mine... 

I will read your recommendations, Flu, but I am not a tech person. I do recall you saying in one of your previous posts, that there is little one can do unless one is an IT expert oneself. I am not working for a government agency like you, but I used to be a green activist, who peacefully opposed government projects because of their impact on the environment  (and I even successfully blocked one, as well as the financial investments....). You don't have to do much these days to be a target. 

The advantage with Ubuntu 20.04: I can at least notice that I am being hacked much more easily than on a Windows system.

---

### Post by Frogs Hair on 2022-07-12
Is the remmina remote desktop client enabled or installed ? If installed it should be disabled by default . This does seem more like a hardware related problem based on what you have described.

---

### Post by TheFu on 2022-07-12
People outside your LAN (over the internet) cannot access any remote desktop on Ubuntu unless you specifically open an inbound port on your router's firewall to the specific ubuntu system and aren't running the normal Ubuntu firewall with the default "DENY" rule.

If you aren't using a router to block stuff like this, that is a security failure on your part.

There are remote desktop tools, usually browser-based, which will reach out from your system to the internet and make remote connections possible through your router, but that is something you'd have to install yourself.  It isn't automatic and it isn't there by default.  I'm think of the built-in Chrome-browser remote stuff (why anyone would actually install Chrome-browser on their own system is beyond my understanding, why provide the largest internet spying and advertising company in the world with direct access to everything you do on the web? That seems foolish to me).

There are other tools ... I don't keep up with them, but stuff like LogMeIn and other remote access tools.  There's little need for those and in most corporations, installing them is a termination violation.

If you don't need remote access, don't install it and certainly don't enable it and disable the firewall which should prevent it by 99.9999% of attackers.  Clean everything on your network. Other devices can be used to get around your router-firewall, then it is free access to your Ubuntu system (or any other system on the same subnet not running a firewall).

These things should be in those links or common sense.

Do you trust your friend? Are they mischievous?  Do you have the default firewall in ubuntu enabled and blocking all inbound connections (at least!)?

---

### Post by bhubunt on 2022-07-12
Hi The Fu,
Thanks so very much for your lengthy and very helpful comments. 

First off, I don't have a router but only a DSL modem  that I got from my internet provider. However, based on your comments, I am now thinking of buying a router with a firewall as an extra protection and as a block. What type of router would be the best one to get for securing my Ubuntu desktop and should I avoid certain routers? 

Second, I have not installed remote access via my browser and wonder if there is any way I can check via the terminal if I have remote access related features activated in my Ubuntu 20.04 OS?  

Third, the rectangle that showed up on my computer means "wired connection" and looks like the rectangle on this image, except that it comes in the purple colors of basic Ubuntu 20.04: [https://www.gnome-look.org/p/1013056](https://www.gnome-look.org/p/1013056)

The problem is that I have had this very same rectangle show up on several other occasions in the past -- not just on this internet laptop but also on what I erroneously thought was an airgapped laptop.  There were other weird things that happened on that airgapped laptop, like unusually large download times as I moved really small files between folders. Then, luckily, another friendly and savvy person on this Ubuntu forum pointed out to me that I should set the UFW on my airgap to "deny outgoing"  to get the airgap secured. And, lo and behold, it worked: I have not encountered one other weird incident on the airgap since I changed the UFW to "deny outgoing."   

Perhaps getting a router with a good firewall might do the trick for the internet laptop?

P.S. Yes, on this internet laptop I have UFW activated and "deny incoming" on, but that's not enough, which is why I'm hoping the router will provide the firewall I am looking for?

---

### Post by TheFu on 2022-07-12
Be careful naming something "internet" or "backup", since those will likely lead you to believe they are true, when they are not. If there is a network connection of any sort, it can be on the internet, especially if it has wifi enabled.

All Ubuntu systems should have the firewall enabled, but YOU need to enable it.  Did you read those threads in the already provided links?  I'm positive some are about enabling and using ufw/gufw.  That's the extremely simplified firewall controller on nearly all Ubuntu systems.

Which router is best?  That's a loaded question, since we all have different needs and price limitations and skills.  Most consumer routers have just a few years of support (firmware updates), so as long as you know that buying a replacement is expected when those end, say, in 3 yrs from the first release of the router model, then that's fine.  Other brands have longer periods of support, but have a premium price (often, but not always).  Then there are generic routers that don't come with any firmware so we can load our own and configure it however we like.  This is more for network nerds, but those generic devices tend to have the best supported software.  I'm using a purpose-designed x86-64 device that has been my router for the last 7 yrs.  Every other week, it gets updates when I run the patching tool.  OTOH, it is extremely capable and more complex than the typical home router. I'm running OPNsense as the routing/firewall software on it.  Bought it new for $144 in 2015. At the time, it seemed expensive, until considering that it would likely last 10, if not 20 yrs.  The learning curve was steep even for me with 20+ yrs of Linux experience, since it isn't based on Linux, but on BSD.  The BSD firewall works only with inbound connections (the router is the center of the universe), on each interface, so knowing which traffic is coming into the router on which interface will determine if it is in for the LAN or out from the LAN.  The interfaces aren't hardcoded like they are in most home routers and any number of additional ports can be added to the hardware to manage everything from a small home network to a University with 50K devices.

For non-technical people, I tend to recommend they get a router from Asus because Asus is under and FTC mandate to patch after being sued by the USgovt for deceptive practices and losing.  The outcome of that lawsuit is that Asus routers have an external watchdog - that they pay for - which has made them possibly the best at providing industry leading security patches for most of their routers almost without regard to price.  Of course, just because a system has some capability, that doesn't mean we are smart enough to use it or know it exists.  Only study can provide that.

For people with intermediate network skills who don't want the fully custom solution of pfSense/OPNSense, there are microtik and ubiquity routers.  Both of these violated the GPL when their businesses were getting started. That may or may not be important to you.  For some people, it is enough reason to never give them money, ever.  Only you can decide. There are lots of youtube videos for each on the setup of these routers.

Due to COVID supply chain issues, all of these choices are still hard to find, but I suspect Asus will be the easiest, but I do not know.  I'm not exactly in the market for routers the last, er ... 7 yrs.

```
$ sudo ufw default deny incoming
```
is the minimum for each computer on your LAN.  Then you'll likely want to open specific ports, for specific needs, when the network requires it.  Outbound are allow with that default rule.
My LAN subnet is: 172.22.22.0/24. Most people would have a 192.168.1.0/24 subnet.  Anyway, to allow ssh into the computer (ssh, sftp, scp, rsync, x2go, sshfs and 20 other types of tools), use:

```
sudo ufw allow 25 from 172.22.22.0/24
```
I think that's the command, but it might be wrong.
This is what my samba server rules look like.
```
$ sudo ufw status
Status: active

To                         Action      From
--                         ------      ----
22/tcp                     LIMIT       Anywhere                  
4949/tcp                   ALLOW       172.22.22.0/24            
Samba                      ALLOW       172.22.22.0/24            
```

* 22/tcp is ssh and I have it setup to be accessed over the internet with ssh-keys. No passwords.  This is useful when I'm traveling.  Also, any brute force connection attempts are caught by a tool called "fail2ban", which will add a firewall rule on the system to block the offender after more than 3 failed attempts.  You see the "LIMIT"?  That's another option to ufw to prevent too many attempts too quickly. It is good at slowing down attackers using thousands of systems around the world to attack that specific system.  They don't know it doesn't allow passwords for authentication and it is nearly impossible for them to provide a valid ssh-key for access, unless they grab them from my portable devices AND know the unlock code to open the ssh-key.
* Samba connections are allowed from anywhere on the subnet.
* 4949/tcp is for a systems monitoring tool that pulls data every few minutes to a central server on the same LAN.

```
sudo ufw status verbose
```
shows more details, but the same basic information.

I should point out that there are inbound attempts that sailed right passed my old consumer router and were only stopped by the firewall on each computer.  There are many tricks used by advertising/spy companies to trick our WAN firewalls into allowing connections that shouldn't be allowed. It is really scary.  But the firewall on the computer 100% knows which connections it opened and which it didn't, so it can be more brutal for unrequested inbound connections that a router device cannot know.

---

### Post by pantazi on 2022-07-13
[COLOR=#000000]'All Ubuntu systems should have the firewall enabled, but YOU need to enable it.'  (TheFu)

I'm sure new Ubuntu users are not aware of this, I wasn't and have done extensive reading, thank you.


[/COLOR]

---

### Post by TheFu on 2022-07-13
> **pantazi said:**
> All Ubuntu systems should have the firewall enabled, but YOU need to enable it.'  (TheFu)

I'm sure new Ubuntu users are not aware of this, I wasn't and have done extensive reading, thank you.

It used to be that Ubuntu wasn't installed with any network services listeners enabled, but that has changed when avahi and a few other "convenience" services were added. Since that time, enabling some firewall rules has been necessary, especially if someone has used remote desktop tools.  I've never used the remote desktop that was added to Ubuntu because the underlying protocol is so very insecure.  There are times when a remote desktop is needed and everything cannot be performed using just an ssh connection - perhaps 0.001% of the time.  For that, there is the NX protocol which uses ssh for authentication and any other ssh blocking/filters/security are used.  ssh is the core method of system-to-system communications for all computers, yet, somehow, Windows people have barely heard of it and most Windows end-users have never heard of it.

ssh is one of the few things that are both more convenience AND more secure.  When I try to think of any others, none come up.  Security always reduces convenience, except where ssh is used.
Of course, if the ssh-server is installed on a system (I install "ssh" which is the client and server on all my systems), then a firewall rule is needed to allow inbound connections, as I've shown above. The convenience that ssh access provides me for remote management and access to different systems is just so great that I wouldn't imaging NOT installing it.

---

### Post by bhubunt on 2022-07-14
Hi The Fu,
Thanks for your very helpful comments.

I have an update about the hacking: about half an hour ago, as I was about to answer you, I was hacked again. The rectangle indicating remote access to my laptop reappeared. (Here again is the link to show you what the rectangle looks like, except that it is purple: [https://www.gnome-look.org/p/1013056](https://www.gnome-look.org/p/1013056) )

I immediately pulled out the lan cable and logged off, hoping to get rid of the hacker as I previously thought I was being hacked over my lan connection. However, when I rebooted the system and left the lan cable unplugged, the hacker was _still_ on my laptop. I know because I opened LibreOffice and the document at the top said "Libre Office (remote)." 

I made a picture of the "LibreOffice (remote)" page and will post it on this forum soon, as evidence. 

In fact, a few months ago, I contacted accessnow.org about my situation, as this has been going on for a while, and they encouraged me to collect evidence through screenshots. While I have been unable to make a screenshot of the rectangle appearing, I photographed the "Libre Office (remote)" with a camera that has no wifi and hope to post it soon.  

I just read this link about Libre Office remote ([https://help.libreoffice.org/6.2/he/text/shared/guide/cmis-remote-files.html](https://help.libreoffice.org/6.2/he/text/shared/guide/cmis-remote-files.html)), but I do not have a server set up.

Now my question to you Flu or to anyone else with technical knowledge: how could this hack be happening? If it is not over lan, then it's probably over wifi, even though my wifi is off (in fact the wifi and bluetooth modules were removed from my Lenovo thinkpad laptop.) 

Is there anyone who can tell me how I can disable the remote desktop tools on my Ubuntu 20.04 OS? 

I found this link about Remote Desktop Hacking but it is a commercial site about windows, businesses and servers, so no help. [https://www.imperosoftware.com/blog/rdp-hacking-how-hackers-enter-remote-desktops-how-to-be-safe/](https://www.imperosoftware.com/blog/rdp-hacking-how-hackers-enter-remote-desktops-how-to-be-safe/)

I have no server, just a laptop with Ubuntu 20.04. And a DSL modem provided by my regular internet provider, just basic internet access. I never entered a wifi password in my laptop, as the wifi module of my laptop was removed while I was present.

---

### Post by TheFu on 2022-07-14
If there isn't any network connection, then the system isn't being remotely hacked.  Period.

BTW, please use my correct handle here.

---

### Post by bhubunt on 2022-07-15
Hi the Fu,
I corrected all incorrect refs to your handle. Sorry about that. 

But, yes, there _is_ a network connection. My laptop is making some kind of a network connection, otherwise I could not get hacked. How it is done, I honestly don't know. Whether it is a connection to my own network, I don't know. I am not a tech person (but I am also not a complete dope ;-)). Also, keep in mind that my Ubuntu 20.04 OS on my Lenovo laptop is still open to network connections, as I can't set the firewall UFW to "deny outgoing." 

As I mentioned earlier, I have two laptops, one for research on the internet, the other one an airgap. And I used to have the same breaches (i.e. the rectangle for "wired connection"; the "Libre Office remote" etc) on my "so-called" airgap laptop. So-called because, obviously, it wasn't really airgapped, it was still being breached. Finally, thanks to another helpful forum user on another thread (I believe it was Psychohermit) those breaches stopped because I set the UFW on the airgap to "deny outgoing."  That's why I appreciate very practical advice. I can't do anything with general statements, but I do appreciate very hands-on concrete suggestions, such as how I can check if I have remote access tools on my Ubuntu 20.04 OS activated or not.

In searching the internet, I found this helpful wiki page about how to detect remote access to a computer, but it only lists features for windows and mac: [https://www.wikihow.com/Detect-a-Remote-Access-to-My-Computer](https://www.wikihow.com/Detect-a-Remote-Access-to-My-Computer)

Does a similar list exist for Ubuntu -- I mean an easy to use list, like the wikihow one, with helpful screenshots that takes people step by step and in non-tech language through all necessary steps?

---

### Post by TheFu on 2022-07-15
Perhaps installing an IDS will help? [https://www.howtoforge.com/intrusion_detection_with_ossec_hids](https://www.howtoforge.com/intrusion_detection_with_ossec_hids)

---

### Post by bhubunt on 2022-07-22
Hi The Fu,
Thanks as always for your helpful replies. I should also add some info to my previous post: I forgot to close a number of ports on reinstalling 20.04, including port 21/tcp. That still doesn't explain how a network connection with my laptop was possible, unless perhaps there's a hidden (wifi) network that my laptop connected to?

Just to follow up on the IDS suggestion you made: the link you provided explains how to install an IDS on your server. I don't have a server. I only have a laptop and a company-provided DSL modem. Can you specify how the IDS would be relevant in my case?

---

### Post by TheFu on 2022-07-22
> **bhubunt said:**
> Hi The Fu,
Thanks as always for your helpful replies.

Just to follow up on the IDS: the link you provided explains how to install an IDS on your server. I don't have a server. I only have a laptop and a company-provided DSL modem. Can you specify how the IDS would be relevant in my case?

"Intrusion Detection System"  - You claim there are intruders.  Detecting them seems like a good idea.  Did you ever enable a router between the modem and computers?  If the company provide device truly is just a modem and you aren't very technical, please, please, please, get a router to place between the computer and the modem.  Please.

---

### Post by bhubunt on 2022-07-22
Hi the Fu,
I am indeed not very technical, will do as you say and get a router. However, I still have a practical question: I have had the intrusion happen, even when my modem was unplugged and thus completely switched off. As mentioned in the previous post, I am wondering if there might be a hidden wifi network. Let's keep this speculative for now, as I cannot prove that there is such a hidden network in my home. But would a router still help protect against intrusion via a hidden network? I think not, as the router is about protecting the traffic between the modem and the computer. Correct?

---

### Post by TheFu on 2022-07-22
A hidden network doesn't mean anything unless you connect to it.
You're 5000x more likely to be hacked over bluetooth.  I hope you've disabled all bluetooth on all your devices. Completely disable that.

---

### Post by bhubunt on 2022-07-27
Hi The Fu and others,
Bad news. Yesterday and just 10 minutes ago, I experienced two more hacking attacks. Just now, the breach happened on my airgapped computer, which has *no* bluetooth or wifi modules anymore. These were removed in my presence and I have had the laptop in constant possession ever since then (in my backback that I take everywhere). I also unplug the modem when I work on my airgap.  Furthermore, the UFW on this airgapped laptop is set to deny everything, incoming and outgoing.

 Once again the rectangle signaling a remote connection to my airgap appeared in the middle of the screen. It looks like this, but purple: 
[https://www.gnome-look.org/p/1013056](https://www.gnome-look.org/p/1013056)

At the time, my airgap was connected via usb to my small printer which predates wi-fi, in other words, the printer too has *no* wi-fi. (However, unlike my airgapped laptop, which I take everywhere in my backpack, my printer has been sitting at home.) Because I have a great Lenovo thinkpad, I immediately pulled out the removable battery to disrupt the connection. But the hacking can clearly bypass Ubuntu's UFW, with all ports closed. I am no technician, so cannot speculate about how a connection is established, but there is still an *unused* lan module in the airgap.

Yesterday, the rectangle appeared on my other Lenovo laptop, which I use on the internet. Both laptops have the same Ubuntu OS 20.04. I should explain that I started using two different Lenovo laptops, both from the Thinkpad series, one for use on the internet, the other as airgap, after a spate of hacking attacks in the past. As mentioned earlier in this thread, I used to be a green (peaceful) activist, and believe this is a sophisiticated government type of hacking. 

Until recently, I was able to work quietly on my airgap for months on end, but just this morning the laptop was breached, despite all ports, incoming and outgoing locked. (For the Fu: I do not use any USB sticks on the airgap anymore, thanks to your earlier warnings in other threads, and the OS was reinstalled recently.)

I don't suspect anyone can help me protect my airgapped Lenovo and its Ubuntu OS any better than they already are. This is a case of force majeure. However, I am reporting this here on the Ubuntu Forum so that other Ubuntu users and perhaps developers can benefit from my experiences.

---

### Post by rsteinmetz70112 on 2022-07-27
To ask a few simple dumb questions:
 
[LIST=1]
[*]When you had you laptop at your friends did the odd behavior continue?
[*]If you disconnect your laptop from your DSL modem does the behavior stop?
[*]Are you connecting to your modem by a wire or via WiFi - if by WiFi try connecting via ethernet and turning off the WiFi.
[/LIST]

---

### Post by TheFu on 2022-07-27
If the system is truly air-gapped, no firewall is needed.

I suspect you don't really know what you are seeing.  It wouldn't be hard to swap the root window background periodically to make it appear that something remote is happening, when nothing is.  To someone who doesn't know how to make things happen automatically, this could easily appear like a remote hacking session, when that was setup months - or years - prior.  

If you have wiped everything from the system and reinstalled the OS, yet still see these things without the computer ever being connected to a network, then it is time to look at the hardware (HDD/SSD/BIOS) for pre-installed cracking tools.  If you connect the box to any network, like your home network, it is easy for other devices also connected to that LAN to gain access. Do you have any IoT devices?

It all starts with securing everything on the LAN, especially the router.

OTOH, only you know who the likely attacker could be.  I've walked into random office supply stores, picked out a computer in a box and left with it to ensure that no specific hardware target attack could be inserted during shipping.  I suspect less than 0.000001% of the people in the world need to be worried about the supply chain and delivery interception.  I'd been doing work for people in excel who the largest known hacking country routinely targeted (the country doesn't like their messages), so being cautious was necessary.  Additionally, I think the country had a few spies working inside the organization and the organization wasn't particularly IT savvy, so attempting to train everyone about data security was a wasted effort.  I ended up splitting the network up and normal people had access to almost nothing except the internet.  The 5 office workers were where I spent my time and setup everything for their needs, made it clear they shouldn't share that access outside those specific 5 people, and it seemed to work for about a year.  I'd moved on and they didn't contract with me for maintenance beyond the 1st year, so I don't know what really happened, but I suspect the office systems weren't locked and the spy inserted a USB drive which created an exfiltration stream to the country.  I don't know if that was continuous or cached, encrypted, then burst sent daily, weekly, or when a specific flash drive was inserted.  My access to the router was cut which could have been used to see these things.  The router was kept in a locked room, away from public access.

BTW, I worked on air-gapped networks for 3 yrs. They are a pain.  Even simple things like password management was a hassle, since there were different air-gapped networks, each with different login credentials and different mandated periods for password changes.  Rather than remember all the different rules (writing them down was a federal offense), Every 28 days, I'd spend 4 hours visiting each network and changing my different credentials.  Sometimes security trumps convenience.  We know today that changing passwords that often doesn't aid security, but is was standard at the time.  I didn't want to go to jail, so I followed their rules.

I've been hacked 3 times over the decades.  All through some sort of network connection.  Only once did I need to wipe everything and start over, but I knew I was going to be in a hostile environment and planned that step already.  After the wipe and reinstall, nothing else 'hacky' ever happened, so the hardware wasn't impacted.

---

### Post by TheFu on 2022-07-27
For your continued paranoia: [https://arstechnica.com/information-technology/2022/07/researchers-unpack-unkillable-uefi-rootkit-that-survives-os-reinstalls/](https://arstechnica.com/information-technology/2022/07/researchers-unpack-unkillable-uefi-rootkit-that-survives-os-reinstalls/)
> Researchers have unpacked a major cybersecurity find—a malicious UEFI-based rootkit used in the wild since 2016 to ensure computers remained infected even if an operating system is reinstalled or a hard drive is completely replaced.

The firmware compromises the UEFI, the low-level and highly opaque chain of firmware required to boot up nearly every modern computer. As the software that bridges a PC’s device firmware with its operating system, the UEFI—short for Unified Extensible Firmware Interface—is an OS in its own right. It’s located in an SPI-connected flash storage chip soldered onto the computer motherboard, making it difficult to inspect or patch the code. Because it’s the first thing to run when a computer is turned on, it influences the OS, security apps, and all other software that follows.


The lesson here - patch your firmware from reputable sources - there's only 1 - the motherboard vendor. If the vendor has been corrupted, there's nothing we can do if we use UEFI booting.  I have UEFI booting on 1 laptop and nowhere else.  Mainly because I was lazy and didn't see the point of using UEFI on systems that get rebooted every other week, at most.

---

