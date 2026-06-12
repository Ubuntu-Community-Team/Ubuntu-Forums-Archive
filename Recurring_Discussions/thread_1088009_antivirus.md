---
title: "antivirus??"
date: 2009-03-05
forum: Recurring Discussions
---

### Post by trinidadflores on 2009-03-05
I know in windows antivirus is a must.  Is that the same as for ubuntu?  if so what antivirus is recommended?

---

### Post by binbash on 2009-03-05
It is a waste of system resources under linux.

---

### Post by Crafty Kisses on 2009-03-05
I mean there is, but honestly it's really not needed. If you feel like you must have something, give ClamAV a look.

---

### Post by Bodsda on 2009-03-05
> **binbash said:**
> It is a waste of system resources under linux.

This is common misconception. There are linux virus's and virus's for windows can be passed on via a linux machine.

Please refer to this excellent thread on security

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by achase79 on 2009-03-05
Unless you are transferring files between Windows and Linux and want to cover all your bases for catching viruses downloaded in Linux on your Windows box, then an antivirus would be good.  Antivirus programs in Linux are usually only for email servers for doing server side virus detection before it gets to the end client.

---

### Post by perlluver on 2009-03-05
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812), have a look at this post, it is all about security in Ubuntu/Linux.

---

### Post by LowSky on 2009-03-05
Let me put this to bed.

Ubuntu doesn't really need antivirus protection. Its availible (just type antivirus in synaptic and you will get some results), but not needed.

Ubuntu force the user to install anything throught the use of a password, unlike windows XP. this will generaly stop any viruses from infecting your computer only because you are in control of what gets installed. Not to mention Windows Viruses cannot infect you linux machine a the are incompatable.

Now things like cookies and other malware that effects things like java or firefox security isues are thing to worry about. But easily fixed. Just remember to back up your files, especially your bookmarks.

---

### Post by kanikilu on 2009-03-05
I don't think ClamAV or Avast are resident (run in the background), so it's not really a waste of system resources (other than disk space). It's not necessarily needed, but I personally use AV on Ubuntu because I work in a predominantly Windows environment. Even though I never had a virus or bad malware while I was on Windows, I do worry that I might somehow inadvertently pass on something bad to an unsuspecting co-worker.

---

### Post by Bodsda on 2009-03-05
> **LowSky said:**
> Let me put this to bed.

Ubuntu doesn't really need antivirus protection. Its availible (just type antivirus in synaptic and you will get some results), but not needed.

Ubuntu force the user to install anything throught the use of a password, unlike windows XP. this will generaly stop any viruses from infecting your computer only because you are in control of what gets installed. Not to mention Windows Viruses cannot infect you linux machine a the are incompatable.

Now things like cookies and other malware that effects things like java or firefox security isues are thing to worry about. But easily fixed. Just remember to back up your files, especially your bookmarks.

You have not really put anything to bed here.

May I refer you to

[http://en.wikipedia.org/wiki/Rootkit](http://en.wikipedia.org/wiki/Rootkit)

---

### Post by kanikilu on 2009-03-05
> **LowSky said:**
> Let me put this to bed. Heh, good luck with that :D How many times has this exact subject been brought up on the forums...just today? At least 2 or 3 I think ;)

---

### Post by trinidadflores on 2009-03-05
thank you this answers my question.  My room mate and i were talking about this last night (he is a die hard bsod idiot), and i hate the sob and that organization based out of redmond. Only have it on here as its needed for my drafting software and dreamweaver.  i use Ubuntu the vast majority of the time. Infact i hate having to  shut down my computer just  to switch so i am looking for software that will do the same as what i use in windows but for ubuntu.  

Personally terrorists need to some how wipe microsoft completely out of the computer arena.

---

### Post by Bodsda on 2009-03-05
> **trinidadflores said:**
> thank you this answers my question.  My room mate and i were talking about this last night (he is a die hard bsod idiot), and i hate the sob and that organization based out of redmond. Only have it on here as its needed for my drafting software and dreamweaver.  i use Ubuntu the vast majority of the time. Infact i hate having to  shut down my computer just  to switch so i am looking for software that will do the same as what i use in windows but for ubuntu.  

Personally terrorists need to some how wipe microsoft completely out of the computer arena.

try a virtual machine if you need things like dreamweaver, or maybe look into wine << although very new versions of software may not work at all

---

### Post by kanikilu on 2009-03-05
> **Bodsda said:**
> try a virtual machine if you need things like dreamweaver, or maybe look into wine << although very new versions of software may not work at all I second that. I use VirtualBox for things like Dreamweaver, Active Directory management, etc. The only problem he might have is with drafting software - if it requires 3D video, then virtualization's not an option :(

---

