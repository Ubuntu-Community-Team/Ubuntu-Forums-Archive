---
title: "Why is Linux secure?"
date: 2011-01-11
forum: Recurring Discussions
---

### Post by raequin on 2011-01-11
I am wondering why Linux is so secure.  Is it the relative popularity of Windows or the inherent robustness of Linux?  What I'm saying is, if Linux supersedes MS in the number of users, would virus writers turn their focus to this operating system and thus create lots of problems?  Or is it that Linux is to these miscreants and impenetrable design?

I hope this is clear.  It just is an interesting question to me why Windows is plagued with viruses and spyware while Linux has no such predators, and whether or not this will continue to be the case.

---

### Post by NightwishFan on 2011-01-11
It is designed with security in mind and the code is open. Try googling "Linus' Law" to learn more.

---

### Post by Miljet on 2011-01-11
Unix, and in turn Linux, was originally designed for multiple users on the same machine. And the security was designed in.

Microsoft was originally designed for one user on one machine with no consideration for networking.

The more Microsoft tries to address security design flaws, the more it starts to looks like Unix.

---

### Post by Quackers on 2011-01-11
I suspect one of the main reasons is that .exe files cannot run by default.

---

### Post by walt.smith1960 on 2011-01-11
I think part but not all the problem with Windows is that XP was first released before the internet was popular so spreading malware was more diffficult.  To make XP easy to use, permissions were set to allow it to do about anything with about anybody.  It took until Service Pack 2 for this to change.  Of course Win7 continues to make the news (and not in a good way) so there are other issues as well.  Microsoft has a huge installed base. How do they fix their myriad problems without causing poorly designed but popular programs to fail and require upgrade$?

A possible second reason Linux is more secure is that the user base in addition to being smaller is also more savvy. Most desktop Linux users know not to click on every banner ad and .exe file they see.

---

### Post by I'mGeorge on 2011-01-11
It's because linux it's mainly built around security while windows focuses more on aspects like functionality and entertainment.

---

### Post by mathgeek2000 on 2011-01-11
When a file is saved/downloaded from the Internet to a Linux machine, generally the permissions are set w/o the Execute bit. -- In otherwords you can't run a script, without thinking about it first.

But I wonder - Is this general 'Linux is more secure' theory still holding true when various web sites can hold hidden dangers in script files, java and javascript which executes in any browser -- are those scripts looking for Windows PCs, or can they affect any OS? - Could a Javascript program for example search for and pull names from a Thunderbird Address book on a person's PC, regardless of that PC being a Linux, Windows, or Mac OS X box?

Also it goes without saying anyone should be cautious of phishing e-mails.

---

### Post by endotherm on 2011-01-11
much of Unix's robustness comes from insulating and isolating multiple users and their processes. when one bad user can take down the platform supporting dozens or hundreds of users at once, you tend to build firewalls to prevent one users issues from affecting the others. 

Unix also has a clear distinction between system space, and user space. this boundary is very important to system security. only trained administrators are allowed to modify system space.

Unix is also much more modular than windows and other newer platforms, and can be composed of numerous optional components, so attackers have much more uncertainty as to whether their exploit code can function on that particular type of host.

---

### Post by Paqman on 2011-01-11
It's a combination of sound design and low usage. 

One of the most important reasons that people often forget to mention is package managers. Linux systems typically get their software from repositories and can upgrade any package they have installed. This means that when a vulnerability is patched, it's rapidly disseminated to users. Ubuntu can push a security update to an app out to the vast majority of all users within a handful of days, which makes the window of opportunity for attack very small.

Windows and OS X have no integrated, automated way of patching vulnerabilities in apps like this. They can only patch vulnerabilities in the core OS. The problem is that it's often apps that are exploited by malware. Those systems are left relying on a patchwork of individual updaters for apps, or worse, relying on users to make sure their apps are to date.

In short, desktop Linux is a smaller, faster moving target than the rest of the herd. As a result, predators go for the bigger, slower moving prey.

---

### Post by s1wood on 2011-01-11
I was trying to explain the advantages of Linux to my teenage son (indoctrinated by Microsoft via his school): when I got to the security bit he snorted and said "It's all these Linux crazies out there who write the viruses, of course they don't mess up their own systems!"
We have some sort of image problem I think..

Susan

---

### Post by NightwishFan on 2011-01-11
No, more likely it is the companies that make money solely on anti-virus products. They at least have something to gain from hundreds of computers working improperly in a way "they" know how to fix.

---

