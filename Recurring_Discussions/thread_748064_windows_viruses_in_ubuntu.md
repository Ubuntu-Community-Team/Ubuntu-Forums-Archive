---
title: "windows viruses in ubuntu?"
date: 2008-04-07
forum: Recurring Discussions
---

### Post by boywholinuxed on 2008-04-07
hi,

just like windows applications made to work in windows only cannot work in ubuntu,does this mean that windows viruses cannot work in ubuntu,right??

then does that mean suppose your pendrive gets a virus from a system that uses windows,you dont need to be worried that it will afefect your computer because your system is ubuntu?


then why do we need antivirus,people are saying there is no need for clam av and firestarter,i installed it but is it really important or just a waste of space?

---

### Post by skymera on 2008-04-07
You cant get viruses on Ubuntu. Full Stop.

The antivirus is for scanning files for windows machines if you transfer files.

Yes it's a waste of space.
Windows users should have their own antivirus

---

### Post by boywholinuxed on 2008-04-07
then why does synaptic provide clam av if its a waste?

is there any anti spyware in ubuntu?

---

### Post by muteXe on 2008-04-07
i think linux can act as carriers for windows virues if you're dual-booting or sharing files over FAT.

---

### Post by Boyohazard on 2008-04-07
Whether or not it's a waste is down to your needs. If you are sharing files with a Windows machine that doesn't have anti virus then it may be worthwhile installing clam av.

---

### Post by bonzodog on 2008-04-07
The idea of having clamav available is for those people whose ubuntu machines run in a network with windows machines. Whilst ubuntu cannot itself get the virus, it can unknowingly transmit the virus. 

Also, Firestarter is a Firewall, and firewalls are as much needed in linux as they are in any other OS.

---

### Post by SunnyRabbiera on 2008-04-07
> **boywholinuxed said:**
> then why does synaptic provide clam av if its a waste?

is there any anti spyware in ubuntu?

clam is there to scan windows drives mainly.
and you dont need anti spyware on linux

---

### Post by Znort_Ubern00b on 2008-04-07
You can get viruses for all OS's but the main(and Best) point with Linux is you do not run as root automatically as you do with windows so for a user to allow a virus onto his/her box would require a greater number of steps not just     click, "yes install" 
The most damage you could do with linux(utter stupidity apart) is delete/damage your home drive

see the article below regarding virus threat...

[Windows vs Linux viruses]("http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/")

[Linux Virus threat May 2003]("http://www.desktoplinux.com/articles/AT3307459975.html")

Don't get me wrong, its not all doom and gloom (lol), I have had Ubuntu for sometime now and as yet no virus problems compared to my old windoze box but we do need to have an objective view, people will write viruses for Ubuntu as it becomes more popular, the recent [pwn2own competition 2nd place person ]("http://www.theregister.co.uk/2008/03/29/ubuntu_left_standing/")said he would have been able to re-write his vuln to work on the ubuntu machine. it seems to be more often than not the 3rd party software that allows atacks etc to be made on our machines.

---

### Post by brian_p on 2008-04-07
> **bonzodog said:**
> Also, Firestarter is a Firewall, and firewalls are as much needed in linux as they are in any other OS.

No they are not. Ubuntu's default configurations are safe. A single machine connected to the net gains no benefit from a firewall.

---

### Post by scramasax on 2008-04-07
> **boywholinuxed said:**
> then why does synaptic provide clam av

Canonical probably have corporate users in mind.

