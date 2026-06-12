---
title: "Nothing but grief with Ubuntu 12.04"
date: 2013-11-10
forum: New to Ubuntu
---

### Post by Don1947 on 2013-11-10
Way back in 2008 I tried Ubuntu 9? and had a very miserable time with it and ditched it. I have tried again after finding a book and disk in a pound shop for Ubuntu 12.04. Should have known better than to buy it and install it as I have spent 3 miserable days since. Ubuntu has since been fully updated I should add here.
Latest problem is that after 6 HOURS of trying to install Bitdefender and finally succeeding, I have lost the icon to access the Bitdefender setup screen on desktop-happened after updating it-(that is all i have managed to do with this Ubuntu 12.04-install and update installations!)
I have tried everything to get access to Bitdefender back i can logically think of to no avail , and now I am getting constant crashes of Ubuntu.
The fact i am posting this using Windows should tell you what getting Firefox to work properly right now is like!
Restarts are of no help for any of these problems. The whole thing seems corrupted.
How do I remove this program  from my computer, please, because I have had enough-it is more fun going to the Dentist-the whole thing should come with a mental health warning-nothing has seemed to change since Ubuntu9-same old incomprehensible and impossible operating system in new clothes.!

---

### Post by buzzingrobot on 2013-11-10
Isn't BitDefender a Windows/Mac antivirus?   Why are you trying to install that on Linux?  Are you using Wine, perhaps?

(ah, I see they have released a deb and an rpm.)

---

### Post by ardchoille422 on 2013-11-10
Bitdefender is an anti-virus app. I have been using Ubuntu since 2005 and have been told repeatedly that you don't really need anti-virus apps in Linux. With the way Linux is designed it's pretty much a waste of time to write a virus for this platform due to the ACL's and the fact that a downloaded program is never able to execute until the user manually changes permissions of the program. This is why so few viruses exist for Linux.

---

### Post by Don1947 on 2013-11-10
Suggest you read[ this]("http://en.wikipedia.org/wiki/Linux_malware") and[ this]("http://www.linux.org/threads/malware-and-antivirus-systems-for-linux.4455/") and [this]("http://www.unixmen.com/meet-linux-viruses/")

Question remains-how do I get Ubuntu off my computer?

---

### Post by craig10x on 2013-11-10
Don..been running ubuntu since 8.04 (April 2008) right up to current 13.10 and never got one single virus, trojan, or any other malware...no anti virus of any kind every installed...and i do tons of web surfing...
just saying ;)  linux isn't windows...i guess it's hard to break old habits, eh?

All i do is download and install GUFW (firewall gui) from the software center and turn it ON....that's it!

---

### Post by david98 on 2013-11-10
Why would you attempt to install bit defender this is linux and there are very few virus's use it on and off for 5 year or so and never had any problem if you are set on having some av software use clam to scan and delete any threats your comp may of picked up even with them they will not do you'r comp any harm this is not windows and doe's not freeze,crash it just work's like it should

---

### Post by ardchoille422 on 2013-11-10
> **Don1947 said:**
> Suggest you read[ this]("http://en.wikipedia.org/wiki/Linux_malware") and[ this]("http://www.linux.org/threads/malware-and-antivirus-systems-for-linux.4455/") and [this]("http://www.unixmen.com/meet-linux-viruses/")

Question remains-how do I get Ubuntu off my computer?

Yes, and the second paragraph in that first linked article seems to support my point. Let's look at this article more closely:

> Like Unix systems, Linux implements a multi-user environment where users are granted specific privileges and there is some form of access control implemented. To gain control over a Linux system or to cause any serious consequences to the system itself, the malware would have to gain root access to the system.
This can only be done if the user manually grants permissions, or gives root access, which users should never do where software comes from unknown sources.

> If an infected binary containing one of the viruses were run, the system would be infected.
This is why we don't run as root user.

> The use of software repositories significantly reduces any threat of installation of malware, as the software repositories are checked by maintainers, who try to ensure that their repository is malware-free.
This is why we don't run software from unknown sources.

> The classical threat to Unix-like systems is vulnerabilities in network daemons, such as SSH and web servers. These can be used by worms or for attacks against specific targets.
This is why we don't run world-facing servers unless we know exactly what we are doing and having some sort of training.

