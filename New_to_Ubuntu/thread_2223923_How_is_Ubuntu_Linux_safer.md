---
title: "How is Ubuntu Linux safer?"
date: 2014-05-13
forum: New to Ubuntu
---

### Post by newbie4 on 2014-05-13
I understand that there's an ongoing debate to why and how safer Linux is in general.
I would like to understand how though... (Not just malware and viruses, but "break-in" aspects also)
For example, there's this article that covered vulnerabilities and holes in Ubuntu: 
[http://www.zdnet.com/ubuntu-forums-hacked-1-82m-logins-email-addresses-stolen-7000018336/](http://www.zdnet.com/ubuntu-forums-hacked-1-82m-logins-email-addresses-stolen-7000018336/)

I'm looking for a break-down/good explanation to a beginner rather than a comparison (attack) to other OS' without backing.
(example of what I'm not looking for: Windows have more holes and vulnerabilities which is why they always need patching, compared to the rare Linux patching)

Some have even argued that the hacked, rooted, and infected Ubuntu machines will of course be way less than Windows, simply because  Linux it's only a small percentage in the OS market, which kinda' makes sense.

Thanks guys (and gals if any)

---

### Post by sudodus on 2014-05-13
This link can be a good starting point

[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

---

### Post by pfeiffep on 2014-05-13
The article is somewhat concerning ... remember that it was published ***[COLOR=#0000cd][FONT=Verdana]July 21, 2013.  [/FONT][/COLOR][COLOR=#6C7376][FONT=Verdana]"[/FONT][/COLOR]***[COLOR=#252525][FONT=Verdana]***The forum itself is understood to be using vBulletin, a popular Web-based forum software."***

[B]Canonical was acting responsibly by disclosing this breech. The article did not disclose whether the OS or hosting software was the weakness (or for that matter if it was an 'inside breech')
[/B]
While security by obscurity is generally not a good practice, leveraging it as a comprehensive solution isn't bad
[LIST]
[*]Linux certainly has a smaller number installed instances than Windows
[*]It is very difficult to gain privileged access when targeting Linux
[*]There have been very few instances of Linux Malware in the wild
[*]Linux users just might be a bit more security / privacy aware
[*]Linux is Open Source - so weaknesses are disclosed and remedied quickly by the community
[/LIST]


[/FONT][/COLOR]

---

### Post by stevebag on 2014-05-13
I don't think the article concerning Ubuntu Forums being hacked and whether or not Linux is a safer operating system are the same thing. Hacking a website and infecting a PC are different questions, at least I don't think that is what you are asking.

My understanding is that the biggest difference has to do with permissions that are given to users. Linux does not run in root by default. What that means is that administrative privileges require permission; the equivalent in Windows is the Administrator and when running as Adminstrator in Windows no permissions are required. Windows has attempted to address this problem with User Account Control; if you are a Windows user you should not run as an Adminstrator, you need to set up users who have non-administrator privileges. I have found their system to be irritating, but you will be safer if you do so.

---

### Post by HiImTye on 2014-05-13
generally, if there is a security issue with the Linux kernel, or a piece of *nix software, it gets patched and rolled out, and it takes very little time for 'security' fixes to be rolled out in most distros (where as feature updates are typically held until the next release).
the general system structure is such that one user's userspace is a possible infection zone, but outside of that zone is generally safe, and the default configurations are typically fine to protect against possible attack vectors (AppArmor profiles, iptables rules, etc).
the icing on the cake is when a user uses Linux, the basic security model forces the user to consider security risks. "I need to enter my password, am I doing something that is potentially dangerous?" a decent level of give-and-take has been reached in the Linux model, the user is not constantly pestered by security questions (Vista, anyone?), but does face a real obstacle to performing system maintenance tasks that forces them to consider whether they should be doing so or not.

---

### Post by QIII on 2014-05-13
The hacking of the Ubuntu forums had exactly nothing to do with the security of Linux nor anything to do with the OS the servers run on.

---

### Post by grahammechanical on 2014-05-13
The hacking of Ubuntu forums should not be used as an example of Linux/ubuntu not being secure because the breach was caused by someone with administrator privileges for the forum software not keeping their administrator password secure. 

[http://www.theregister.co.uk/2013/08/02/ubuntu_forum_hack_postmortem/](http://www.theregister.co.uk/2013/08/02/ubuntu_forum_hack_postmortem/)

How many security breaches in large corporations are down to management not having proper security oversight? Think Wikileaks. Think Snowden. Think also of those cases where one "rogue" trader has managed to bring a massive investment institution into bankruptcy. Ineffectual management oversight is, in my opinion, a greater security risk than badly written software code. Or, clever crooks.

Linux is safer because it is open source.  This means that independent investigators can legally  examine the source code to identify vulnerabilities. And the Linux developers can then respond quickly to patch the vulnerability.

Ubuntu is safer because it is using the open source code of other developers and if a vulnerability in what is called "upstream" code is identified the ubuntu developers can put in a patch without waiting for the upstream developer to do so. Ubuntu users will get an updated version of the code within days. An example of this was the recently identified OpenSSL vulnerability called "heartbleed."

Regards.

---

### Post by HiImTye on 2014-05-13
the human element is almost always the weakest element

---

### Post by coffeecat on 2014-05-13
First - as has been already stated, the security breach last July had absolutely nothing to do with the underlying operating system the servers run on, which is Ubuntu. The foot in the door, so to speak, was a compromised sub-forum moderator account, from which the attacker gained access to an administrator account by means of some cunning trickery, combined with (now fixed) vulnerabilities in the vbulletin forum software.

Second, if people wish to comment on the security breach would they please double-check any facts before posting:

> **grahammechanical said:**
> The hacking of Ubuntu forums should not be used as an example of Linux/ubuntu not being secure because the breach was caused by someone with administrator privileges for the forum software not keeping their administrator password secure. 

The initial compromised account was not an administrator one, but a sub-forum moderator account. We have no idea how the attacker gained access to that account. Maybe the account holder did not keep their password secure, or maybe the email account registered to the forum account was compromised, but that is all speculation and will always be so.

Rather than rely on second-hand accounts, the source story can be seen here:

[http://blog.canonical.com/2013/07/30/ubuntu-forums-are-back-up-and-a-post-mortem/](http://blog.canonical.com/2013/07/30/ubuntu-forums-are-back-up-and-a-post-mortem/)

Many of the discussion comments in the znet article (linked in the OP) display a breathtaking and distressingly profound presumptuous ignorance.

---

### Post by buzzingrobot on 2014-05-13
If memory serves, at least a few other vBulletin sites were also attacked last year.

Windows and Linux use different security models.  Detemining if one is more secure than the other depends on an endless string of variables, the most important being user behavior.  Certainly, Windows is a much more frequent target because attacks there return the most profit. In that sense, an inattentive lazy Windows user is more likely to be open to threats than on Linux.

Most attacks these days seem to come as invitations to users to do something stupid on the net. Little an OS can do if you agree to be conned.

---

### Post by oldrocker99 on 2014-05-13
And I will add, that after six years of Ubuntu usage, I have had exactly 0 (none) examples of malware, port attacks, or any other kind of attack. GNU/Linux is simply safer, far, far safer than any closed-source OS by its very nature.

And, you can take that to the bank.

---

### Post by newbie4 on 2014-05-13
Thanks for all the responses.  
Now how about the "breaking-in" issue?  (As in someone hacking, rooting, etc., rather than just malwares and viruses...)
Is Linux less-vulnerable to attacks such as hacking, rooting, etc. ?

I watched this video and the way things were addressed is pretty much the explanation I was looking for. Brief but informative...
[http://www.youtube.com/watch?v=Liw86dRI0Qo](http://www.youtube.com/watch?v=Liw86dRI0Qo)

---

### Post by oldrocker99 on 2014-05-13
If you, right after installing, open a terminal and type
```
sudo ufw enable
```
then (if you check with a port scan) you will see that your system is 100% unscannable. Take anything Kapersky says with at least a grain of salt; they **are** in the business of selling antimalware. I repeat that, in six years, I have had **0** malware instances.

---

### Post by HiImTye on 2014-05-13
> **newbie4 said:**
> Thanks for all the responses.  
Now how about the "breaking-in" issue?  (As in someone hacking, rooting, etc., rather than just malwares and viruses...)
Is Linux less-vulnerable to attacks such as hacking, rooting, etc. ?

I watched this video and the way things were addressed is pretty much the explanation I was looking for. Brief but informative...
[http://www.youtube.com/watch?v=Liw86dRI0Qo](http://www.youtube.com/watch?v=Liw86dRI0Qo)

the points he raises in the start of that video are valid (I only watched about a minute of it). if your Linux system is never updated, it is a giant security hole. the same can be said of any other operating system that is never maintained. internet facing appliances whose firmware is never updated or whose firmware doesn't contain recent security updates to libraries or software it ships with is the biggest problem in security these days, as is evidenced by the numerous reports of their exploitation (eg. the Target credit card hacks). most of these appliances run Linux, which does a big disservice to the question of security on Linux.

that said, a well maintained and configured Linux system is much more secure than the average Windows system, and I would even go so far as to say a default Linux install for any of the most common 'every day' computer use distros (and by this, I mean to say that I don't include 'special purpose' distros such as BackTrack) is more secure than a well configured Windows system, and the main reason is that uneducated users have less ability to break their system by mistake by simply browsing the interwebs, or accidentally installing a .exe on a Windows forum, or through a pop-up ad.

and then there's the ability to deeply configure your system to be even more secure. below are a list of common tools to secure your Linux system, and none of these come with the 'unknown' element of a questionable source, or fighting to find an affordable alternative:
*for configuring your firewall (netfilter) there are several front ends. here are a few:
-iptables - all other front ends rely on this, and it is the most powerful option. there's no substitute for learning iptables.
-ufw - ufw is very simple to use and offers great configuration. it is command line based, so you do need to be comfortable in the command line to make use of it.
-gufw - a (gnome) graphical front end for ufw. this makes the process of configuring ufw a little easier, but it is known to be a little buggy sometimes
*for antivirus
-clamAV - offers the same antiviral protection that you would find in other related tools, but is available in the repositories of most distributions
*for locking down application permissions:
-AppArmor - a (relatively) simple mechanism for controlling application profiles
-SELinux - a more complex mechanism for controlling application profiles
*for locking down users and/or application permissions:
-cgroups - a very powerful framework for controlling permissions for users and programs
-file/folder permissions - a powerful system for controlling system access, including to kernel 'files'

there's also tools for scanning for rootkits, etc, but there's a lot of reading associated with the above, so I'll leave it at this for now ;)

---

### Post by newbie4 on 2014-05-14
HilmTye, thank you for your last reply.  That's exactly what I was looking for and hoping to get.  
I've started with the Clam so far, and the rest I will have to do more reading/studying and what not.
And oldrocker99, thank you for the tip and reassurance about the tight ports.

One might ask: why am I so concerned?
Let's just say I was hacked before - in a nuisance way, for I didn't really have important data in my PC, but rather just nuisance and inconvenience.  (It's like someone breaking into your car without really stealing your car, but rather vandalized your dash, mirrors, etc.)

---

### Post by kurt18947 on 2014-05-14
There is I feel another advantage to open source O.S. the ability to run more than one install.  I have a totally separate install that I use only for accessing secure web sites such as banks, credit card companies and other sites that if my credentials were compromised it'd be a real bother.  That install has no flash and no java installed.  I feel that the liklihood of getting some sort of malicious 'drive-by download' is reduced by only visiting web sites where security is - or at least should be a priority. I'm not certain Windows licensing would permit installing two independent installs on the same machine, I doubt it.

A related factor is the tendency in Windows world for users to install random apps and games from unknown/untrusted sources.  

Oh look! 
A shiny! 
<click> 
Oh crap!

This is not a OS problem but it's a problem none the less and it seems far more prevalent in Windows world than in linux world where users - responsible users anyway - restrict downloads to known and trusted sources.

---

### Post by deadflowr on 2014-05-14
If you want to get a feel as to what security features are included in Ubuntu read through this
[https://wiki.ubuntu.com/Security/Features](https://wiki.ubuntu.com/Security/Features)

---

### Post by QIII on 2014-05-14
> **buzzingrobot said:**
> Windows is a much more frequent target because attacks there return the most profit. 

This is actually one of the myths about Linux security.  There is a GREAT incentive to hack into Linux, since the majority of the internet backbone is made up of Linux servers and many Fortune 500 companies run Linux.  Security by obscurity is not security.

And, as I have said for years, Open Source does not guarantee security just because there are many eyes looking at it.  If you add all the breaches of Microsoft products together, I would not be surprised to see that a single issue with an Open Source project -- OpenSSL -- outweighed them all.

Heartbleed certainly had the potential to cause -- and possibly has and we don't know it yet -- the most far reaching damage and loss yet on the internet.  If we find that those who took advantage of the OpenSSL flaw have gotten what they need and are simply biding their time before they strike (or intend to nibble so as not to draw attention), then we will have to eat our hats.

The point is this:  we should NOT be convincing ourselves or others that "Linux is more secure".  We should NOT be telling potential users that all is hunky-dory.  Down that path of pride lies destruction.

I have been preaching this for years, and when Heartbleed came to light the first words out of my mouth were, literally, "Told you so."

We cannot say unequivocally that Linux is more secure and should never drop our guard.

By the way, there are millions of Windows users who have never been compromised, so saying that any of our individual experiences with Linux is somehow different is of little value.

Linux and Windows are only as secure as the user makes them.  Security is a process not a product.  We need to assume we are as vulnerable as anyone else and act accordingly.

This ends the QIII lecture for the evening.

---

### Post by coldcritter64 on 2014-05-14
> **QIII said:**
> ...This ends the QIII lecture for the evening.

A lecture worth reading, +1 to those comments QIII.

---

### Post by mastablasta on 2014-05-14
i still think it is more secure. but it stilld doesn't mean one should drop their guard.

at least it doesn't have backdoors built in on purpose. or does it?!

---

### Post by newbie4 on 2014-05-15
Well said... Thank you QIII and everyone!  Really helpful!

---

### Post by T.J. on 2014-05-15
Hi, Newbie4, and welcome!  You ask a good question.

To clear away some of the common rhetoric, any computer system can be hacked, even Linux.  I can say this because I have been a programmer about 25 years.  I've seen Linux, Windows and OS X all get gobsmacked.  No one is 100% safe, nor ever will be.  

Primarily, the main reason why Linux is often called "safer" than others is that security privileges are not automatically assumed.  You don't get full run of the computer by default. When you run a program, you don't need administrator privileges to play a game or paint.  So the program runs under your account, which typically does not have security privileges to the rest of the machine, even if you have the ability to elevate yourself to full access via the "sudo" command.  You actually have to enter a password in order to gain the ability to edit or change system files.  

The services that run on Linux and other Unix systems are run on special accounts so even if the webservice gets hacked, like Canonical's did, the damage is limited to what the service account can access.  

The other reason that Linux is safer is that it is opensource.  At any point you can see the code for yourself (minus some optional things like Nvidia's special drivers) and you can see for yourself that no one has inserted a "backdoor" as the NSA has been accused of doing.

---

### Post by newbie4 on 2014-05-15
T.J., I like how you put that down nice and smooth for a newbie (me) to understand easier.  Thank you.

---

### Post by T.J. on 2014-05-15
> **newbie4 said:**
> T.J., I like how you put that down nice and smooth for a newbie (me) to understand easier.  Thank you.

You're very welcome.  =)

If you have other questions, no matter how "newbie" they may seem, please feel free to message me here at your convenience.

---