Apple ships [Leopard Server](http://www.apple.com/server/macosx/) with ClamAV pre-installed.

Both companies will be making the software available for the same reason.  Suppose you're running a business and you want to use a Unix box as the mail gateway.  You'll likely have Windows users on your network -- you want to stop Windows malware at the mail gateway before it gets to your users.

There's very little malware for Unix-based systems around in the wild.  As a home user you don't need the software, and, therefore, probably don't want to waste CPU cycles running it.  Business users are in a different boat, because of the nature of their networks.  But, if it makes you feel more comfortable, use it.

---

### Post by Sef on 2008-04-07
> No they are not. Ubuntu's default configurations are safe. A single machine connected to the net gains no benefit from a firewall.

That is not correct.  Ubuntu has a firewall installed by default: iptables.  A firewall is necessary, unless the machine is not connected to the net either directly or indirectly.

---

### Post by scramasax on 2008-04-07
> **brian_p said:**
> A single machine connected to the net gains no benefit from a firewall.

This is a different issue from AV scanners.  There's always a danger that some service you have running may have a hole in it, and people can poke at it if you're not running a firewall.

Now, you're OK if you're sitting at home connecting via a NAT router, because NAT routers, by their nature, don't pass unsolicited traffic.

But if you're out and about in the coffee shop or wherever, you really should be using a software firewall.  Canonical wouldn't be making a new, user-friendly firewall available in Hardy Heron:

[http://www.itwire.com/content/view/17452/1141/](http://www.itwire.com/content/view/17452/1141/)

if they weren't aware that this is an up-and-coming need for users.

---

### Post by brian_p on 2008-04-07
> **Sef said:**
> That is not correct. . . . 

What is not correct? Ubuntu's default configuration is unsafe?

>  . . .  Ubuntu has a firewall installed by default: iptables. . . .

iptables is in the kernel. What is Ubunt's default configuration for it?

>  . . .  A firewall is necessary, unless the machine is not connected to the net either directly or indirectly.

What does the firewall protect you against?

---

### Post by hyper_ch on 2008-04-07
iptables is by default unconfigured upon an installation - which does not really matter as no services are running that are listening...

---

### Post by brian_p on 2008-04-07
> **scramasax said:**
> This is a different issue from AV scanners.  There's always a danger that some service you have running may have a hole in it, and people can poke at it if you're not running a firewall.

It is a different issue but it was brought up here.

If you are offering a service you cannot firewall it off. A service with a known security issue should be updated to the secure service which will be available, Or switched off if you are overly concerned.

> Now, you're OK if you're sitting at home connecting via a NAT router, because NAT routers, by their nature, don't pass unsolicited traffic.

But if you're out and about in the coffee shop or wherever, you really should be using a software firewall.  Canonical wouldn't be making a new, user-friendly firewall available in Hardy Heron:

[http://www.itwire.com/content/view/17452/1141/](http://www.itwire.com/content/view/17452/1141/)

if they weren't aware that this is an up-and-coming need for users.

A machine which is configured safely at home is safe anywhere is the world.

---

### Post by boywholinuxed on 2008-04-11
so the bottom line is if u r a home user like me ,theres no use of clam av ?

then is the firewall necessary?

---

### Post by SunnyRabbiera on 2008-04-11
> **boywholinuxed said:**
> so the bottom line is if u r a home user like me ,theres no use of clam av ?

then is the firewall necessary?

well it can come in handy, the system is still vulnerable if you are running it on a constant internet connection.
no OS is 100% secure or safe and this includes linux, however by default a linux system is far more secure then a windows system can hope to be.

---

### Post by Tatty on 2008-04-11
By default, all ports are closed in ubuntu via iptables.  Firestarter is often reccomended as a firewall, however in reality it is simply a GUI for managing iptables.

There is no need to install an extra firewall onto a ubuntu installation.  However, if you want to manage it yourself then you will need to install firestarter to do that.

---

### Post by hyper_ch on 2008-04-11
> **Tatty said:**
> By default, all ports are closed in ubuntu via iptables.

Ports are not closed by default... by default iptables isn't configured at all... but as no services are listening to incomming connections there is no need to close ports. Only after you instal server services you may want to configure iptables - however if you are behind a router, configure the router to do that...

---

### Post by Tatty on 2008-04-11
> **hyper_ch said:**
> Ports are not closed by default... by default iptables isn't configured at all... but as no services are listening to incomming connections there is no need to close ports. Only after you instal server services you may want to configure iptables - however if you are behind a router, configure the router to do that...

Very correct, i apologise :)

Researching it now.

---

### Post by scramasax on 2008-04-11
> **brian_p said:**
> A machine which is configured safely at home is safe anywhere is the world.

If you take your NAT router with you wherever you go.

---

### Post by brian_p on 2008-04-11
> **scramasax said:**
> If you take your NAT router with you wherever you go.

A laptop I have offers ssh as a service and runs an up-to-date sshd. There are no known vulnerabilities in the ssh protocol so communication with it is secure.  That's true whether the machine is at my home or in a hotel in another part of the world.

Being able to ssh into the machine is what I want so blocking with NAT is rather pointless. As is punching a hole in NAT to allow the service to be offered. If I didn't want the machine to be available via sshd the service would be switched off. Conclusion: a router with NAT is not required.

---

### Post by Zralou on 2008-04-11
> **brian_p said:**
> A laptop I have offers ssh as a service and runs an up-to-date sshd. There are no known vulnerabilities in the ssh protocol so communication with it is secure.  That's true whether the machine is at my home or in a hotel in another part of the world.

Being able to ssh into the machine is what I want so blocking with NAT is rather pointless. As is punching a hole in NAT to allow the service to be offered. If I didn't want the machine to be available via sshd the service would be switched off. Conclusion: a router with NAT is not required.

And how many non-techie Ubuntu users run an 'up-to-date sshd'.
Any OS can be vunerable if used by a novice and a hacker is persistant.  Also any OS can be made reasonably secure given the knowledge and tools, the main difference between Windows and Linux is, Linux, by design, has better damage limitation, and most virus writers create them for windows, as that is the primary OS of most computer users, and therefore, will cause the most distruption.

There is only one way to be 100% safe from attacks and viruses, don't turn the machine on!!!.

Sara Lou

---

### Post by Martje_001 on 2008-04-11
> **Znort_Ubern00b said:**
> Don't get me wrong, its not all doom and gloom (lol), I have had Ubuntu for sometime now and as yet no virus problems compared to my old windoze box but we do need to have an objective view, people will write viruses for Ubuntu as it becomes more popular, the recent [pwn2own competition 2nd place person ]("http://www.theregister.co.uk/2008/03/29/ubuntu_left_standing/")said he would have been able to re-write his vuln to work on the ubuntu machine. it seems to be more often than not the 3rd party software that allows atacks etc to be made on our machines.
I wouldn't be that sure.. for several reasons:

Ubuntu cannot execute files from the internet (Windows can)
Ubuntu needs root privileges to continue installing a virus
Ubuntu gets update (if needed) every day

---

### Post by hyper_ch on 2008-04-11
> **Zralou said:**
> And how many non-techie Ubuntu users run an 'up-to-date sshd'.

sudo apt-get install openssh-server

and then running the updates regurarly ;)

---

### Post by KevinD_Atl on 2008-04-11
[FONT="Tahoma"]I use a Ubuntu share for downloading and keeping junk on. I had a WinISO version which contained a downloader.trojan or something like that.  Nothing saw it until I moved it to a Windows share, and the Symantec Corp caught it, and deleted it from the Ubuntu share also. I set the SAV to do that, so Windows and Ubuntu both did thier jobs, respectivly~[/FONT]

---

### Post by brian_p on 2008-04-11
> **Zralou said:**
> And how many non-techie Ubuntu users run an 'up-to-date sshd'.

Ubuntu provides security updates. A user not using them should ask themselves why they do not want to install them to keep their machine safe. Earlier today I did

```
dselect update ; apt-get dist-upgrade
```

Easy, wasn't it? There are other ways. How it is done is unimportant, but it must be done.

> Any OS can be vunerable if used by a novice and a hacker is persistant.

Ubuntu is delivered to you in a non-vulnerable condition and is suitable for use by novices and the more expert alike. If you think it isn't - file a bug. It is the user's job to keep it safe with package updates.

>  Also any OS can be made reasonably secure given the knowledge and tools, the main difference between Windows and Linux is, Linux, by design, has better damage limitation, and most virus writers create them for windows, as that is the primary OS of most computer users, and therefore, will cause the most distruption.

Viruses aren't a problem; none exist for Linux. Trojans and worms are a danger.

> There is only one way to be 100% safe from attacks and viruses, don't turn the machine on!!!.

This defeats the purpose of communication.

---

### Post by hyper_ch on 2008-04-11
> **brian_p said:**
> Viruses aren't a problem; none exist for Linux.

Remember the other thread? ;)

