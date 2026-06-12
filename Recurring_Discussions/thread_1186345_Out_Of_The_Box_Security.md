---
title: "Out Of The Box Security"
date: 2009-06-13
forum: Recurring Discussions
---

### Post by scythian on 2009-06-13
Hi, can anybody please tell me how secure is Ubuntu 8.04LTS Desktop out of the box.

Mainly I want to know what are best options for anti-virus and firewall - what are the main packages that people are using ?

Many thanks for any advice.

---

### Post by Cheesemill on 2009-06-13
Take a read of this thread, it should answer most of your questions.
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

Cheesemill

---

### Post by albinootje on 2009-06-13
> **scythian said:**
> Hi, can anybody please tell me how secure is Ubuntu 8.04LTS Desktop out of the box.

Mainly I want to know what are best options for anti-virus and firewall - what are the main packages that people are using ?


See also here : [http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

I recommend :
- No anti-virus software 

(To the anti-virus-software-installation fans on Linux, please show me --evidence-- that your suggested anti-virus software supports detection of Linux malware!)

- gufw as firewall

- NoScript and WOT and adblock-plus as Firefox addons

- Use a separate /home partition and mount /home with the noexec flag

- Forget about AppArmor and SELinux for now, way to difficult and annoying for a new Linux user.

- install the packages harden-clients harden-servers

---

### Post by 3rdalbum on 2009-06-13
> **scythian said:**
> Hi, can anybody please tell me how secure is Ubuntu 8.04LTS Desktop out of the box.

Out-of-the-box it contains security flaws that I'm sure are well-known amongst "the bad people" by now. I recommend applying all updates ASAP.

> Mainly I want to know what are best options for anti-virus and firewall - what are the main packages that people are using ?

1. It's like moving to Antarctica and stocking up on fly spray. There are no flies in Antarctica, so you're wasting your time. There are no viruses on Linux. Enjoy.

2. I use the one on my ADSL router as it protects my whole network, while still allowing the computers on my network to communicate with eachother. By default, Ubuntu doesn't listen to any ports, so a personal firewall is unnecessary. If you install server services that should only be accessed from your own computer, then you can just enable the UFW firewall.

For more information on UFW, type "man ufw" into a command prompt.

If you want to configure UFW from a GUI, install the "gufw" package.

---

### Post by scythian on 2009-06-13
I am surprised to hear there are absolutely no viruses which can infect Linux. Is this the case with all distributions of Linux ? It sounds like a major advantage over Windows.

I assume therefore that anti-virus products like Clam are used only to provide a check that any files we send to Windows users are virus free, ie there is no point in having a 'resident shield' as with AVG Anti-Virus on Windows.

---

### Post by albinootje on 2009-06-13
> **scythian said:**
> I am surprised to hear there are absolutely no viruses which can infect Linux. 

Where did you hear or read that ? Please provide a link, thanks.
> 
Is this the case with all distributions of Linux ? It sounds like a major advantage over Windows.


There are viruses for Linux. See here : [https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)  However, most, if not all, of those are old, too old to function.

Some viruses can run in Wine in Linux. See an old (from 2005) article about that here : [http://www.linux.com/archive/feature/42031?theme=print](http://www.linux.com/archive/feature/42031?theme=print)

There is also the issue of dot desktop files in KDE and Gnome.
[http://www.geekzone.co.nz/foobar/6229](http://www.geekzone.co.nz/foobar/6229) but that is not necessarily a Linux problem, it is a KDE and Gnome problem, and KDE and Gnome exist, amongst others, also for FreeBSD, OpenSolaris, and.. MS-Windows.

(In Ubuntu Jaunty there's an update in Gnome for the dot desktop files problem, as the Wine related desktop files need confirmation to be run first, and marked "trusted" before you can use them without confirmation each time)

But remember, we're talking about viruses.  ...Worms and trojan horses are different things.

---

### Post by Subban on 2009-06-13
> **albinootje said:**
> Where did you hear or read that ? Please provide a link, thanks.

He read it in the post directly before his own.

---

### Post by Cheesemill on 2009-06-13
> **scythian said:**
> I assume therefore that anti-virus products like Clam are used only to provide a check that any files we send to Windows users are virus free, ie there is no point in having a 'resident shield' as with AVG Anti-Virus on Windows.

Yup. Out of all of the Ubuntu servers and desktops that I administrate the only 2 that have ClamAV installed are mail servers.

Cheesemill

---

### Post by dhughes on 2009-06-13
> **albinootje said:**
> ...
(To the anti-virus-software-installation fans on Linux, please show me --evidence-- that your suggested anti-virus software supports detection of Linux malware!)...

 If you share a lot of files with friends who use the Microsoft Windows OS, or if you use Windows at work and Ubuntu at home but share files between the two systems e.g. Open Office to Excel and vice versa.

 I don't know if it's technically possible for a virus to hitch a ride that way but it would be a smart or at least considerate and a good personal security policy to prevent the spread of viruses.

---

### Post by albinootje on 2009-06-13
> **Subban said:**
> He read it in the post directly before his own.

Okay, thanks for that. 

There are however viruses for Linux, see here :
[https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)
But as said before, those are .. old and are likely not to "work".

---

### Post by albinootje on 2009-06-13
> **dhughes said:**
> If you share a lot of files with friends who use the Microsoft Windows OS


So.. for the sake of my friends who do *not* run anti-virus software on their [cough] "secure" MS-Windows OS ... I would have to also run anti-virus software ?

That doesn't make sense to me.

The thing with people chosing to run a MS-Windows OS and *not* using anti-virus software and *not* caring about computer-security (read: train and inform themselves and improve "security") is that it is their decision and their responsibility.

I will tell them more about Linux if they ask for it, but for the rest I will tell them to find a knowledgeable MS-Windows user to help them out with their problems.

---

### Post by aysiu on 2009-06-13
> **albinootje said:**
> 
The thing with people chosing to run a MS-Windows OS and *not* using anti-virus software and *not* caring about computer-security (read: train and inform themselves and improve "security") is that it is their decision and their responsibility. Antivirus isn't security. This goes for Windows, too.

If Windows users want to protect themselves, they should do the following: [list][*]Use almost exclusively a limited user account. If you must run as admin and you use Vista, don't turn off UAC, no matter how annoying you think it is[*]Install Windows updates automatically[*]Use Firefox with NoScript[*]Use strong passwords[*]Educate yourself about social engineering[*]Don't pirate software, music, or movies[/list]

---

### Post by oldsoundguy on 2009-06-13
Yes, there are virus programs that have been written for Linux, but unlike Windows where you can open a file or click on a picture and install a hidden virus,  in Linux you have to go through an installation procedure to install that virus.  
If you confine your downloads to the repositories and known trusted sites such as Softpedia or others, you will not "accidentally" pick up a virus program.

A firewall, on the other hand, SHOULD be used (either hardware such as a router or software as furnished in your build of Linux.)

And keep your browsers up to date as there are items that can get installed in a browser that will not install in the system itself that can cause grief.
ALL browsers have vulnerabilities .. some less than others, but NONE are perfect.
The latest RSS patch for Firefox is a good example.

---

### Post by oldsoundguy on 2009-06-13
toadd to aysiu's comments re Windows.

An anti virus program of today spends most of it's time checking your downloads and your eMail for VIRUS FILES.  Many to NOT cover other forms of malware very well. (especially the free ones such as avast and avg.)

So, IF you are to use Windows on line, it is a good idea to install some anti-spyware programs.
In the area of FREE programs, Spyware Blaster is a real time program that rides in the background and will catch MOST of it kept up to date.
It's sister program, Spyware Guard is a nice little alarm program that will alert when something attempts to re-write your browser preferences .. what a LOT of malware programs do .. flipping you to a porn site or changing your preferred search engine, etc.
Ad-Aware now has a real time protector as well.  Not sure how well that one works, but since it is also FREE, no harm/no foul.
As with all "protection" programs for Windows, they have to be kept UP TO DATE in order to do their job.  That means MANUALLY updating the free ones (if you pay they will auto update .. that is their gig!)

---

### Post by NCLI on 2009-06-13
> **aysiu said:**
> Antivirus isn't security. This goes for Windows, too.

If Windows users want to protect themselves, they should do the following: [list][*]Use almost exclusively a limited user account. If you must run as admin and you use Vista, don't turn off UAC, no matter how annoying you think it is[*]Install Windows updates automatically[*]Use Firefox with NoScript[*]Use strong passwords**[*]Educate yourself about social engineering[*]Don't pirate software, music, or movies**[/list]

Why not? Infected torrents get taken down very quickly.

---

### Post by donkyhotay on 2009-06-13
Back to what the OP said my opinion on anti-virus in linux can be summarized in the following rootless root story (I've posted this in similar threads)





Master Foo and the Nervous Novice
There was a novice who learned much at the Master's feet, but felt something to be missing. After meditating on his doubts for some time, he found the courage to approach Master Foo about his problem.

“Master Foo,” he asked “why do Unix users not employ antivirus programs? And defragmentors? And malware cleaners?”

Master Foo smiled, and said “When your house is well constructed, there is no need to add pillars to keep the roof in place.”

The novice replied “Would it not be better to use these things anyway, just to be certain?”

Master Foo reached for a nearby ball of string, and began wrapping it around the novice's feet.

“What are you doing?” the novice asked in surprise.

Master Foo replied simply: “Tying your shoes.”

Upon hearing this, the novice was enlightened.

---

### Post by aysiu on 2009-06-13
> **NCLI said:**
> Why not? Infected torrents get taken down very quickly.
They don't have to be torrents, and are you saying "quickly enough" so that *no one* gets trojans through pirated downloads? Because that isn't true, as some thousands of Mac users know from pirating iWork and Photoshop.

Social engineering can come in a variety of forms, in any case.

---

### Post by Sef on 2009-06-13
> Mainly I want to know what are best options for ... (a) firewall - what are the main packages that people are using ?

A firewall is enabled by default, so no need to install one.   It is called[ IPTables]("http://en.wikipedia.org/wiki/Iptables").

---

### Post by rookcifer on 2009-06-13
> **scythian said:**
> I am surprised to hear there are absolutely no viruses which can infect Linux. Is this the case with all distributions of Linux ? It sounds like a major advantage over Windows.

There are viruses that can infect Linux.  Hundreds of proof of concept viruses have been written over the years.  The problem is getting them to spread.  It's extremely difficult because of the Discretionary Access Controls built into all Unix like OS's.  In other words, it takes social engineering to infect a Linux box with malware.  Like the others have said, I have been around Linux forums for years and I have never seen even **one** instance of someone being infected with "malware" or a "virus" (rootkits, yes, but that's different).

If you want a very detailed explanation as to why Linux viruses are rare, [read here]("http://linuxmafia.com/~rick/faq/index.php?page=virus").

> I assume therefore that anti-virus products like Clam are used only to provide a check that any files we send to Windows users are virus free, ie there is no point in having a 'resident shield' as with AVG Anti-Virus on Windows.

The only reason you *might* need AV is if you plan on networking with Windows computers and you are worried a piece of malware might traverse from Linux to Windows.  But, why not just run AV on your Windows box?  

It must be said that the DAC model in Unix/Linux is not perfect.  It's called "Discretionary" for a reason -- users have the discretion.  What this means is that if a malicious process is running with the permissions of "John" it will have access to all of John's processes and can modify them and generally cause damage.  The same goes for root owned processes.  If someone cracks a root owned process with the right exploit, it's game over for your entire system.  Owning one root process *usually* means being able to get a root shell. 

The answer to this is Mandatory Access Controls (SELinux, AppArmor, Tomoyo, Grsecurity).  They will essentially lock processes down into their own domain, so that even if exploited, the process cannot break out of its "jail" and affect other processes.  Even if someone has root, they can't break out of the "domain" of the process. Even though they have pwned that one process, it is essentially worthless to them inasmuch as gaining further access to the system is concerned. (This is indeed a simplification, but good enough to get a general idea of the concept). 

It should be noted that not even MAC's are perfect as there have been a few [kernel exploits]("http://kernelbof.blogspot.com/") out there that allow attackers to completely bypass protections like SELinux or AppArmor.

And I disagree with the following from [http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

> Don't click on links in emails. Don't open attachments from people you don't know. Don't be dumb. 

While I agree that you don't want to be dumb and fall for social engineering, I must say that clicking on links is not dangerous nor is opening e-mail attachments (no Linux e-mail clients will execute anything by default).   Again, don't fall for social engineering or give your root password to some unknown file you randomly download.  But refusing to click on "dangerous" links is simply silly.  The "malware" cannot do anything without your direct interaction.  On Windows, it often doesn't take ANY interaction other than clicking a link, which is why you hear this same "security advice" passed onto Linux users, even though it is meaningless here.  Programs cannot execute by "accident" in Linux like they can on Windoze.  This is Micro$oft thinking.

---

### Post by aysiu on 2009-06-14
Well, the idea of not clicking links in emails is so much for your computer's protection as it is for your protection. URLs for links in emails (particularly HTML emails) can easily be disguised, and that's how most phishing scams work. I read my emails in plain text (not HTML), so I can easily see how the scammers are trying to trick me.

And even though email clients can't execute dangerous attachments directly, up until recently, they could do so indirectly:
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/153438](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/153438)

In the future, there may be other ways that we don't know about. Better to be safe and just not open attachments you aren't expecting.

---

### Post by yabbadabbadont on 2009-06-14
> **aysiu said:**
> And even though email clients can't execute dangerous attachments directly, up until recently, they could do so indirectly:
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/153438](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/153438)


Bah!  That only applies to you silly graphical file manager users...  See, proof that desktop environments are Evil and should be exorcised from the default install.  :D

---

### Post by scythian on 2009-06-14
[FONT=Times New Roman][SIZE=3]Hi, thanks for all info this is very helpful. It seems though despite Master Foo’s guidance a lot of effort has gone into security on Linux with technologies like AppArmor, SELinux and hardened kernels. I agree that anti-virus companies are not the best people to listen to as the more people that are alarmed by potential threats the more sales they will make. I wonder why it is Windows is so virus prone by comparison, with 100,000’s viruses written for it. Maybe it is because nobody (even evil virus writer types) want to harm Linux and it is only companies like Micro$oft that provoke their ire![/SIZE][/FONT]
[COLOR=black][FONT=Times New Roman][SIZE=3] [/SIZE][/FONT][/COLOR]

---