### Post by orethrius on 2009-03-05
> **Bodsda said:**
> This is common misconception. There are linux virus's and virus's for windows can be passed on via a linux machine.

> **TFA (emphasis added)]Viruses

The fact of the matter is: viruses/worms take advantage of flaws or holes in the code. At this time of this writing, **there are no significant Linux viruses "in the wild".** Linux boxes are no less targets than any other OS, many of the large (ie valuable) Internet sites run on *nix so there is no lack of motivation to crack into *nix.[/quote]

Windows viruses, on the other hand, can be passed on at any time without sufficient vetting procedures.

[QUOTE=Bodsda said:**
> May I refer you to

[http://en.wikipedia.org/wiki/Rootkit](http://en.wikipedia.org/wiki/Rootkit)

[quote=TFA (emphasis added)]The term rootkit (also written as root kit) originally referred to **a set of recompiled Unix tools such as ps, netstat, w and passwd that would carefully hide any trace of the intruder** that those commands would normally display, thus allowing the intruders to maintain root access (highest privilege) on the system without the system administrator even seeing them.[/quote]

Further, if you read more into the Wikipedia article on rootkits previously cited, it points out the key difference between rootkits and viruses - i.e., that rootkits are typically designed to maintain control of a single machine, whereas viruses are designed to spread to as many machines as possible.  Technically speaking, viruses, trojans, and rootkits are all distinct branches of the same evil tree.

Linux is certainly not immune to the threat of malware, but that shouldn't be an excuse to confuse a less common avenue-of-attack with the most common.

---

### Post by presence1960 on 2009-03-05
> **LowSky said:**
> Let me put this to bed.

Ubuntu doesn't really need antivirus protection. Its availible (just type antivirus in synaptic and you will get some results), but not needed.

Ubuntu force the user to install anything throught the use of a password, unlike windows XP. this will generaly stop any viruses from infecting your computer only because you are in control of what gets installed. Not to mention Windows Viruses cannot infect you linux machine a the are incompatable.

Now things like cookies and other malware that effects things like java or firefox security isues are thing to worry about. But easily fixed. Just remember to back up your files, especially your bookmarks.

Nothing in this world is ever perfectly safe & protected. Linux is no exception. BUT it is inherently light years more secure than Windows. Also most hackers, malware writers, etc don't focus too much energy on Linux because not that many people use it. When that does change you will see more virus, malware & rootkits for Linux. 

You can buy the biggest lock made out of the strongest, most durable material, yet even this is only really strong enough to keep honest people out. 

Don't be lulled into an overly false sense of security with Linux to the point you think you are invulnerable and it can't happen to you. If Linux was so secure that you needed nothing then none of the softare for security would exist because there would not be a need for it.

I am referring to personal PCs not servers that run on Linux. My banking info, etc is an easy target on a Personal PC.

Just my 2 cents.

---

### Post by bodhi.zazen on 2009-03-05
Moved to recurring discussions.

> **trinidadflores said:**
> I know in windows antivirus is a must.  Is that the same as for ubuntu?  if so what antivirus is recommended?

This is a FAQ on these forums and as you can see seem to be a magnet for all kinds of comments.

You already have a link to the security sticky and I suggest you read it.

The question is what do you wish to use antivirus for ?

Right now there are a small handful of "proof of concept" viruses for Unix / Linux and there are no know viruses in the wild.

So scanning your computer for Linux Viruses will not increase your linux security much.

Now if you are sharing files with windows and wish to scan them or are running a mail or file (samba) server with windows clients you may wish to use antivirus to scan for windows viruses.

You may also wish to scan for viruses in an attempt to keep windows viruses from passing through your computer.

In the end the decision is up to you, but before using any tool you should understand the tools and how to use them.

---

### Post by dragos240 on 2009-03-05
I beleive that the known linux viruses et cetera, are about 12, compare that to windose's billions. So you are very unlikely to run into any, but they're out there ;)

EDIT: There are 35 viruses, trojans et cetera, out there. Be carefull, 35 is pretty big compared to microsoft's billions, take care!

---

### Post by cardinals_fan on 2009-03-05
You don't need an antivirus app on either Windows or Linux, unless you like being conned out of your resources or money.

You do need a limited account (default on Ubuntu) and a cautionary attitude.  Think before you click.  On Ubuntu, I recommend a) [changing the sudo timeout to 0 ]("http://ubuntuforums.org/showpost.php?p=3974258&postcount=3")and b) only installing apps from the default repos and extremely trusted sources.

Read [http://www.happyassassin.net/2009/01/20/on-linux-security/](http://www.happyassassin.net/2009/01/20/on-linux-security/)

---

### Post by nerdman978 on 2009-03-05
Honestly, linux straight up kicks viruses in the teeth.

---

