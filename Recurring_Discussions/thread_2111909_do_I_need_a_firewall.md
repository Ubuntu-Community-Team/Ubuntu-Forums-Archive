---
title: "do I need a firewall?"
date: 2013-02-03
forum: Recurring Discussions
---

### Post by Old Jimma on 2013-02-03
Hi Ubuntu Community:

I hope this is the place to ask stupid questions!

Since it seems that everybody is hacking everybody else these days, I wondered whether I need a firewall.

The purpose of this email is to find out whether I do, and to learn about what I should take into consideration when setting up Firestarter or gufw.

:-k

I'm just an old geezer, so I'm asking the community of smart young folks who know the answers. However, I definately want the "old Ubuntu" guns to weigh in, if they want!

:)

Currently, I've got only 2 machines on my home network, both connected to my home's router.

The first is an "Ubuntu Machine" that does many tasks, including sending receiving email thru T-bird, and also as a MythTV frontend and backend. This machine holds the "family jewels," like  
[LIST]
[*]documentation of scraps of communication with the ubuntu forums that I couldn't live without, and
[*]letters from Aunt Harriet. I'd just die if I lost those.
[/LIST]

:)

All of those treasures are backed up every week to 2 other hard drives.

The second machine is a 6 year old iBook (ugh!), that occasionally connects with the "ubuntu machine" to access recorded music, and other stuff.

In 2 months, I will add a third machine to my network. It will be a Mythbuntu HTPC that will serve almost exclusively as a frontend to play TV programs stored on the first "ubuntu machine" described here. My guess is that there will be some sort of "port usage" on the Ubuntu machine when I do that. The third Mythbuntu HTPC will not have a hard drive, just a mobo with processor and memory, mythbuntu loaded on an adequately sized SSD, and a wired connection to our home's router.

I think that there could be some "port usage" from the 2nd and third machine on my "ubuntu machine." For example, the Myth backend on my "Ubuntu machine" has 2 ports that are specified in its MythTV backend configuration.

However, that's just a guess, because when people from my generation think about "ports," they think about 
[LIST]
[*]Barcelona,
[*]Murmansk,
[*]the famous port of Savanah, GA; and
[*]a sweet desert wine that people from my generation drink right after dinner.
[/LIST]

;)

So, my questions to the forum are:
[LIST=1]
[*]"Do I need a firewall to protect the family jewels?", and
[*]"How should I take into account the various ways my iBook and third computer (Mythbunt frontend) in setting up Firestarter or fugw?"
[/LIST]

Sorry about my ignorance. I'm just an old man with not very much hair left.

:)

Thank you!
Old Jimma from the Old Country

---

### Post by Frogs Hair on 2013-02-03
See the security sub forum and read the stickies. [http://ubuntuforums.org/forumdisplay.php?f=338](http://ubuntuforums.org/forumdisplay.php?f=338)

---

### Post by Sef on 2013-02-03
> I hope this is the place to ask stupid questions!



The only stupid question is the one that is not asked; therefore, since you asked, your question is not stupid.  Questioning is learning, and learning is always smart.

---

### Post by 3rdalbum on 2013-02-03
Your router already contains a NAT firewall that will protect the whole network from incoming connections, without making your home network more difficult to manage.

You don't need an additional firewall. It would just make things more difficult without adding any security benefits.

---

### Post by sudodus on 2013-02-03
> So, my questions to the forum are:
1. "Do I need a firewall to protect the family jewels?", and
2. "How should I take into account the various ways my iBook and third computer (Mythbunt frontend) in setting up Firestarter or fugw?"


1. Not necessarily (in the computer), because your LAN is behind a router, and it probably has a firewall. Check that there is a firewall in the router, and that it is properly set to deny everything, that is not necessary for you. I guess you need to browse the internet, email and some chat or voip program, but nothing fancy like connecting to your computer from the outside. For more details and security, read this link

[[COLOR="Red"]https://wiki.ubuntu.com/BasicSecurity[/COLOR]]("https://wiki.ubuntu.com/BasicSecurity")

I would add that today you should be aware of 'new' threats via normal browsing, so I recommend that you use the add-on ***NoScript*** in Firefox. You should also be careful using java runtime (not only java-script).

2. It depends. Without firewall in the ubuntu computer, no problems ...

---

### Post by JKyleOKC on 2013-02-03
> **Old Jimma said:**
> Currently, I've got only 2 machines on my home network, both connected to my home's router.

--snip--

So, my questions to the forum are:
[LIST=1]
[*]"Do I need a firewall to protect the family jewels?", and
[*]"How should I take into account the various ways my iBook and third computer (Mythbunt frontend) in setting up Firestarter or fugw?"
[/LIST]

Sorry about my ignorance. I'm just an old man with not very much hair left.Since you're running behind a router, you don't really need any firewall at all on the computer side since the router itself will reject any unsolicited connection attempts unless you take pains to let it do so.

However a firewall to prevent anything from "calling home" is always nice to have; the one time (years ago on Win95) that I got an actual virus infection, the outgoing firewall was what alerted me to the situation. I'd recommend "gufw" for this; it's already installed but not enabled. A single command, one time, to enable it is all you need to do. Avoid FireStarter; it hasn't been maintained for years. None of these need to be started every time you power up; they remember the settings and restore them automagically...

And I'll bet that you're at least 10 years younger than me...

---

### Post by Paqman on 2013-02-03
> **Old Jimma said:**
> a sweet desert wine that people from my generation drink right after dinner.

Also quaffed heartily by gunners and armourers of all generations, generally in lieu of food. Which is why you often get pictures of artillery on the bottle.

> 
How should I take into account the various ways my iBook and third computer (Mythbunt frontend) in setting up Firestarter or fugw?"


I agree with the advice above, you don't need a software firewall on your individual machines. However, if you were to use one Firestarter is no longer maintained and I wouldn't use it. If you've been reading advice that suggests Firestarter as a firewall it's probably years out of date and should be treated with suspicion.

---

### Post by Bucky Ball on 2013-02-03
*Thread moved to **Security Discussions**.*

---

### Post by Old Jimma on 2013-02-03
JKyleOKC:

If you are not older than rocks, then you are not older than I am.

Old, old Jimma, the Elder

---

### Post by samiux on 2013-02-03
> **Old Jimma said:**
> Hi Ubuntu Community:

I hope this is the place to ask stupid questions!

Since it seems that everybody is hacking everybody else these days, I wondered whether I need a firewall.

The purpose of this email is to find out whether I do, and to learn about what I should take into consideration when setting up Firestarter or gufw.

:-k

I'm just an old geezer, so I'm asking the community of smart young folks who know the answers. However, I definately want the "old Ubuntu" guns to weigh in, if they want!

:)

Currently, I've got only 2 machines on my home network, both connected to my home's router.

The first is an "Ubuntu Machine" that does many tasks, including sending receiving email thru T-bird, and also as a MythTV frontend and backend. This machine holds the "family jewels," like  
[LIST]
[*]documentation of scraps of communication with the ubuntu forums that I couldn't live without, and
[*]letters from Aunt Harriet. I'd just die if I lost those.
[/LIST]

:)

