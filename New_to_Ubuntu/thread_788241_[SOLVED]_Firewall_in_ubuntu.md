---
title: "[SOLVED] Firewall in ubuntu?"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by kamitsukai on 2008-05-09
How do i install and setup a firewall for ubuntu 8.4? which is best?

---

### Post by tech9 on 2008-05-09
you can install...

firestarter

```
sudo apt-get install firestarter
```

But, just to clarify - firestarter is merely a front-end GUI to IP Tables running in the background.

It's a nice tool to configure your IP Tables though.

---

### Post by guildofghostwriters on 2008-05-09
There's already a firewall working in the background so to speak. There are various firewall GUIs which help you to configure it but I'd advise against them based on my own experience. I'm new to all this and a firewall was the first thing I wanted to add when I'd got it up and running so I installed firestarter first but got rid of it because (it seemed to me) it kept shutting itself down. SO I tried guarddog but I couldn't follow the GUI (and I used commodo in Windows so I thought I knew what I was doing!) so I got rid of that as well. But somehow one or t'other of em left behind their configurations of my iptables preventing me from getting online for the best part of a weekend until someone on here sorted me out. I've seen various posts here that say you don't need firestarter, guarddog or the like if you're just connecting with a desktop pc to do normal stuff like web, email, im, p2p, torrent, streaming etc.

---

### Post by wootah on 2008-05-09
> **guildofghostwriters said:**
> There's already a firewall working in the background so to speak. There are various firewall GUIs which help you to configure it but I'd advise against them based on my own experience. I'm new to all this and a firewall was the first thing I wanted to add when I'd got it up and running so I installed firestarter first but got rid of it because (it seemed to me) it kept shutting itself down. SO I tried guarddog but I couldn't follow the GUI (and I used commodo in Windows so I thought I knew what I was doing!) so I got rid of that as well. But somehow one or t'other of em left behind their configurations of my iptables preventing me from getting online for the best part of a weekend until someone on here sorted me out. I've seen various posts here that say you don't need firestarter, guarddog or the like if you're just connecting with a desktop pc to do normal stuff like web, email, im, p2p, torrent, streaming etc.

As tech9 pointed out, Firestarter is merely a front-end GUI tool to configure IP Tables. Firestarter does not need to be running for your firewall to be active, but it does need admin. privs to be ran as it must use iptables.

---

### Post by kamitsukai on 2008-05-09
Ok so im confused...i already have a firewall installed by default? so all this is, is a gui to see connection attempts?

---

### Post by tech9 on 2008-05-09
> **kamitsukai said:**
> Ok so im confused...i already have a firewall installed by default? so all this is, is a gui to see connection attempts?

yes... firestarter is - you have ip tables running in the background - that's your firewall.

firestarter is a nice tool, because you can setup rules to allow IPs much easier than configuring it in the IP Tables at the command line

---

### Post by SunnyRabbiera on 2008-05-09
> **kamitsukai said:**
> Ok so im confused...i already have a firewall installed by default? so all this is, is a gui to see connection attempts?

correct, so if you want a GUI you can use firestarter.

---

### Post by brian_p on 2008-05-09
> **kamitsukai said:**
> Ok so im confused...

That can be rectified. Would you outline why you think you need to make use of iptables (in your terminology, install a firewall)?

---

### Post by kamitsukai on 2008-05-09
dunno was told it was a good idea lol

---

### Post by Wicca on 2008-05-09
Hi,

Although there's a firewall running after a base install, it is a misconception that it is actually working. By default, no rules are active so everything from everywhere is accepted. As a result you are not 'firewalled' at all.

If you want to run a firewall in Ubuntu you have to configure it running iptables (terminal based) or firestarter (GUI). Both are interfaces to configure the firewall itself, which is called 'Netfilter' btw.

Do you need a (active) firewall?
My opinion is you do, when:
1. Your machine is directly connected to internet.
2. Your machine is a host for some servers made available to the internet.

If you are behind a NAT router, as most people are these days, and you are not running servers than the inbuild firewall of your router should give enough security.

---

### Post by brian_p on 2008-05-09
> **kamitsukai said:**
> dunno was told it was a good idea lol

I'll tell you you do not need a firewall but, unlike your source, I'll give you reasons.

1. The default Ubuntu installation has no ports open. It is impossible for connections to be made to your machine from the internet.

2. Unless you have very special requirements there is no necessity to restrict outgoing connections.

---

