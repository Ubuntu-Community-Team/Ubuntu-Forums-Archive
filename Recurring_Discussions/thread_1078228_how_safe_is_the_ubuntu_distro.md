---
title: "how safe is the ubuntu distro?"
date: 2009-02-23
forum: Recurring Discussions
---

### Post by colifato13 on 2009-02-23
Is it safe enough to not install security programs if there is no personal data on the pc.

---

### Post by binbash on 2009-02-23
You don't need to install anything on a desktop computer.

---

### Post by bertolo on 2009-02-23
yeah. hackers don't fly on air.

---

### Post by colifato13 on 2009-02-23
not even a firewall?
[U]
to binbash[/U]
what do you mean by "You don't need to install anything on a desktop computer."
are you talking about linux based systems?

---

### Post by geirha on 2009-02-23
Linux has a built-in firewall called iptables, which is completely open by default. A fresh install does not have any processes listening on the network, so there's no need for a firewall. If you still want to restrict access with the firewall though, there are several graphical front-ends to iptables; [firestarter](apt:firestarter) is often mentioned. 

I've got apache, openssh-server and vnc listening on the network with no firewalls blocking the path. Never had any problems. Ubuntu is secure by design, unlike certain other OSes.

---

### Post by colifato13 on 2009-02-23
That's what i heard a while ago, that linux was proven the most secure OS in the tipping point contest, But i wasn't sure about files that come with malware.

Does firestarter allow to block traffic going from your pc to outside?

thanks for helping

---

### Post by AndyCee on 2009-02-23
> Is it safe enough to not install security programs if there is no personal data on the pc. 
As usual with computing security, it depends on your set up. Most modems/routers come with a firewall. So if the machine in question is behind one with a firewall, you shouldn't need to set up one in Ubuntu.

I'm not an advocate of the concept that Linux = no security threats. It's just very very unlikely at this time to be compromised in a basic home setup. I'd hate to be one of the few, however.

Short answer - firewall doesn't hurt, but that's all you should possibly need for a typical home set up at this point.

---

### Post by AndyCee on 2009-02-23
> **colifato13 said:**
> That's what i heard a while ago, that linux was proven the most secure OS in the tipping point contest, But i wasn't sure about files that come with malware.

Does firestarter allow to block traffic going from your pc to outside?

thanks for helping

Most malware only runs on windows machines, but it's perfectly possible to download a trojan on linux - it's just 99.9% unlikely to do anything on Ubuntu.


How to write a linux virus
[http://www.geekzone.co.nz/foobar/6229](http://www.geekzone.co.nz/foobar/6229)

---

### Post by konqueror7 on 2009-02-23
just install the graphical front-end as said above, firestarter, update your system regularly (not that it has a security hole, just to make it stronger;)) and you will be fine...

leave your paranoia in windows, this linux!:D

---

### Post by geirha on 2009-02-23
> **colifato13 said:**
> That's what i heard a while ago, that linux was proven the most secure OS in the tipping point contest, But i wasn't sure about files that come with malware.


If you only install software from the repositories, you'll be as safe as can be, but if you need software not in the repositories, then you should thread softly. Installing a package with malware will of course compromise your system, so it all depends on how much you trust the site you download from. This goes for any OS. If you are told somewhere to run a script or a command, and you don't understand what the script/command does, ask at the forums if anyone can interpret it for you. Chances are high that someone can.

> 
Does firestarter allow to block traffic going from your pc to outside?

thanks for helping
iptables can do that, so firestarter probably will allow you to set that up, but I haven't used firestarter myself, so I don't know what it allows you to do.

---

### Post by albinootje on 2009-02-23
> **colifato13 said:**
> Is it safe enough to not install security programs if there is no personal data on the pc.

Only saying that Linux is very secure is not enough imho.
It also depends on the behavior of (you) the user.
If you fill in credit card details on a dodgy website, then it doesn't matter whether you use OpenBSD, Linux or MS-Windows.