All of those treasures are backed up every week to 2 other hard drives.

The second machine is a 6 year old iBook (ugh!), that occasionally connects with the "ubuntu machine" to access recorded music, and other stuff.

In 2 months, I will add a third machine to my network. It will be a Mythbuntu HTPC that will serve almost exclusively as a frontend to play TV programs stored on the first "ubuntu machine" described here. My guess is that there will be some sort of "port usage" on the Ubuntu machine when I do that. The third Mythbuntu HTPC will not have a hard drive, just a mobo with processor and memory, mythbuntu loaded on an adequately sized SSD, and a wired connection to our home's router.

I think that there could be some "port usage" from the 2nd and third machine on my "ubuntu machine." For example, the Myth backend on my "Ubuntu machine" has 2 ports that are specified in its MythTV backend configuration.

However, that's just a guess, because when people from my generation think about "ports," they think about 
[LIST]
[*]Barcelona,
[*]Murmansk,
[*]the famous port of Savanah, GA; and
[*]a sweet desert wine that people from my generation drink right after dinner.
[/LIST]

;)

So, my questions to the forum are:
[LIST=1]
[*]"Do I need a firewall to protect the family jewels?", and
[*]"How should I take into account the various ways my iBook and third computer (Mythbunt frontend) in setting up Firestarter or fugw?"
[/LIST]

Sorry about my ignorance. I'm just an old man with not very much hair left.

:)

Thank you!
Old Jimma from the Old Country

To protect your network from attacks, only firewall is not enough.  You need an [Intrusion Prevention System (IPS)]("http://en.wikipedia.org/wiki/Intrusion_prevention_system") which can block/prevent the attacks (based on rules/signatures) from the real time.

In the old days, IPS is very expensive and the performance is not good.  However, nowadays IPS can be setup by yourself free of charge, which is an Open Source software, namely Suricata.

Suricata can be act as gateway (you need 3 network interfaces, 2 are bridged and one for management purpose) which is also known as network-based.  It can be also installed to the servers, desktops and laptops which is known as host-based.

I have two articles for setting up Suricata in host-based for [servers]("http://samiux.blogspot.com/2013/01/howto-suricata-on-ubuntu-1204-lts-server.html") and [desktops]("http://samiux.blogspot.com/2013/01/howto-suricata-on-ssd-and-ubuntu-1204.html").

The performance of the Suricata is quiet good on an Intel Atom D510 ITX machine which is hosting a web server.

Samiux

---

### Post by Old Jimma on 2013-02-03
Y'all:

Thanks for your replies! I should have guessed that alot of other people had wondered about whether they needed a firewall.

To check and improve the security of my system, here is what I did:

1. I looked at my router (192.168.1.254), and verified that its firewall was ON.

2. I added NoScript, Click&Clean, and Adblock Plus, and Better Privacy (same function as Click&clean) to my firefox addons (I had already had some of these installed!)

3. I got educated about Firestarter (wow! stay away from that!)

4. I read some of the web pages recommended. Some where easier for Old Jimma to read than others. Some were easier to read and dispelled some misconceptions that everybody should be disabused about.

5. I read samiux's advise and will study it more thoroughly!

6. I'm going to look at gufw more closely, and hope that my router firewall will protect me.

7. I'm going to encrypt all of my precious letters from Aunt Harriet.

Thanks for your replies!

Very Old Jimma from the Oldest Country in the Galaxy