### Post by Quackers on 2011-01-11
> **NightwishFan said:**
> No, more likely it is the companies that make money solely on anti-virus products. They at least have something to gain from hundreds of computers working improperly in a way "they" know how to fix.

An excellent point! One that my cynical mind has been mulling over for quite some time :-)

---

### Post by marin123 on 2011-01-11
while using windows i had a lot of cracked programs, and a lot of cracks contain viruses, spyware, etc...
linux users are more careful than windows users (the civilians :D) and youre less likely to catch something.
this is my opinion and my experience with linux vs windows.

---

### Post by hansolo4949 on 2011-01-11
One of the main reasons Linux is so "secure" is that it sort of under the radar in the (malicious) hackers world, so why try create a virus for a OS that has a few thousand people on it, when he can write a virus for windows, which is far easier to exploit, and there are millions of people who are potentially affected. Plus, linux software mostly comes from trusted sources, and most of the time, you can't download linux software from [www.joesinfectedsoftware.org](www.joesinfectedsoftware.org) (a made-up url by the way), so you're pretty safe that way, too. If you want even more protection, there are many firewalls and antivirus suites for linux, which are completely free! (that's the one of the aspects where I love Ubuntu). I don't know about hackers trying to gain control of your computer, but Ubuntu makes it a lot harder to hack into it than microsoft does.

hansolo4949

---

### Post by A_M_S on 2011-01-11
Trusted software  repositories are also a good way to avoid virus propagation.

---

### Post by bodhi.zazen on 2011-01-11
*Thread moved to **Recurring Discussions**.*

Popularity of an OS has little or nothing to do with security.

Security has to to with many factors including convienience and how often, if ever, vulnerabililties are patched.

Microsoft has a poor track record of patching security holes, and thus one need any variety of third party applications to harden the OS.

If you are interested in Linux security see:

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

[http://www.debian.org/doc/manuals/securing-debian-howto/](http://www.debian.org/doc/manuals/securing-debian-howto/)

[http://docs.fedoraproject.org/en-US/Fedora/14/html/Security_Guide/](http://docs.fedoraproject.org/en-US/Fedora/14/html/Security_Guide/)

[http://www.theregister.co.uk/2004/10/22/security_report_windows_vs_linux/](http://www.theregister.co.uk/2004/10/22/security_report_windows_vs_linux/)

Or google search for yourself.

---

### Post by Ubunt2u on 2011-01-11
i dual boot vista/ubuntu.  i have been a loyal ubuntu user and hardly ever even use my vista.  this point has been argued over and over but i suspect windows is less secure because a) its design b) its the most popular os so that's what attackers go after.  i thought it was funny when vista first came out and the uproar over microsofts futile attempt to emulate linux by implementing the UAC (user account control).  windows users simply didnt want to be bothered with it.  of course us linux users had been seeing such behavior in linux forever.  no big deal to me.  what's funnier, is UAC doesn't do squat.  it's so sad how UAC never keeps viruses, spyware and malware from infecting pcs.

---

### Post by abdulapopoola on 2011-01-11
I bet if Linux were as popular as Windows, we would have as many virus problems too.
Also, the design and software repositories in Linux make it much more secure.

Open source rocks!!!
[http://abdulapopoola.wordpress.com](http://abdulapopoola.wordpress.com)

---

### Post by bodhi.zazen on 2011-01-11
> **abdulapopoola said:**
> I bet if Linux were as popular as Windows, we would have as many virus problems too.

This is a popular fallacy.

---

### Post by 3Miro on 2011-01-11
[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

- If Linux were more popular, then there would be more malicious attempts to break the system, however, Linux is more secure by design. The only way to prevent the user from damaging their own machine is to prevent the user form using their own machine; however, there are ways to prevent unintended damage.

- Linux (and a FOSS system in general) will never need an AV software to keep it safe (just keep it updated). 

- Unix is very restrictive to what can and cannot be done, so in general it is much harder to bypass security. It is incredibly hard for a browser vulnerability to grow to a vulnerability of the entire system. Even if damage is done, it is localized (there is a long road form reading your browser history, to sending spam to everyone in somebody's mailing list).

- With free repository, the need to download software from the internet to do simple tasks is gone. People download less, then they run less risk.

- Linux runs on may (if not most) very sensitive machines. There is huge commercial interest to keep the system safe.

---

### Post by NightwishFan on 2011-01-11
Not to mention apparmor which is installed in Ubuntu seems promising.
[http://en.wikipedia.org/wiki/AppArmor](http://en.wikipedia.org/wiki/AppArmor)

---

### Post by walt.smith1960 on 2011-01-11
> **mathgeek2000 said:**
> When a file is saved/downloaded from the Internet to a Linux machine, generally the permissions are set w/o the Execute bit. -- In otherwords you can't run a script, without thinking about it first.

But I wonder - Is this general 'Linux is more secure' theory still holding true when various web sites can hold hidden dangers in script files, java and javascript which executes in any browser -- are those scripts looking for Windows PCs, or can they affect any OS? - Could a Javascript program for example search for and pull names from a Thunderbird Address book on a person's PC, regardless of that PC being a Linux, Windows, or Mac OS X box?

Also it goes without saying anyone should be cautious of phishing e-mails.

I recall reading about a cracking contest a few years ago--OSX, Vista(at the time) and Linux.  OSX was cracked pretty quickly, not because OSX was flawed but because Java or Flash had a weakness known to the contestant like mathgeek2000 references which enabled him to control the OS.  Vista took longer but was eventually cracked. Linux wasn't cracked in the allotted time.

---

### Post by raequin on 2011-01-11
Thanks for all the replies.  These are great answers to the original question.

---

### Post by kaldor on 2011-01-11
> **walt.smith1960 said:**
> I recall reading about a cracking contest a few years ago--OSX, Vista(at the time) and Linux.  OSX was cracked pretty quickly, not because OSX was flawed but because Java or Flash had a weakness known to the contestant like mathgeek2000 references which enabled him to control the OS.  Vista took longer but was eventually cracked. Linux wasn't cracked in the allotted time.

I believe OS X's problem was with Safari, not Flash/Java.

---

### Post by Pogeymanz on 2011-01-11
In the era of Windows Vista/7, I'd venture to say that desktop Linux distros are no more secure than Windows.

They are actually both moderately secure, but if Linux were as popular as Windows, I'd bet that there would be a fair amount of malware for it.

Sure, a server with well-configure SELinux rules and IPTables will be pretty secure, but that is not a reality often realized on home computers.

EDIT:
These days, it's not the OS that is insecure, it's the software you run on it. In the last few years there have been huge holes found in Apache, Openssh and even the Linux Kernel(!!!).

Web browsers and email programs will always be the best way to attack a home user. Adobe products make good targets, whether on Windows or Linux.

Also, Koobface virus can now infect Linux computers.

---

### Post by bodhi.zazen on 2011-01-11
> **Pogeymanz said:**
> In the era of Windows Vista/7, I'd venture to say that desktop Linux distros are no more secure than Windows.

citation needed.

> They are actually both moderately secure, but if Linux were as popular as Windows, I'd bet that there would be a fair amount of malware for it.

citation needed.

> Sure, a server with well-configure SELinux rules and IPTables will be pretty secure, but that is not a reality often realized on home computers.

From your post I see you have not run Fedora in a while. selinux is up an running on a Fedora desktop , has been for a while now.

On the Ubuntu side we have apparmor, to bad it is not as mature as selinux, but one can enable it if you so desire.

> EDIT:
These days, it's not the OS that is insecure, it's the software you run on it. In the last few years there have been huge holes found in Apache, Openssh and even the Linux Kernel(!!!).

first it is one thing to have a vulnerability reported and another to see an exploit taking advantage of such vulnerabilities.

Second, there are patches patches for all that. Microsoft is notorious for leaving security  holes unpatched for years.

The question is not if there are or are not vulnerabilities, the question is how long does it take them to get patched. Micrisoft is so slow at patching code there is an entire security industry selling people firewalls to patch vunlerable services and antivirus to clean up after exploits to the code have done their damage.

Linux security is much much more proactive in patching potential exploits, often a fix is available within 24 hours.

> Web browsers and email programs will always be the best way to attack a home user. Adobe products make good targets, whether on Windows or Linux.

Also, Koobface virus can now infect Linux computers.

The easiest target is and likely always will be social engineering. It is much easier to fool someone with Phishing or Hey install this nifty package or what not then it is to reverse engineer the code.

---

### Post by 3Miro on 2011-01-11
> **Pogeymanz said:**
> In the era of Windows Vista/7, I'd venture to say that desktop Linux distros are no more secure than Windows.

They are actually both moderately secure, but if Linux were as popular as Windows, I'd bet that there would be a fair amount of malware for it.

Sure, a server with well-configure SELinux rules and IPTables will be pretty secure, but that is not a reality often realized on home computers.

EDIT:
These days, it's not the OS that is insecure, it's the software you run on it. In the last few years there have been huge holes found in Apache, Openssh and even the Linux Kernel(!!!).

Web browsers and email programs will always be the best way to attack a home user. Adobe products make good targets, whether on Windows or Linux.

Also, Koobface virus can now infect Linux computers.

If it were more popular, Linux would be more vulnerable. Inept users are vulnerable under any system. However, ultimately Linux is better. Any problem found is patched very fast and there is no need for third party AV software. Out of the box Ubuntu is as secure as it gets, out of the box Windows needs quite a bit of work to be taken to a "secure enough" level.

Someone covered AppArmor and SELinux. Also, Ubuntu doesn't need full scale IPTables firewall, unless you are running a server or installing from untrusted sources. Having no ports open is better than any Firewall.

Under a Unix environment, even if a Browser/Flash has a vulnerability, the damage is well contained. There is a big difference between small vulnerability like seeing what pages I have visited and being able to completely take over a machine. There are levels of damage and vulnerability and the Unix architecture is much better in preventing and containing problems.

---

### Post by Wood Prof on 2011-01-11
My opinion, for what is worth, is that it is the permissions that the users have  (individual programs and operating system wide) that makes Linux more secure.  Along with all of the updates and the turn around on producing them when a problem is spotted.  As it was said earlier, MS leaves some things un-patched for a long time.

I have had two machines hacked, both running XP.  One was left on by a technician I had over a weekend (this is pre service pack 2) and when I came in on Monday it had been turned into a server for Indian porn.  That was user error and a weak password on technician's part.

The other XP computer was hacked as I was logging off and shutting it down for the weekend.  There was a known flaw in XP at the time (the sys admin and I were both unaware of it), and the person gained control of the computer.  We could find where they had been in looking around, but couldn't find where they changed anything.  To be safe, the computer was formatted and everything was put back on from the image before the attack.  Two weeks later MS provided a patch.

So in one case it was user error, in the other it was a known hole in the operating system that was exploited.

As a side note to all of this, I taught GIS for two years.  At the time the school had two labs, one running UNIX, the other running Windows 2000.  All of the computers were Silicon Graphics Inc. machines.  There was a flaw at the time in the hardware that allowed hackers to create a new admin account on them (that's what we were told).  They were successful at doing it on the Windows computers (25 individual computers), but on the UNIX stations, they could create the account, but had no permissions to do anything to the data.

---

### Post by Ahava591 on 2011-01-12
There's an entire security sub-forum devoted to nothing but this topic; why the OP started a thread asking "Why is Linux secure?" is beyond me.



Next time, try Google and try actually reading the forums.

---

### Post by Evil-Ernie on 2011-01-12
I really REALLY hate the 'If Linux was a popular as Windows...' etc etc.
 
I think it comes down to 4 big facts that make Linux more secure:
 
1) Informed Users - Generally Linux users are more computer literate so are less likely to download malware, open a bad email or click on something they shouldnt.
 
2) Free Software Repositories - It is more likely on a Windows machine a cracked piece of software is uploaded or dodgy freeware from a bad source. On Linux we dont need to go down those routes to get our software.
 
3) Root Access - To gain root access you need to put a password in. A big stumbling block for mischief.
 
4) Constant Updates - With a whole community reporting bugs and holes, patching them and the speedy distribution of patches makes it difficult to exploit these breaches.
 
Granted if Linux was much more popular there would be focus on trying to break into the system but even still I think any hacks would revolve around the human element rather than the security of the system.

---

### Post by walt.smith1960 on 2011-01-12
> **kaldor said:**
> I believe OS X's problem was with Safari, not Flash/Java.

You're probably right. I knew it was some sort of add-on.

---

### Post by oldos2er on 2011-01-12
> **Evil-Ernie said:**
> Granted if Linux was much more popular there would be focus on trying to break into the system but even still I think any hacks would revolve around the human element rather than the security of the system.

People always seem to forget the "popularity" of Linux servers; granted they are most likely security-hardened beyond an average Linux desktop system.

---

### Post by Com_2_Reset on 2011-01-12
Because of all the above answers, I stopped using windows  (3 months ago)and started using Linux. I can feel the difference between them. Linux is more fast, stable, secure and free. I appreciate the good work of the people behind Linux.

---

### Post by Pogeymanz on 2011-01-12
> **bodhi.zazen said:**
> 

Second, there are patches patches for all that. Microsoft is notorious for leaving security  holes unpatched for years.

Citation needed.

> 
The question is not if there are or are not vulnerabilities, the question is how long does it take them to get patched. Micrisoft is so slow at patching code there is an entire security industry selling people firewalls to patch vunlerable services and antivirus to clean up after exploits to the code have done their damage.


Citation needed.

> 
Linux security is much much more proactive in patching potential exploits, often a fix is available within 24 hours.


Citation needed.

Besides me trolling you, I think these claims of open source software being patched immediately are highly exaggerated.

No, I do not have any citation, but I'd be willing to bet that any security hole that was patched in 24 hours was a very, very simple fix. This also doesn't take into account that it will take time for that to trickle down to the Ubuntu repos.

On the other hand, as soon as Microsoft fixes a problem in their software, they can push an update to their users. They don't have to wait for distro developers to get the memo.

And there were some holes in free software that were around for a long time. Just because it was fixed two days after going public doesn't mean that somebody wasn't exploiting it already. I think the recent kernel hole to which I referred had been there for at least a few years before we all knew about it. That's dangerous.

---

### Post by Pogeymanz on 2011-01-12
> **oldos2er said:**
> People always seem to forget the "popularity" of Linux servers; granted they are most likely security-hardened beyond an average Linux desktop system.

The second half of your sentence is the key point. Servers monitor traffic through their open ports. They also don't allow write access to all users/applications. Most ports are closed.

Desktop users want to torrent the latest Metallica album and allow Firefox to write flash cache to the disk. They also connect to peers to play games.

Lots more ways to compromise a desktop.

And plenty of servers are compromised anyway with dictionary brute-force attacks.

If we perpetuate the myth that Linux is bullet-proof then people wont take security seriously. Then, if Linux every becomes popular, it will be more virus-infected than Windows, because at least Windows users know to run anti-virus software.

---

### Post by endotherm on 2011-01-12
> **Pogeymanz said:**
> 
Desktop users want to torrent the latest Metallica album....

no we don't

---

### Post by bodhi.zazen on 2011-01-12
> **Pogeymanz said:**
> I think these claims of open source software being patched immediately are highly exaggerated.

They are ?

Top of the list
[http://www.ubuntu.com/usn](http://www.ubuntu.com/usn)

[http://www.ubuntu.com/usn/usn-1009-2](http://www.ubuntu.com/usn/usn-1009-2)

[https://bugs.launchpad.net/ubuntu/+source/eglibc/+bug/701783](https://bugs.launchpad.net/ubuntu/+source/eglibc/+bug/701783)

Fix released within 3 hours of the report.

Does not look like an exaggerated claim to me.

Lets look at some data.

_Microsoft_:

[http://secunia.com/factsheets/Windows7-2010Q3.pdf](http://secunia.com/factsheets/Windows7-2010Q3.pdf)
[http://secunia.com/factsheets/IE8-2010Q4.pdf](http://secunia.com/factsheets/IE8-2010Q4.pdf)

Here is a summary for Windows 7

[http://secunia.com/advisories/product/27467/](http://secunia.com/advisories/product/27467/)

13 % (7 of 52) unpatched vulnerabilities.

_Ubuntu_:

Same reporting agency, look at Ubuntu 10.04

[http://secunia.com/advisories/product/30524/](http://secunia.com/advisories/product/30524/)

0 of 89 remain unpatched

And Ubuntu 10.10

[http://secunia.com/advisories/product/32688/](http://secunia.com/advisories/product/32688/)

0 of 38 remain unpatched

Same for [Debian](http://secunia.com/advisories/vendor/47/) and [Fedora](http://secunia.com/advisories/product/33024/).

I agree there are varying degrees of complexity in patching code and not all code can be patched rapidly.

But I think you over generalize, and you need to compare apples to apples.

Unknown vulnerabilities in any OS or application are exactly that , unknown. How many unknown vulnerabilities are there ? When will the be discovered ? Who knows.

A vulnerability is a potential, and has not yet been exploited. Just because in your example there is a vulnerability in an application does not mean it has been exploited. If you look at a few hundred reports, these vulnerabilities are relatively rapidly patched in Linux (relative to Windows) and slower in Windows (relative to Linux).

An exploit is the ability to take advantage of known unpatched vulnerabilities. Vulnerabilities exploited by viruses and worms remain unpatched in Windows, this is a larger problem then the kernel example you cite. Although there have been Linux viruses and worms, the Linux code is patched. Microsoft simply takes longer, and leaves things unpatched, and thus Windows users rely on third party applications and antivirus scanners.

---