---

### Post by brian_p on 2008-04-11
> **hyper_ch said:**
> Remember the other thread? ;)

Yes, it was a pleasant exchange of views. Still searching for malware  which will spread without root assistance? :smile:

---

### Post by hyper_ch on 2008-04-11
> **brian_p said:**
> Yes, it was a pleasant exchange of views. Still searching for malware  which will spread without root assistance? :smile:

Why should I? I've profen there are viruses for linux... another question is how much damage they actually do in the wild is something totally different ;)

---

### Post by Tyke91 on 2008-04-11
that's true... it's very possible for us to GET windows viruses... they come with email attachments and unsecured shared folders (among other things), but how much damage they do is completely different... maybe they waste a few kilobytes of disk space?

---

### Post by scorp123 on 2008-04-11
> **Sef said:**
>  Ubuntu has a firewall installed by default: iptables.  A firewall is necessary,. The firewall doesn't do anything per default, it's not active. And what do you need a firewall for if per default you have no services, no daemons and no programs whatsoever listening and waiting for incoming connections?

This isn't Windows. On Windows you have tons of stupid and obsolete network services _always_ running in the background which are _always_ waiting for connections from anywhere. Instead of fixing those services or --even better-- getting rid of them Microsoft decided to give XP this joke of "personal firewall" ("joke" because it's still easy to trick it into allowing things it should not allow ...) to protect the services ... which would not need protection at all if they were not there in the first place!

