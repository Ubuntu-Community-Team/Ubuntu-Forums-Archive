---
title: "Linux security, true, half-true or myth?"
date: 2009-07-08
forum: Recurring Discussions
---

### Post by UranUtan on 2009-07-08
Hi,

We use Windows at work. Mostly Win XP and Win 2003. About once a month we receive a note from our network admin to invite us to install an urgent Hot fix. Otherwise our machines could be opened to attack when surfing certain web site or even via the internal network (like Conflicker in Jan 2009). In addition, all our machines have Antivirus & Firewall installed.

I am not a security expert nor I want to understand how such an attack could be possible. Surfing web sites, reading emails, using Instant Messenger, connecting to the internal LAN are basics everyday tasks. I don't go to "dangerous" web sites, the people in my Instant Messenger list are trustworthy. Why would such common tasks could allow someone to infiltrate into my machine? This sounds so outrageous.

So far I rely on Ubuntu to prompt for a password when an important system change is going to take place. As such I think that my Ubuntu computer is safe. But is it really?

Some say that Linux security is an illusion. It is not attacked yet because its market share is so small it looks less attractive to the criminals.

So the question is: if I am reasonable (installing software from trust sources and only communicate with known web sites and people). Is Linux safe enough?

In other words, if someone on the Internet wants to attack my Ubuntu machine (take control, plant trojan, steal data, etc.) is it possible?

Thanks in advance for any insight.

---

### Post by doas777 on 2009-07-08
linux security is real, but often overstated. security is not simple, and never will be, so there is lots of wiggle room to get in if you really want to and have the skills.

if ubuntu gets more than 8% market share, then some exploits will start being seen, but they will do less damage on the whole.

Linux (contrary to popular belief) is not at all immune to malware. it has no *Viruses* (a very specific type of malware) but can fall prey to worms, trojans, rootkits, adware/spyware,  service attacks (weak key on your ssh, huh?) and social enginering attacks.

in the long run, you still have to be smart about running your PC, so, in that regard linux is jsut a vulnerable as any other platform. nothing is fool-proof.

at least with linux, a smart competent user can avoid most of these nasties. thats just not true of the competition.

---

### Post by chriskin on 2009-07-08
if you are reasonable or midly unreasonable, linux is 100% safe

if you install any suspicious linux-related app out there, you MIGHT find a rootkit or something else bad enough to need some help to fix the pc.

if you were talking about windows it would be like
"if you are reasonable you would get less than 200 malware/viruses/etc
if you are midly unreasonbale, you would get less than 1000 malware/viruses/etc
if you install anything suspicious , your pc won't open next time you try to open it"

:popcorn:


also, if you ever find a linux "virus" , please tell me where you found it, i'm searching for one for more than 2 years now :S

---

### Post by wojox on 2009-07-08
From the ground up, Linux was designed to be a multi-user, networked operating system. Even now, Windows shows its creaky history as the descendent of a single-user, stand-alone PC operating system.

The bad thing about the Windows approach, where everything from the highest level user applications like a Web browser or a word processor is linked to the lowest level of the core operating system, is that almost any vulnerability can be used to attack the entire system.

Make no mistake though, while Linux is far more secure than Windows, it is not invulnerable. No operating system is.

---

### Post by UranUtan on 2009-07-08
Thanks for your inputs. Let imagine a little challenge game.

1. Install the latest version of Ubuntu (or any Linux distribution).

2. Run system update.

3. Personalize the computer: some files in ~/Documents, some *.ogg in ~/Music, changing desktop themes, etc.. Then I surf some web sites so Firefox gather history and cached data.

3. Now the challenge: I give out my IP or surf a web page designated by the hacker.

Could anyone hack into my machine and give me the proof than my computer has been compromised (for example: tell me what is the wallpaper or content of some files in ~/Documents, etc.)

If the proof is convincing, then I will give the hacker the computer. 

Do you think that I will lose my computer?


NOTE 1: I use reasonably strong password for eveything (linux user account, forum user account and these account are different) 

NOTE 2: I am generally discipline. I don't fall easily to phishing or social engineering scams.

---

### Post by chriskin on 2009-07-08
even if most hackers sit right next to you, the possibility of one managing to compromise your security is less than 0 :P

if you play safe AND have a strong pass, i can't see how someone would ever manage to get you...

by the way what kind of computer is it? if it's a new one, i might start hacking lessons :)

---

### Post by doas777 on 2009-07-08
> **UranUtan said:**
> Thanks for your inputs. Let imagine a little challenge game.

1. Install the latest version of Ubuntu (or any Linux distribution).

2. Run system update.

3. Personalize the computer: some files in ~/Documents, some *.ogg in ~/Music, changing desktop themes, etc.. Then I surf some web sites so Firefox gather history and cached data.

3. Now the challenge: I give out my IP or surf a web page designated by the hacker.

Could anyone hack into my machine and give me the proof than my computer has been compromised (for example: tell me what is the wallpaper or content of some files in ~/Documents, etc.)

If the proof is convincing, then I will give the hacker the computer. 

