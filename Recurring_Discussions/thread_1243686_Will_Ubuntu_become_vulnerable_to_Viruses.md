---
title: "Will Ubuntu become vulnerable to Viruses"
date: 2009-08-18
forum: Recurring Discussions
---

### Post by kevil99 on 2009-08-18
Will Ubuntu become as Virus proned as Windows if it makes it Mainstream.

I belive unfortunantly it will, well not to the same extent.  I do not wish this demise
On One of the Greatest Distros ever.  Seems I came across an article claiming this 
downfall on Ubuntu. There may be some truth to this, but as I stated before not
The same extent.

Any thoughts???....

---

### Post by sasho_zl on 2009-08-18
First of all very important part of the security of a linux system is the way a kernel handles the system calls. This is the essential part of the system integrity - the way a system protects itself from malicious programs. It will be a long very long writing to cover only small bits of that kernel system policy so in a few words  I can tell you that it's very unlikely a malicious program could compromise the linux system without your approval. That is why you should be careful what software you install on your system and from where are you getting it. The repositories are safe. When you download software from a web site (even official software vendor one), you should always check if the checksum provided for that program matches the one you have downloaded! There are cases when hackers break into a server and change the programs with "modified" products. If even one bit of the program has being changed the checksum won't match! 
The fact that you use linux doesn't mean that you are undestructable. It really makes it a lot harder for people and programs to compromise your system compared to windows and this is the reason that those programs are generally written for windows. Why would some body bother to write a virus for linux and prey that some guy may execute it with root privileges when for a quarter of that time he can write easyer windows virus which will be started by the operating system itself. And another thing is that a big part of the windows users don't have even a little computer literacy! And exactly those people are easy targets. GNU/Linux users in general have the tendency to have some basic knowledge on how stuff in the internet works and that makes them not that good of a target.
I will stop here for now because as I have wrote earlier this is a very vast toppic.

---

### Post by rookcifer on 2009-08-18
> **kevil99 said:**
> Will Ubuntu become as Virus proned as Windows if it makes it Mainstream.

I belive unfortunantly it will, well not to the same extent.  I do not wish this demise
On One of the Greatest Distros ever.  Seems I came across an article claiming this 
downfall on Ubuntu. There may be some truth to this, but as I stated before not
The same extent.

Any thoughts???....

ZZZZZZZZZZZZZZZZ

Discussed a million times.  Use the search feature.

---

### Post by gn2 on 2009-08-18
> **kevil99 said:**
> Will Ubuntu become as Virus proned as Windows if it makes it Mainstream.

No, don't be ridiculous.

Linux is already installed on 3.7 bajillion servers connected to the internet (stat courtesy of Random Guy On The Internet™) and yet there are no viruses for them in the wild.

Viruses are nothing whatsoever to do with popularity, they are a phenomenon made possible by the poor design of Windows.

---

### Post by MikeTheC on 2009-08-18
> **gn2 said:**
> Viruses are nothing whatsoever to do with popularity, they are a phenomenon made possible by the poor design of Windows.

Oh, thank goodness finally someone else "gets it".

Big +1, gn2. Good on you!

---

### Post by lisati on 2009-08-18
Here's another statistic: 99% of all computers problems (including malware) are directly attributable to [PEBKAC errors]("http://en.wikipedia.org/wiki/PEBKAC"). The remaining 1% are attributable to [ID-10-7 errors]("http://en.wikipedia.org/wiki/ID-Ten-T_Error"). [SIZE="1"][Citation needed][FONT="Comic Sans MS"][/FONT][/SIZE]

---

### Post by Bachstelze on 2009-08-18
> **gn2 said:**
> Viruses are nothing whatsoever to do with popularity, they are a phenomenon made possible by the poor design of Windows.

I beg to disagree.

Remember [this]("http://ubuntuforums.org/showthread.php?t=1239826")? Well, who knows how many security holes like this still remain undiscovered? Now let's suppose Linux became popular to the point that it will actually be profitable to, for example, install keyloggers on the computer of Joe Average who sometimes buy stuff online using his credit card. Now what will happen? A security hole will be discovered, an exploit will be posted, and within a few minutes, you will have an authentic Linux virus propagating on millions of Joe Averages' computers and installing keyloggers or whatnot on them. Sure, the issue will be fixed in a few days, maybe in a few hours, but viruses propagate faster than that.