:)

---

### Post by scorp123 on 2008-04-11
> **bonzodog said:**
> and firewalls are as much needed in linux as they are in any other OS. What do you need a firewall for if you are not running any services whatsoever that would need that protection in the first place?? :)

---

### Post by scorp123 on 2008-04-11
> **boywholinuxed said:**
>  does this mean that windows viruses cannot work in ubuntu,right??  Linux uses a different binary format than e.g. MS-DOS and Windows. In other words: There is no way how you could natively start a binary program for those other operating systems on Linux. Same is true for viruses. Ultimately they are just programs too. And there is no way they could be started, activated or executed on Linux ... the binary format is totally different.

For Windows programs --and that includes viruses-- to become active on Linux you'd have to give them an environment in which they can function, e.g. VMware or WINE. VMware basically simulates an entire PC and you have to have a real Windows installation in there in order to use Windows. So yes, a virus could infect a VMware virtual machine and do damage in there. Similar for WINE: Some viruses can become active in WINE (e.g. if you activate an infected program) and they could damage other programs installed inside the WINE environment, but they cannot break out of this "sandbox" and do real damage to your Linux system or to your real /home directory .... One would have to be really really creative here in order for this to happen.

So to summarise my answer:
- DOS/Windows viruses cannot be activated natively on Linux
- Anti-Virus software for Linux is a waste of space
- DOS/WIndows viruses could be activated and do some damage inside VMware or VirtualBox virtual machines running DOS or Windows as OS
- DOS/Windows viruses could be activated and do some limited damage inside a WINE environment, but they cannot break out of their "sandbox" and do any real damage (just wipe your WINE folders and get rid of those infected files, and voila, you're done).

---

### Post by Zralou on 2008-04-11
> **hyper_ch said:**
> sudo apt-get install openssh-server

and then running the updates regurarly ;)

NOW I know how to install openssh, 10 minutes ago I didn't, until you tolds me.  Just like if I was having problems with Linux and you offered to help by telling me to run a script with the 'sudo' command that just happened to be a virus (commonly called "social engineering"), my system would then be infected, and able to do damage because I used 'sudo' giving it full reign on my system.
All of you who are claiming Linux is 100% safe are baising your assumptions on the fact the user has enough knowledge not to do anything to make their system vunerable.  That isn't always the case, I myself, in the past, have downloaded Linux and just play'd around in it, not knowing what I was doing, but thats how I learn, just the same as I did with Windows 3.1 14 years ago (I crashed that system SO many times in the first month, it wasn't funny).

So, yes, Linux is 100% more secure than windows will ever be, but 100% secure, no, I disagree.

Sara Lou

---

### Post by hyper_ch on 2008-04-11
if people refuse to think they will be victims ;) however I assume people on here have the ability to think...

---

### Post by nico_h on 2008-04-11
> **bonzodog said:**
> 

Also, Firestarter is a Firewall, and firewalls are as much needed in linux as they are in any other OS.

it isn't a firewall, it is a gui to manage the firewall (which is actually included in deeper components, maybe the kernel... see iptable...) firestarter is useful if you want to define special filtering rules, for example...