---

### Post by JKyleOKC on 2013-02-03
> **Old Jimma said:**
> JKyleOKC:

If you are not older than rocks, then you are not older than I am.

Old, old Jimma, the ElderWell, that depends on the rock, doesn't it? Out in Hawaii there's a mountain constantly making new ones...

I'm a quarter of the way into my ninth decade and still going...

---

### Post by Bucky Ball on 2013-02-03
> **Old Jimma said:**
> 

5. I read samiux's advise and will study it more thoroughly!



Complete overkill for a bog standard netbook/laptop/desktop setup. What you've done already is more than enough and more than I've had installed for the last six years. Never had an issue ...

Your main concern really is if you're swapping files/emails between your Ubuntu install and a Windows install. Water off a duck's back to Ubuntu but you can easily pass an infected file to a Win machine without being aware of it. This is where extra security may be relevant.

---

### Post by conquerorodueko on 2013-02-04
OLD JIMA

Do you need a firewall?
Simple answer: It depends on your needs and use.

If it is a laptop that you use on public [wifi] - certainly you do because the internal network is already compromised. I would strongly recommend looking into [ufw] manually and tailoring it to your needs.

OH and one last thing: STAY ABSOLUTELY CLEAR FROM FIRESTARTER.

Sadly i would agree with [samiux] that what you need is an [intrusion prevention] system however you do not need to go that complex [serious overkill]. [ufw] if properly configured can accomplish something close. YOU WILL JUST HAVE TO TUNE YOURS.... TAILOR IT TO FIT.

---

### Post by 3rdalbum on 2013-02-05
You do NOT need an intrusion detection system. An IDS is only useful if you are opening ports in your firewall, which you are not doing.

It's like wearing a knife-proof jacket when standing behind a wall that nobody can get over. 

Also, I see from your other thread that you turned on UFW with your router firewall on, and now are having problems with your home network (as I said would happen in my post). Removing the GUFW package will not turn off the firewall. Reinstall GUFW and turn off the firewall. GUFW is merely a way of talking to the firewall built into the Linux kernel. Ripping off a man's clothes will not kill him.

---

### Post by Zill on 2013-02-05
> **conquerorodueko said:**
> ...If it is a laptop that you use on public [wifi] - certainly you do because the internal network is already compromised. I would strongly recommend looking into [ufw] manually and tailoring it to your needs...
This is an interesting point!

My PCs are behind a NAT router and so I have always understood that there was no need for a software firewall to be installed on the PCs.

However, with a laptop that *may* be used on public wifi connections, presumably it *is* best to install a software firewall.

Would anyone like to confirm this?

---

### Post by samiux on 2013-02-05
> **Zill said:**
> This is an interesting point!

My PCs are behind a NAT router and so I have always understood that there was no need for a software firewall to be installed on the PCs.

However, with a laptop that *may* be used on public wifi connections, presumably it *is* best to install a software firewall.

Would anyone like to confirm this?

In my opinion, firewall is for the old day guys.  You need an IPS.  I wonder if anyone know what is IPS.  Someone says that it is over killed for desktops and laptops but anyone knows that Linux is very easy to compromised compare with Windows as the attackers are not required to overcome the AV.

Samiux

---

### Post by cariboo on 2013-02-05
> **samiux said:**
> In my opinion, firewall is for the old day guys.  You need an IPS.  I wonder if anyone know what is IPS.  Someone says that it is over killed for desktops and laptops but anyone knows that Linux is very easy to compromised compare with Windows as the attackers are not required to overcome the AV.

Samiux

I hope you mean something other than anti-virus software when you say AV, as the first thing [ransomeware]("http://en.wikipedia.org/wiki/Ransomware_(malware)") does when infecting a Windows system, is disable the anti-virus software.

---

### Post by samiux on 2013-02-05
> **cariboo907 said:**
> I hope you mean something other than anti-virus software when you say AV, as the first thing [ransomeware]("http://en.wikipedia.org/wiki/Ransomware_(malware)") does when infecting a Windows system, is disable the anti-virus software.

First of all, when an attacker is targeted to your systems/network, s/he will do a lot of information gathering tasks.  Once s/he get enough information, s/he will perform the attack, sometime it takes several minutes only.  However, s/he will spend a lot of time to do information gathering, e.g. a week, a month, a year or so.  