Linux is alreadey installed on million of servers? True, but the vast majority of those servers are managed by extremely skilled people who know what they're doing, not by Joe Averages.

---

### Post by cmay on 2009-08-18
> **gn2 said:**
> No, don't be ridiculous.

Linux is already installed on 3.7 bajillion servers connected to the internet (stat courtesy of Random Guy On The Internet™) and yet there are no viruses for them in the wild.

Viruses are nothing whatsoever to do with popularity, they are a phenomenon made possible by the poor design of Windows.

there is not virus as such now but all the first rootkits and worms came from UNIX. 
however they are proven to be most effective in windows judged by the amont of spyware and malware for windows.  
from wikipedia articles. 
> 
The term *rootkit* or *root kit* originally referred to a maliciously modified set of administrative tools for a [Unix-like]("http://en.wikipedia.org/wiki/Unix-like") [operating system]("http://en.wikipedia.org/wiki/Operating_system") that surreptitiously granted [root]("http://en.wikipedia.org/wiki/Superuser") access. If an intruder could replace the standard administrative tools on a system with a rootkit, the modified tools would allow the intruder to maintain root access over the system while concealing these activities from the legitimate [system administrator]("http://en.wikipedia.org/wiki/System_administrator"). The earliest known rootkit was written in about 1990 by [Lane Davis]("http://en.wikipedia.org/w/index.php?title=Lane_Davis&action=edit&redlink=1") and [Steven Dake]("http://en.wikipedia.org/w/index.php?title=Steven_Dake&action=edit&redlink=1") for [SunOS]("http://en.wikipedia.org/wiki/SunOS") 4.1.1.[*[citation needed]("http://en.wikipedia.org/wiki/Wikipedia:Citation_needed")*] There was an earlier exploit equivalent to a rootkit that was perpetrated by [Ken Thompson]("http://en.wikipedia.org/wiki/Ken_Thompson") of [Bell Labs]("http://en.wikipedia.org/wiki/Bell_Labs") against a naval laboratory in California to win a bet.[*[citation needed]("http://en.wikipedia.org/wiki/Wikipedia:Citation_needed")*] Thompson subverted the C compiler in a distribution of Unix to the Lab.
 A rootkit cannot elevate an attacker's privileges before it is installed on the target system. Installation requires the intruder to have root or administrator access, which may be achieved by having physical access or exploiting a [security vulnerability]("http://en.wikipedia.org/wiki/Vulnerability_%28computing%29") that allows [privilege escalation]("http://en.wikipedia.org/wiki/Privilege_escalation") in a computer system. Alternatively, the installation program of the rootkit may simply be started unwittingly by an administrator, for example via a [Trojan application]("http://en.wikipedia.org/wiki/Trojan_horse_%28computing%29"). Once installed, the rootkit maintains administrator-level access over time by subverting the system in some way, and actively hides its presence from other processes.
 In 2005, [Sony BMG]("http://en.wikipedia.org/wiki/Sony_BMG") caused a [scandal]("http://en.wikipedia.org/wiki/2005_Sony_BMG_CD_copy_prevention_scandal") by including rootkit software on music [CDs]("http://en.wikipedia.org/wiki/Compact_disc") that, in an attempt to enforce [DRM]("http://en.wikipedia.org/wiki/Digital_rights_management"),[[2]]("http://en.wikipedia.org/wiki/Rootkit#cite_note-1") opened a [backdoor]("http://en.wikipedia.org/wiki/Backdoor_%28computing%29") that allowed root access to anyone aware of the rootkit's installation.[[3]]("http://en.wikipedia.org/wiki/Rootkit#cite_note-2") The scandal raised the public's awareness of rootkits, while the public relations fallout for Sony was compared by one analyst to the [Tylenol scare]("http://en.wikipedia.org/wiki/1982_Chicago_Tylenol_murders").[[4]]("http://en.wikipedia.org/wiki/Rootkit#cite_note-3")
 
 ** **



however i dont see any connection at all between popularity and virus. a virus is a program and it takes time to write it. its harder to get users that stick to the distributions package manager get infected wiht something if it can be done at all. 

