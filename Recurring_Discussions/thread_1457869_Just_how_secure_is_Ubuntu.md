---
title: "Just how secure is Ubuntu?"
date: 2010-04-19
forum: Recurring Discussions
---

### Post by seanlano on 2010-04-19
There are increasing reports of cyber-attacks on corporations and governments around the world, including Google, Rio Tinto, BHP Billiton, etc. Links [here]("http://blogs.aljazeera.net/business/2010/03/23/google-and-rio-tinto-find-its-tough-doing-business-china"), [here]("http://news.brisbanetimes.com.au/breaking-news-national/mining-firms-hit-by-china-cyber-attacks-20100419-spc9.html"), [here]("http://www.smh.com.au/business/netbank-woes--cyber-attacks-set-to-spread-20090702-d5un.html"). 

I recall hearing of a case where an employee of Rio Tinto while on a business trip inserted a flash drive into his laptop, which then "infected" his computer with malware which reported back to hackers about business secrets etc., as well as then being able to hack into the entire network when the businessman returned to his office. This is obviously a huge problem. 

There are countless thousands of hacking attempts each day, some of which (like the above) seem fairly easy to prevent. I would assume most of these companies use Windows, which already is a security weakness as far as I am aware. 


My question is: If everyone was using Ubuntu, not Windows, how many and what types of these attacks would be possible? I don't want to get a bunch of "Windows is ****, so it serves them right" sort of things, but an actual justified response please. Presumably DoS attacks would still be possible, but these don't steal private information. What other attacks are there? Are these attacks possible to execute on an Ubuntu target system?

---

### Post by lisati on 2010-04-19
Moved to "Security Discussions"

---

### Post by new_tolinux on 2010-04-19
AFAIK Windows is more vulnerable to attacks like virus-attacks and they are not that easy to use on Linux because the "root" ("sudo") user isn't the same as the normal user. Therefore the main system can't get infected that simple.

A potential security risk in this are upgrades to different software, if the main Ubuntu repository gets poisoned by a virus, guess how many users are ;)

Besides that, it's not impossible to hack yourself a way into linux. It's not impossible to hack your way into _any_ working machine which is connected to the internet. It only should be a bit more work to do so in Linux, due to the constant updates and it's architecture.

---

### Post by iponeverything on 2010-04-19
> 
My question is: If everyone was using Ubuntu, not Windows, how many and what types of these attacks would be possible? I don't want to get a bunch of "Windows is ****, so it serves them right" sort of things, but an actual justified response please. Presumably DoS attacks would still be possible, but these don't steal private information. What other attacks are there? Are these attacks possible to execute on an Ubuntu target system?


As your not wanting to get a bunch of anti-windows junk, I don't even think you needed mention it -- as that type of baiting behaviour is not tolerated in these forums. 

The main threat to Linux systems is poor administration -

- not paying attention to logs (I have seen brute force attacks that persisted for over a year)
- bad passwords (ssh, mysql, etc. etc.)
- badly written web applications
- server misconfiguration (nfs, mail, imap, mysql, etc. etc. etc.)

Your standard desktop install sitting on a private IP running a recent browser and having a person with moderate amount of common sense behind the keyboard -- Is very secure.

---

### Post by ahmatti on 2010-04-19
> **iponeverything said:**
> 
Your standard desktop install sitting on a private IP running a recent browser and having person with moderate amount of common sense behind the keyboard -- Is very secure.

That's a good point! A lot of the security problems occur when the user does something stupid then it doesn't help even if the OS is secure. So Ubuntu doesn't save you from e.g [Phishing]("http://computer.howstuffworks.com/phishing.htm").  