Do you think that I will lose my computer?


NOTE 1: I use reasonably strong password for eveything (linux user account, forum user account and these account are different) 

NOTE 2: I am generally discipline. I don't fall easily to phishing or social engineering scams.


not with just the IP, unless you have installed attackable services. ubuntu ships with no open ports (which is why samba sharing is broken unless you install samba itself). 

now the website may be able to hurt you, if it is allowed to run active code of some form. I know of no such exploits at present, but they are possible. your browser and it's plugins are the enemy here, so it is best to constrain them with a system like apparmor.

you prolly won't lose your PC over it, unless you hosted the challenge at defcon or blackhat, with prize money from tipping point, and some publicity for the pen testers.

---

### Post by UranUtan on 2009-07-08
> **chriskin said:**
> by the way what kind of computer is it? if it's a new one, i might start hacking lessons :)

A gorgeous Pentium 3, 1 GHz, 768 MB Ram. It runs pretty quiet, (CPU runs with no fan). You may also like the collection of art & abstract wallpapers.

Oh I forgot to mention that Samba is turned on on this machine. May be that could give some leverage to the hacker.

---

### Post by wojox on 2009-07-08
samba sure.
download nmap and play around with it.
scan for port 139

---

### Post by UranUtan on 2009-07-08
> **wojox said:**
> samba sure.
download nmap and play around with it.
scan for port 139

Can you jump directly to the conclusion? Would that mean the computer is vulnerable because of Samba?

---

### Post by doas777 on 2009-07-08
> **UranUtan said:**
> Can you jump directly to the conclusion? Would that mean the computer is vulnerable because of Samba?

ok. hacking 101. if you want to get into someones box, you need a way to issue it commands. network applications are services are the mainstay for network hacking.

if I try to hack your PC, first I need to identify a service running on it, that is capable of taking input that I provide. I then need to trick that service into allowing me to do what I want, not what it was designed to do.

samba is a common network service that allows file and print sharing with MS networks (their implementation is called NetBIOS). netbios is a pretty easy hack, so many attackers look for accessible computers that they can contact for netbios services. 

as I said above, samba is not installed by default (nor are any other network services) so unless you install it (so you can share files) then you do not have ports 137/139/445 open. as a result, no hacker in the world could use samba against you.

---

### Post by doas777 on 2009-07-08
> **UranUtan said:**
> Can you jump directly to the conclusion? Would that mean the computer is vulnerable because of Samba?


all computers are vulnerable. computers with samba (or any network service) are just *more *vulnerable.

---

### Post by cariboo on 2009-07-08
I wish people would stop saying the only reason Linux isn't vulnerable to malware is because of the small market share. I can't find the figures right now, but the last time I looked 68% of the servers on the internet were linux powered. That seems to be a pretty big share of the market if you ask me.

The reason it is so hard to create malware, is that Linux was designed from the start to be a multi-user system. When you have multi-users running on the system at the same time you want to keep their data seperated so no-one else has access to it. That is also why you have to be root to install system wide applications.

The biggest security problem on the linux desktop is the user, if the user can be social engineered into installing malicious software, then he has a problem.

The other problem with open ports is a matter of common sense. If you are behind a router and you have no ports forwarded you can run all the services you want. Personally I have ftp, samba, smtp, apache, cups and mysql all running on my server, but none of the services are outward facing. The minute you open a service to the outside world, you better know what you are doing. One of the biggest holes is vnc, usually because of weak passwords. Ssh can be a problem too again becayse of weak passwords. If you plan on opening any services to the world, I would suggest a password length of at least 8 characters and you shouldn't be able to find it in the dictionary.

Any linux distibution is much more secure out of the box than any Windows version.

---

### Post by chriskin on 2009-07-08
what this thread teaches us is that you need to work a lot to make linux weak (security-wise), and you might even not "succeed" , while you need to work even harder to make windows strong(security-wise again) and will almost certaintly fail 

or was i the only one who saw this meaning?

:popcorn:

---

### Post by doas777 on 2009-07-08
> **cariboo907 said:**
> I wish people would stop saying the only reason Linux isn't vulnerable to malware is because of the small market share. I can't find the figures right now, but the last time I looked 68% of the servers on the internet were linux powered. That seems to be a pretty big share of the market if you ask me.

The reason it is so hard to create malware, is that Linux was designed from the start to be a multi-user system. When you have multi-users running on the system at the same time you want to keep their data seperated so no-one else has access to it. That is also why you have to be root to install system wide applications.

The biggest security problem on the linux desktop is the user, if the user can be social engineered into installing malicious software, then he has a problem.

The other problem with open ports is a matter of common sense. If you are behind a router and you have no ports forwarded you can run all the services you want. Personally I have ftp, samba, smtp, apache, cups and mysql all running on my server, but none of the services are outward facing. The minute you open a service to the outside world, you better know what you are doing. One of the biggest holes is vnc, usually because of weak passwords. Ssh can be a problem too again becayse of weak passwords. If you plan on opening any services to the world, I would suggest a password length of at least 8 characters and you shouldn't be able to find it in the dictionary.