> Linux servers may also be used by malware without any attack against the system itself, where e.g. web content and scripts are insufficiently restricted or checked and used by malware to attack visitors.
Downloaded items are never made executable, i.e. they can't run. The user is required to manually make them executable before they can be run. Which is why we (a) don't run scripts from unknown sources, and (b) don't make anything executable unless we know exactly what it will do.

> Older Linux distributions were relatively sensitive to buffer overrun attacks
This is why we keep our software up-to-date.

> As is the case with any operating system, Linux is vulnerable to malware that tricks the user into installing it through social engineering
No operating system will ever be immune to social engineering, in my opinion. This is why we educate ourselves about the OS that we use rather than trusting that it will not perform undesired actions.

> There are a number of anti-virus applications available which will run under the Linux operating system. Most of these applications are looking for exploits which could affect users of Microsoft Windows.
Notice the last sentence there.

> The following is a partial list of known Linux malware. However, few if any are in the wild, and most have been rendered obsolete by Linux updates or were never a threat.
As I was saying..

As to the second linked article, viruses are a small subset of malware.. try to avoid equating the two.

As to the third linked article, please re-read the third sentence in that article.

The fact of the matter is that there are no active Linux viruses in the wild, it would be a waste of time to write/distribute one due to the way Linux is designed.

As to the question of how to remove it from your system, we'll need to know how it was installed.

Finally, don't let my bean count fool you, I've been using Linux as my sole OS since 2001 and have been using Ubuntu as my sole distro since 2005.

---

### Post by philinux on 2013-11-10
> **Don1947 said:**
> 

Question remains-how do I get Ubuntu off my computer?

How did u install it? Wubi? Or dual boot.

---

### Post by Don1947 on 2013-11-10
Will someone please just tell me how to remove Ubuntu from my Computer-short of using a utility like" Killdisk."?
Thanks.

---

### Post by SuperFreak on 2013-11-10
Had to laugh reading the original post. I just spent the last 5 hours wrangling with a Win 7 machine infected with malware. The computer booted to a black screen and didn't seem to be able to go into safe mode. Eventually sorted it out but was reminded how Linux machines just work once set up and seem immune from security intrusions as long as they are updated

---

### Post by Don1947 on 2013-11-10
> **philinux said:**
> How did u install it? Wubi? Or dual boot.
Wubi I guess-no other OS on the computer now other than Ubuntu-intentional as an old unused computer .

---

### Post by ajgreeny on 2013-11-10
I do hope you have the free version and did not pay for a licensed version that cost you money. If you paid anything you wasted money.

As many others have said quite firmly, y**ou do not need antivirus** applications on a standard Linux desktop system; if you are running a server, particularly a mail server, or serving other users who may be running windows, it does perhaps make sense to have some way of checking, but for most desktop users it is a total waste of time, resources and perhaps money.

I have been using ubuntu since 2005 just like ardchoille422, have never had a virus checker except for a quick look at clamav when I first started, and in those eight years have never had any malicious files on my system.  If you only use downloaded applications from the repos, or occasionally from other trusted sources like sourceforge, you have nothing to worry about.

Honestly, you don't!!

Forget your windows ideas and ways and learn to live with and love Linux.

PS:
If you really do want to remove ubuntu totally from the disk you can just delete the partitions with gparted on the live ubuntu DVD, and then install whatever you want in its place.

If you do go back to windows, don't forget you **definitely do need an antivirus application.**

---

### Post by ardchoille422 on 2013-11-10
> **Don1947 said:**
> Wubi I guess-no other OS on the computer now other than Ubuntu-intentional as an old unused computer .

If there is no OS on that computer other than Ubuntu, then removing Ubuntu completely would leave you with an empty hard disk. You won't be able to remove Ubuntu and return to Windows, if that's what you were hoping to do.

Linux is quite nice, though. I'm a very picky and impatient 50 year old man and I love Ubuntu, still wonder how I lived so long in the computer world before discovering Ubuntu in 2005. You've also stumbled upon one of the best Linux communities on the planet.

Perhaps give Ubuntu a try without bitdefender? You'll get plenty of help and support here.

---

### Post by Don1947 on 2013-11-11
I have now found several ways of removing Ubuntu.

---

### Post by mastablasta on 2013-11-11
good for you! it's easy to remove it.