When the attacker is going to attack your systems/network (no matter what the OS is), s/he will try to bypass the security devices/softwares (including IDS/IPS, firewall and anti-virus (AV).

Attacker will not disable the function of the security devices/softwares in order to keep the victims innocence.  If the attacker disable the function of security devices/softwares, the vicitms will be alerted something is going wrong.

During the post-exploitation, the attacker may plant a backdoor in the victims' systems/network.  Or, the attacker will do what they want to do.  It is just depends on the purpose of the attack.  For example, they will alter the logs when necessary.  Sometime, they are not required to do so as their IP address is a fake one or by any other reason.

IPS may or may not prevent all the attacks but it is a good appliance/software to implement to your systems/network as it will prevent some of the known attacks.  The modern IPS can also acts as WAF (Web Application Firewall) which is working on OSI Layer 7 (Application Layer).  By the way, IPS is working very close to the stateful iptables.  You can say that IPS is an advanced firewall.  IPS will protect your systems/network in real time by inspecting and comparing the packets for the traffic.  Basic firewall cannot do that, e.g. iptables only.

By the way, anti-virus also may not prevent your systems/network from being infected.

Ransomeware is not targeted to a specific victim, it is target to all victims by chance and the purpose of the malware is for ransome only.

Samiux

---

### Post by Zill on 2013-02-06
> **samiux said:**
> ...but anyone knows that Linux is very easy to compromised compare with Windows...
Have you got any *evidence* for this statement?

---

### Post by haqking on 2013-02-06
> **Zill said:**
> Have you got any *evidence* for this statement?

I am a penetration tester and security professional what evidence do you want ?

try here

[https://cve.mitre.org/](https://cve.mitre.org/)
[http://www.exploit-db.com/](http://www.exploit-db.com/)


If a system is connected then it is vulnerable, all end user OS whether it be a Linux Distro or Windows meet EAL 4 or 4+ in the common criteria which means they are all secure within reason whilst leaving functionality and ease of use the primary goals.

There are systems which meet higher criteria but they are not meant for end user use such as bespoke military or aerospace systems and the like.

[http://www.commoncriteriaportal.org/products/](http://www.commoncriteriaportal.org/products/)

Most Ubuntu distors meet EAL 4+ which is the same as most Windows versions, of course not every version or company puts forward for certification, Why ? because there is no need as they are end user OS.

The methods are often similar or vastly different but all connected systems have some type of vulnerability which is par for the course for being connected.

Point metasploit/meterpreter at most systems and something will pop up, usually a reverse shell ;-) (joke)

The whole "secure" thing is sadly misunderstood, I read in here all the time about not needing a firewall if behind a router.....shame people know nothing about how easy it can often be to compromise a home based NAT router, firewalk, use Hping to ping using TCP past firewalls that block ICMP, session splice, XSS, NMAP idle scans or FTP bounce, reverse connections from arbitrary port creation as no outgoing traffic is controlled....... ad nauseum ad infinitum  I dont bother replying anymore.

Peace

---

### Post by Zill on 2013-02-06
> **haqking said:**
> I am a penetration tester and security professional what evidence do you want ?...
Err... slight misunderstanding. ;-)

My question was to samiux in post [#17]("http://ubuntuforums.org/showpost.php?p=12493317&postcount=17") and referred to his statement "...but anyone knows that Linux is very easy to compromised compare with Windows...".

---

### Post by Bucky Ball on 2013-02-06
Is it time for this thread to head to Recurring Discussions yet? Me thinks so.

*Thread moved to **Recurring Discussions**.*

Everything you want to know is out there if you look, great advice from some folk that know on this thread, and this is solved if you process the information. Please feel free to continue the discussion. ;)

---

### Post by samiux on 2013-02-06
> **Zill said:**
> Err... slight misunderstanding. ;-)

My question was to samiux in post [#17]("http://ubuntuforums.org/showpost.php?p=12493317&postcount=17") and referred to his statement "...but anyone knows that Linux is very easy to compromised compare with Windows...".

I think haqking has answered your question.  However, if you are insisted to see the visual demo, I will show you some of them.  Be reminded that they are just examples.  

For linux exploit, please see [here]("http://www.youtube.com/watch?v=UhOKmqm4dcs"), [here]("http://www.youtube.com/watch?v=fmC4csWbGLQ") and [here]("http://www.youtube.com/watch?v=YskA9sne7Pg").

For Windows anti-virus bypass, please see [here]("http://www.youtube.com/watch?v=GejYsldcIYk")

Hope I have answered your question.

Samiux

---

### Post by mamamia88 on 2013-02-06
Do you need one?  Nobody "needs one".  Should you use one?  Couldn't really hurt. Ubuntu ship with UFW a command line firewall by default.  Just sudo ufw enable, sudo ufw default deny, and then sudo ufw allow portsyouneedopen

---

### Post by haqking on 2013-02-06
> **Zill said:**
> Err... slight misunderstanding. ;-)

My question was to samiux in post [#17]("http://ubuntuforums.org/showpost.php?p=12493317&postcount=17") and referred to his statement "...but anyone knows that Linux is very easy to compromised compare with Windows...".

I know it was directed to samiux, i was just jumping in ;-)

Peace

---

### Post by Zill on 2013-02-06
> **haqking said:**
> I know it was directed to samiux, i was just jumping in ;-)
No problem.  I am questioning the apparent assertion by samiux that Linux systems are more easily compromised than Windows.

I understand from your postings that *all* systems connected to the internet are vulnerable but I also believe that a default Linux system is (relatively!) *more* secure than a default Windows system.  Am I mistaken?

---

### Post by haqking on 2013-02-06
> **Zill said:**
> No problem.  I am questioning the apparent assertion by samiux that Linux systems are more easily compromised than Windows.

I understand from your postings that *all* systems connected to the Internet are vulnerable but I also believe that a default Linux system is (relatively!) *more* secure than a default Windows system.  Am I mistaken?

I cant speak for samiux but I dont think English is the first language for them, I don't think samiux meant it is "easier" but just meant as "easy" as.

The whole thing about this is it cannot be stated that "Linux" is more secure than "Windows" which is common statement, it needs to be very specific such as Ubuntu 10.04 out of the box with no updates and no services installed etc compared to a windows 7 out of the box machine etc etc.