If you need information about Ubuntu vulnerabilities go to: [http://www.ubuntu.com/usn/](http://www.ubuntu.com/usn/)

---

### Post by seanlano on 2010-04-19
OK, so there's still work for the admins to keep it secure. I suppose everything needs maintenance.  

But what things would a Windows admin be doing that a Linux admin wouldn't have to bother with? 

Is it even possible to open a flash drive or e-mail and just be "infected" like it apparently is in Windows?

---

### Post by new_tolinux on 2010-04-19
About a flashdrive: yes. You'll have to be root to mount it.
About email: only a very small posibility. Email runs as the user, therefore the virus/malware has a way to go before it can take over the system.

In my opinion there's nothing a Windows admin would be doing that a good Linux admin isn't doing. I know it's mentioned elsewhere that you don't need to run virusscan software, but the main point of such software is to be protected to any known attack before that attack reaches your machine. Therefore, as an admin, I would suggest installing a virusscanner isn't a bad idea. If you're the only local user on your private machine maybe it's less valuable, but when dealing with other untrusted users in a corporate enviroment I wouldn't take that chance. Untrusted, because a good admin never trusts their users by default, since the machine is their responsibility and not that of the users.

And yes, everything needs maintenance. Always apply the latest (stable!) security patches, otherwise you're probably inviting others to exploit the known issues with the older version.

---

### Post by iponeverything on 2010-04-19
> **seanlano said:**
> OK, so there's still work for the admins to keep it secure. I suppose everything needs maintenance.  

But what things would a Windows admin be doing that a Linux admin wouldn't have to bother with? 

There are a slew of registry modifications that can be made on made on a Windows machine that can go long way toward making less vulnerable. Windows, with it primary focus being ease of use for its customers and ease of installation for third party applications -- Far to many things have fully automated with little or no regard to the potential misuse an application's install process being given access to rings 0 and 1. Many government system have very strict guidelines in place with regard to use and transfer of removable media. It is very hard to protect a windows system from a highly targeted attack from well funded, professional entity. The reason for is that there is a thriving market for unpublished exploits. It's my option that the case of financial, government and corporate institutions that only real way to keep data safe is though a very high degree of data compartmentalization and extreme requirements on user training and policy enforcement.  
> 
Is it even possible to open a flash drive or e-mail and just be "infected" like it apparently is in Windows?

The short answer is yes and no, as I know of no applications in Linux that  will take an automatic action for email attachment or the contents of a thumb drive. Though I am quite sure that if someone wanted have something like this happen it would be possible, it just not the default behaviour. And even if someone was able execute something from userspace in Ubuntu, the ability application to "infect" would be severely limited. 

Also, I should mention that a targeted attack by a professional against an unsuspecting individual, is very hard to guard against, regardless of the operating system. As these types of attacks are rarely confined to just something coming over-the-wire

---

### Post by DrMelon on 2010-04-19
The handy thing is that any viruses manufactured for Windows will not take effect on Linux (unless you explicitly run them using WINE or some virtualization software). Do check for viruses using ClamAV though, as you may not want to pass on a virus to someone who DOES use Windows.

---

### Post by Soul-Sing on 2010-04-19
1) stick to the off. software sources
2) protect your web browser with apparmor and noscript/etc.
3) setting up a server is full of risk when not reading the manuals how to set up and secure it
4) update your system as soon as possible

---

### Post by arubislander on 2010-04-19
Some attacks are aimed at stealing data. If the data the attacker is after is in the user's home directory then the virus (or whatever is used to get at the data) need not have root privileges. The privileges of the logged in user would do just fine.

---

### Post by airtonix on 2010-04-19
1. P.E.B.K.A.C. : 

No one is immune.

2. Virus Scanners : 
see placebo.

3. Root Privileges : 
Circumstantial.


Moral of the story is, stupidity never fails at finding ways to fubar your system.

---

### Post by oldos2er on 2010-04-19
I would add:

4. Social engineering

5. Physical access

---

### Post by EJeanmaire on 2010-04-19
> **seanlano said:**
> 
I recall hearing of a case where an employee of Rio Tinto while on a business trip inserted a flash drive into his laptop, which then "infected" his computer with malware which reported back to hackers about business secrets etc., as well as then being able to hack into the entire network when the businessman returned to his office. This is obviously a huge problem. 