### Post by imT on 2008-05-09
> **brian_p said:**
> I'll tell you you do not need a firewall but, unlike your source, I'll give you reasons.

1. The default Ubuntu installation has no ports open. It is impossible for connections to be made to your machine from the internet.

2. Unless you have very special requirements there is no necessity to restrict outgoing connections.

i'm no expert but before i configure the firewall with firestarer my ports are open, i check with sites like pcflank.com => the ports are open and your not invisible to the world (no stealth thing)

again, i'm no expert but that's how i configure my firewall and it pass good in the tests.

---

### Post by brian_p on 2008-05-09
> **Wicca said:**
> Hi,

. . .  so everything from everywhere is accepted.

That's incorrect.

> Do you need a (active) firewall?
My opinion is you do, when:
1. Your machine is directly connected to internet.
2. Your machine is a host for some servers made available to the internet.

If you are offering services, whether the connection is direct or not, they cannot be firewalled

---

### Post by Wicca on 2008-05-09
> **brian_p said:**
> That's incorrect.

Just do a....

```
sudo iptables -L
```
.... on a not firewall configured Ubuntu machine and tell me what you see. All three chains (input, output and forward) accept all packets.

> If you are offering services, whether the connection is direct or not, they cannot be firewalled
Yes they can.
In a firewall you make special rules concerning the services you provide (limit amount of connections, block certain subnets etc.) It's even very advisable if you are doing serious business on the internet.

---

### Post by brian_p on 2008-05-09
> **imT said:**
> i'm no expert but before i configure the firewall with firestarer my ports are open, i check with sites like pcflank.com => the ports are open and your not invisible to the world (no stealth thing)

again, i'm no expert but that's how i configure my firewall and it pass good in the tests.

This is what I get:

> We have scanned your system for open ports and for ports visible to others on the Internet. As a rule an open port means your computer is vulnerable to attacks by crackers. They gain access to your computer and its files through these open ports.
	

Warning!
The test found visible port(s) on your system: 21, 23, 80, 135, 137, 138, 139, 1080, 3128

I know exactly what services I have open to the internet (ports 22 and 25) so I expect this is the sort of nonsense you got too. Offering a service with up to date software does not make the machine vulnerable. Quite the opposite in fact.

As for being visible. So what?

---

### Post by Wicca on 2008-05-09
If you want a serious online scanner use ShieldsUp
[http://www.grc.com]("http://www.grc.com")

> **brian_p said:**
> This is what I get:
As for being visible. So what?

You don't want ports to be visible, unless you provide a service over it. A visible port might be closed but is still open to connection requests, the good or the bad. The only safe port is a stealth one.

---

### Post by brian_p on 2008-05-09
> **Wicca said:**
> Just do a....

```
sudo iptables -L
```
.... on a not firewall configured Ubuntu machine and tell me what you see. All three chains (input, output and forward) accept all packets.

I was a bit hasty in my interpretation of 'accepted'. All traffic is allowed but where is the problem with that? If no services are running there can be none. If a service is running and properly configured then again there is no problem.

> Yes they can.
In a firewall you make special rules concerning the services you provide (limit amount of connections, block certain subnets etc.) It's even very advisable if you are doing serious business on the internet.

That sort of thing can be done in the service's configuration file(s). If it cannot then iptables might be an option. As far as I can see, most people appear to use iptables for nothing more rejecting everything and then (just perhaps) they poke a hole in it to allow, for example, ssh. Seems a bit pointless when the default configuration is safe.

---

### Post by brian_p on 2008-05-09
> **Wicca said:**
> 
You don't want ports to be visible, unless you provide a service over it.

I've no use for an invisible service.

 > A visible port might be closed but is still open to connection requests, the good or the bad. The only safe port is a stealth one.

A closed port is offering no service. Let the whole world come and stare and poke at it - it is completely and utterly safe.

---

### Post by Wicca on 2008-05-09
> **brian_p said:**
> I was a bit hasty in my interpretation of 'accepted'. All traffic is allowed but where is the problem with that? If no services are running there can be none. If a service is running and properly configured then again there is no problem.


A properly configured service might be sensitive for vulnerabilities, this is where a firewall might add an extra security layer. As an example: DDOS attacks can't be avoided by just properly configuring your service (well, some can, some don't)

But in a way we do agree.
My firewall story was a reaction on the assumption that in ubuntu there is a firewall running so 'we are safe'. I just wanted to clarify that it is not.  I gave my opinion whether it's necessary to configure it, or not. And in most cases, a 'normal' user behind a NAT router would not need a firewall.