i still dont use any virus protection on my systems and i never had anything other than some of these fake pop ups claiming to be a virus scan that shows me how many windows virus i got on my hard disk. the last one i saw on open solaris and i admit they look very real. but its not easy to convince someone running open solaris that my c:\ drive is infected wiht a lot of windows trojans and get me to install anti virus for it. 

i think that no system is absolutely safe. no design is perfect. but in my everday computing i doubt i have anything to worry about in terms of virus. so i dont. :)

---

### Post by juancarlospaco on 2009-08-18
Yes,
Ubuntu is already vulnerable to a Virus,
a Virus named *"**Troll**"*, 
it try to attack with social ingeniering on Ubuntu Community core.

:)

---

### Post by bodhi.zazen on 2009-08-18
> **gn2 said:**
> No, don't be ridiculous.

Linux is already installed on 3.7 bajillion servers connected to the internet (stat courtesy of Random Guy On The Internet™) and yet there are no viruses for them in the wild.

Viruses are nothing whatsoever to do with popularity, they are a phenomenon made possible by the poor design of Windows.

+1

Although that is not the same as saying Linux is invulnerable to cracking.

I think the importance of Linux security is underestimated on these forums and not enough people use Apparmor / SELinux.

If it helps, here is a listing of apparmor profiles (the Ubuntu 9.04 set is most up to dae and includes a prfile for firefox 3.5.2 and Icecat):