There are countless thousands of hacking attempts each day, some of which (like the above) seem fairly easy to prevent. I would assume most of these companies use Windows, which already is a security weakness as far as I am aware. 


My question is: If everyone was using Ubuntu, not Windows, how many and what types of these attacks would be possible? I don't want to get a bunch of "Windows is ****, so it serves them right" sort of things, but an actual justified response please. Presumably DoS attacks would still be possible, but these don't steal private information. What other attacks are there? Are these attacks possible to execute on an Ubuntu target system?


The answer is most ALL of them.  The tactic used is call social engineering, qhich basically relies on the ignorance of the person(s) using the computer to divulge information that they shouldn't or to perform a malicious action for the attacker.  When the problem is the user, it doesn't matter what operating system they are running.

---

### Post by rookcifer on 2010-04-19
Anytime an adversary has physical access to your machine, he can do what he wants (unless the disk is encrypted and turned off), so those attacks will be the same on Windows or Linux.

As far as remote attacks go, a lot of the problems on Windows are because of stupid users, especially in recent years since Windows security has gotten better (starting with Vista).  Whether it be Linux or Windows, if a user voluntarily gets social engineered into installing malicious software, it's game over.  Therefore, neither OS is immune from stupid users.  I do, however, think Linux makes this more difficult for the social engineers out there since Linux users are more reliant on repositories.  Windows has no concept of repositories (I am not counting websites like download.com, which are not the same).  So, Linux users are not prone to go searching around questionable corners of the web looking for software to install.

As for attacks that do not require user stupidity or interaction, I give the advantage to Linux for a few reasons:

1) Linux users don't run as root by default, whereas 90% of Windows users still do.

2) Most Windows users still use XP or a 32 bit version of Vista or 7.  These versions of Windows don't have the added security benefits of Vista/7 64 bit (namely the increased ASLR strength due to the larger memory register and the native DEP).  Linux has had both ASLR and DEP (NX bit) well before Microsoft put them into Windows.  Not only that, but most Linux distros are good about compiling most of their programs with ASLR, RELRO, PIE, etc., which makes exploiting the apps much more difficult.  Linux also has built in stack smashing protection in the kernel.

3) Linux has built-in Mandatory Access Control mechanisms like SElinux, AppArmor, Grsec, etc.  Windows Vista/7 have "integrity controls" (Protected Mode, etc.) but they are nowhere near as comprehensive or powerful as tools like SELinux.

---

### Post by Nisal on 2010-04-19
what about using strong encryption method to protect your data ?

---

### Post by iponeverything on 2010-04-19
> but they are nowhere near as comprehensive or powerful as tools like SELinux.

Its amazing what you can do with a huge budget, GPL code and a small army of NSA security analyst.

---

### Post by longbeard on 2010-04-20
Em, nobody was talking about firewalls in this thread. Does Linux benefit from a firewall, or is this just a stupid question? (Don't know much about Linux architecture.)

---

### Post by d3v1150m471c on 2010-04-20
> **new_tolinux said:**
> AFAIK Windows is more vulnerable to attacks like virus-attacks and they are not that easy to use on Linux because the "root" ("sudo") user isn't the same as the normal user. Therefore the main system can't get infected that simple.

A potential security risk in this are upgrades to different software, if the main Ubuntu repository gets poisoned by a virus, guess how many users are ;)

Besides that, it's not impossible to hack yourself a way into linux. It's not impossible to hack your way into _any_ working machine which is connected to the internet. It only should be a bit more work to do so in Linux, due to the constant updates and it's architecture.

It's easier than you think. A simple bash script can send emails and the like. It doesn't require root to delete someone's entire home folder and how many people save all their important stuff in root protected folders? Speaking of root, it's not the most difficult thing in the world to obtain as I've written simple code to obtain it using native linux commands :popcorn:. How about adding malware to startup? Simply tell echo to pipe a line of code to .profile. Linux is only as secure as the user and the amount of people who use it. Windows catches the herpes because it's popular.