But as other said you attemted to install a program that would scan for windows viruses on linux maschine. this is usually done only on mail servers that distribute e-mails to windows network computer. even then it is often omited as widnows desktops usually have their own AV protection. mayb eon a mashicne that serves files - it would make sense to that users can't distribute windows viruses.

anyway good luck with whatever OS you intend to use.


and restarting doens't really solve anything (unless the system hangs). 

the line in IT Crowd series "Have you tried turning it off an on again?" is a joke since the guy doens't really want to deal with the issue.

---

### Post by Niemil on 2013-11-11
> **mastablasta said:**
> ...the line in IT Crowd series "Have you tried turning it off an on again?" is a joke since the guy doens't really want to deal with the issue.

:lolflag:



To topic starter:

If you wanna remove ubuntu you should first install another OS (and as you install a new OS, often/always you're able to clean the harddrive, meaning deleting ubuntu).
Like my computer (HP 625), have Windows 7 in it. I don't need any CD or any USB memory stick in order to install Windows 7, as it's fabric formatation or whatever named.
Maybe your computer is familiar?

If not, you may just buy or download any other OS? 

Before I used ubuntu on an old computer that didn't have any OS in the computer. And I wanted Windows back (because I gave up very easy on Ubuntu and thought it was very limited, because it really feels limited when being a newbie for sure).
So I downloaded windows and installed it on an USB memory stick and booted it (well, can't remember how I did, but I read some tutorial I can't find right now).

Now however, I'm back on ubuntu again. Mostly for design and security reasons. And because I feel I wanna learn me more about new things.

---

### Post by th.sigit on 2013-11-11
My first linux distro was Ubuntu 8.04, several years ago. Still feeling more comfortable using a proprietary OS back then, until I tried to dive in further using 10.04. Ever since, I never looked back at the proprietary OS, and there are times when I regretted why I did not do that any sooner ..

The best experience using Ubuntu (or any other technology, I think) is when you have one or two mentors around you to inspire what you want to do next --and there's the internet to research how you can achieve that.

Here's what I said to my friends comparing Linux to Windows:

Installing linux is like having a dinner like a king: you sit on your table and you can have everything on the menu served before you. Installing windows is like sitting in a food-court, where you have to go to every vendors to get your menu and waited for each menu to be prepared before you can have everything you want on your table.

---

### Post by Turbine1991 on 2013-11-11
You don't just uninstall an operating system like you do with a program.

Just install your os of choice and partition it appropriately. It's not rocket science.

---

### Post by sha1sum on 2013-11-11
First of all, if your day is miserable because your computer doesn't do what you want it to do, I suggest you visit a psychologist. Really. Second, don't install anti-virus software on Ubuntu. It doesn't need it. Just install a fresh Ubuntu and you´re good to go.

---

### Post by Mopar1973Man on 2013-11-11
I get a chuckle from this thread as well. I was once a Windows user as well and use to believe the anti-virus and firewall thing. Now I'm tickle pink with Ubuntu because that's all a thing of the past. No longer have to worry about virus, malware, etc. I bit a firewall twaeking but that's all. I suggest the OP take a peek over here...

[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by Allavona on 2013-11-11
All I can say about this thread is Good Grief!

---

### Post by verymadpip on 2013-11-12
> **Allavona said:**
> All I can say about this thread is Good Grief!

It's not the only one around here like that these days buddy ;)

Nevertheless, for the novice to these things, some tasks, & issues, can seem insurmountable.  They may well be.
I recall my first dual boot attempt, in which I accidentally wiped out Vista.  No great loss there, sure, but I lost all my documents & images.
(I've learned about backing up since, however, I have recently lost a bunch more data because only having stuff on the one "backup" drive means it isn't backed up.  Another lesson learned ).

These days I'm more inclined to check things out before throwing myself headlong into something that may break my system.
I come here & I search.  If I'm still unsure I *ask* here, or on IRC.  This is the singularly most helpful community on the web I've encountered.

I'd go with the popular suggestion of reinstalling  anew & taking things from there.
No need to throw the baby out with the bathwater.
Each to their own I guess.

---

### Post by philinux on 2013-11-12
I'm closing this now as it has gone way off topic.
To the OP please raise a new thread if you need further help with a specific problem. Thanks.

---