Amongst others I recommend the WOT and noscript add-on for web surfing with Firefox :
[https://addons.mozilla.org/en-US/firefox/addon/3456](https://addons.mozilla.org/en-US/firefox/addon/3456)
[https://addons.mozilla.org/en-US/firefox/addon/722](https://addons.mozilla.org/en-US/firefox/addon/722)

With the warning that noscript has a learning curve and can be a pain to use if you don't want to spend time on it per page that you visit.

For more information on Linux viruses and worms :
[http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses](http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses)
[https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)

---

### Post by colifato13 on 2009-02-23
thanks for helping me.

lately I've been reading alot about linux, i even so the movie revolution OS and i never heard of the fact that _AndyCee_ said, I'm gonna start telling people that as one of the top 5 reasons to change to linux/GNU.


I don't really belive that linux is unhackable, but the community is doing a really good job in keeping it clean.


dude seriously, i do get paranoid on windows i get outgoing traffic from programs that i've deleted a long time ago.

---

### Post by sisco311 on 2009-02-23
[thread=510812]Ubuntu Security[/thread]

---

### Post by colifato13 on 2009-02-23
thank you for clarifying that _geirha_ that's what i was asking about. I'm going to try firestarer as soon as i get ubuntu to boot.

Thanks for those add-ons _albinootje_ i'm going to try them as soon as i can. if its a good app i don't care about learning it.

hey _sisco311_ thanks for point me to that thread.

---

### Post by Faolan on 2009-02-23
People banter Linux as being secure. For a home user it's fairly secure but soon as you start putting services such as SSH, SAMBA, etc on your box then you will need to lock it down. Don't fall into the Mac fallacy it's secure. All systems that have user interaction are vulnerable by their nature.

Have a read of this report. Linux Kernel is considered to be more insecure than any Window varient. Don't confuse this with active malware this is publically declared vulnerabilities. How you measure how severe a vulnerability is far more complex and will go outwith the remit of this post suffice to say if you lock down Windows it's just as secure as Linux can be and can be just as easy if you use the Group and User policies for multiple users and roll outs.

[X-Force Trend Report - [COLOR="Red"]PDF[/COLOR]]("http://www-935.ibm.com/services/us/iss/xforce/trendreports/xforce-2008-annual-report.pdf")

This a post about Windows and it's security, partially to back up what I say about the system:

[Restriction of privileges]("http://www.securecomputing.net.au/News/136475,removing-admin-rights-can-stem-microsoft-exploits.aspx")

Windows Vista is far more secure than any other Microsoft OS (other than M$ server varients) previously which has annoyed the hell out of many users and software manufacturers because it 'broke' how they liked to work.

Also a brief overview of a Linux security flaw by design:

[Crafting a Linux Virus]("http://www.geekzone.co.nz/foobar/6229")

Overall Linux Desktop enjoys a good security reputation for several reasons, most users are usually technically aware of vulnerabilities and solutions, it's vector profile is fairly narrow compared say to Windows and also it's a minority OS (excluding servers which are not applicable here). Skript kiddies, haxors, criminal gangs, etc. won't spend the time creating something that doesn't give a return on investment. For example for a long time Firefox was considered secure and safe from hackers but in recent months it's profile is being more aggressively targetted by all groups. This is the nature of the beast and will continue as long as their is profits to be made.

What to do about all this? Education to the user will certainly help as most breaches now occur because of social engineering but Darwinism will take it's place irregardless. At the end of the day all we can do is do lockdowns and minimise our exposure to security threats irregardless of the OS. It's easier for users to lockdown Windows as it's been spoon fed to them since XP however transitioning to a new OS with a whole new architecture is likely to cause a lot of problems as newbies won't know about securing it...

---

### Post by albinootje on 2009-02-23
> **Faolan said:**
>  Have a read of this report. Linux Kernel is considered to be more insecure than any Window varient. Don't confuse this with active malware this is publically declared vulnerabilities. How you measure how severe a vulnerability is far more complex and will go outwith the remit of this post suffice to say if you lock down Windows it's just as secure as Linux can be and can be just as easy if you use the Group and User policies for multiple users and roll outs.

[X-Force Trend Report - [COLOR="Red"]PDF[/COLOR]]("http://www-935.ibm.com/services/us/iss/xforce/trendreports/xforce-2008-annual-report.pdf")

Where exactly in this mentioned pdf is it written that the Linux kernel is less secure than any MS-Windows kernel ?

---

### Post by cdenley on 2009-02-23
> **albinootje said:**
> Where exactly in this mentioned pdf is it written that the Linux kernel is less secure than any MS-Windows kernel ?

I think this is what he's referring to:
> 
For vulnerable operating systems, operating systems from Apple and the base Linux kernel have dominated the top spots for vulnerability disclosures over the past three years.

bottom of page 2

Of course, you shouldn't measure security by the number of disclosed vulnerabilities. The undiscovered vulnerabilities are much more relevant, but of course we don't know about them. I think you should measure security by the number of vulnerabilities which were only discovered after being exploited.

---

### Post by albinootje on 2009-02-23
> **cdenley said:**
> I think this is what he's referring to:

bottom of page 2

Thanks.
> 
Of course, you shouldn't measure security by the number of disclosed vulnerabilities. 
Right.

I would be surprised to see a lot of highly critical remote exploits in the Linux kernel compared to "any" MS-Windows kernel.

And since Microsoft has been putting money in all kind of so-called independent research to show that MS-Windows is supposedly more secure than Linux, it is pretty likely to imagine that Microsoft will not be fairly open about every security hole that they find, and who knows what has not been found yet, and is still being exploited in the wild.

---

### Post by kaldor on 2009-02-23
Linux is definitely hackable; it is just harder to do, and not many people care enough to write viruses and such.


If you are worried about security, enable Ubuntu Firewall:

```
ufw enable
```

---

### Post by Faolan on 2009-02-23
> **albinootje said:**
> Thanks.

Right.

I would be surprised to see a lot of highly critical remote exploits in the Linux kernel compared to "any" MS-Windows kernel.

And since Microsoft has been putting money in all kind of so-called independent research to show that MS-Windows is supposedly more secure than Linux, it is pretty likely to imagine that Microsoft will not be fairly open about every security hole that they find, and who knows what has not been found yet, and is still being exploited in the wild.

This is exactly the same issue I have with Apple if anyone is worse than M$ for security then it's Macs and the lack of transparency they have with their OS. 

At the end of the day most exploits don't come from the OS but the applications running on top of it. Poor coding practices can leave a OS wide open for attack irregardless of OS. This was proven with a Hack to Own competition where a Apple Mac fell first before Windows, and that was through the Safari browser. Ubuntu survived unscathed. Both Vista and OS X was comprimised by another program. No system fell with remote exploits over a LAN which was on the first day of the competition the rules was relaxed on the second day for physical attacks.

[Pwnto0wn]("http://www.techworld.com/security/news/index.cfm?newsID=11825&pagtype=all")

Also people have a nasty habit of blowing security problems out of proportion to drive traffic to their site, fanboys or whatever reason. For example a critical vulnerability may look serious in that it can allow control over the system but the actual steps required makes it harder if not impossible.

I didn't state Microsoft is more secure than Linux, it can be just as secure if you lock it down. Also in many ways it's easier for someone to secure a Windows system due to the tools available for a beginner to use. With Linux it's more difficult because of the sheer variety of tools and dependancy of people expecting newbies to understand CLI interfaces and sometimes archaic command structures.

It's popular to bash Microsoft but their products have become a lot more secure than they used to be. They are not perfect and yes the desktop is bloated but no more so than many Linux distros. With Vista and Win 7 it's getting harder to take out a system. In many ways XP SP 2 was a watershed moment for Microsoft (and as is Win 7 which has been on a diet).

It's impossible for any company or group of people to remove every single vulnerability considering the eco-system that a PC has to live in. You have drivers, programs, third party hardware that can and do introduce new and dangerous vectors. On top of this think of all the thousands upon thousands of code that makes up a OS. So it's easy to miss problems and issues, plus any interaction of a program can cause havoc. Microsoft is the biggest target and will always attrack the most attacks so there's little wonder people will find flaws in the system.

It's also up to users to make sure all systems are updated regularly. The recent Conficker trojan despite Microsoft releasing a patch 6 months previously people still didn't update the OS resulting in the recent botnet. People also run in Admin mode in Windows mainly because they was forced to by software vendors who wanted admin rights notably game companies. It's amazing how many games won't run if you're just a User under Windows. This was and still is a major issue with XP.

So before people jump on to the bandwagon and say a operating system is insecure take a moment to step back and consider what the security measures are in place, what software is being used and also more importantly the knowledge level of the user.

---

### Post by Vince4Amy on 2009-02-23
Ubuntu also includes Apparmor. 

[http://en.wikipedia.org/wiki/Apparmor](http://en.wikipedia.org/wiki/Apparmor)

---

### Post by aysiu on 2009-02-23
> **Faolan said:**
> 
I didn't state Microsoft is more secure than Linux, it can be just as secure if you lock it down. Except that running a limited user account all the time isn't very convenient for most Windows users. The "Run as..." functionality is a bit crippled, and it's also an annoying extra step.

With *sudo*, Ubuntu and Mac OS X have implemented a good balance between security and convenience.

I've generally found with Windows that the proper locking down makes things so inconvenient for users that they take the locks right off and just run as administrator all the time.

---

### Post by WatchingThePain on 2009-02-23
Who remembers that film with Dustin Hoffman called Marathon Man?.
Remember the line.."Is it safe?", put me off going to the dentist for years.

---

### Post by abn91c on 2009-02-23
> **colifato13 said:**
> Is it safe enough to not install security programs if there is no personal data on the pc.
check this article [http://blogs.zdnet.com/security/?p=995](http://blogs.zdnet.com/security/?p=995)
and this one, [http://www.cyberciti.biz/tips/linux-remains-unbeaten.html](http://www.cyberciti.biz/tips/linux-remains-unbeaten.html)
it will answer your questions and help you decide to install Ubuntu
[http://www.ubuntu.com](http://www.ubuntu.com)

---

### Post by sydbat on 2009-02-26
> **WatchingThePain said:**
> Who remembers that film with Dustin Hoffman called Marathon Man?.
Remember the line.."Is it safe?", put me off going to the dentist for years.Best answer yet!

---