---

### Post by d3v1150m471c on 2010-04-20
> **longbeard said:**
> Em, nobody was talking about firewalls in this thread. Does Linux benefit from a firewall, or is this just a stupid question? (Don't know much about Linux architecture.)

Ubuntu comes with iptables. For a GUI i'd recommend firestarter, despite it being a stopped project, it makes no difference as it simply adjusts iptables.

---

### Post by LeeDaugherty on 2010-04-20
Linux is pretty much secure out the box, most distributions (like Ubuntu) don't by default have alot of unneeded services on out-of-the-box.  This is where the firewall discussion would enter in.  It depends on your setup.  Most of the time, no a firewall isn't needed.  For 99% of home users, a properly configured router (DSL/cable/wifi) doing NAT and firewall is enough to thwart any would-be's.  If you use or leave certain services open (or just don't like being port scanned) and don't user a router, or use open-wifi's alot, a firewall might give you peace of mind.  But a fresh-install Ubuntu?  It is "virtually" impossible to login or hack remotely (the term virtually leaves open the ability for remote-exploits that are not curently known (rare for linux though)).  If you use remote desktop server or ssh (server), and samba server (plus more)....you should spend time securing your system, and possibly even using a firewall (iptables).  Otherwise, relax and enjoy the peace of mind.

I wouldn't recommend firestarter, along with iptables scripts (which correct it's are very good), it does some sysctl tuning that is seriously outdated and will cause problems on newer systems.

---

### Post by Pjotr123 on 2010-04-20
> **d3v1150m471c said:**
> How about adding malware to startup? Simply tell echo to pipe a line of code to .profile.

Sounds plausible. For determining the actual risk: in which common use situations could you make echo do this? 

> 
Linux is only as secure as the user and the amount of people who use it. Windows catches the herpes because it's popular.

That's an exaggeration. Linux does provide a lot more security by design, than Windows.

By the way: my own firewall needs are served very well by ufw. **sudo ufw enable** is the magical incantation. :-)

---

### Post by d3v1150m471c on 2010-04-20
The same way people catch viruses all the time. Slipping code into a seemingly innocent looking program. As far as the exaggeration goes, simply look at apple when they claimed mac doesn't get viruses. Mac got popular and in came the viruses. People don't usually sit around writing viruses for operating systems that aren't commonly used. They want people to either suffer and/or obtain their personal information. I know we Linux users like to sit around and pride ourselves on the lack of viruses and malware but I fail to see the logic in this.

---

### Post by seanlano on 2010-04-20
So would there be any merit in the statement: "The world's computers would be more secure if no-one used Windows."? 

Suppose Linux usage was more common that Windows, the argument that "Windows has viruses because it's the most popular" would be reversed to apply to Linux... or would it? Some argue that why would someone target Linux with a virus if you can do more damage if you target Windows. But would it even be possible to do this? Surely it must be possible to some extent.

---

### Post by LeeDaugherty on 2010-04-20
Excellent question.  Two ways to look at it.  Market share would rule if Linux overtook Windows in popularity.  But I think everyone would agree, cybercrime would definately have a much harder time if that was the case.  Email viruses would be written for Linux and still wreck havoc.  One could easily argue that as Firefox has taken more and more market-share, it's exploits have remained low (and they have an excellent response time to such).  The world would be a MUCH safer place and probably up to even 50% of current infections wouldn't be around, but malware is big business and a way would be found.  The other way to look at it is from the original "black-hat" mission to simply disrupt Microsoft as the evil-empire, those missions would cease to be as long as Linux stayed true to open-source.  But as long as there is money to be made, a way will be found.  And as for targeted attacks, session-hijacking, wifi-hijacking, and the sort aren't OS dependent (but aren't typically done remotely).

---