the collective terms of Linux and windows cannot be compared.

then even if specific with versions etc then you have to say OK what does "more secure" mean, if one has 12 vulnerabilities and 8 known exploits vs one with 10 vulnerabilities and 4 known exploits etc.  it is stupid argument, you only need one window open in a house to get in whatever alarm system you have.

Does the fact that you running Linux prevent a compromise from a XSS attack ? no.  Does it prevent you from an attacker getting a remote command shell ? no.

Whatever OS you are running the things that prevent or mitigate these things are user education, patch management and regular updates along with changing browsing habits and the like.

Linux is not more secure than windows, you don't "need" a firewall in Linux, and you don't "need" one in Windows, the point is you should use them in both whether behind a NAT router or not, don't run scripts, use least privilege, don't run unknown or untrusted software, stay vigilant etc etc.

Every system in a connected world is vulnerable, whether or not an exploit exists or if it does if it is worth the time of the attacker to attack is a different matter, of course it is also a case of whether the asset is worth the cost of protection and so forth.

Regardless what OS you use the same security principles apply, it is a process not a product.  yes there are not known wild "viruses" for Linux but if then means you can use the same nonchalant browsing behaviors as in windows then sooner or later another type of compromise is likely to happen.

Both systems can and do get compromised all the time. it isnt any more difficult to compromise one or the other, one configured system may have more defences but the action taken to compromise one or the other no more difficult than another, one may take 5 minutes and one may take an hour, does that mean easier, I dont think so, i take it as different.

peace

---

### Post by Zill on 2013-02-06
haqking:  Thanks for the clarification and it is interesting to see that you recommend using a software firewall even when a PC is behind a NAT router.

I have been using pure Linux systems for around ten years now (no Windows or Macs here!) on fixed PCs *without* a software firewall or antivirus software etc and have had no problems whatsoever.  I would think that very few Windows users can say this!

However, with the addition of a netbook for use out and about on public wifi networks, I have considered using UFW.  Again, maybe I have been lucky but there is no evidence that my netbook has been attacked since I got it around 18 months ago.  I guess from your comments that you would definitely advocate enabling UFW on netbooks/laptops used on public networks?

---

### Post by haqking on 2013-02-06
> **Zill said:**
> haqking:  Thanks for the clarification and it is interesting to see that you recommend using a software firewall even when a PC is behind a NAT router.

I have been using pure Linux systems for around ten years now (no Windows or Macs here!) on fixed PCs *without* a software firewall or antivirus software etc and have had no problems whatsoever.  I would think that very few Windows users can say this!

However, with the addition of a netbook for use out and about on public wifi networks, I have considered using UFW.  Again, maybe I have been lucky but there is no evidence that my netbook has been attacked since I got it around 18 months ago.  I guess from your comments that you would definitely advocate enabling UFW on netbooks/laptops used on public networks?

I would advocate a firewall in all instances, it is not a one stop solution but is part of a layered defence which is the best process for securing a system.  For a start most people think of firewalls as stopping attackers getting in, well what about getting out ;-)...controlling outgoing traffic is as important to prevent reverse connections on arbitrary port creations from malware or malicious code embedded in webpages or bad code in applications etc.

Also alot of people think oh its ok im behind a firewall, well like a any wall it can be climbed over, burrowed under or gone around the side or beaten down with a sledge hammer, firewalls are not impenetrable by any means.

The most basic thing people seem to worry about is "oh i will block ICMP" then no one can see me...LOL.....well there are many ways and tools without using PING, hping uses TCP for example and not ICMP, Nmap can scan using IDLE scans from IDLE machine or node and no packets are returned to the attacker from the target only to the trusted or IDLE machine, PING can be diabled in NMAP scans and so on.  This is just a few simple things as examples and not provided in detail but you get my point.  I used these examples as they are very basic and most people can grasp it without too much in depth security knowledge and cover basic things which most people already know about, there are much more advanced methods for bypassing firewalls.

Also you mentioned you have never had a problem, well that maybe true indeed probably very likely, but how do you know ? not all attacks or compromises result in damage or "things going wrong" sometimes it is merely exploratory, nosy, and do no damage and a skilled attacker can cover tracks very easily, just cause someone isnt stepping on my rose garden doesnt mean I want them in my garden at all ;-)

Peace

---

### Post by Zill on 2013-02-07
> **haqking said:**
> I would advocate a firewall in all instances, it is not a one stop solution but is part of a layered defence which is the best process for securing a system...
So, if I understand this correctly, you recommend a software firewall such as iptables/ufw even for machines behind a NAT router?  Is there any performance hit in using firewalls, particularly if you use *both* NAT and iptables?

I agree with the layered defence approach and try to comply with this to the level of my understanding. ;-)  However, I also believe that Windows systems, in particular, are so loaded up with "security" measures as to make them considerably more bloated and slow than Linux systems.  I don't want to drag my machines down to the level of Windows!
> **haqking said:**
> ...For a start most people think of firewalls as stopping attackers getting in, well what about getting out ;-)...controlling outgoing traffic is as important to prevent reverse connections on arbitrary port creations from malware or malicious code embedded in webpages or bad code in applications etc...
A good point but it is difficult for those of us without "expert" security knowledge to know exactly *how* to control this without disrupting genuine communications with the internet.  Are there any simple but definitive guides on this?