check [this article]("http://librenix.com/?inode=21") too

---

### Post by scorp123 on 2008-04-11
> **Zralou said:**
>  All of you who are claiming Linux is 100% safe  Nobody said that. Linux **does have** security problems like every other OS. Just not viruses or spyware. Other OS ... other problems.

In my experience as sysadmin the most security issues arise if people install stuff they have no clue about and then leave it open ... Example: One of my apprentices once installed a MySQL database .... But did he care to change the default DB admin password? Nope. There you go. Big security problem. And had we connected this machine to the Internet we would have been hacked in no time. That's the kind of security problems you will most likely face on Linux.

But viruses? Nope.

> **Zralou said:**
>  but 100% secure, no, I disagree.  And you are perfectly right to do so, because nothing can ever be 100% secure. All I am saying is that viruses are not an issue here and unless you don't run any services that allow incoming connections you even don't need a firewall here.

---

### Post by Zralou on 2008-04-11
To quote a speaker at the 2006 Virus Bulletin conference:
> The weakest component in a secure network is the person between the keyboard and the chair.

Is there not 'malware' aimed at Mac operating systems?, and, correct me if i'm wrong, don't Linux and Mac share the same Unix base system?.
The more 'user friendly' linux gets, the more people will use it, and once it becomes a major player in the OS market, hackers, coders, etc will turn their attention to it with the intention of infecting the niave, the unweary, and the unprepared, its just a matter of time.

Sara Lou

---

### Post by scorp123 on 2008-04-11
> **Zralou said:**
>  correct me if i'm wrong, don't Linux and Mac share the same Unix base system?  You are hereby corrected. Linux and Mac are different beasts. They are both "UNIX-like", yes. And Mac OS does have a "UNIX-like" operating system underneath Apple's shiny GUI (that part is called "Darwin" and is based on the MACH kernel project and derived from a BSD UNIX ... Read here: [http://en.wikipedia.org/wiki/Mac_os_x#History](http://en.wikipedia.org/wiki/Mac_os_x#History) )

Linux was written from scratch back in 1990 and does not have any sources in common with MACH, BSD oder Mac OS ...  Technically one could argue that Linux is a "UNIX emulation". It behaves like a UNIX OS, it feels like a UNIX OS, but technically and legally it isn't one.

> **Zralou said:**
>  The more 'user friendly' linux gets, the more people will use it, and once it becomes a major player in the OS market, hackers, coders, etc will turn their attention to it with the intention of infecting the niave, the unweary, and the unprepared, its just a matter of time. I keep hearing and reading this FUD since I switched to Linux back in 1996 .... And guess what? It's still not happening. :lolflag:

And as for hackers: They are already long attacking Linux ... just not the home user but rather those big fat juicy corporate servers everyone seems to use these days. These are far more interesting targets. 

So your argument is rather weak, sorry to say so.

---

### Post by aysiu on 2008-04-11
You're kind of contradicting yourself there, scorp123. The big, fat, juicy corporate servers are interesting targets because Linux is popular among servers. That was Zralou's point: the more popular Linux becomes on the desktop (home use), the more attracted a target it will be.

And there's only so much an OS can do to protect "the naive... and the unprepared," since social engineering bypasses all built-in security and relies on the user being tricked into installing something malicious. This could happen on Windows, Mac, or Linux.

---

### Post by hyper_ch on 2008-04-11
or one could lock down a system so much that a normal user can't do anything anymore... not even using the system any longer --> sort of the Vista + 2

---

### Post by scorp123 on 2008-04-11
> **aysiu said:**
>  The big, fat, juicy corporate servers are interesting targets because Linux is popular among servers. Yes, and that's been the case since 1992 or so, since people started to buy the first commercial distros that were available and installed these things on their PC-based servers. Those servers have been targets for hackers ever since. **This isn't a new development.**

That's what I was trying to say here. The argument "just you wait until Linux gets more popular and then hackers will attack it" is therefore a weak one. They are already attacking it, since the early 90's.

> **aysiu said:**
>   That was Zralou's point: the more popular Linux becomes on the desktop (home use), the more attracted a target it will be.  As I said, I keep hearing that since 1996. And I haven't seen it happen yet. As Linus Torvalds once said: "Show me the code ... "

