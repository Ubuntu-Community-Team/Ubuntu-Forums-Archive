---
title: "does I need antivirus on Ubuntu 11.10 ?"
date: 2011-11-11
forum: Recurring Discussions
---

### Post by alain.roger on 2011-11-11
Hi,

i read some forum discussion about antivirus on Ubuntu, if it is necessary or not.
this topic was mainly from 2008 and i would like to know if today something's changed or not ?
basically do i need to install an Antivirus on my Ubuntu 11.10 OS ?
if yes, which one ? is there a review on antivirus on ubuntu ? something like topten review do sometimes.

thx

---

### Post by nothingspecial on 2011-11-11
Hi,

No you do not need antivirus for Ubuntu.

If you share files with Windows though you may wish too.

[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

---

### Post by Starfleet on 2011-11-11
Yes, it's best to run an antivirus program. Also switch on your firewall. This is so you do not pass on a virus to other computers running Windows based systems. And your firewall just makes things a bit more private.

To install your firewall from the terminal type: sudo apt-get install gufw

I use Bitdefender on my installation of 11.10 as I found Clamav Clamtk doesn't operate correctly on the Unity desktop. Bit defender works very well indeed and of course is free. Here is a link to a 'to do list' that gives the instruction for loading the necessary commands to install bitdefender. It's easy...

[http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/]("http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/")

Good luck.

Just to be clear...I concur with 'nothingspecial. You don't _have _to run antivirus.

---

### Post by BillyBoa on 2011-11-11
One great advantage of Linux is the security. But if you are connected to a Windows network, you should install an antivirus to protect the others, because the Windows files you pass to the others, you will don't know if they are infected.

---

### Post by Ms. Daisy on 2011-11-11
> **alain.roger said:**
> Hi, i read some forum discussion about antivirus on Ubuntu, if it is necessary or not. this topic was mainly from 2008 and i would like to know if today something's changed or not ?
basically do i need to install an Antivirus on my Ubuntu 11.10 OS ?
if yes, which one ? is there a review on antivirus on ubuntu ? something like topten review do sometimes
I had the same question. I encourage you to read this: [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity) .  It gives you a lot of resources to look into regarding Ubuntu security.

---

### Post by Rubi1200 on 2011-11-11
> **Ms. Daisy said:**
> I had the same question. I encourage you to read this: [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity) .  It gives you a lot of resources to look into regarding Ubuntu security.
That's a very useful, well-written, and informative link.

Kudos to all those who worked on it!

---

### Post by Ms. Daisy on 2011-11-11
> **Rubi1200 said:**
> That's a very useful, well-written, and informative link.

Kudos to all those who worked on it!Thank you. It's not quite done, we're working to expand a few parts.  But as it stands right now it's a good start for alain.roger to find some answers.

---

### Post by Rubi1200 on 2011-11-11
> **Ms. Daisy said:**
> Thank you. It's not quite done, we're working to expand a few parts.  But as it stands right now it's a good start for alain.roger to find some answers.
+1 to that.

And, of course, also for other users who need an introduction to some of the basic concepts of security on Ubuntu.

---

### Post by OrangeCrate on 2011-11-11
This article has been around a long time, but, it's worthwhile to post it again occasionally...


**The Truth About Linux and Viruses**

> 1. If you run Linux and only Linux, you do not need antivirus software. In its efforts to make Windows easier to use, Microsoft simplified the process of running executables under its operating system many years ago. Not only can a user launch a program by clicking an e-mail attachment, but it's possible for an executable to launch automatically just by hitting the preview pane of some email packages, including older versions of Outlook and Outlook Express. Scot's Newsletter Forums member Nathan Williams has provided an excellent FAQ for the All Things Linux forum explaining why Linux when used alone does not need antivirus protection.

Under Linux the steps for launching an executable from an e-mail are separate, discrete steps. A user would have to read the email, save the attachment, give the attachment executable permissions, and then run the executable. And to be truly damaging, the latter two would have to be done as root &#8212; not something informed users would allow.

2. If you dual boot Linux and Windows and get a virus-infected mail in Linux, it can NOT jump to your Windows partition. Nor can it spread over the local network to other systems. You can even store the attachment in your /home directory and open the zip or click the file, and it will be dead in the water. Windows executables won't run under Linux. Linux files need to be granted permission to become executable. And even then, it can't spread beyond the home folder. (This is also why Linux AV programs do not have a "live guard" module in them &#8212; the virus does not execute or move.) You could even leave a virus executable there as long as you wanted to without risk. Windows will not get infected, unless you deliberately copy the virus to your Windows partition.

3. If you dual boot, however, you better get a good antivirus program for Windows. Microsoft's operating system and its bundled applications, Outlook and Internet Explorer, offer users powerful functionality in their attempts to be easy to use and easy to update. As a result, it's all too easy for virus writers to exploit the same functionality in a malicious way. Don't leave them an opening. Install an antivirus program and keep it updated.

4. The only time you'll need a Linux antivirus program is if you're running a mail server. And that's just good social behavior. It's not to protect your Linux server or client computer so much as to make sure you don't pass a virus on to a Windows system.

Think about it this way: If you have two warehouses, and you use the first one to store cheese, are you going to place mouse-traps in the second one where you only store stainless steel? I mean, be reasonable, mice do not eat stainless steel! So don't let antivirus vendors make you unnecessarily paranoid.

[http://www.linuxclues.com/articles/21.htm](http://www.linuxclues.com/articles/21.htm)

---

### Post by Dangertux on 2011-11-11
> **OrangeCrate said:**
> This article has been around a long time, but, it's worthwhile to post it again occasionally...


**The Truth About Linux and Viruses**



[http://www.linuxclues.com/articles/21.htm](http://www.linuxclues.com/articles/21.htm)

It would be even more worthwhile if it were still relevant. The statements made on that website, are not accurate in the current Linux ecosystem. Particularly in regards to Ubuntu and other systems that strive for "single click easy". 

I'm not entirely sure why people continually propogate that code can not perform malicious tasks without super user privileges. It's completely untrue. Here is a list of things a piece of malicious software COULD do with just regular user privileges, this is not all inclusive, but should get you thinking in the right direction.

-- Read STDIN/OUT : You know that sudo password that is so much more secure than root? Yeah it can get keylogged.

-- Create a connection (that keylogged sudo password, public domain now.)

-- Survive a reboot 

-- Hook any process that the user it runs as owns (if the user is you, I'm thinking about your browser, particularly any credentials you may place into it)

-- Attempt to download and run exploit code against your kernel  to escalate locally to root. 

-- modify any settings the user it runs as has access to, since the user is likely your user that's quite a bit.

These are just some things, again not all inclusive, but definitely enough to get you thinking properly. The argument that you'd have to compile it against your kernel and install it. Hardly, package managers like the debian package manager have made it very easy to distribute code in the Linux world.  (don't even get me started on apt-url either lol)

Also think about, browser based exploitation, it wasn't as big when that article was likely written, the amount of freedom most users give firefox would probably make them wince if they actually realized it. Browsers are amazing code delivery vehicles, everyone has them and they all speak javascript. 

So I answer the question with another question. Do you need anti-malware solutions? You tell me.

---

### Post by OrangeCrate on 2011-11-11
> **Dangertux said:**
> 

<snip>

Do you need anti-malware solutions? You tell me.

No.

---

### Post by haqking on 2011-11-11
> **OrangeCrate said:**
> No.

So you think Linux is impervious to malware ? which by the way it is not

You never heard of a rootkit ? among others

Dont fall into the Linux is secure trap, Linux is not a concrete bunker

---

### Post by Thewhistlingwind on 2011-11-11
> **Dangertux said:**
> 

-- Read STDIN/OUT : You know that sudo password that is so much more secure than root?, yeah it can get keylogged.



I think we all know the solution to THAT! ([http://catb.org/jargon/html/os-and-jedgar.html](http://catb.org/jargon/html/os-and-jedgar.html)) Not a worry for REAL hackers! ;) (It's important to note that the ITS system didn't use passwords; at all.)

> **Dangertux said:**
> 
Also think about, browser based exploitation, it wasn't as big when that article was likely written, the amount of freedom most users give firefox would probably make them wince if they actually realized it. Browsers are amazing code delivery vehicles, everyone has them and they all speak javascript. 

Not to mention that just about anyone who's needed to do something non-trivial with a webpage knows it.

> **Dangertux said:**
> 
So I answer the question with another question. Do you need anti-malware solutions? You tell me.

It's important to note that signature based anti-malware solutions are very inefficient.

A better solution is to have a web account with no sudo access. And a MAC to keep things from writing themselves to wherever it is that your bridging the gap between your web account and your real account.

EDIT: I should also note that you can do an okay job of this already with the built in POSIX DAC. (File permissions.)

---

### Post by BillyBoa on 2011-11-11
I spent about 10 minutes searching the Forum for threads like:

"I have a virus or malware problem"

We have millions of different problems but never heard for a problem like that.

---

### Post by Ms. Daisy on 2011-11-11
So to be clear, no one in this thread is actually recommending anti-virus/anti-malware software for Ubuntu.  But that doesn't mean that Ubuntu is free & clear from any POTENTIAL viruses/ malware.  There are steps that a prudent user would take to improve security in Ubuntu, but those steps do not include anti-virus/anti-malware software.

Do we all agree on that?

---

### Post by Thewhistlingwind on 2011-11-11
> **Ms. Daisy said:**
> 
Do we all agree on that?

Heuristics based anti-malware solutions (Detecting based on abnormal or patterns of behavior.) could be useful, however I know of no such (non-primitive/trivial) systems for Linux at this point in time.

---

### Post by haqking on 2011-11-11
> **Ms. Daisy said:**
> So to be clear, no one in this thread is actually recommending anti-virus/anti-malware software for Ubuntu.  But that doesn't mean that Ubuntu is free & clear from any POTENTIAL viruses/ malware.  There are steps that a prudent user would take to improve security in Ubuntu, but those steps do not include anti-virus/anti-malware software.

Do we all agree on that?

Myth. Linux cannot get a virus or malware

Truth.  Yes it can and could

Myth. AV is not needed on Linux

Truth.  The solutions around are not very good and are better served for windows file sharing as it does not contain heuristic technology

Myth. Linux is secure

Truth.  NO unless you do your best to secure it, however in a networked world it needs to be layered and ongoing process and dont fall into the linux is secure trap, stay vigilant.

---

### Post by Dangertux on 2011-11-11
> **BillyBoa said:**
> I spent about 10 minutes searching the Forum for threads like:

"I have a virus or malware problem"

We have millions of different problems but never heard for a problem like that.


So this is essentially the I've never had my system compromised by a "whatever" argument.

So let me ask you this. Would you know how to tell if your system was compromised? I think a big part of the problem is the average Ubuntu user knows just enough about Linux to get themselves in trouble. (Hence the fact that we are currently dicussing this on a support forum).

I also agree that Linux Anti-malware solutions pretty much stink. The existing free solutions are terrible in comparison to their Windows based counterparts.

---

### Post by Rubi1200 on 2011-11-11
Thread moved to Recurring Discussions.

Thanks for understanding.

---

### Post by Dangertux on 2011-11-11
> **rubi1200 said:**
> thread moved to recurring discussions.

Thanks for understanding.


+1

The ultimate reality here is, even if you do need an anti-malware solution, there isn't much on the market for Linux right now, at least that is free. Some of the enterprise versions are pretty good though.

---

### Post by needhelppeeps on 2011-11-11
Some of the security tools for Linux seem to be quite old. For example, when was chkrootkit last updated? If Ubuntu users had malware planted on their systems, how quickly would it be discovered? Judging from the forum the last few weeks, there seems to be some safe browsing issues cropping up already. Most desktop Linux users are installing Adobe applications like Flash. Can anyone have any faith in Adobe? I can't understand why by default the directories it stores flash cookies in are not read only? I have been browsing this way for over a year and not noticed any ill effects. Why is firefox allowed access to the documents and pictures folders by default? If the user wants to save something, can he or she not pull it out of downloads? Apparmor is also somewhat annoying. I had a script written to block access all but downloads folder but it is broken with recent firefox versions and now I must rewrite it. Personally, I've taken to browsing with a separate profile than I store my data and do my banking/shopping/sudoing in. A good malware analyzer would be a nice touch but it must be something managable or it will never really be used. For example, it would need to integrate and coordinate updates into its fingerprint (hash) systems so that users don't end up with 200 warnings... the boy who cried wolf story and where could the database be safely stored in a way that does not thoroughly annoy the user (ie having to unlock media daily). Application whitelisting with fingerprints so filenames couldnt be faked might be worthwhile, too.

---

### Post by cbanakis on 2011-11-11
I have never ran antivirus of any kind, using mac windows and linux.

I have never had a problem, but I am knowledgable and careful.
(If I download a video, and the extension is .exe, I know its not really a video)
Same goes with the file size.
If you have enough experience, you can usually tell by the file size, if your downloading what you want, instead of some BS.

I'm not expert with Linux, but I know its really not any more secure than windows.
It is just the minority, and is seldom a target for viruses and spyware.

I think as long as the average user sticks to the software center instead of google for apps, they should be safe from virus's.

Key words being "I think" and "should be safe"

But of course, Antivirus is always a safe bet.
I prefer to stay away from it, because of the extra drag it puts on your system.
But if your not confident that you have the experience and tenacity to avoid virus's on your own, antivirus may be for you.

---

### Post by lisati on 2011-11-11
AV software is just a tool. Its effectiveness is limited by its not knowing about threats that haven't made it to AV databases yet. [PEBKAC]("http://en.wikipedia.org/wiki/User_error#PEBKAC") errors are another potential confounding factor. :D

---

### Post by haqking on 2011-11-11
> **cbanakis said:**
> I have never ran antivirus of any kind, using mac windows and linux.

I have never had a problem, but I am knowledgable and careful.
(**If I download a video, and the extension is .exe, I know its not really a video)**
Same goes with the file size.
If you have enough experience, you can usually tell by the file size, if your downloading what you want, instead of some BS.

I'm not expert with Linux, but I know its really not any more secure than windows.
It is just the minority, and is seldom a target for viruses and spyware.

I think as long as the average user sticks to the software center instead of google for apps, they should be safe from virus's.

Key words being "I think" and "should be safe"

But of course, Antivirus is always a safe bet.
I prefer to stay away from it, because of the extra drag it puts on your system.
But if your not confident that you have the experience and tenacity to avoid virus's on your own, antivirus may be for you.

Just so you know even if you verify it is a .avi for example, videos, images etc can all contain malicious code.

And players such as VLC have known vulnerabilities also from remote hijacks to buffer overflows. example here [http://news.softpedia.com/news/Highly-Critical-Vulnerabilities-Identified-in-VLC-Media-Player-211528.shtml](http://news.softpedia.com/news/Highly-Critical-Vulnerabilities-Identified-in-VLC-Media-Player-211528.shtml)

---

### Post by Dangertux on 2011-11-11
You know what. I have come to a realization on this and many other security related topics. I have spent a lot of time preaching security along with others like haqking and many others( if I didn't mention you by name don't hate me. )

That being said I think we are all approaching it the wrong way. The average Ubuntu user wants, no NEEDS to feel safe and secure, in fact a lot of people switched because the operating system "is more secure"(tm). 
The reality there is nothing is ever 100% secure. I can tell you all about the multitude of ways in which an Ubuntu system can be compromised. I can demonstrate them,  I can tell you to how prevent it. However, by and large that's not what people want. It seems they want to be told everything is okay. Well the truth is whether you know the threats are out there or not and whether you choose to protect our system or not. They are there. That being said you have to do what youre comfortable with. 

If you feel your security model is adequate for you. Then by all mean go with it. However, outright telling a user  asking a question about the realistic potential for a threat that it doesn't or cant exist isn't fair to the community. In fact it hurts the overall knowledge level of the community. I can't male you use anti virus, I don't even use it. However, I can inform you of the risks and let you make te decision yourself. We should not sell rainbows and sunshine where there are clouds. That is all. 

Hope this makes sense

---

### Post by aysiu on 2011-11-12
I find it troubling when people equate antivirus with security or the lack of antivirus to a denial of malware.

Antivirus does not make your system secure.

---

### Post by 1clue on 2011-11-12
Sorry I'm late to the party!  It seems as though it's already winding down.

The trouble with this argument revolves around details.  The problem is with words like "virus" instead of "intrusion" or "malware" or "rootkit".

Some intrusions that are really popular now are cross-platform and you can trash your user account just as easily on Linux as on Windows.  Some things on Windows just don't apply to a Linux box, and Linux is likely to be wide open in ways that just don't apply to a Windows box.

You don't need to have an open port to be vulnerable.  Anyone who insists they are not at risk is either uninformed or stupid.  Or both.

As an exercise for the skeptics, try installing a Linux box on the Internet, and then jump through the hoops to prove you're secure enough to process credit card information and on-line checks.  Even looking through the list, you get an appreciation for the shortfalls of any standard Linux distro, and even more so the number of things you can't do without additional hardware between your Linux box and the outside world.

---

### Post by Dangertux on 2011-11-12
> **1clue said:**
> Sorry I'm late to the party!  It seems as though it's already winding down.

The trouble with this argument revolves around details.  The problem is with words like "virus" instead of "intrusion" or "malware" or "rootkit".

Some intrusions that are really popular now are cross-platform and you can trash your user account just as easily on Linux as on Windows.  Some things on Windows just don't apply to a Linux box, and Linux is likely to be wide open in ways that just don't apply to a Windows box.

You don't need to have an open port to be vulnerable.  Anyone who insists they are not at risk is either uninformed or stupid.  Or both.

As an exercise for the skeptics, try installing a Linux box on the Internet, and then jump through the hoops to prove you're secure enough to process credit card information and on-line checks.  Even looking through the list, you get an appreciation for the shortfalls of any standard Linux distro, and even more so the number of things you can't do without additional hardware between your Linux box and the outside world.

LOL I see you've come to appreciate the finer points of a PCI-DSS compliance audit :-P

[quote=aysiu]
I find it troubling when people equate antivirus with security or the lack of antivirus to a denial of malware.

Antivirus does not make your system secure. 	
[/quote]

Security always has been and always will be a process, and an uphill battle. Security is not an application, policy or control. It is a mind set.

---

### Post by 1clue on 2011-11-12
> **Dangertux said:**
> LOL I see you've come to appreciate the finer points of a PCI-DSS compliance audit :-P


YOU SAID THE FORBIDDEN WORD!  NI!

And since I wasn't actually storing financial information, I only had to do the "easy" form.

> 
Security always has been and always will be a process, and an uphill battle. Security is not an application, policy or control. It is a mind set.

I honestly hadn't noticed the absence of "security applications" in Linux.  I just install my distro, and then tweak things here or there to make it safer.

I shudder every time I listen to Windows users assume that their antivirus software solves all their problems.  I REALLY don't want that sort of application on Linux.

---

### Post by Dangertux on 2011-11-12
> **1clue said:**
> YOU SAID THE FORBIDDEN WORD!  NI!

And since I wasn't actually storing financial information, I only had to do the "easy" form.



I honestly hadn't noticed the absence of "security applications" in Linux.  I just install my distro, and then tweak things here or there to make it safer.

I shudder every time I listen to Windows users assume that their antivirus software solves all their problems.  I REALLY don't want that sort of application on Linux.

I think a lot of people assume I'm like tinfoil hat paranoid because I'm always harping on threats that are out there. Maybe I am because I'm aware of the threats, or maybe its because I understand how easy a default install of anything is to compromise.  In any case, I think in the desktop realm applications like anti-virus DO serve a purpose.

Unfortunately, they are not where they need to be, and certainly not on Linux. In the corporate world there are diverse (albeit expensive) solutions to malware, and they're not perfect, but they're head and shoulders above Mcafee or Avast or whatever desktop product is the latest greatest. They serve their purpose, they are great for detecting if something malicious hits the hard drive. 

That being said if you are careful, understand what you're doing and have a well configured system it shouldn't be that necessary. In any case it really doesn't matter because Linux solutions (at least free ones) are WAAAAY behind the curve compared to their Windows brethren. This makes sense of course, Windows has been fighting an uphill battle with malware for the better part of two decades. This comes with holding 95% of the desktop market share I guess.

---

### Post by 1clue on 2011-11-12
It's not whether you're paranoid, it's whether you're paranoid *enough*.

Antivirus apps certainly serve a purpose and we really could stand a more sophisticated malware detector in Linux, but my objection comes from the blind faith that average users give to them.

I had a small exposure to security when I worked at IBM awhile back, but really only picked up a small bit.  Defense in depth and all that, and some strategies about DMZ and minimal software capability of a firewall.

I've picked some up over the years using Linux, and having managed a Linux firewall for a small business.  The disparity between the amount I know and the amount I don't know is cause for despair.

---

### Post by Starfleet on 2011-11-12
Lots of good advice on here from many. Worrying naivety from some. But I think we mustn't forget, and this has been said by some that Linux is still the very best for security. This has been proven over and over again. In my work a couple of years ago I was trained in ethical hacking (I have involvement with networks in colleges and manage parts of those networks). During that training a Windows desktop was setup (most of our networks still use Windows) and another machine was setup using Linux as the OS. Services were started on both machines and Firefox browsers opened. No software firewalls were enabled, no antivirus, and both machines were linked to the same router _without_ firewalls enabled NATS or SPI. 

Our training continued and both machines were checked after two hours to see what state they were in. Predictably, the Windows machine had completely stopped working and was overloaded with so much maleware it just couldn't function. The Linux machine was completely unaffected, apart that is from a poor helpless Windows Trojan that had come onto the hard drive but could not do anything except be passed on to some other Windows machine. Clamav removed it no problem.

I think that illustrates why so many people are now using Ubuntu or other flavours of Linux even if they are not fully aware of the realities of security.

PS. just an interesting add-on. 6 out of 10 UK banks now say don't access your bank details using a Windows based operating system. Instead, use Linux. But if you cannot do that use the security software the banks provide you free of charge. It helps.

---

### Post by haqking on 2011-11-12
> **Starfleet said:**
> Lots of good advice on here from many. Worrying naivety from some. But I think we mustn't forget, and this has been said by some that Linux is still the very best for security. This has been proven over and over again. In my work a couple of years ago I was trained in ethical hacking (I have involvement with networks in colleges and manage parts of those networks). During that training a Windows desktop was setup (most of our networks still use Windows) and another machine was setup using Linux as the OS. Services were started on both machines and Firefox browsers opened. No software firewalls were enabled, no antivirus, and both machines were linked to the same router _without_ firewalls enabled NATS or SPI. 

Our training continued and both machines were checked after two hours to see what state they were in. **Predictably, the Windows machine had completely stopped working and was overloaded with so much maleware it just couldn't function. The Linux machine was completely unaffected, apart that is from a poor helpless Windows Trojan that had come onto the hard drive but could not do anything except be passed on to some other Windows machine. Clamav removed it no problem.**

I think that illustrates why so many people are now using Ubuntu or other flavours of Linux even if they are not fully aware of the realities of security.

PS. just an interesting add-on. 6 out of 10 UK banks now say don't access your bank details using a Windows based operating system. Instead, use Linux. But if you cannot do that use the security software the banks provide you free of charge. It helps.

Well no offence meant, but malware infection is a small example of comparative vulnerability as discussed many times on here, of course windows is more vulnerable to virus and other malware that is well stated many times for many reasons, not that Linux couldnt suddenly be targeted in the same way.

As an ex instructor of CEH courses and the like,  the methods to penetrate a Linux box are as many and varied as are the windows counterpart which you should have also learnt on the course.

The whole linux is more secure argument is an old one (i think often stems from the lack of wild malware as compared to others) but is flawed and lets people assume too much of a safety net.

If you are using Windows it is often easy to see the effects of said malware or similar, if using Linux often people think they are fine because they dont know enough about the system to tell any difference, and all along they were pwn3d months ago if they had bothered to look and analyse the logs for example.

Penetration/Cracking/Hacking (ethically) are OS agnostic. IMO as a Security Professional.

But opinions vary greatly ;-)

Which of course is good for the sec industry, if there wasnt people thinking they were safe there would be nothing to for us to do

Peace

Edit: Let me just add as people often mis-read what i say, am i saying Linux is not secure (not exactly) but im not saying that windows is insecure either, both can be hardened against many attack vectors, nothing is secure in a networked world that is the mentality we all need to embrace and not the marketing of things are secure concept (if you are going to display and use personal information online which so many do these days then you need to be paranoid at least a little).  From a malware point of view yes Linux is stronger currently (but dont think it couldnt easily fall victim to it as it could) from a general can it be 0wn3d point of view, let me tell you yes it can in both the MS and *nix world.

Security is a process not a product - Bruce Schneier (and the last cryptologist who questioned Bruce Schneier was found floating face down in his own entropy pool, he is also the only person to know "victorias secret"

---

### Post by Starfleet on 2011-11-12
haqking, yes, I don't disagree with anything much you say in your post. But my point merely being that there is quite a difference in the level of security in Windows and Linux. It is easier to be secure in Linux due to fewer threats in the first place yes, but in a properly set up Linux machine it is very much harder to inflict damage or take information. But as we all keep saying, much is down to individuals who use these machines. I would say however, that in the last couple of years I have converted huge numbers of people from college and amongst my friends to Linux (mostly Ubuntu). Many of these individuals ran Windows and had problems with security inspite of good software protection. Since conversion, I've yet to have anyone come forward with a problem. I would add that I set up all machines in the most secure way I could but of course have to rely on the individuals to be sensible still. But so far in two years, no problems at all.:)

---

### Post by 1clue on 2011-11-12
If your argument contains something like "Linux is safer because..." then you're wrong.

Look at it from the other point of view.  Let's say Software Hank plans on nailing pretty much anything he can touch.  So he's going to have Windows penetration scripts, and Mac penetration scripts, and Linux penetration scripts.  Not necessarily in that order.

So when he looks at what to hack, he's going to look for his target audience.  He might look at Linux in general, but more likely he will choose the least knowledgeable users and a relatively common distribution.  IMO there are a lot of Ubuntu users out there who think that just installing Ubuntu makes them safe, so Software Hank is going to download Ubuntu and check it out.

He's not going to change anything at first, so he writes a script to take advantage of whatever the easiest exploit is in that configuration.  Then he's going to make the most likely security settings changes that he figures a security novice is going to make, and then try to crack the easiest exploit there.

Hacking is equal parts technical, psychology and surveillance.  Many black hat hackers know something about their target, and more just get into the psychology of their target victims.

It's not nearly as small a problem if you aim at the ignorant masses.  A bare Ubuntu install is a known quantity and if somebody finds an exploit for that then they can just try a few options to see if it works.

---

### Post by Dangertux on 2011-11-12
> **1clue said:**
> If your argument contains something like "Linux is safer because..." then you're wrong.

Look at it from the other point of view.  Let's say Software Hank plans on nailing pretty much anything he can touch.  So he's going to have Windows penetration scripts, and Mac penetration scripts, and Linux penetration scripts.  Not necessarily in that order.

So when he looks at what to hack, he's going to look for his target audience.  He might look at Linux in general, but more likely he will choose the least knowledgeable users and a relatively common distribution.  IMO there are a lot of Ubuntu users out there who think that just installing Ubuntu makes them safe, so Software Hank is going to download Ubuntu and check it out.

He's not going to change anything at first, so he writes a script to take advantage of whatever the easiest exploit is in that configuration.  Then he's going to make the most likely security settings changes that he figures a security novice is going to make, and then try to crack the easiest exploit there.

Hacking is equal parts technical, psychology and surveillance.  Many black hat hackers know something about their target, and more just get into the psychology of their target victims.

It's not nearly as small a problem if you aim at the ignorant masses.  A bare Ubuntu install is a known quantity and if somebody finds an exploit for that then they can just try a few options to see if it works.

+1

Also something to note here. For everyone running around on a public internet forum saying "I don't need security applications Ubuntu is safe"

If I were a black hat and I were using google to find a large concentration of users running default configurations of a specific operating system, what do you think my search terms would be?  "I don't need security applications Ubuntu is safe" would definitely be in my top 10.

Read through your posts, a determined attacker could gain a lot of information about your security posture from a forum like this. If you think its something they don't do, think again.

---

### Post by Thewhistlingwind on 2011-11-12
> **Dangertux said:**
> 
Read through your posts, a determined attacker could gain **a lot** of information about your security posture from a forum like this. If you think its something they don't do, think again.

Bold, for emphasis.

And +1. But you already knew that.

---

### Post by Ms. Daisy on 2011-11-12
> **Dangertux said:**
> +1

Also something to note here. For everyone running around on a public internet forum saying "I don't need security applications Ubuntu is safe"

If I were a black hat and I were using google to find a large concentration of users running default configurations of a specific operating system, what do you think my search terms would be?  "I don't need security applications Ubuntu is safe" would definitely be in my top 10.

Read through your posts, a determined attacker could gain a lot of information about your security posture from a forum like this. If you think its something they don't do, think again.
+1!!!!!

It occurred to me that the way to couch this whole thing is this: the virus debate is a red herring.  It's not the thing that's most likely to get you cracked.  So it doesn't matter whether there are existing viruses, potential viruses, or any protection against them.  If you begin & end the security debate with viruses, then you've defeated yourself.  That's what Dangertux just said. It's what haqking said, I think it's what most people are saying (except for the "Linux is secure" people of course).

I edited the Basic Security Wiki to reflect this argument. God willing there are a few "Linux is secure" people out there that will actually read it.

---

### Post by 1clue on 2011-11-12
> **Ms. Daisy said:**
> ...

I edited the Basic Security Wiki to reflect this argument. God willing there are a few "Linux is secure" people out there that will actually read it.

It's fine.  They'll get pwned a few times and then they'll understand.

Lucky for me when I was starting out, the main goal of a black hat was to somehow bring the system or its network to its knees.  In other words, it was the main goal to cause mayhem in an obvious way.

Nowadays, you could be pwned without even knowing it happened, and almost anything could be happening without your knowledge.  The main focus now is money.  Yours isn't so big a deal although they might take that too if they can figure it out, but more likely they're using your system to run a distributed attempt to breach a financial site or possibly some other thing they value.

---

### Post by Xara on 2011-11-12
Lots of discussion about needing anything security related. When it comes down to "do I need" it all depends on you. I'd say, for most people, you don't really need much, if anything, for any linux distro. As some have said if you have any kind of web/mail/file server it's better to be courteous as you can pass on unwanted bits.

For people who feel they need something more it's not like there isnt anything you can use. As mentioned by others, and I agree, there isn't really anything spectacular about available(free/cheap/affordable) anti-virus programs. Also mentioned was they don't implement any kind of active protection. I say that when I had a private mail server I read up on how to have your anti-virus program to check everything that comes in on a specific port. While this worked for my needs I would rather not see how that would affect a high traffic server. As far as malware goes, SElinux is a pretty powerful tool. It's not terribly hard to configure, but can be so anal that it can keep your distro from mounting / if configured improperly. Firewalls are also available and fairly easy to configure.

As I said before what you need depends on you. But as far as something being "secure" as I saw getting thrown around, bashed, beheaded and what not doesn't exist. The only secure devices that come in contact with something someone else has "touched" are the ones that have never been turned on and are still in their original box, assuming they aren't already compromised.

Anonymity is great unless someone else has it too.

---