Slightly off-topic but still relevant IMHO, I know that enabling UPnP in a router is regarded as a security hole but how important is UPnP to internet services?  i.e.  What kinds of internet connectivity will be degraded by disabling UPnP?  I am thinking of things like torrents and SIP communications etc.

---

### Post by haqking on 2013-02-07
> **Zill said:**
> So, if I understand this correctly, you recommend a software firewall such as iptables/ufw even for machines behind a NAT router?  Is there any performance hit in using firewalls, particularly if you use *both* NAT and iptables?

I agree with the layered defence approach and try to comply with this to the level of my understanding. ;-)  However, I also believe that Windows systems, in particular, are so loaded up with "security" measures as to make them considerably more bloated and slow than Linux systems.  I don't want to drag my machines down to the level of Windows!

A good point but it is difficult for those of us without "expert" security knowledge to know exactly *how* to control this without disrupting genuine communications with the internet.  Are there any simple but definitive guides on this?

Slightly off-topic but still relevant IMHO, I know that enabling UPnP in a router is regarded as a security hole but how important is UPnP to internet services?  i.e.  What kinds of internet connectivity will be degraded by disabling UPnP?  I am thinking of things like torrents and SIP communications etc.

yes, behind a NAT router is irrelevant in my opinion, yes it offers you some protection but like i said a layered defence is best.  and a software firewall gives you finer grained controls for your own applications right through the seven layers (as in OSI or 4 if you are a purist ;-)

As for performance, a few simple rules in a UFW or IPTables will not effect anything, obviously if its gonna be a HIDS or something then yes you may take a performance hit but a simple UFW/IPTable filter wont do any harm.

In windows nothing is different really apart from a "need" for a malware solution but MSE is fine and doesnt effect performance, if its Windows 8 then it is built into Windows defender, MSE or Defender is as good as any commercial pay for applications outside of a enterprise solution for a email server for example.  All AV products are full of false positives and negatives and often "spyware" anyways, best alter browsing habits for a better solution ;-).

As for how do you know, disable all then allow out what you use as you use it, most things have well defined ports or ranges you can see an example here of how to configure it [http://ubuntuforums.org/showpost.php?p=11428970&postcount=1](http://ubuntuforums.org/showpost.php?p=11428970&postcount=1)

A little bit of work initially but then you have a finer grained control of your traffic if you want it that is.

As for UPNP, I never use it, things such as torrents I control manually with my own configured ports for DHT, UDP trackers and torrents in general.

but it is all choice of course, I am not preaching to anyone, merely offering my knowledge and experience based on 20+ years in IT security and seeing many different "secure" systems compromised all the time, and you would be surprised how easy it can be even if "firewalls" and the like are in the way, which is why I get paid so well...LOL.  I usually dont bother with these threads or discussions anymore, but seeing as you are open to it I am blah blah blah ing for a little while ;-)

Peace

---

### Post by Zill on 2013-02-07
haqking:  Thanks for that - food for thought. :-)

I still don't really understand how a software firewall provides protection that NAT does not.  For instance, if I run a couple of local services (such as SHH and NFS) on my LAN, *how* are these visible to the "outside world" after going through my NAT router?  eg nmap on my LAN reports:
```
Not shown: 997 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
111/tcp  open  rpcbind
2049/tcp open  nfs
```
but GRC ShieldsUP claims full stealth mode on all ports facing the internet.

If a NAT "firewall" cannot stop such traffic then why would a software firewall manage to do so?

I appreciate that you make your living selling security knowledge to businesses who are, presumably, running internet services.  In such circumstances I know that additional hardening is essential.  However, for home users who generally run few, if any, servers, is a high level of hardening really desirable if configuration and maintenance of the necessary rules will make usability difficult?

I must admit that I keep thinking of "elephant powder". ;-)
> A man was sprinkling white powder on his front yard."Whats the powder for?" asked his neighbor. "It's to keep the elephants off the grass," replied the first man. "But we don't have any elephants around here!" "I know great stuff isn't it?"

---

### Post by haqking on 2013-02-07
> **Zill said:**
> haqking:  Thanks for that - food for thought. :-)

I still don't really understand how a software firewall provides protection that NAT does not.  For instance, if I run a couple of local services (such as SHH and NFS) on my LAN, *how* are these visible to the "outside world" after going through my NAT router?  eg nmap on my LAN reports:
```
Not shown: 997 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
111/tcp  open  rpcbind
2049/tcp open  nfs
```but GRC ShieldsUP claims full stealth mode on all ports facing the internet.

If a NAT "firewall" cannot stop such traffic then why would a software firewall manage to do so?

I appreciate that you make your living selling security knowledge to businesses who are, presumably, running INTERNET services.  In such circumstances I know that additional hardening is essential.  However, for home users who generally run few, if any, servers, is a high level of hardening really desirable if configuration and maintenance of the necessary rules will make usability difficult?

I must admit that I keep thinking of "elephant powder". ;-)