### Post by Ko$ on 2010-04-20
I think that the main reason why linux more secure then windows is that linux is more flexible and you can do with it whatever you want and there are many people who can do it. As windows requires no understanding of how it actually works, so you can`t ask or discuss any windows "security" issues. Because people can`t possibly protect their systems, linux goes on top of security. Look at how many linux servers are there. And people who understand windows on the very low level either do not say that windows is "not secure".

It`s like a discussion about how your or your body is vulnerable if someone goes against you with a shotgun. Obviously, you must have a shotgun (security knowledge) too in order to protect yourself.

)))

---

### Post by Pjotr123 on 2010-04-20
> **d3v1150m471c said:**
> Slipping code into a seemingly innocent looking program.

That would mean that if you stick to the official repositories, you're fine, I suppose.

Look, of course you have to be careful in Linux as well. Same with cars: even when driving a Mercedes Benz S class, you can kill yourself on the road. Nevertheless, you're much safer in such a car than in a Suzuki Alto. **Ceteris paribus**, naturally....

Blind trust in Linux is wrong, I agree, but you can also exaggerate on the other side. :)

---

### Post by uRock on 2010-04-20
> **seanlano said:**
> There are increasing reports of cyber-attacks on corporations and governments around the world, including Google, Rio Tinto, BHP Billiton, etc. Links [here]("http://blogs.aljazeera.net/business/2010/03/23/google-and-rio-tinto-find-its-tough-doing-business-china"), [here]("http://news.brisbanetimes.com.au/breaking-news-national/mining-firms-hit-by-china-cyber-attacks-20100419-spc9.html"), [here]("http://www.smh.com.au/business/netbank-woes--cyber-attacks-set-to-spread-20090702-d5un.html"). 

I recall hearing of a case where an employee of Rio Tinto while on a business trip inserted a flash drive into his laptop, which then "infected" his computer with malware which reported back to hackers about business secrets etc., as well as then being able to hack into the entire network when the businessman returned to his office. This is obviously a huge problem. 

There are countless thousands of hacking attempts each day, some of which (like the above) seem fairly easy to prevent. I would assume most of these companies use Windows, which already is a security weakness as far as I am aware. 


My question is: If everyone was using Ubuntu, not Windows, how many and what types of these attacks would be possible? I don't want to get a bunch of "Windows is ****, so it serves them right" sort of things, but an actual justified response please. Presumably DoS attacks would still be possible, but these don't steal private information. What other attacks are there? Are these attacks possible to execute on an Ubuntu target system?

If everyone used ubuntu, then there would definitely be a lot more crackers looking at the ode finding exploits to get their missions accomplished. At the same time, being an open source community, anyone who could find a new exploit could also figure out how to block it and pass on the code to the maintainers, who in turn would pass it on to the clients. This is a primary reason that Snort, when properly maintained, is one of the best Network Intrusion Detection Systems(NIDS).

---

### Post by aysiu on 2010-04-20
Moved to Recurring Discussions

---

### Post by Shining Arcanine on 2010-04-20
> **new_tolinux said:**
> About a flashdrive: yes. You'll have to be root to mount it.

You do not have to be root to mount it. You just need to be in a usergroup that allows you to mount drives. On Gentoo Linux, this group is called plugdev. I am not sure what it is called on Ubuntu, but I think that the key thing here is that there is no auto-run functionality.

---

### Post by SteveWh on 2010-04-21
The first post mentioned business trips, so it's maybe worth mentioning the hazard of using hotel, airport, or any public hotspot for an internet connection. 

The connection is by radio and is in plain text, so someone nearby can eavesdrop on all your traffic (read the same emails you read, or watch your passwords being transmitted, etc.) unless you are using https or SFTP.

---

### Post by beast2k on 2010-04-21
It is so secure,...the light from insecure will take a billion years to reach us. 
Sorry I just couldn't resist that one.:lolflag:

---

### Post by no0ne on 2010-04-26
Well, it's build with security in mind. However, it's left as your sole responsibility to keep it secure after out of the installation media. **A system is only as strong as it's weakest component.**

This means that you have to:


0. Keep your software up to date. Since mainstream repositories tend to struggle behind you need to add a few of your own. And set it up with Cron while you're at it. (If you don't know Cron, please go educate yourself with wikipedia or any decent adminguide really.) And please, use "add-apt-repository" for whatever you can, it handles the public key cryptography very nicely. Remember to have the keys for all your repositories.

My current repositories are listed at [http://ubuntuforums.org/showpost.php?p=9179093&postcount=1556]("http://ubuntuforums.org/showpost.php?p=9179093&postcount=1556")


1. Keep your firmware up to date. (the average user lives in the bliss of not updating firmware, ever.) There is an increasing risk of running hardware with an exploitable firmware, happened with HP hardware recently, just for example.

Download firmware off your hardware manufacturers website and install it. This is not so easy to automate, so suggest you follow the site static.


2. Keep your hard drive encrypted to keep your information including but not limited to your username and password secure.

Setting your Ubuntu flavor up with whole disk encryption:
[http://kuparinen.org/martti/comp/ubuntu/en/cryptolvm.html]("http://kuparinen.org/martti/comp/ubuntu/en/cryptolvm.html")

Just get the alternative installation media and follow the instructions above. Do apply yourself and your own partitioning.


3. Run only the necessary services. **Disable what your don't use.** Get yourself scanned with Nmap or which ever flavor you prefer. Free online scanners do exist.

[http://insecure.org]("http://insecure.org")

4. Have your iptables configured to relay only relevant traffic. This means getting all of your three chains.

[https://help.ubuntu.com/community/IptablesHowTo]("https://help.ubuntu.com/community/IptablesHowTo")


And that's just what I'd consider basics. If you're about security: 

5. You should have a different strong password for every single instance or service. You should never write them down, neither your user names. **The best defence you have is often the one best ignored.**

6. You should take the time to verify the integrity of your downloads, especially software.

7. You have a screen lock time set and you habitually press "ctrl-alt-L" when you leave you box. Don't leave it on long enough for anyone to coldboot though, shut it down if it's not in use or doing anything. Have a panic script written and several environmental triggers if you have to leave the box out of your sight.

8. There's also the matter of how you have your Modem/ISDN/3g/HDSPA/Cable/DSL/T1,T3 set up, which largely depends on where you have this box, which again depends on where you use your computer?

a. Office

    Your best hope is to have an administrator who knows what he's doing. A bit better in especially large companies, smaller ones tend to have their work done for them periodically not full time so their assets are often configured in a 'lockdown' manner in order to cut cost. In the public sector it depends on which level of risk your organization has to handle, but generally you're quite well off.

b. Home

    Your average DSL router comes configured quite well these days, unlike what I've seen in the last ten years. If you modify the configuration, keep in mind what security implications your actions have and act accordingly.

c. Someplace else (Place X)

    This is where it gets ugly. You're at the mercy of the network owner. Generically don't use anything unencrypted or WEP and you're fine, most of the time. 

Prefer WPA, prefer your own connection resources to external ones, should you have any (3g, hdspa etc). 

Please consider security implications while on the web, if you have anything you don't want to be public knowledge, use an encrypted protocol, like TLS,SSH,SMTP, use TOR or another anonymizing proxy.

9. Run an IDS on all network links, one in the last box before the net which on a laptop would mean on your own hardware if you use wireless.

10. Be aware of changes and vulnerabilities.

This is quite an easy task really, but I thought a common sense guide was needed. Security isn't just about setting the box up right though, it's also about how you do what you do, which means best practices, I listed a few previously.

For more, visit such gurus like:

bodhi.zazen
[Ubuntu Security, ubuntuforums]("http://ubuntuforums.org/showthread.php?t=765421")

matthewlye
[http://matthewlye.com/index.php/ubuntu-sec]("http://matthewlye.com/index.php/ubuntu-sec")

or order a book on security (Security Powertools, O'Reilly)...

For production servers you really might also need to consider BSD or RedHat.

---