Show me a Linux virus that is spreading "Windows-style" in the wild and I will admit that you / she was right and I was wrong. But until then this is FUD I have been hearing for the past 10+ years.

Besides, as for the malware that recently was found for Mac OS X:

I did some research and some Googling concerning this and it appears that this stuff is being spread e.g. via certain adult web sites (there are articles in German on [www.heise.de](www.heise.de) describing the details). The user first receives an error message saying something like "The content can't be displayed" and then gets tricked into believing they are installing some newer version of Apple QuickTime so they can see whatever they were supposed to see on that "adult" web site. They get asked for their admin password and voila, the malware can install itself thanks to the help of the user ...

I question whether this could happen on Ubuntu. For this to work the same way you'd have to trick people into downloading a prepared *.deb or *.rpm package .... Maybe this would indeed work? Or maybe not.

Fact is that on all the machines where I am admin users have no access to "sudo" or the "root" account. Not ever. Same for all the people I converted to Ubuntu: They don't have and don't need access to "sudo" (on the other hand: if they need anything they can call me in the middle of the night ... so far all of them are happy with this arrangement). So I can pretty much guarantee that on all the machines I have touched something like the above can't happen.

The thing that really worries me lately is a few users using really weak passwords on their mail accounts ... But viruses? Malware? Nope, trust me: Haven't yet lost any sleep over that ;)

---

### Post by scorp123 on 2008-04-11
> **hyper_ch said:**
> or one could lock down a system so much that a normal user can't do anything anymore ...  "anything critical or dangerous". Yes. That's what I do. See above. Even in my private sector. All the neighbours, friends and relatives I converted to Ubuntu: None of them has access to "sudo". They know this. I told them. And they also know where and how to reach me if they need something. And guess what? So far nobody has ever called me during the night. All these people are happy beyond description that their PCs "just work". And I can sleep happily during the night knowing that they can't hose their own system.

Updates etc. are done automagically via "cron" jobs behind their backs. They all know this as well. And they are happy -- the less they have to bother with these sysadmin things the happier they are. :)

As I said ... that's how I do it here.

---

### Post by aysiu on 2008-04-11
> **scorp123 said:**
> 
That's what I was trying to say here. The argument "just you wait until Linux gets more popular and then hackers will attack it" is therefore a weak one. They are already attacking it, since the early 90's.

 As I said, I keep hearing that since 1996. And I haven't seen it happen yet. As Linus Torvalds once said: "Show me the code ... " But desktop Linux hasn't become a big enough target yet--that's the whole point.

> Show me a Linux virus that is spreading "Windows-style" in the wild and I will admit that you / she was right and I was wrong. But until then this is FUD I have been hearing for the past 10+ years. No one said anything about a Linux virus spreading Windows-style. We're just talking about being the target of more malware in general.

> Besides, as for the malware that recently was found for Mac OS X:

I did some research and some Googling concerning this and it appears that this stuff is being spread e.g. via certain adult web sites (there are articles in German on [www.heise.de](www.heise.de) describing the details). The user first receives an error message saying something like "The content can't be displayed" and then gets tricked into believing they are installing some newer version of Apple QuickTime so they can see whatever they were supposed to see on that "adult" web site. They get asked for their admin password and voila, the malware can install itself thanks to the help of the user ...

I question whether this could happen on Ubuntu. For this to work the same way you'd have to trick people into downloading a prepared *.deb or *.rpm package .... Maybe this would indeed work? Or maybe not. It's not in question at all. If you can trick people into downloading and double-clicking a .deb package, the .deb package has system-wide privileges and can install a rootkit or do pretty much anything it wants.

Social engineering can work in Linux just as well as on other platforms if you have enough users.

> Fact is that on all the machines where I am admin users have no access to "sudo" or the "root" account. Not ever. Same for all the people I converted to Ubuntu: They don't have and don't need access to "sudo" (on the other hand: if they need anything they can call me in the middle of the night ... so far all of them are happy with this arrangement). So I can pretty much guarantee that on all the machines I have touched something like the above can't happen. That's great, but most Ubuntu home users install Ubuntu themselves and *do* belong to the *admin* group.

---