I am not saying a software (local) firewall does something your router does not.  A typical home user will have a router which will provide a NAT based firewall typically.  This is good and yes does offer protection.  What I am saying is that this does not mean you are "secure", can an attacker get past a a firewall ? YES...you mentioned NMAP, there tons of different types of scan which yields all types of information aside from the typical NMAP  <ip address> which will only be a stealth scan if running with admin privilege otherwise it defaults to a connect (TCP) scan by the way.  Anyways without being tool specific, a NAT based home router does not secure you from outside attack, it merely offers a defence, bit like a front gate to your garden, does that mean you don't want a door on your house as well ? so again, layered defence.  My point is really this, the majority of Linux users tend to lean towards it is Linux so I am secure which is not correct, this often comes from people who have no real working concept of security or penetration tools, methods, vectors etc.

The idea of a firewall for a lot of typical users means they are protected, obviously this is not true, even if they do have one, have they configured it ? Do they know how to ? even more reason to throw another one in there for a layered defence, when you know and understand how to configure it based on attack vectors then you will understand the "need" to and the requirement to run one locally as well.

NAT offers some protection, a Firewall offers some protection.....so does a coat but it wont stop you getting wet forever.

Do you need to run a local firewall ? NO, should you ? probably ? Would i recommend it ? yes.  Will a home router protect you ? NO....will it offer you some protection ? yes, can a skilled attacker get past it ? yes.  Will a software.local firewall help you ? yes, will it protect you completely ? NO, in a connected world you are always vulnerable.

As for GRC, i don't even want to get started on Steve Gibson...LOL anyways all that does anyways is scan your Public IP and shows what a typical scan would show when looking at your router, it not trying to get in, it is merely reporting what it can see from a typical scan.  There is nothing "typical" about an attacker or penetration tester conducting their scanning phase where they may be using a XMAS, IDLE, ACK, FIN, NULL, UDP, Protocol scan etc etc or using more than one tool to do so.

read here on GRC, he is a joke in the security community:
[http://radsoft.net/news/roundups/grc/20060121,00.shtml](http://radsoft.net/news/roundups/grc/20060121,00.shtml)
[https://allthatiswrong.wordpress.com/2009/10/11/steve-gibson-is-a-fraud/](https://allthatiswrong.wordpress.com/2009/10/11/steve-gibson-is-a-fraud/)
[http://www.theregister.co.uk/2001/06/25/steve_gibson_really_is_off/](http://www.theregister.co.uk/2001/06/25/steve_gibson_really_is_off/)

There are many, you could read what an idiot he is all day long ;-)

As for scanning your machine from behind a firewall like a NAT router, there is not enough space here to do so.  I suggest you read up on the various scan methods with tools such as hping and Nmap which are the most popular and perhaps read something like these

[https://pentestlab.wordpress.com/2012/04/02/nmap-techniques-for-avoiding-firewalls/](https://pentestlab.wordpress.com/2012/04/02/nmap-techniques-for-avoiding-firewalls/)
[http://nmap.org/book/man-bypass-firewalls-ids.html](http://nmap.org/book/man-bypass-firewalls-ids.html)
[http://www.tenable.com/blog/using_nessus_to](http://www.tenable.com/blog/using_nessus_to)
[http://www.vesaria.com/Firewall/Testing/eye_of_hacker.php](http://www.vesaria.com/Firewall/Testing/eye_of_hacker.php)


And so on, none of these are complete, they merely offer you some insight.  I appreciate only security people know this stuff like anything, which is why i try to help where I can.  Just dont rest on the "Linux is secure" laurel that is all.

I love Linux and and consider myself a guru, but with that I am also a security pragmatist and rational empiricist ;-)

Edit: oh and please excuse my typing, grammar etc as I have a broken finger...LOL........I guess i should stop poking at firewalls ;-)

Peace

---

### Post by Zill on 2013-02-07
haqking:  Thanks for the info and the interesting links.  Although I have been using Linux for around ten years now I still find much of this above my head.  As a retired electronics engineer my background is primarily in "hardware", rather than this new young upstart "software". ;-)

I like to keep my systems light and reliable, generally preferring LTS releases and taking best advice with security.

On this basis, I may well try out (g)ufw with my netbook as this would seem to be most at risk due to public wifi connections.  It will be interesting to see if there is any performance hit, which should be readily apparent due to the low-spec atom processor!

Of course, I don't run any services to speak of with this netbook, just ssh.  It is regularly updated to make sure most of the latest security holes are covered.

Hopefully, (g)ufw will help keep the black-hats out.  But, as I mentioned earlier, I never seemed to have any problems without it!  Effectiveness of elephant powder is a tricky one to quantify. ;-)

---

### Post by haqking on 2013-02-07
> **Zill said:**
> haqking:  Thanks for the info and the interesting links.  Although I have been using Linux for around ten years now I still find much of this above my head.  As a retired electronics engineer my background is primarily in "hardware", rather than this new young upstart "software". ;-)

I like to keep my systems light and reliable, generally preferring LTS releases and taking best advice with security.

On this basis, I may well try out (g)ufw with my netbook as this would seem to be most at risk due to public wifi connections.  It will be interesting to see if there is any performance hit, which should be readily apparent due to the low-spec atom processor!

Of course, I don't run any services to speak of with this netbook, just ssh.  It is regularly updated to make sure most of the latest security holes are covered.

Hopefully, (g)ufw will help keep the black-hats out.  But, as I mentioned earlier, I never seemed to have any problems without it!  Effectiveness of elephant powder is a tricky one to quantify. ;-)