Any linux distibution is much more secure out of the box than any Windows version.

true, but linux and unix servers are hacked everyday:
[http://isc.sans.org/diary.html?storyid=6742](http://isc.sans.org/diary.html?storyid=6742)
[http://nic.phys.ethz.ch/news/1210776776/index_html](http://nic.phys.ethz.ch/news/1210776776/index_html)
[http://www.theregister.co.uk/2008/04/16/mystery_web_compromise_unpicked/](http://www.theregister.co.uk/2008/04/16/mystery_web_compromise_unpicked/)
[http://httpd.apache.org/security/vulnerabilities_20.html](http://httpd.apache.org/security/vulnerabilities_20.html)
[http://www.linux-magazine.com/Online/News/Psyb0t-Attacks-Linux-Routers-Update](http://www.linux-magazine.com/Online/News/Psyb0t-Attacks-Linux-Routers-Update)

all of these are exploits in the server arena. desktops are much harder to secure than a cli only install with nothing but sshd, mysql, and a stripped-down apache.

Yes *nix is more robust because of its inherent multiuserish-ness, its years of review, quality design, and because there is no single default configuration.

most importantly, look at this one:
[http://www.milw0rm.com/exploits/8572](http://www.milw0rm.com/exploits/8572)

isn't that supposed to be impossible?

---

### Post by doas777 on 2009-07-08
> **chriskin said:**
> what this thread teaches us is that you need to work a lot to make linux weak (security-wise), and you might even not "succeed" , while you need to work even harder to make windows strong(security-wise again) and will almost certaintly fail 

or was i the only one who saw this meaning?

:popcorn:

I'm not sure that the word "windows" has come up at all. regardless, no there is no way to tell if a wintel box is clean.

---

### Post by chriskin on 2009-07-08
> **doas777 said:**
> I'm not sure that the word "windows" has come up at all. regardless, no there is no way to tell if a wintel box is clean.

check the first post again
edit : also, isn't the whole point of this thread about changing his computers from windows to linux to be more secure?

---

### Post by UranUtan on 2009-07-08
> **chriskin said:**
> check the first post again
edit : also, isn't the whole point of this thread about changing his computers from windows to linux to be more secure?

No this is not to switch from Windows to Linux. I have already used Ubuntu 9.04 x64 at home. But I got confused by many rumors about security. Most of the time, the argument "Linux is not attacked b/c of its market share". But by experience I do see that Linux is safer.

What I want to learn from this thread is the experience from knowledgable users so that I can tell to the Windows friend that "Linux is really safe. Here is my machine, prepared in a standard way, try to hack it".

---

### Post by lykwydchykyn on 2009-07-08
> **cariboo907 said:**
> I wish people would stop saying the only reason Linux isn't vulnerable to malware is because of the small market share. I can't find the figures right now, but the last time I looked 68% of the servers on the internet were linux powered. That seems to be a pretty big share of the market if you ask me.


While I generally agree with your post, I wish people would stop throwing this statistic around. It's based on (fairly old) webserver market share stats of Apache.  Apache runs on Linux, yes, and quite often.  But it also runs on BSD, OSX, Netware, commercial Unixes, and even Windows.  

Certainly the thrust of the argument stands -- that Linux is used extensively on servers, and that a successful Linux exploit would be valuable to black hats.  But the stat is bogus, so lets stop spreading it.

It could be argued as well that server marketshare is different from a security perspective than desktop marketshare.  A server on a public IP is much more likely to be secured and monitored for security than Aunt Tillie's home PC.  And it doesn't typically have some flunkee logged into a desktop surfing for porn or free screensavers, so social engineering is out for the most part.

I think there is partial truth to the marketshare argument, but it's not the whole story.  Inherent diversity, better LUA support, mount options like noexec and nosuid for partitions, and other things help make Linux a more secureABLE environment IMHO, but security is subject to supply and demand:  there will always be a demand for compromised computers, and so there will always be people working to supply that demand.  That demand isn't going away just because the marketshare swings one way or the other.

---

### Post by bodhi.zazen on 2009-08-04
A default installation of Linux (ubuntu) is more secure then a Default installation of Windows.

IMO a default installation of Ubuntu is more secure then a hardened version of Windows.

IMO a hardened installation of Ubuntu is almost impossible to crack.

See : 

[Securing Debian Manual]("http://www.debian.org/doc/manuals/securing-debian-howto/") 

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812")

 [How to Secure Firefox - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=671604")

[USN list | Ubuntu - Security alerts]("http://www.ubuntu.com/usn") 
 

And also the stickies in the security forum (Apparmor, Snort, and OSSEC).

See also SELinux (used in Fedora and Centos / RHEL)

So, as has been stated in this thread, Linux is not immune from cracks. Firefox, in particular, is vulnerable to cross platform attacks, almost always java or java script.

---

### Post by UranUtan on 2009-08-04
Thanks bohdi for your expert opinion. Bookmarked the links you suggested. Lots of interesting reading in perspective.

---

