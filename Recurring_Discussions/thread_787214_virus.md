---
title: "virus"
date: 2008-05-08
forum: Recurring Discussions
---

### Post by sweeneytodd on 2008-05-08
could someone please explain why linux doesn't need any any antivirus and other stuff.
Is there a firewall, if so can i access it, if not should i have one.
I'm just a little worried about it

---

### Post by SuperSon!c on 2008-05-08
> **sweeneytodd said:**
> could someone please explain why linux doesn't need any any antivirus and other stuff.
Is there a firewall, if so can i access it, if not should i have one.
I'm just a little worried about it

[http://linuxmafia.com/~rick/faq/index.php?page=virus](http://linuxmafia.com/~rick/faq/index.php?page=virus)


even though viruses won't affect *you* doesn't mean you don't need to be careful.  say you opened and edited an infected word doc you imported into Open Office and sent it off to your buddy to collaborate or review.  bam, he may likely get hit.

also, it's ALWAYS a good idea to be behind a hardware firewall, especially since they're dirt cheap.

---

### Post by p_quarles on 2008-05-08
Moved to Recurring Discussions. 

The sticky on "Ubuntu Security" in the Security Discussions support forum is a good overview of this topic.

---

### Post by tamoneya on 2008-05-08
ubuntu already has a firewall installed called IPTables but if you want it to be any use you need to configure it.  Take a look at firestarter
```
sudo apt-get install firestarter
```

---

### Post by IHATEDLINK on 2008-05-08
There are a few known Virus but the chances about getting one are the same as in finding Britney Spears naked in your bed.
The main reason is that 90% of the computers of the world use Windows, so almost every virus is aimed to Windows.
Also Linux is more secure and stable than windows

---

### Post by SuperSon!c on 2008-05-08
> **tamoneya said:**
> ubuntu already has a firewall installed called IPTables but if you want it to be any use you need to configure it.  Take a look at firestarter
```
sudo apt-get install firestarter
```

still doesn't replace being behind a hardware firewall.

---

### Post by tamoneya on 2008-05-08
if configured correctly it can come very close but even I dont want to take the time to correctly configure it to that extent and use a hardware firewall myself.  Its just easier.

---

### Post by Sef on 2008-05-08
> The main reason is that 90% of the computers of the world use Windows, so almost every virus is aimed to Windows.

Not true.  Web servers are about 2/3 GNU/Linux, but the viruses and other malware are built for Windows.  Windows is a lot easier to infect.

---

### Post by SuperSon!c on 2008-05-08
> **tamoneya said:**
> if configured correctly it can come very close but even I dont want to take the time to correctly configure it to that extent and use a hardware firewall myself.  Its just easier.

at it's most basic level, yes, but there are more options and advantages using a hardware firewall not to mention the extensibility some routers (linksys) using third party firmware (DDWRT, tomato, OpenWRT, etc).  software firewalls are good for outgoing transmissions though, but with a linux box i'm not concerned with that.

---

### Post by SuperSon!c on 2008-05-08
> **Sef said:**
> Not true.  Web servers are about 2/3 GNU/Linux, but the viruses and other malware are built for Windows.  Windows is a lot easier to infect.

DESKTOP computers would have been more accurate.

---

### Post by phaed on 2008-05-08
It should be noted that the number of Linux viruses more than doubled from 422 to 863 in one year (2005).  

[http://en.wikipedia.org/wiki/Linux_Virus]("http://en.wikipedia.org/wiki/Linux_Virus")

Who knows how many there are now, but as Linux continues to grow in popularity, you can expect a lot more of them.

Every ecosystem has parasites.

---

### Post by p_quarles on 2008-05-08
> **phaed said:**
> It should be noted that the number of Linux viruses more than doubled from 422 to 863 in one year (2005).  

[http://en.wikipedia.org/wiki/Linux_Virus]("http://en.wikipedia.org/wiki/Linux_Virus")

Who knows how many there are now, but as Linux continues to grow in popularity, you can expect a lot more of them.

Every ecosystem has parasites.
Take a look at the article cited there: it starts off by equivocating between "virus" and "malware," and as the article proceeds, it finally acknowledges that trojans and OS exploits are the main source of compromised systems (this holds true of all operating systems). In other words, that number relies on ignoring the actual definition of a software virus and using it to many any kind of system intrusion. 

The problem with that is that any kind of security measure *requires* that you make a distinction between different kinds of threats. An anti-virus program isn't going to prevent you from running a malicious perl script as the root user, and a spyware catcher isn't going to examine your kernel for remote privilege escalation exploits. 

Yes, Linux users have to be mindful of security, but the first requirement for this is to understand the security issues they face. There are no "viruses" (in the strict sense) for Linux known to be in the wild. This makes running an anti-virus application superfluous. Far worse than wasting system resources, however, is the assumption that security == running an anti-virus program. That doesn't hold on Windows, and it's certainly not true for an OS where a virus would represent the absolute least efficient way of attacking it.

---

### Post by sweeneytodd on 2008-05-08
So what I understand from all this is that the main reason write virus?s is to attack windows..........problem, it sounds like it is just as easy to write virus for linux and eventually they will, so it is a worry then isn't it.
  A hardware firewall, mmmmmm....that sounds nice, especially if they are cheap, anyone know a good compatible brand with hardy

---

### Post by smartboyathome on 2008-05-09
Get a Linksys WRT54G, that is the router I use. Also, Linux would have viruses if it was very easy to crack, the fact that it is used on at least 2/3 (if not more) of the world's servers shows that it is very safe from viruses.

---

### Post by Phenax on 2008-05-09
A virus is malicious software, period. If I sent you a script containing ```
sudo rm -rf /
``` - that would be a virus.


Linux doesn't "get" viruses because of the way it works and members of the community.

Linux users generally get their software out of repositories that contain already-approved software.

Executable files do not have executable permissions unless explicitly set by the user.

Root access isn't given by default.


A quick Google search can reveal more reasons as to why.. Market share is one of them of course, but I don't foresee viruses being a large problem when Linux gains market share.

---

### Post by p_quarles on 2008-05-09
> **Phenax said:**
> A virus is malicious software, period.
Only according to part-time tech writers for big newspapers. In computing, a virus is malicious code which can facilitate its own reproduction. In other words, it requires little to no help from a human user. 

Malware that relies on "tricking" the user, or exploiting their inexperience in any way, is usually called a trojan, or a social engineering attack. 

This distinction is made not to be pedantic, but because they are two *very* different kinds of attacks, and defending against them requires different countermeasures.

---

### Post by akiratheoni on 2008-05-09
> **sweeneytodd said:**
> So what I understand from all this is that the main reason write virus?s is to attack windows..........problem, it sounds like it is just as easy to write virus for linux and eventually they will, so it is a worry then isn't it.


As long as you don't run random executables, you'll be fine. There's sudo for a reason. Only the root user can hurt the system. If you're on Windows, you're most likely running as the administrator who can harm your system. That's one reason why Ubuntu discourages running as root.

---

### Post by wootah on 2008-05-09
> **akiratheoni said:**
> As long as you don't run random executables, you'll be fine. There's sudo for a reason. Only the root user can hurt the system. If you're on Windows, you're most likely running as the administrator who can harm your system. That's one reason why Ubuntu discourages running as root.

That is exactly why the majority of virii on Windows machines pre-Vista are nasty stuff. You run with full administrator privs. all the time by default (unless otherwise explicitly set).

Linux on the other hand was designed as a network based OS with/for multiple users. So look at it this way: say you did manage to get some sort of 'virus'. More than likely the virus would execute under your privileges which would result in what? Losing anything owned by you, which would probably be your profile which contains your app. settings, maybe music/pic and other non-critical components that don't affect the overall stability of the machine. Of course this assumes that you didn't execute it as root or it isn't owned by root with a sticky execute bit set.

Overall, it's a pretty good situation to be in! The other types of virii are the bad ones--ones that can elevate privileges by exploits. I'm not completely sure, but I don't think you would really find those in the form of common scripts ?

Regardless of the method and from what I understand, the majority of 'virii' will be in the form of some sort of script that you will have to download, set file privs + 111 (or +x) and actually execute to cause damage.

Either way, we are relatively safe behind a hardware firewall along with iptables setup (maybe with a frontend like Firestarter to help out) :D

---

### Post by SuperSon!c on 2008-05-09
> **sweeneytodd said:**
> So what I understand from all this is that the main reason write virus?s is to attack windows..........problem, it sounds like it is just as easy to write virus for linux and eventually they will, so it is a worry then isn't it.
  A hardware firewall, mmmmmm....that sounds nice, especially if they are cheap, anyone know a good compatible brand with hardy

Linksys WRT54G**L**.  then flash with DD-WRT and you're set and then some.

p.s. all hardware firewalls are compatible with all the OS's i know of.

---

### Post by LaRoza on 2008-05-09
> **sweeneytodd said:**
> So what I understand from all this is that the main reason write virus?s is to attack windows..........problem, it sounds like it is just as easy to write virus for linux and eventually they will, so it is a worry then isn't it.


As someone who has written things that weren't quite-so-nice (but not harmful!) for some people, Windows is the easiest to mess with.

For running something in Linux, it has to be marked executable. In Windows, it relies on file extensions (if you want, go find the source for that "I love you" thing that was causing trouble a while back, you will see it is plain text. VBScript to be exact).

Windows, by default, hides known file extensions but uses them in opening files. Double click a file with a .vbs extension and it is executed. That is a serious security flaw. (.com, .exe, .js, .bat, and a few others are also executed)

Also, Windows has a central registry, and allows users to alter the registry. Linux has no such thing.

---

### Post by phaed on 2008-05-09
> **akiratheoni said:**
> As long as you don't run random executables, you'll be fine. There's sudo for a reason. Only the root user can hurt the system. If you're on Windows, you're most likely running as the administrator who can harm your system. That's one reason why Ubuntu discourages running as root.

Even without root privileges, malware could destroy all the data in your home directory, which could be really bad if you have sensitive or important data.  I guess regular back ups are one solution.

Quite frankly, I think there's not much worry about..yet.  I've been using Ubuntu for 3 years as of May 15, and I've never had a security breach that I know of.  What worries me is, again, if the popularity of Linux increases, then Linux will become a more interesting target for malware developers.

---

### Post by LaRoza on 2008-05-09
> **phaed said:**
> Even without root privileges, malware could destroy all the data in your home directory, which could be really bad if you have sensitive or important data.  I guess regular back ups are one solution.

Quite frankly, I think there's not much worry about..yet.  I've been using Ubuntu for 3 years as of May 15, and I've never had a security breach that I know of.  What worries me is, again, if the popularity of Linux increases, then Linux will become a more interesting target for malware developers.

So? Why wipe home directories (which do nothing) by tricking people into running programs when you can really mess with Windows systems?

Yes, it is possible, but the chances that someone would take the time to do that to random people is very remote.

(I have backups of my home, mainly to allow me to set up new systems quickly and use all my settings)

---