---

### Post by Wicca on 2008-05-09
> **brian_p said:**
> I've no use for an invisible service.

A closed port is offering no service. Let the whole world come and stare and poke at it - it is completely and utterly safe.

A closed port DOES offering a service, all hackers know. It is, only at this particular moment, closed. But the service behind it is listening and willing to react on connection requests, and therefore vulnerable. 

If you provide a service (ssh, http etc) it is of course necessary that these services are visible (thus port open or closed), but a closed port instead of a stealth one can also indicate that there is something going on the user is not aware of, like services running you didn't ask for (have especially ms-windows in mind here :-) and therefore should be handled with suspicion.

Good night.

---

### Post by nowshining on 2008-05-09
i suggest arno-iptables-firewall in the repos, u edit it with txt editors and restart the firewall if u change any options, add-rules, etc.. by sudo /etc/init.d/arno-iptables-firewall restart

---

### Post by Wicca on 2008-05-10
Good morning,

Well I have to correct myself. The way I wrote it it is wrong:
> **Wicca said:**
> A closed port DOES offering a service, all hackers know. It is, only at this particular moment, closed. But the service behind it is listening and willing to react on connection requests, and therefore vulnerable. 


There is no service active behind a closed port, so it is not the service that is listening ofcourse, but the port itself is still reacting on connection requests. A SYN-bit is accepted, the port may react in a way 'service not available' where a stealth port is not reacting at all.
A closed port does a hacker tell that there is a service active, but not at this moment. He may come back later and find the port is open.
This, and the fact a closed port responses to connection requests (a syn flood attack may occur), makes a closed port more vulnerable than a stealth port.

Have a nice day!

---

### Post by brian_p on 2008-05-10
> **Wicca said:**
> A properly configured service might be sensitive for vulnerabilities, this is where a firewall might add an extra security layer. As an example: DDOS attacks can't be avoided by just properly configuring your service (well, some can, some don't)

A DDOS attack denies a service to legitimate users but does not threaten the security of it, provided the software is up to date.

> But in a way we do agree.
My firewall story was a reaction on the assumption that in ubuntu there is a firewall running so 'we are safe'. I just wanted to clarify that it is not.  I gave my opinion whether it's necessary to configure it, or not. And in most cases, a 'normal' user behind a NAT router would not need a firewall.

The default iptables rules are more than adequate for a single linux box, with or without a NAT router. Default service configurations bind only to localhost and, with updates, are still safe if made accessible from the internet.

---

### Post by brian_p on 2008-05-10
> **Wicca said:**
> Good morning,

Well I have to correct myself. The way I wrote it it is wrong:


There is no service active behind a closed port, so it is not the service that is listening ofcourse, but the port itself is still reacting on connection requests. A SYN-bit is accepted, the port may react in a way 'service not available' where a stealth port is not reacting at all.
A closed port does a hacker tell that there is a service active, but not at this moment. He may come back later and find the port is open.
This, and the fact a closed port responses to connection requests (a syn flood attack may occur), makes a closed port more vulnerable than a stealth port.

A closed port means *there is no service listening*. There is nothing to connect to. An attacker would be wasting her time trying to attempt a connection and that is true whether the packets are rejected or dropped.

> Have a nice day!

And you too.

---

### Post by hyper_ch on 2008-05-10
why do you think you need a firewall?

---

### Post by nowshining on 2008-05-10
brian_p - Bots, Worms, People are all scanning all the time to find non-firewalled computers to break into. Linux can be broken into just like windows, altho it is a bit harder as it's easier to break into windows.

When u get hacked or already are don't come crying to us. ;)

---

### Post by JGFuller on 2008-05-11
As a recent new Ubuntu user, I was also concerned about a firewall, having always used the built-in Windows XP firewall.

So I tried Firestarter, and activated it using the GUI, with no additional information added.  I was then not able to print to a Windows shared network printer, until Firestarter was Disabled.

Ubuntu is installed on a Compaq Presario 2200, using Wubi.  The Windows config is Windows XP Home; SP 2.

Any suggestions?

---

### Post by Herman on 2008-05-11
There are **no open ports** when you install Ubuntu.
Ubuntu is completely stealth on the internet or in your LAN. You can do port scans to prove it.. 