for public wireless you should also if not already encrypt your traffic with something like a VPN, wireless sniffing at public hotspots is rife whatever elephant dust you sprinkle...LOL

Peace

---

### Post by Zill on 2013-02-08
> **haqking said:**
> for public wireless you should also if not already encrypt your traffic with something like a VPN...
AIUI, VPN tunnelling is to establish a secure connection to a specified server, such as an employer.  In my case, I only use the netbook to send and receive the odd personal email (via my isp) and for general web browsing.  No secure content there!  So I doubt if I would be able to use a VPN connection.

Thanks for the suggestion though and hopefully it will be of use to others reading this thread,

---

### Post by haqking on 2013-02-08
> **Zill said:**
> AIUI, VPN tunnelling is to establish a secure connection to a specified server, such as an employer.  In my case, I only use the netbook to send and receive the odd personal email (via my isp) and for general web browsing.  No secure content there!  So I doubt if I would be able to use a VPN connection.

Thanks for the suggestion though and hopefully it will be of use to others reading this thread,

Then you understand it wrong ;-)

A VPN is often used in a corporate envinroment for sure but is not only for that.

When you connect to a public hotspot you are giving over all your traffic (which if not encrypted) may sometimes be in cleartext , to the owner of the hotspot not to mention everyone else using that network sat there with tcpdump or wireshark or whatever sniffer they choose.

it takes 30 seconds to create a filter in Wireshark to build a complete trace of a HTTP traffic flow for example so the person sniffing can see your entire browsing experience.

The pages you visit may or could quite easily be an exact copy of the real pages but on an attackers own server as the DNS is coming from the AP you connected to or which has been compromised by someone else in the network etc etc, deigned to capture logins and the like which then redirect you to the real site so you dont even know it happened.

there are tons of VPN services around alot are free, fast and simple and encrypts traffic.

Along with things such as HTTPS everywhere and the like.

But if you dont see your email or whatever you access as important then it is upto you, no one can manage your own traffic except you.

Peace

---

### Post by JKyleOKC on 2013-02-08
> **haqking said:**
> there are tons of VPN services around alot are free, fast and simple and encrypts traffic.But how do you know that any specific one of these services is trustworthy, and not a MITM (man in the middle) using your supposedly secure connection to grab up all your traffic?

Somewhere along the way it always boils down to trust. Unless you control every inch of the connection path -- obviously not possible outside of one's private LAN -- your traffic will always be subject to interception.

Contrary to popular belief, it's possible to have a totally secure computer. However to reach that goal you must remove all capability for input and output, making it quite useless. Once you make the machine usable, it becomes insecure. The only hope is to minimize the insecurity, and that's where the process comes in. Only one person -- yourself -- can determine where the dividing line between "caution" and "paranoia" lies...

---

### Post by Zill on 2013-02-08
> **haqking said:**
> ...there are tons of VPN services around alot are [COLOR="Red"]free[/COLOR], fast and simple and encrypts traffic...
"free" in this case being similar to "free beer" rather than "free speech"!

I'm afraid I am distrustful of such services as I do generally believe the old adage... "if you're not paying for a service then *you* are the service". :-(

I appreciate that a "free" VPN might improve security from one point of view but then you may lose any advantage by routing data through some mysterious third-party.

---

### Post by haqking on 2013-02-08
> **Zill said:**
> "free" in this case being similar to "free beer" rather than "free speech"!

I'm afraid I am distrustful of such services as I do generally believe the old adage... "if you're not paying for a service then *you* are the service". :-(

I appreciate that a "free" VPN might improve security from one point of view but then you may lose any advantage by routing data through some mysterious third-party.

OK, well its only information.

best of luck.

Peace

---

### Post by Old Jimma on 2013-02-11
Hi Folks:

I think we all should be concerned about the security of our machines...

Please read: [COLOR="Red"]**[http://www.washingtonpost.com/world/national-security/us-said-to-be-target-of-massive-cyber-espionage-campaign/2013/02/10/7b4687d8-6fc1-11e2-aa58-243de81040ba_story.html?hpid=z1]("http://www.washingtonpost.com/world/national-security/us-said-to-be-target-of-massive-cyber-espionage-campaign/2013/02/10/7b4687d8-6fc1-11e2-aa58-243de81040ba_story.html?hpid=z1")**[/COLOR]

Hacking is evil. :evil:

Old Jimma

---

### Post by samiux on 2013-02-11
> **Old Jimma said:**
> Hi Folks:

I think we all should be concerned about the security of our machines...

Please read: [COLOR="Red"]**[http://www.washingtonpost.com/world/national-security/us-said-to-be-target-of-massive-cyber-espionage-campaign/2013/02/10/7b4687d8-6fc1-11e2-aa58-243de81040ba_story.html?hpid=z1]("http://www.washingtonpost.com/world/national-security/us-said-to-be-target-of-massive-cyber-espionage-campaign/2013/02/10/7b4687d8-6fc1-11e2-aa58-243de81040ba_story.html?hpid=z1")**[/COLOR]

Hacking is evil. :evil:

Old Jimma

Everyone here do not understand what is "hacking", too sad.

Samiux

---