### Post by scorp123 on 2008-04-11
> **aysiu said:**
>  But desktop Linux hasn't become a big enough target yet--that's the whole point.  I fail to see why desktop Linux even should become a target ... Windows users are interesting targets because you can turn their machines into zombies and then have them distribute your spam mails for you in anonymous ways ... But as far as UNIX / Linux hacking goes: Why would a UNIX / Linux hacker bother with home users? I am not questioning the feasibility but rather the logic behind this: If a hacker or cracker manages to crack his way into a server he's in Heaven anyway. He can manipulate daemons, databases, web pages and log files and pretty much do whatever he wishes once he has gained access to some important system accounts and possibly and ultimately gained "root" priviledges. Servers have way better internet connectivity, they are way more interesting targets ... Why should any self-respecting hacker ever even consider to attack a Linux home desktop? Chances are that Linux home desktops aren't running any exploitable services anyway, and that people will turn those machines off e.g. during the night.

A server however has a far better chance of running exploitable services (e.g. a web server, application server, FTP, mail, whatever ...) and being available as target 24 x 7 day and night.

If I wanted to spread spam I'd be stupid if I targeted Linux home desktop users ... Way too much work. It's so easier to either infect a few Windows desktops or to attack a MTA-server somewhere somehow. If you keep scanning long enough on the right TCP ports you will sooner or later find a server with an unpatched version of e.g. "sendmail" or "wu-ftpd" or maybe even one of those vulnerable "bind" releases. That's in any case much much much easier than going after Linux home desktops.

So even if Linux were more popular on the desktop ... I am not really convinced it would become such a big target.

> **aysiu said:**
>   It's not in question at all. If you can trick people into downloading and double-clicking a .deb package, the .deb package has system-wide privileges and can install a rootkit or do pretty much anything it wants.  Yes, I agree. But then again that's why we keep telling users not to download packages from dubious sources, right? And why things such as Automatix are bad because you don't really know what this thing is doing behind your back in addition to potentially breaking your system beyond repair.

> **aysiu said:**
>  Social engineering can work in Linux just as well.  Yes, true.

> **aysiu said:**
>  most Ubuntu home users install Ubuntu themselves and *do* belong to the *admin* group.  I wonder if it would not be a good idea to change that? e.g. offer the users a "hardened Install" option where they would not be in the admin group automatically ... ?

---

### Post by brian_p on 2008-04-11
> **Zralou said:**
> To quote a speaker at the 2006 Virus Bulletin conference:
> The weakest component in a secure network is the person between the keyboard and the chair. 


I've seen this statement in one form or another on a number of occasions. It is glib and misleading. While the operator of a machine (I'm using the word in its most general sense) is a link in the security chain she is dependent on the machine operating as designed. Poorly designed machines are not unknown and neither are the disasters which they sometimes produce.

The giveaway in the quote is the use of 'secure' to describe the network. This is the classic way of shifting the responsibility from where it belongs to someone lower down the chain and diverting attention away from the question of why that so-called secure network failed.

> The more 'user friendly' linux gets, the more people will use it, and once it becomes a major player in the OS market, hackers, coders, etc will turn their attention to it with the intention of infecting the niave, the unweary, and the unprepared, its just a matter of time.

No OS can completely protect the user from his own follies. Provided he does not have root access any damage is limited to his own files.

---

### Post by Zralou on 2008-04-11
> **scorp123 said:**
> 

 Yes, I agree. But then again that's why we keep telling users not to download packages from dubious sources, right? And why things such as Automatix are bad because you don't really know what this thing is doing behind your back in addition to potentially breaking your system beyond repair.


People have been telling windows users the same thing for years, but people still download stuff without really knowing whether its safe or not.
> **scorp123 said:**
> 

 I wonder if it would not be a good idea to change that? e.g. offer the users a "hardened Install" option where they would not be in the admin group automatically ... ?

Kinda like the Bill Gates line of thinking really, users don't need to know whats going on, just give them what they're told they want.
I always thought the idea of Linux was freedom to do as you wish with the operating system, without restrictions.  Locking it down so people can't screw it up, kind of goes against the whole principle of the Linux project.  Perhaps we could introduce some kind of "activation" process to make sure the system is running the way it was designed to run. :)