[http://bodhizazen.net/aa-profiles/bodhizazen/](http://bodhizazen.net/aa-profiles/bodhizazen/)

There are other profiles as well (go up a directory).

The problem with these discussions is a virus is only one form of malware and the vulnerability is so far limited to Windows. With that said people often use the term virus indiscriminately.

My advice, take the time to learn at least the basics of [Ubuntu Security]("http://ubuntuforums.org/showthread.php?t=510812") and securing your browser [How to Secure Firefox]("http://ubuntuforums.org/showthread.php?t=671604")

---

### Post by Bachstelze on 2009-08-18
> **bodhi.zazen said:**
> The problem with these discussions is a virus is only one form of malware and the vulnerability is so far limited to Windows.

The keyword is "so far". I stand with my belief that the more people will start to use Linux, the greater the chance a virus for it will appear. Users who don't secure their Windows aren't going to be any more careful when they switch to Linux.

---

### Post by bodhi.zazen on 2009-08-18
> **HymnToLife said:**
> The keyword is "so far". I stand with my belief that the more people will start to use Linux, the greater the chance a virus for it will appear. Users who don't secure their Windows aren't going to be any more careful when they switch to Linux.

+1

The user is the weakest link in the security chain and social engineering is easier than kernel cracking.

---

### Post by kayvortex on 2009-08-18
I personally agree with HymnToLife. Yes, poor OS design plays a major part, but no more so than an idiot user: Viruses have everything to do with popularity; although, I concede, I doubt it will ever be as prevalent as it is with M$. I *could*, say, "offer" a Linux program (like Mathematica, say) via a popular p2p application and add a harmless little script with "rm -f /" in it somewhere. How will the user know? Will he/she bother to check before running sudo ./install? (Of course, nobody'll put "rm -f /" in there: they'll look to steal information in some way; but the point is that careless users are important security flaws in *any* system).

You might argue that Linux is so better designed than Windows that no criminal organization would expend the effort to make a novel virus. Maybe. Still, I'm of the opinion that greed always finds a way.

---

### Post by Viva on 2009-08-18
Malware != Viruses. Viruses are only a subset of malware. There might be more malware for Ubuntu as it becomes popular, but there won't be too many viruses. There will be trojans and other malware that requires user interaction and depend on social engineering, but Viruses? Nah.

---

### Post by kayvortex on 2009-08-18
> Malware != Viruses

Fair enough, but this is just semantics. Sticking to proper defns is fine, but I assumed it was clear that the OP meant precisely that "virus" meant all malware: more people know it like that now.

I do agree that viruses would be very difficult to spread if Linux became popular; but, then again, I can see the faex populi logging in as root. Would viruses be so rare then?

---

### Post by dtoronto on 2009-08-18
> **gn2 said:**
> 
Linux is already installed on 3.7 bajillion servers connected to the internet (stat courtesy of Random Guy On The Internet™) and yet there are no viruses for them in the wild.

Viruses are nothing whatsoever to do with popularity, they are a phenomenon made possible by the poor design of Windows.

I would say that OS security has more to do with a misunderstanding by the user than with the OS.  It's true that Linux is more secure by its constructs, but the mechanics of your OS won't do any good if you leave the front door wide open.

---

### Post by doas777 on 2009-08-18
OP: not viruses, but yes, there will be vulnerable flaws and exploits as linux becomes a more valuable target. Linux servers are already a hot target, and yes systems are being infiltrated (usually via spear fishing or application exploits or insecure configurations or by poor security practices). mabey it's a weak ssh key, or a failure to configure banning against bruteforce attacks, or a vulnerability apache install, or a php app with serious script injection vulnerability. 

Linux is designed to be secure, and for the most part it is, but it is starting to face the same problems as windows: its hard to be secure and easy to use at the same time. most security experts would argue against the 15 min login grace period after using sudo/gksu, but it does make it easeier to use.

also there is so much code that is trusted, but without recent review against new threat methodologies.  they just found a 6 year old privilege escalation bug in the kernel last week, hence this weeks updates. Can we guarantee that this won't happen again? heck, I can almost guarantee that it will. [http://news.cnet.com/8301-1009_3-10291022-83.html](http://news.cnet.com/8301-1009_3-10291022-83.html)

Viruses, no probably not, by their narrow definition. worms, probably, but will continue to be rare. trojans will increase dramatically if linux ever exceeds 10% share. social engineering has always been a problem and is one that will get worse, rather than better, as the complexity of the system increases. 

don't get me wrong, you are much safer using linux, and I applaud your choice, but it takes a lot more than a stock os to acheive real saftey, whatever platform you're on.

---

### Post by doas777 on 2009-08-18
> **kayvortex said:**
> Fair enough, but this is just semantics. Sticking to proper defns is fine, but I assumed it was clear that the OP meant precisely that "virus" meant all malware: more people know it like that now.

I do agree that viruses would be very difficult to spread if Linux became popular; but, then again, I can see the faex populi logging in as root. Would viruses be so rare then?

I always assume the exact opposite. my users know only two kinds of bad computery-things: hackers (bad but smart and potentially kewl people), and viruses (bad software). it never occurs to them that a hacker might use a virus. they think they are naturally occuring, I presume.

lol.

---

### Post by Frak on 2009-08-18
If Linux becomes as big as Windows in terms of popularity, yes, it will have viruses designed for it, in much of an ether-sense. Just like Windows, the exploits would not be written for Ubuntu in itself, but through it's most available ends. Such this could be exploiting pulse-audio, an application common on nearly Ubuntu computer, and using it to gain elevated rights.

As for those that say, "Well, it's on the server like a bajillion times everywhere! There's no viruses in the wild for it." In the same sense as above, you don't see viruses being written for Linux itself, as that would be an incredibly stupid move. If you think on your toes for a second, you'll realize that nearly all exploits you hear are through PHP, or a hole in Mono, or a security issue in ColdFusion, or a tiny bug in Ruby, etc. This is because so much more damage can be caused by attacking the Common Scripting Engine in able to do harm.

Say I was to attack a server that was involved in E-Commerce and wanted to benefit from it. One way would to be to write a trojan that would allow me to have remote SSH access to the server in able to bring up the database files and see customer information, such as credit card numbers and possible SSN's.

Or...

I could go after the source directly, and disregard the platform altogether and attack the, say for this instance, PHP interpreter. Instead of taking long hours to write and test a virus, I could get everything I need through a well placed SQL injection. With a simple hex-line appended to the URL string I have all the information I need. I disregarded the platform and it brought me great rewards and allowed me to forget about Windows or Linux exploits altogether. To repeat it for the infinite time, in this scenario I was able to completely disregard the platform that the engine ran on.

Open Source has the benefit of having prying eyes (although, we've just lately seen where prying eyes blindly scan over the termite infestation in the wall), but it will never have an advantage over the lazy, incompetent administrator. In this case, the administrator is noone more than the user at the controls.

---

### Post by bodhi.zazen on 2009-08-18
> **kayvortex said:**
> Fair enough, but this is just semantics.

As frustrating as it is, semantics is a big part of these recurring discussions simply because "virus" means different things to different participants.

In addition, viruses are so prevalent that every time some users have a problem on Windows they assume it is due to a virus.

Thus "virus" can essentially mean, depending on the participant, anything from a hardware malfunction, to buggy code, to malware, to social engineering, to a specific type of attack vector.

IMO best be as precise as possible and understand what the term "virus" means in the context of the post to which you are replying.

---

### Post by kayvortex on 2009-08-18
> As frustrating as it is, semantics is a big part of these recurring discussions simply because "virus" means different things to different participants.

Actually, I have a conjecture that *all* arguments are the result of mismatched definitions, but that's another story...
In any case, from the non-technical manner of the OP's Ps, and some of the other posts, I played the odds and guessed the broader definition; but, you're right: it is best to be clear (although it would make things a hundred times more boring!).

> my users know only two kinds of bad computery-things: hackers (bad but smart and potentially kewl people), and viruses (bad software). it never occurs to them that a hacker might use a virus. they think they are naturally occuring, I presume.

To analogize and quote Philip J. Fry: Insane theories: one, regular theories: a billion. [/obscure reference and convoluted analogy]

OK then, strict definitions on, would viruses be so rare? The vast majority of people just don't understand that you only get out of a computer what you put in. They expect computers to do things effortlessly. Could they not circumvent its normal, basic security measures? Could not an unscrupulous company pander to the illiterates and neuter the OS's basic security features, promising to create a "user-friendly system that doesn't bug you for passwords," in order to make a profit (via advertising, I foresee)?

---

### Post by bodhi.zazen on 2009-08-19
> **Frak said:**
> I could go after the source directly, and disregard the platform altogether and attack the, say for this instance, PHP interpreter. Instead of taking long hours to write and test a virus, I could get everything I need through a well placed SQL injection. With a simple hex-line appended to the URL string I have all the information I need. I disregarded the platform and it brought me great rewards and allowed me to forget about Windows or Linux exploits altogether.

I agree with the essence of this. In the future I think these cross platform exploits are becoming a reality.

I think this list includes Apache (Apache modules) , Mono (Moonlight), PHP, SQL, java, java script, and flash.

Again, IMO, the best defence you have against such exploits is to keep your system up to date and use Apparmor / SELinux.

With that said, I still think "social engineering" is the easiest attack vector.

---

### Post by Frak on 2009-08-19
> **bodhi.zazen said:**
> With that said, I still think "social engineering" is the easiest attack vector.

And there is no program to fix ignorance.

---

### Post by gn2 on 2009-08-19
> **HymnToLife said:**
> I beg to disagree.

Remember [this]("http://ubuntuforums.org/showthread.php?t=1239826")? Well, who knows how many security holes like this still remain undiscovered? 

Security holes like the one you link to are not viruses.
The OP asked about viruses, not vulnerabilities.
Same principle applies though, those vulnerabilities do not exist because the software is popular.

---

### Post by tsali on 2009-08-19
> **gn2 said:**
> No, don't be ridiculous.

Linux is already installed on 3.7 bajillion servers connected to the internet (stat courtesy of Random Guy On The Internet™) and yet there are no viruses for them in the wild.

Viruses are nothing whatsoever to do with popularity, they are a phenomenon made possible by the poor design of Windows.

This get really old.

SERVER is NOT DESKTOP

Servers are typically administered by professionals. The system is designed to put the needs of the SYSTEM above that of the users. It must do so to protect other users from the malicious acts of any one user.

When you design a desktop system, typically administered by non-professionals, it's value is in the user account. I think you'll see plenty of vulnerability.

The SYSTEM on a desktop is cheap...one might even say it could be free...

---

### Post by automaton26 on 2009-08-19
> **bodhi.zazen said:**
> 
With that said, I still think "social engineering" is the easiest attack vector.

+1

Yes, social engineering is almost always the key that opens the door. 

If Linux became widespread on the desktop, the user demographic would unfortunately mean that both the conditions and incentives would be in place.

Education is the best defence, but can never be a guarantee.

---

### Post by 3rdalbum on 2009-08-19
> **tsali said:**
> This get really old.

SERVER is NOT DESKTOP

Servers are typically administered by professionals.

Web developers are supposed to be professionals, but how many times do you hear that an attacker has managed to download users' cleartext passwords from a site's database? Perhaps once a month? These are often big sites too.

---

### Post by lancest on 2009-08-19
In my opinion there are thousands of newbie Linux desktop users now. Why aren't we hearing of security problems from them? Not just a matter of education but OS design is crucial.

---

### Post by doas777 on 2009-08-19
> **gn2 said:**
> Security holes like the one you link to are not viruses.
The OP asked about viruses, not vulnerabilities.
Same principle applies though, those vulnerabilities do not exist because the software is popular.

you are correct in that an os vulnerability would be "wormable" rather than viral, but almost all malicious code is allowed to act badly because of a vuln like the one in question.

Viruses are by definition application based parasites, in that they perform their bad actions and lifecycle events (spreading) via holes in existing applications. 

a worm, is the same kind of thing, but it attacks holes in the OS itself rather than a specialised application. as a result, a worm generally has more code than a virus, in that it is capable of performing it's bad actions and lifecycle events without the aid of external programs. remember all the hype about conficker earlier this year? it was made possible by an 8 year old vulnerability in the network stack. the kernel vuln from last week is not wormable but would be of great use to any worm that managed to get in via another vector. just getting in is only half the battle.

---

### Post by doas777 on 2009-08-19
> **lancest said:**
> In my opinion there are thousands of newbie Linux desktop users now. Why aren't we hearing of security problems from them? Not just a matter of education but OS design is crucial.

how would they know it was there at all? 
it's not exactly easy to get good insight into what is going on underneath gnome, without some serious study. Heck, I'm still not sure how to view a processes' threads, and each threads mod stack and performance stats.
additionally if they ask for help, they're jumped on by a bunch of folks saying that it is impossible for their linux box to be infected "just cause it;s linux".

---

### Post by lancest on 2009-08-19
> **doas777 said:**
> how would they know it was there at all? 

If your Linux desktop OS is about as secure as Windows and can inherit the same kinds of problems from viruses and worms it should act just the same right? 
Then you might know the same way you know your Windows box is sick; unexplained problems with your mouse, usb viruses, slowdowns, total loss of important files, unexplained packets being sent out because you are part of a criminal botnet etc. 
 Again there are enough thousands of Linux desktop users in my book, that we should be hearing more about the kind of security problems Windows has by now IF THEY EXIST.

---

### Post by Bachstelze on 2009-08-19
> **gn2 said:**
> Security holes like the one you link to are not viruses.
The OP asked about viruses, not vulnerabilities.
Same principle applies though, those vulnerabilities do not exist because the software is popular.

And how do viruses work? By exploiting vulnerabilities in the OS.

---

### Post by bodhi.zazen on 2009-08-19
> **doas777 said:**
> how would they know it was there at all? 
it's not exactly easy to get good insight into what is going on underneath gnome, without some serious study. Heck, I'm still not sure how to view a processes' threads, and each threads mod stack and performance stats.
additionally if they ask for help, they're jumped on by a bunch of folks saying that it is impossible for their linux box to be infected "just cause it;s linux".

+1

Most Windows users do not know they are infected either. Modern cracks are quite sophisticated, Linux cracks even more so.

---

### Post by razorboy5 on 2009-08-19
When viruses were explained to me on Ubuntu, they explained it to me like...

There are holes in the OS. However since it's open source there are unlimited amount of people who can view it and find "holes" in the OS and create patches for it

if this case is true wouldn't more people mean safer Ubuntu?

---

### Post by Bachstelze on 2009-08-19
> **razorboy5 said:**
> When viruses were explained to me on Ubuntu, they explained it to me like...

There are holes in the OS. However since it's open source there are unlimited amount of people who can view it and find "holes" in the OS and create patches for it

if this case is true wouldn't more people mean safer Ubuntu?

No, because very few Linux users actually look at the code and are knowledgeable enough to find holes in it.

---

### Post by razorboy5 on 2009-08-19
well then i hope for some great Open Source anti-Virus programs in the near future :P

---

### Post by bodhi.zazen on 2009-08-19
> **razorboy5 said:**
> well then i hope for some great Open Source anti-Virus programs in the near future :P

Antivirus is not such good technology. Antivirus applications can only scan for known vulnerabilitiies.

Since there are no known active Linux viruses (your system was patched long ago) antivirus will not help you.

If (when) a Linux virus is developed, you will more then likely have a patch available in the time it would take to update antivirus scanners.

We have better technology already, both selinux and apparmor are superior to antivirus scans and I suggest you learn to use them.

Apparmor is default in Ubuntu and I have some profiles here :

[http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-9.04/](http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-9.04/)

Other people have submitted profiles and if you go up a directory or two you will find additional examples.

---

### Post by doas777 on 2009-08-19
what I would like to see is behavioural detection. don;'t look at the executable, but what actions it attempts to take.

---

### Post by doas777 on 2009-08-19
> **razorboy5 said:**
> When viruses were explained to me on Ubuntu, they explained it to me like...

There are holes in the OS. However since it's open source there are unlimited amount of people who can view it and find "holes" in the OS and create patches for it

if this case is true wouldn't more people mean safer Ubuntu?

yes, if the people did nothing but review code. 
as it stands more users => more developers => more apps => more review required.
and as several have pointed out, some folks discovered an 8 year old kernel vulnerability just last week.

the more complex and useful code is, the less secure it can claim to be.

---

### Post by Sealbhach on 2009-08-19
We won't ever really know until Linux distros face the same conditions as Windows - millions of users who don't know how to be careful + a full onslaught from virus creators.

.

---

### Post by gn2 on 2009-08-19
> **HymnToLife said:**
> And how do viruses work? By exploiting vulnerabilities in the OS.

Which OS?

GNU/Linux?

Name one succesful GNU/Linux virus that currently thrives in the wild.

As I have said before, **viruses** are a Windows phenomenon.

Pebcak errors (facilitated by vulnerabilities or otherwise) are universal and unpreventable. ;)

---

### Post by Bachstelze on 2009-08-19
> **gn2 said:**
> 
Name one succesful GNU/Linux virus that currently thrives in the wild.

Stay on topic. The question at hand is not whether Linux viruses *currently* exists, but whether they are likely to appear in the future.

---

### Post by gn2 on 2009-08-19
> **HymnToLife said:**
> Stay on topic. The question at hand is not whether Linux viruses *currently* exists, but whether they are likely to appear in the future.

OK, the future.....
When looking to the future, usually lessons are learned from the past.
What we know is that since Linux came into being no effective Linux viruses have been created and that none exist right now.
This is what we know now of the past and present.
We cannot know what will happen in years to come, sadly there is no certain method of predicting the future*, but in my view it is extremely unlikely that the trend of the past two decades will change significantly.

It is the nature of Linux, not it's (perceived) lack of popularity which has prevented creation of effective viruses for it.
Increasing the popularity will have no effect.
Breeding more dogs won't make dogs susceptible to fish diseases.

*If you know otherwise can you pm me this coming saturday night's winning lottery numbers please? :)

---

### Post by aysiu on 2009-08-19
> **doas777 said:**
> what I would like to see is behavioural detection. don;'t look at the executable, but what actions it attempts to take.
A lot of antivirus software does this, too (in addition to screening for a large subset of known offenders).

Unfortunately, since it has to follow some kind of algorithm, this method is not foolproof and ends up with a lot of false positives, ultimately leaving it to the user to decide what is trustworthy and what is not.

Bottom line: no matter what OS you run, antivirus software is not good security or protection. It's useful pretty much for mail servers.

---

### Post by afmGM on 2009-08-22
When the market share becomes big, there will be some, but not like how Windows is.  No matter how secure an OS is, **if someone wants to do something, they will do it.**

Viruses are made by people.  People can get stubborn and determined, and not give up till they do what they want. 

Although it would much harder to make viruses for linux.  There have been linux viruses before.

P.S  Even if the virus needs to request administrative purposes, the standard user would allow it.  Probably making social engineering exploits used on linux (which is currently happening to mac).

Edit:  Saying that viruses will never happen on linux, is giving people the view that we don't have to worry, and that we could do risky computer moves.  Attitude like that is why mac users are being infected with trojans, as they think it's safe to download anything.

---

### Post by MikeTheC on 2009-08-22
> **HymnToLife said:**
> Stay on topic. The question at hand is not whether Linux viruses *currently* exists, but whether they are likely to appear in the future.

"Objection, Your Honor..."

Remember the adage "Those who fail to study history are condemned to repeat it."

With all due respect, trying to predict the future -- which is what your warning clearly is targeted towards -- is unrealistic at best without considering the historical fact which is there have been perhaps what, two or three viruses written, ages ago, and were largely considered to be kind of proof-of-concept and not really distributed.

One should also wisely consider that at present there aren't any viruses for Linux despite how many Linux boxen there are out there, and despite how many of them are publicly exposed servers. That is not a trivial thing to be able to say.

---

### Post by Frak on 2009-08-22
> **MikeTheC said:**
> "Objection, Your Honor..."

Remember the adage "Those who fail to study history are condemned to repeat it."

With all due respect, trying to predict the future -- which is what your warning clearly is targeted towards -- is unrealistic at best without considering the historical fact which is there have been perhaps what, two or three viruses written, ages ago, and were largely considered to be kind of proof-of-concept and not really distributed.

One should also wisely consider that at present there aren't any viruses for Linux despite how many Linux boxen there are out there, and despite how many of them are publicly exposed servers. That is not a trivial thing to be able to say.
For servers, go back and read what I had to say about attacking the service, not the host.

If you look to the past, you have to look at events that followed the same timeline. When Apple computers were popular, there were a lot of viruses written for it. When MS-DOS became popular, a lot of viruses were written for it. When Apple's computers dwindled in sales, surprise, there weren't many viruses written for it.

---

### Post by nomnomnom on 2009-08-22
nutkinnz was ere' 2

---

### Post by MikeTheC on 2009-08-23
Yes, but what you folks aren't getting at is how massively peer-reviewed Linux is. Hands down that's why it's become as secure and solid as it actually is, over and above (and in rather stark contrast to) anything Microsoft has put out -- both MS-DOS and Windows tyvm -- and even compared to Classic Mac OS (especially) and Mac OS X (less so, but still to a very significant extent).

It's not that it is "physically impossible" to write a virus for it, or some other kind of malware for it, but then again I could defeat all the security arrangements at Fort Knox if, theoretically, I had a big enough helicopter and long enough and strong enough cables to wrap around the building and rip it out of the ground.

Security is a layered and progressive thing anyway, not an absolute concept.

---

### Post by staf0048 on 2009-08-23
Yes it will.  For the simple fact that as it's popularity increases, more and more people with limited computer knowledge will begin to use the system and unknowingly or ignorantly let intruders do what they will.  "Oh I got an email saying I'll win $1,000,000 if I just open this link.  Sure, I'll enter my root password for a million big ones!!!"  

Thankfully the same virus won't spread as much due to Ubuntu's security, but they'll still be around.

---

### Post by gn2 on 2009-08-24
> **staf0048 said:**
> Yes it will.  For the simple fact that as it's popularity increases, more and more people with limited computer knowledge will begin to use the system and unknowingly or ignorantly let intruders do what they will.  "Oh I got an email saying I'll win $1,000,000 if I just open this link.  Sure, I'll enter my root password for a million big ones!!!" 

What you describe isn't a computer virus.
Popularity plays no part in virus creation.

---

### Post by Frak on 2009-08-24
> **gn2 said:**
> What you describe isn't a computer virus.
Popularity plays no part in virus creation.
Creation... No.
Proliferation... Yes.

---

### Post by Bachstelze on 2009-08-24
> **MikeTheC said:**
> Yes, but what you folks aren't getting at is how massively peer-reviewed Linux is.

With awesome results.

---

### Post by gn2 on 2009-08-24
> **Frak said:**
> Creation... No.
Proliferation... Yes.

How does that which is has not been created manage to proliferate? :confused:

---

### Post by Sealbhach on 2009-08-25
> **HymnToLife said:**
> With awesome results.

Is this sarcasm? I can't tell.:confused:

.

---