The IPtabels is there but it's not configured by default.
As long as you don't install software that opens 'services', (such as Frostwire or Samba or something like that), which open ports, you don't need any firewall configured.. 
Only when you open ports do you need a firewall configuration tool

A firewall is a stupid name for it, a 'filter' is a better term.
Ubuntu is already as solid as a rock, and when you open ports you are opening holes in it, therefore you want to filter what's allowed in through those holes.

The name 'firewall' implies a soft operating system like a sponge to begin with, over which you need some kind of shield to keep the bad guys out.
In Linux it's the other way around. We start with a secure system.

---

### Post by JGFuller on 2008-05-11
I do use SAMBA [I think - told you I was a rookie!] to enable the network printer for Ubuntu on my laptop.  Should I tell Firestarter about this?  What port would Samba use for the networked printer?  or rather, how would I determine this?

---

### Post by Herman on 2008-05-11
[COLOR=#000000]**Port Scanning with Ubuntu** (your other computers in your LAN)
If we have more than one Ubuntu computer in our network we can use each one to scan the others for open ports. Ubuntu comes with some very good networking software of its own.
I went 'System'-->'Administration'-->'Network Tools', and clicked on the 'Port Scan' tab.
You need to know the IP number for each of your other computers that you want to scan.
The easiest way to get that is just to go to the other computer and run 'ifconfig'.
The scan only takes a few seconds.

You will find no open ports in any computer with a fresh Ubuntu installation.

For having your computer scanned from the internet, try out some of these links,
[/COLOR][COLOR=#000000][**'Shields Up!**]("https://www.grc.com/x/ne.dll?bh0bkyd2")' is a well known [/COLOR][COLOR=#000000]internet firewall testing site, your Ubuntu system should pass all tests as 100% stealth with or without any added firewall. I don't use any added software firewall and mine is 100% stealth, and has always been. It will tell you your external IP also.
[/COLOR]
[**AuditMyPc.com**]("http://www.auditmypc.com/") is another firewall testing site you can visit.

[HackerWatch.org]("http://www.hackerwatch.org/probe/") is good too.

[COLOR=#000000][CanYouSeeMe.org - Open Port Check Tool]("http://www.canyouseeme.org/") - Check just one port at a time - any port.


[/COLOR]

---

### Post by Herman on 2008-05-11
> I do use SAMBA [I think - told you I was a rookie!] to enable the network printer for Ubuntu on my laptop. Should I tell Firestarter about this? What port would Samba use for the networked printer? or rather, how would I determine this?Some people do need Samba for sharing network printers. 
Firestarter is a good IPtables configuring tool, if you have Samba server installed you probably do need Firestarter.
I don't have any computer with Firestarter handy right now, so I will just need a few minutes to install it so I can remember how to use it again.
To install it, the quick way is,
```
sudo apt-get install firestarter
```
... or you can look for it in 'Add/Remove Programs or Synaptic Package Manager and install it through either of those.

---

### Post by ramjet_1953 on 2008-05-11
Something else to realise is that if you are connecting to the Internet via an ADSL router, any port scanning sites, such as Shield Up will report back on the firewall in your router, not iptables.

Regards,
Roger :cool:

---

### Post by Herman on 2008-05-11
When Firestarter is installed in your system, you will find it in 'Applications'-->'Internet'.
When you open it for the first time a wizard will ask you a few questions and help you set it up and get started with it.
How you answer those questions depends on your won particular set-up, but there are only three of four questions and then you'll see the Firestarter Window in front of you.

There are three tabs: 'Status', 'Events', and 'Policy'.

The 'Status' tab is more or less just a summary, and when I run a port scan from another computer in the LAN, it comes up as 1 serious inbound event.
I can click the 'Events' tab to learn more.
In the 'Events' tab, I can see the time and date I scanned this PC from my other PC, along with the IP address of teh machine I ran the scan from. 
The 'Policy' tab is more interesting, that's where we set our firewall rules.
There's a spinbox called 'Editing' close to the top of that, and you can use that to enable editing of either inbound or outbound traffic. 
You can set up your IPtables in countless numbers of different ways, and probably there are experts who will debate the vritus of different ideas and schemes.

To start I would click 'Add Rule', and up pops a window asking me what IP address, hoist or network I want to allow connections from.
I could type in the IP address of my other computer there.
If I want to be strickter and fussier, if delete that entry and I right-click in the bottom pane, I can add a rule to allow that same IP address, (or any others I like), but restrict it to access only through a certian port, say the SSH port, 22 for example.

I don't know much about Samba at all, but the idea is to find out what port it uses, and filter any incoming traffic to that port to only IP addresses that you know.
You'll see the open port when you run a port scan.

If you want to know the IP addresses of your other Ubuntu machines, run the command 'ifconfig', and that has the IP address in the output.

If you click the 'help' menu, there's an on-line users manual, and Firestarter has it's own website too.

---

### Post by Herman on 2008-05-11
> Something else to realise is that if you are connecting to the Internet via an ADSL router, any port scanning sites, such as Shield Up will report back on the firewall in your router, not iptables. Yes, that's right, and actually, to get through your ADSL router when you want to let someone in you need to do what is called 'port forwarding', or else you or a friend of yours can't connect to your own computers from the internet.
Maybe you'll need to do that in your router too, if you have a router between your computer and your ADSL modem. 

There's a special website dedicated to helping you do that if you need to, 
**[PortForward.com - Free Help Setting up  Your Router or Firewall]("http://portforward.com/")**

---

### Post by Herman on 2008-05-11
A link to a nice but short video about network packets and firewalls, [Warriors of the Net]("http://www.warriorsofthe.net/")

---

### Post by Herman on 2008-05-11
Here are a few links about the new UFW (_U_ncomplicated _F_ire _W_all) that is a new feature in Ubuntu Hardy Heron.

[U][UbuntuFirewall - Ubuntu Wiki]("https://wiki.ubuntu.com/UbuntuFirewall")


[UFW (Uncomplicated firewall) For Ubuntu Hardy -- Ubuntu Geek]("http://www.ubuntugeek.com/ufw-uncomplicated-firewall-for-ubuntu-hardy.html")


[My Mom Learns the “Uncomplicated Firewall” on Ubuntu 8.04]("http://beginlinux.wordpress.com/2008/04/23/my-mom-learns-the-uncomplicated-firewall-on-ubuntu-804/")
[/U]       
I'm trying it out right now to see what it's like. It seems to be all command line stuff at this stage, anyway, which is okay for those of us who have been using Ubuntu for a while. I wonder if they'll be working on a nice GUI for it later on. Quite possibly.

---

### Post by brian_p on 2008-05-11
> **nowshining said:**
> brian_p - Bots, Worms, People are all scanning all the time to find non-firewalled computers to break into. Linux can be broken into just like windows, altho it is a bit harder as it's easier to break into windows.

Happens fairly frequently to this machine. The scans are scripted or from infected Windows machines and they often find the open ports 22 and 25. But there is no intelligence behind them and they are futile.

The closed ports (it's unfashionable I know, but they are not stealthed) are of no concern and because I really, really want to offer smtp and ssh services there is nothing a firewall can offer me.

> When u get hacked or already are don't come crying to us. ;)

My software is up to date. There are no existing worms capable of attacking the services and if one did appear a firewall would be of no use. But you would like me to install a bot? I'll think about it!

---

### Post by Gone fishing on 2008-05-11
I think my take is there is some good advice in this thread, however, folk can get a bit over paranoid about being hacked particularly if they come from Windows (and we mostly do!) as the security in 9x and XP is close to non existent.

If you have a default install and are protected by your router I wouldn't worry, and remember that if you get your system scanned using grc you are scanning the router not your PC. However, if you start running services such as SAMBA yes you probably do need to configure a firewall. One thing that can be useful in a firewall is to open only requests coming from a particular device or a particular (say local area network) IP range.

---

### Post by brian_p on 2008-05-11
> **JGFuller said:**
> As a recent new Ubuntu user, I was also concerned about a firewall, having always used the built-in Windows XP firewall.

Knowing why you needed a firewall with XP would clue you in to why you do not need one for a single machine running Linux.

> So I tried Firestarter, and activated it using the GUI, with no additional information added.  I was then not able to print to a Windows shared network printer, until Firestarter was Disabled.

Ubuntu is installed on a Compaq Presario 2200, using Wubi.  The Windows config is Windows XP Home; SP 2.

Any suggestions?

Return the iptables rules to their defaults. Uninstall firestarter. Read the Networking section of /etc/samba/smb.conf. Note that you can make samba inaccessible from the internet. Forget about firewalls.

---

### Post by brian_p on 2008-05-11
> **Gone fishing said:**
> . . . . However, if you start running services such as SAMBA yes you probably do need to configure a firewall.

That is the second time that claim has been made regarding samba. I imagine it means using iptables to block all ports (none of which are open in the first place) and then opening the ports used by samba. So - back to where you would be by simply installing the service!

> One thing that can be useful in a firewall is to open only requests coming from a particular device or a particular (say local area network) IP range.

This can be handled very effectively by smb.conf.

---

### Post by hyper_ch on 2008-05-11
I still think for most people here they don't need to configure iptables at all...

---

### Post by Gone fishing on 2008-05-11
> That is the second time that claim has been made regarding samba. I imagine it means using iptables to block all ports (none of which are open in the first place) and then opening the ports used by samba. So - back to where you would be by simply installing the service!

True but if you have two interfaces you can drop requests coming from the public interface so that only requests come from the private interface the same is true for public versus private IP ranges. Yes you can do it in the samba conf file and in other applications such as the squid conf etc, but I can't see anything wrong with blocking requests coming from a public interface using a firewall and the squid conf file isn't as user friendly as some firewalls and the user might wish to open other services for example VNC etc which they would like to be available on the local area network but not publically yes I agree again we could/should block on the application but... surely Linux has a firewall capability because it's useful?

However, I do agree ubuntu is safe by default and many users don't need a firewall.

---

### Post by rye_ on 2008-05-11
without trawling through the previous comments in this thread......
ufw is installed by default

type at the command line 
   man ufw

---

### Post by brian_p on 2008-05-11
> **Gone fishing said:**
> . . . .  yes I agree again we could/should block on the application but... surely Linux has a firewall capability because it's useful?

Indeed it is useful and there can be situations in which packet filtering may be the best or only option, especially where there is a network of machines. For example, suppose you have a VoIP device with ftp, telnet and http services exposed to the internet and the manufacturer doesn't provide updates. Also there is no facility to switch the services off. Effectively you have no control over the device and may see the need to use iptable rules to block access to the relevant ports on the device.

> However, I do agree ubuntu is safe by default and many users don't need a firewall.

Most queries about firewalls come from people who have Ubuntu on a machine or two. They are in a position to control what runs, how it runs and how often to update. And yet a frequent response is to point them immediately in the direction of firestarter or ufw. It's almost as though there is some niggling doubt about the security of Ubuntu. Or it could be the result of the conditioning Windows users are subjected to.

---

### Post by nowshining on 2008-05-11
having no firewall is like wearing NO armor when one is about to go into an un-known and darkened forest.

With Windows - ur running yelling thru the forest letting everyone know ur there incase there are inhabitants there who have became one with the forest & don't know of ur kind and either they be g ood or bad and incasee their bad - ur dead - 'cause u got no armor.

With Ubuntu/Kubuntu - same thing, excpet for ur real quiet and if the inhabitants were there itta be awhile for them to find you since ur sooo quiet however when they do it's death time for u if ur armorless, however if u have armor - u can still put a fight and won't be immediately killed 'cause u have on armor on which gives u a chance to put up a fight.

:)

---

### Post by hyper_ch on 2008-05-12
If you're running linux your so agile and quick that you won't get killed anyway in the forrest ;)

---

### Post by wootah on 2008-05-12
> **brian_p said:**
> 
...<snip>...
Most queries about firewalls come from people who have Ubuntu on a machine or two. They are in a position to control what runs, how it runs and how often to update. And yet a frequent response is to point them immediately in the direction of firestarter or ufw. It's almost as though there is some niggling doubt about the security of Ubuntu. **Or it could be the result of the conditioning Windows users are subjected to.**

I think you got it there brian_p. When I moved to Linux, I felt the need to lookup information about firewalls pretty much as the first task. At that point I wasn't even running any services! I guess that is the 'Windows conditioning' at play :( 

On the other hand, I think a tool like firestarter can provide a gentle intro into iptables. We all know iptables can get a little... evil ](*,)

---

### Post by Gone fishing on 2008-05-12
Agreed many Windows users want to install an AV and a firewall immediately, as they're used to an OS that has almost no security by default. I think I largely agree with brian_p Ubuntu is safe by default and you don't need to start adding this stuff unless you need it. I remember that Xandros used/still does? add a security center with firewalls etc - why? - not because it was needed but to make ex Windows users happy.

Its probably best to keep things minimal and only add stuff thats needed, however, I think when you start opening services on a PC thats directly connected to the net maybe it's now sensible to use a Firewall, but if your not running any services and have no open ports do you need a firewall?

---

### Post by kamitsukai on 2008-05-14
Erm....well thanks lol

---