Sara Lou

---

### Post by scorp123 on 2008-04-11
> **Zralou said:**
>  People have been telling windows users the same thing for years, but people still download stuff without really knowing whether its safe or not.  The difference being that on Windows you're already logged in with full admin powers and that many Microsoft products for extremely stupid reasons will often auto-execute things without even bothering to ask you. Take Outlook for example: It used to auto-execute attachments, and to achieve this it was enough if you had the preview pane activated.

This is not really comparable to e.g. Ubuntu where downloading a *.deb package per se doesn't yet do anything. You have to click on it and type in your admin password for anything to happen.

> **Zralou said:**
>  Kinda like the Bill Gates line of thinking really, users don't need to know whats going on And how so? Hardened installations are pretty much standard in company environments and I also do this in my private environment (see above) and people are happy with this. If anyone needs to do anything special they could still use "su - adminname" to switch into an account which indeed is in the "admin" group or I setup "sudo" so that they can execute specific commands. That's pretty much standard and has nothing to do with "users don't need to know whats going on" .... Let's face the truth: Most users **don't want to know** what's going on. They just "want to use their machine". I keep hearing that over and over again by all the friends and relatives who I converted to Ubuntu. That is just fine with me and the very reason why those people don't have access to "sudo" ... they don't need to.

And as I said above: I don't want to enforce this model on anyone. But a "hardened install" where the users are not automatically members of the "admin" group should at least be available as option.

> **Zralou said:**
>  I always thought the idea of Linux was freedom to do as you wish with the operating system, without restrictions.  Sure, go ahead.

> **Zralou said:**
>   Locking it down so people can't screw it up, kind of goes against the whole principle of the Linux project. Nonsense. This has nothing to do with the "Linux project" in any way. And the boxes I am administrating are locked down because either company policy **dictates** those boxes be locked down or because the people whom I converted **want it** to be locked down for their own safety (if they need something they call me instead ... free 24 x 7 support, what could you want more?)

Looking at Vista and the UAC thing ... Actually I have to give credit to Microsoft that the idea per se isn't so bad. It's just that the implementation of this whole thing is downright bad and totally sucks. I think this Apple commercial hits the nail pretty much on the head and illustrates what I mean:
[http://www.youtube.com/watch?v=l-7C-w8jc0w](http://www.youtube.com/watch?v=l-7C-w8jc0w)

Good idea per se ... but the actual implementation leaves much to be desired.

The fact that users could easily be tricked into downloading and installing *.deb packages from dubious sources will sooner or later necessitate something similar ... You yourself said something along these lines a few postings further up. The Mac OS X malwares you mentioned function exactly in this way: users are tricked into believing that they are downloading and installing an update to Apple QuickTime ...

> **Zralou said:**
>  Perhaps we could introduce some kind of "activation" process to make sure the system is running the way it was designed to run.  "Activation" ... ? What would that be good for?

But the rest of your sentence isn't such a bad idea. There are tools out there such as "tripwire" and "rkhunter" which are usually used on servers and check for changed files. Home users most likely don't know these tools and they are not installed per default. Maybe something like those tools would make sense, e.g. a background task that checks important system binaries (e.g. kernel files and shells) for unexpected changes and then alerts the user if those files changed in unexpected ways. Same for network monitoring ... IMHO there should be a tool that informs the user of open network ports and ongoing network traffic ... As admin I have no trouble getting that info out of a shell command ("sudo lsof -n -i -P") but there could be something friendlier for the home user.

The fact that Canonical has decided to include AppArmor since Ubuntu 7.04 and that it will come activated in 8.04 tells me that they are also thinking about these kind of improvements.

And as for your sentence "make sure the system is running the way it was designed" ... Well, I as admin know how to reset an user account or even the entire system to its defaults. No big deal really ... for me. But for the average home user maybe a "Reset to Default" tool wouldn't be such a bad idea? There is already something like this in the repos: Package "gnome-reset" ... But it is not installed per default and it deals with GNOME's settings only. Maybe something system-wide wouldn't be such a bad thing.

---

### Post by Zralou on 2008-04-12
> **scorp123 said:**
> 

 "Activation" ... ? What would that be good for?



That comment was 'tongue in cheek'.....

Sara Lou

---

