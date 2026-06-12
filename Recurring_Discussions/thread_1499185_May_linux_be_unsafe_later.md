---
title: "May linux be unsafe later?"
date: 2010-06-01
forum: Recurring Discussions
---

### Post by multisystem on 2010-06-01
As far as I know, one of the main reasons Linux is safe is that it's not as common as Windows. Most computer users use Windows, so viruses are made mainly for it.

My question is:
Linux is growing up day after day, and many users migrate from Windows to Linux. Is it possible that, after a certain period of time, all viruses will attack Linux as the most common OS?

This really annoys me :(

---

### Post by kaldor on 2010-06-01
Noooo, nono!

UNIX based (and UNIX-like) operating systems really are safer. Windows has many problems with stuff like that.

Plus, Linux has MUCH more market share than Windows in the server/supercomputer areas. And those are also less targeted.

A lot of it has to do with the multiuser setup.

---

### Post by NightwishFan on 2010-06-01
It is possible and probably likely. The difference is that the software is open and so all of it is reviewable. Also many distibutions package software and sign the repositories so that nothing can change them. Not to mention that the OS is multiuser from the ground up and thus is safer to administer.

I fear more for socially engineered attacks where users manually install a false package, or they offer up account information, etc..

---

### Post by YuiDaoren on 2010-06-01
All OSs are as safe as the user makes them. Windows is virusland not only because it's ubiquitous, but also because the majority of its users don't know much (and probably don't much care either) about how to secure their systems.

Linux OSs have an advantage, though, in their package managers. Sticking with your repos vastly reduces the opportunity for viruses and whatnot from being able to lodge themselves in some deep crevasse of your system. That we run regular user accounts instead of root/administrator accounts helps too.

There has already been a couple of examples of trojan horses for Linux OSs, and they were little more than flashes because of the speed at which their sources were removed. So, I don't think it's going to be all that big of a pain in the butt even if Linux OSs become the mainstream OSs.

---

### Post by amauk on 2010-06-01
[http://ubuntuforums.org/showpost.php?p=8424962&postcount=13](http://ubuntuforums.org/showpost.php?p=8424962&postcount=13)

---

### Post by Kai69 on 2010-06-01
> **amauk said:**
> [http://ubuntuforums.org/showpost.php?p=8424962&postcount=13](http://ubuntuforums.org/showpost.php?p=8424962&postcount=13)
 
Very good article answered some questions I had as well :P

---

### Post by aysiu on 2010-06-01
In case you're wondering why this is in Recurring Discussions, I refer you to these threads (and these are just from the past year):
[what happens when linux succeeds?](http://ubuntuforums.org/showthread.php?t=1481953)
[The Future Of Ubuntu(And linux on general...)](http://ubuntuforums.org/showthread.php?t=1418259)
[Will Ubuntu become vulnerable to Viruses](http://ubuntuforums.org/showthread.php?t=1243686)
[Does Linux have the potential to be worse than Windows?](http://ubuntuforums.org/showthread.php?t=1191349)

---

### Post by McRat on 2010-06-01
I've heard this a lot, that Linux systems and Mac systems don't have viruses simply because it's not as profitable for virus writers to hack those systems.  I suppose having 10,000,000 potential victims is not enough to bother with.

The first viruses I saw were bootloader viruses.  They traveled by floppy disc.  As long as you weren't dumb enough to get a disc from a stranger, you were OK.  Then came the BBS file viruses, which were trojan horses that appeared to be legitimate executable files, but has a small virus rider attached to the header that would go TSR.  Then came email viruses.  They would be an attachment to an Email, but were always EXE files at first.  Nothing other than a EXE/COM file could be a virus because data was not executable back then.

There were anti-virus software even back then.  And there were under 1,000,000 desktop computers total.  So I don't buy the "not enough computers" argument.

Microsoft made it very easy to infect computers starting with Excel Macros.  Before then, data and executable code were different.  With the Excel files, they could carry interpreted code.  IIRC, you could not even turn off the macro-execution at first.  That was done after things went really bad.

Then Microsoft put in code to "spy" on users.  It was first to find bugs in their code, then to help you remotely, then to see if you were using an illegal copy.  Problem was, if Microsoft could get into your computer, so could anyone else.  It had gotten so bad, that if you plugged in an early WinXP computer, you could get a virus in seconds if it had a internet connection.  That was the first sign of how bad things were going to get.

I doubt it will ever get as bad as WinXP did as far as ease of malware, simply because Linux and Macs currently do not spy on you as much.

But if you execute an email attachment or download an executable, you'll be at risk on any computer.  Nobody can save you from that.

---

### Post by chessnerd on 2010-06-01
It is definitely possible, and if Linux ever becomes the most popular OS it will certainly see a massive increase in the number of attacks. However, there are several key differences between Linux and Windows:

1. Linux is based on UNIX - UNIX was designed in the 1960s. It is powerful, proven, and reliable. The very core of the UNIX system is meant to be safe under multi-user, networking situations. This makes it harder to attack a UNIX-based OS than a Windows NT-based one. However, it is not impossible.

2. Linux is open-source - because thousands of people look at Linux's source code ever day, most software problems are solved very quickly. While this doesn't always happen with some issues (like hardware compatibility), it does happen with security vulnerabilities. They are typically found on day 1 and fixed not long after that. Linux has a Borg-like quality about it. There might be unforeseen flaws, but Linux is quick to adapt. Thankfully, it hasn't tried to assimilate humanity... yet.

3. Most software for Linux is open-source - this a the key reason. As long as the software used with Linux is open-source, and people go to their distribution's repositories to get software, it will be very hard for malicious code to make it's way on to a user's system.

Really, though, it comes down to the user. If you, the end user, doesn't install the latest security updates and installs questionable software from unreliable sources then you are just asking for trouble and that isn't the fault of Linux, Canonical, or anyone other than yourself. Being a smart user is the first line of defense.

---

### Post by Sub101 on 2010-06-01
If a virus writer wanted to do real damage they would, if they could, target Linux as it is essentially what runs most company systems.

The claim that Windows has more market share therefore is targeted more is, in my opinion, wrong. I believe it is far more to do with the Linux security structure versus Windows security structure.

---

### Post by juancarlospaco on 2010-06-01
No

---

### Post by amauk on 2010-06-01
Also remember that Linux (and other Unix & unix-like systems) are used extensively on servers

Servers used by banks, insurance companies, core infrastructure (ISPs, etc), public services, and anything else you can imagine.
They store all manner of important and sensitive information and run all manner of important and critical services

They are an *enormous* target for attack

Compare this against one random guy's Windows machine
which probably can be used to nab 2 or 3 important things at the most (bank / credit card details) or be amalgamated into a larger botnet for distributed attacks on others

Which, really, is the larger target?
I mean, come on

Windows is targeted because Windows in insecure
no more, no less

*nix is so far above windows, in terms of payoff for a successful attack, it's not even worth arguing about

---

### Post by formaldehyde_spoon on 2010-06-01
Windows servers are the minority among servers, but attacks against them are far more successful than attacks against Linux servers.

---

### Post by Peter09 on 2010-06-03
The only way a virus can really work is to propogate, this means that it may be possible to target a particular user if you know something about his setup, but to get from there to control his system and spread succesfully to a significant number of other machines is much harder. This is where windows imakes an easy target, the ease of gaining control and spreading elsewhere.

---

### Post by mickie.kext on 2010-06-03
There are lot of factors why Linux is more secure than Windows. Linux is designed around UNIX guidlines. Banks and militry ran UNIX for decades, and those institutions are most interesting for hackers so whole 'sercurity through obscurity' idea that haters are FUDsters and haters and pushing is missing the point because neither UNIX nor Linux are obscure. Most web hosting agencies run Linux almost exclusively, enterprises are mixed envoirment with UNIX, Linux and Windows, supercomputer are all the way Linux. There a lot incentive for security breakers to go after Linux. Yet, no malicious program have managed to spread like it spreads over Windows computers. It is possible to write Linux virus, but you have to jump through lot of hops to infect one machine, and when you do that, it won't spread. You must do it again for every machine. That makes impossible for Linux user to become a victim of random attack. If you get virus on Linux, it means that there is somebody somewhere who hates your guts and it means that you have been foolish to run a program (as root) which that person have given you. It is your fault. 

With Windows, it enough just to visit some malicious site, and you have been infected. Not just infected, but now your MSN account will send message to your friends which say: Hi buddy!!! Look those pictures <link to malicious site here>". And when they click it, they are infected too, and virus will spread further. With Linux, that is not possible and it will never be possible. 

Why it is possible with Windows? Because Microsoft puts convenience before security. Because their development decisions are made based on business, political and marketing factors, rather than technological factors. Because to fix Windows, they would need to admit that was broken in the first place and they refused to admit most security holes that have been reported so far. 

If you think that Linux has security flaw, you can fix it and push it upstream yourself. If you find security flaw in Windows, Microsoft wont listen. You have to make virus and prove the flaw. And they still wont listen. That is one more reason why there are viruses in Windows. 

Here is little something from the expert:
[http://www.youtube.com/watch?v=YMywg-ePx-E](http://www.youtube.com/watch?v=YMywg-ePx-E)
[http://www.youtube.com/watch?v=HlfJjFIw5fE&feature=related](http://www.youtube.com/watch?v=HlfJjFIw5fE&feature=related)
[http://www.youtube.com/watch?v=9xc8WNMbhQ4](http://www.youtube.com/watch?v=9xc8WNMbhQ4)

---

### Post by SunnyRabbiera on 2010-06-03
No OS is bulletproof

---

### Post by Shining Arcanine on 2010-06-03
I suggest that you run [COLOR="Green"]lsof -i -P | grep -i "listen"[/COLOR] on your system. If that does not display any console output, your system should be fairly secure. When no services are exposed to the outside world, hacking into a system requires user assistance.

---

### Post by murderslastcrow on 2010-06-03
Software can't run without having, at least at one point, your permission. You can't run standalone executables without marking them as such, and you can't run them without clicking on them or activating them in some sort (in other words, there is no ActiveX control running software for you).

Aside from having this separation between system and user files, which disables any program from directly affecting the system without your explicit permission, via PASSWORD, every open source package you have (which is, by default, your whole system) is constantly updated with security fixes. These are marked as flaws not because they've been exploited, but because people analyze them closely, because thousands of people view the source of each program. This makes it more secure faster even from hypothetical attacks.

Closed source has nowhere near that capacity, no matter how much money you throw at it. Read Cathedral and the Bazaar if you don't believe me.

Also, in Ubuntu, the repositories use the Gnu Privacy Guard's public keys to mark software as trustworthy. So, even if you find the need to install a third-party repository for something, it will need a trusted key. If not, it will inform you it's not trusted, and every time you try to install something from it, it will remind you of this fact.

Fortunately, 99 percent of the open source software you will ever install is already in the Ubuntu Software Center ANYWAY. Most PPAs are trusted for anything worth installing (Gnomenu, DockbarX, Nautilus-Elementary, Google Chrome).

Also, if plans continue with the Software Center, closed-source and commercial titles that you currently have to go out and download or buy will now be included if they are trustworthy and without malware.

So, with these criteria, the only way you can get malware is if you go the hard way, to some shady site, or some email, mark a file as executable, and offer your password if it tries to modify something in the system. OR, install a deb from an untrustworthy source, entering your password when you do so.

These incidences are only likely if you know more than the average noob user, so my Grandmother for example is not likely to do this (she uses Ubuntu, I'm not kidding), and people who are more likely to do this are usually safer in their practices and know of better ways to obtain their software.

The only other likely way is to install pirated software or run IE in Wine going to an unsafe site, in which case Wine is a sandboxed environment which can in no way touch your system files, and all contained within the wineserver process, and can only affect its own environment.

Of course, as Wine becomes more integrated with Gnome or KDE, we'll want to tighten security as necessary, but at this point that integration is merely on the "put Wine in our fancy looking window manager, not Windows'."

So really, the basic security model, coupled with thousands of security dogs in the form of developers, along with the decreased likelihood of stupid people finding a way to install malware, makes any issues regarding security pretty much impossible. There's also SELinux which inhibits certain programs from performing activities they don't really need in order to function normally.

All of this together is probably more security than Linux needs, but it's there, and people are constantly solving hypothetical security holes years before anyone would think to use them.

Also, Windows, even with its wide user base and utter lack of security, tends not to get viruses on a DAILY BASIS, for most people, and many people who don't use an antivirus don't run into one (although Windows has plenty more issues than that, we all know).

Even if every one of those Windows users changed to Ubuntu, it wouldn't change how secure Ubuntu is by its very nature. Also, more users would mean more developers to check for bugs and security issues. It will always be secure given the support it currently has, and it doesn't seem to be losing support in the foreseeable future.

I hope that abides your paranoia for today.

---

### Post by T-rock007 on 2010-06-03
Personally I think you hit it right on the head.Linux really isn't as secure as everybody says even though I love Linux its just that it's not that common so therefore there aren't that many viruses made for it.

---

### Post by Shining Arcanine on 2010-06-03
> **T-rock007 said:**
> Personally I think you hit it right on the head.Linux really isn't as secure as everybody says even though I love Linux its just that it's not that common so therefore there aren't that many viruses made for it.
Okay, I am running a Gentoo Linux system on a certain IP address. It has no services available to the outside world and all ports are closed. If you had that IP address, tell me how would you hack it.

---

### Post by Diluted on 2010-06-04
> **Shining Arcanine said:**
> Okay, I am running a Gentoo Linux system on a certain IP address. It has no services available to the outside world and all ports are closed. If you had that IP address, tell me how would you hack it.
Web browser vulnerability?

---

### Post by jrothwell97 on 2010-06-04
Ubuntu, along with other *nixes (and, let's be honest, modern versions of Windows) are both pretty secure as long as you exercise common sense: namely, *not running as an administrator all the time*.

UAC, sudo, PolicyKit etc. are all there for a reason: it may be annoying, but that doesn't mean you should disable it.

(Also: security through obscurity is a myth that's been debunked thousands of times before. Viruses are a comparatively small threat, and if a virus writer can target a home computer, why can't he instead target a server [running *nix or a locked-down Windows] and potentially knock out half a continent?)

---

### Post by Diluted on 2010-06-04
> **jrothwell97 said:**
> Viruses are a comparatively small threat, and if a virus writer can target a home computer, why can't he instead target a server [running *nix or a locked-down Windows] and potentially knock out half a continent?
That's because they are two different target markets. When's the last time you've heard of system administrators accidentally executing malware on their servers? In comparison, how often do you hear home users getting malware on their computers?

---

### Post by mickie.kext on 2010-06-04
> **Diluted said:**
> That's because they are two different target markets. When's the last time you've heard of system administrators accidentally executing malware on their servers? 

A lot of times in fact, if you are talking about Windows servers. MS is handing certificates to every bozo who want to be Windows administrator, so I am not even surprised.

---

### Post by jrothwell97 on 2010-06-04
And here we come to the crux of the argument: the weakest link will *always* be the user. As long as there are gullible, ignorant or uninformed people out there with access to a computer, they will be at risk to themselves.

It doesn't matter if they're running Windows, Linux, MS-DOS, OS/2 Warp or whatever - unless they live in an entirely locked-down platform, there's a definite probability that at some point, they'll end up with a nasty on their machine.

---

### Post by Diluted on 2010-06-04
> **mickie.kext said:**
> A lot of times in fact, if you are talking about Windows servers. MS is handing certificates to every bozo who want to be Windows administrator, so I am not even surprised.
I was referring to competent system administrators.

Although I would be interested to see the source of your statement.

---

### Post by mickie.kext on 2010-06-04
> **Diluted said:**
> I was referring to competent system administrators.

Although I would be interested to see the source of your statement.

I like my brain being a source, like you know, when I see things with my very eyes? Some people have expirience with things they post about instead of repeating conventional wisdom.

---

### Post by Diluted on 2010-06-04
> **mickie.kext said:**
> I like my brain being a source, like you know, when I see things with my very eyes? Some people have expirience with things they post about instead of repeating conventional wisdom.
Then I would be interested in knowing how many occurrences you have witnessed. I hope it is a large enough number to cover your generalization about Microsoft handing certificates to everyone who want to be Windows administrator.

---

### Post by mickie.kext on 2010-06-04
> **Diluted said:**
> Then I would be interested in knowing how many occurrences you have witnessed. I hope it is a large enough number to cover your generalization about Microsoft handing certificates to everyone who want to be Windows administrator.

I do not keep count, but it is huge. Huge enough that when I see a borked Windows server, I first ask if administrator had any Microsoft certificates.

---

### Post by Diluted on 2010-06-04
> **mickie.kext said:**
> I do not keep count, but it is huge. Huge enough that when I see a borked Windows server, I first ask if administrator had any Microsoft certificates.
Indeed? Would that be due to malware, or misconfiguration which allowed hackers to exploit it?

---

### Post by mickie.kext on 2010-06-04
> **Diluted said:**
> Indeed? Would that be due to malware, or misconfiguration which allowed hackers to exploit it?

Do you want me to list and explain to you every single case? Maybe pictures too?

---

### Post by Linuxforall on 2010-06-04
> **Sub101 said:**
> If a virus writer wanted to do real damage they would, if they could, target Linux as it is essentially what runs most company systems.

The claim that Windows has more market share therefore is targeted more is, in my opinion, wrong. I believe it is far more to do with the Linux security structure versus Windows security structure.

So very true, 91% of the world's super computers run Linux, the lure to hack them and get sensitive data is far more lucrative than to hack an end user's PC with just a measly bank data worth at the most maybe a couple of thousands. The market share theory is so hollow.

---

### Post by Diluted on 2010-06-04
> **mickie.kext said:**
> Do you want me to list and explain to you every single case? Maybe pictures too?
That would be interesting to see.

Regardless of how they have happened, I think you'd agree that these people may have trouble securing a Linux server. This is why I'm only talking about competent administrators when I said it would be very unlikely for them to execute a malware, hence the low incentives to create malware targeting servers. Hackers would rather look for vulnerabilities in say, the LAMP stack.

> **Linuxforall said:**
> So very true, 91% of the world's super computers run Linux, the lure to hack them and get sensitive data is far more lucrative than to hack an end user's PC with just a measly bank data worth at the most maybe a couple of thousands. The market share theory is so hollow.
Supercomputers, embedded devices, enterprises and wherever Linux is used, they are different target markets. Just because Linux is dominant elsewhere and targeted heavily doesn't mean it will be the same at the desktop level, which I believe is the OP's concern.

---

### Post by Frak on 2010-06-04
Yes, to say Linux is immune to malware is pure delusion. The #1 reason for viruses in Windows is due to user apathy and/or lack of knowledge. I've run this very Windows system (XP SP3) for about a year and a half now. No antivirus, no anti-anything. Lo-and-behold, I have no malware. Why? I paid attention to what I was doing.

Arguably, it is much more difficult to contract infection in 7 due to UAC. There's malware for OS X and there's malware for Linux. Recently, a trojan of sorts spread on gnome-look.org. It was successful in infecting some people. No OS can keep you safe from viruses.

---

### Post by aysiu on 2010-06-04
> **Frak said:**
> Yes, to say Linux is immune to malware is pure delusion. To say there are no such things as better security approaches and worse ones is also delusional.

Yes, social engineering works on any platform, and almost all security breaches I've seen take advantage of it, but that doesn't mean you can't try to make it a little more difficult for system files to get infected.

Forcing people to password-authenticate to install software doesn't stop them from intentionally installing trojans, but it does prevent reflex accidental clicks from compromising the entire operating system.

A chain is only as strong as its weakest link, but since you can have both weak *and* strong weakest links, might as well make all the other links as strong as you can.

It's important for Linux users to recognize the prevalence of social engineering-based attacks, since they will work on any operating system, as long as the user is gullible enough to be tricked into installing a trojan. At the same time, there seems to be a false dichotomy popularized by the anti-Linux crowds that an operating system is either invulnerable or full of security holes.

---

### Post by sydbat on 2010-06-04
> **Frak said:**
> I've run this very Windows system (XP SP3) for about a year and a half now. No antivirus, no anti-anything. Lo-and-behold, I have no malware.Just curious about this part of your post - How do you know? What do you do to ***check*** that you have no malware on your XP box?

---

### Post by perspectoff on 2010-06-04
> **Frak said:**
> Yes, to say Linux is immune to malware is pure delusion. The #1 reason for viruses in Windows is due to user apathy and/or lack of knowledge. I've run this very Windows system (XP SP3) for about a year and a half now. No antivirus, no anti-anything. Lo-and-behold, I have no malware. Why? I paid attention to what I was doing.

Arguably, it is much more difficult to contract infection in 7 due to UAC. There's malware for OS X and there's malware for Linux. Recently, a trojan of sorts spread on gnome-look.org. It was successful in infecting some people. No OS can keep you safe from viruses.

Hear hear.

When you market Windows to "5-year-olds with crayons", that's who buys it.

I've used Windows from the very beginning and have never had a virus (or trojan) that I know of. But I also don't allow scripts to run from websites (yeah, I don't watch ads, allow Javascript or Java, watch Flash except very selectively, allow ActiveX or other extensions) and have access controls on every hard drive and network device (including the router and wireless access points). 

Noscript (for Firefox) is a vital security device (which can be used in both Windows and Linux).

Trojans are a potentially big problem for Linux, though, and they can probably be found in unregulated / unsanctioned repositories.

It is easy to put up a software repository and lure people into installing programs that do something other than what they claim.

Heck, a similar type distribution method was the original method for distributing shareware (anyone remember Gopher?), and while the tradition is valid, it is also a gigantic security risk.

The reason that "distributions" (such as Debian/Ubuntu/Kubuntu and RedHat/Fedora/CentOS) came into existence were as a method for creating and maintaining relatively secure repositories where some modicum of security could be relied upon (for the software included in those repositories).

The trust factor placed in the administrators of these repositories determines the eventual security of each distribution. 

In fact, smaller distributions with questionable oversight may not be as secure as larger distributions, for this reason. As my neighborhood watch group says, "more eyes means more security". 

Yes, the open nature of Linux makes writing trojans easy. The question is whether a user will be tricked into installing them from an insecure repository.

Fortunately, malicious events can often be discovered quickly in Linux, where everything is open and examinable and there are lots of people watching for them.

In Windows systems, in contrast, code is not open (except, perhaps to the Chinese since Microsoft reportedly opened up its code to them under pressure, even though they did not to American companies). Zero-day security risks (i.e. able to be deployed without anyone knowing about it) are therefore more likely in Windows than in Linux.

Probably that is the biggest and most crucial difference between the two OS paradigms (and, of course, you have to be a customer in good standing with Microsoft if you want your Windows OS to stay secure).

---

### Post by aysiu on 2010-06-04
> **sydbat said:**
> Just curious about this part of your post - How do you know? What do you do to ***check*** that you have no malware on your XP box?
One can never truly know.

Or are you trying to say that antivirus software detects 100% of malware?

---

### Post by sydbat on 2010-06-04
> **aysiu said:**
> One can never truly know.

Or are you trying to say that antivirus software detects 100% of malware?No, that would be impossible. But there has to be some kind of way to find out if there is malware on any computer. For example, I run rkunter and chkrootkit regularly. Sure, they might miss something, but they are a form of checking.

I guess what I am asking is, if you do not use any application to check for malware, how do you know if there is no malware?

---

### Post by Frak on 2010-06-04
> **sydbat said:**
> No, that would be impossible. But there has to be some kind of way to find out if there is malware on any computer. For example, I run rkunter and chkrootkit regularly. Sure, they might miss something, but they are a form of checking.

I guess what I am asking is, if you do not use any application to check for malware, how do you know if there is no malware?
I just said I don't use anti-malware, I never said I didn't check for it.

---

### Post by aysiu on 2010-06-04
> **sydbat said:**
> 
I guess what I am asking is, if you do not use any application to check for malware, how do you know if there is no malware? I guess what I am asking is if you do use an application to check for malware, how do you know if there is **no** malware?

---

### Post by sydbat on 2010-06-04
> **aysiu said:**
> I guess what I am asking is if you do use an application to check for malware, how do you know if there is **no** malware?Touché.

And Frak, what do you use to check? I am really just trying to find out. Serious question. Because when someone new shows up and this thread is read, they might want to know too.

---

### Post by wojox on 2010-06-04
So far Ubuntu or any of my other distro's have been secure systems where viruses and spyware are not a problem.

---

### Post by Frak on 2010-06-04
> **sydbat said:**
> Touché.

And Frak, what do you use to check? I am really just trying to find out. Serious question. Because when someone new shows up and this thread is read, they might want to know too.
Rootkit - [http://technet.microsoft.com/en-us/sysinternals/bb897445.aspx](http://technet.microsoft.com/en-us/sysinternals/bb897445.aspx)
Malwarebytes - [http://www.malwarebytes.org/](http://www.malwarebytes.org/)

Also
[http://www.cs.arizona.edu/~jhh/papers/ccs08.pdf](http://www.cs.arizona.edu/~jhh/papers/ccs08.pdf)
> This work demonstrates that it is trivial for an attacker
to control an official package mirror. Mirrors are used to
provide fault tolerance and offload traffic from the distribution’s
main repository but are usually hosted by outside
organizations. Therefore, package managers must recognize
and mitigate the dangers posed by malicious mirrors given
a threat model in which they cannot trust the mirrors from
which they obtain content.
This paper evaluates the security of the eight most popular
[8, 14] package managers in use on Linux: APT [1], APTRPM
[2], Pacman [3], Portage [16], Slaktool [20], urpmi [23],
YaST [26], and YUM [27]. Also examined is the popular
package manager for BSD systems called ports [17] and a
popular package manager in the research community called
Stork [21]. These package managers use one of four different
security models: no security, signatures embedded within
packages, signatures on detached package metadata, or sig-
natures on the root metadata (a file that contains the secure
hashes of the package metadata).
The package managers that provide some form of security
recognize the threat posed by mirrors that are under the
control of a malicious entity. However, each of the ten package
managers studied is vulnerable to attacks by malicious
mirrors. This means that any attacker that controls a mirror
can compromise a large number of computers on the Internet
today.
Remarkably, many the security flaws that enable these attacks
are conceptually simple to understand as well as easy
fix in practice. Neither the flaws discovered nor the solutions
to them are novel. However, surprisingly these problems
exist across a wide range of package managers that
were implemented by different developers.

---

### Post by sydbat on 2010-06-04
> **Frak said:**
> Rootkit - [http://technet.microsoft.com/en-us/sysinternals/bb897445.aspx](http://technet.microsoft.com/en-us/sysinternals/bb897445.aspx)
Malwarebytes - [http://www.malwarebytes.org/](http://www.malwarebytes.org/)

Also
[http://www.cs.arizona.edu/~jhh/papers/ccs08.pdf](http://www.cs.arizona.edu/~jhh/papers/ccs08.pdf)Thanks.

---

### Post by formaldehyde_spoon on 2010-06-04
> **Frak said:**
> Rootkit - [http://technet.microsoft.com/en-us/sysinternals/bb897445.aspx](http://technet.microsoft.com/en-us/sysinternals/bb897445.aspx)
Malwarebytes - [http://www.malwarebytes.org/](http://www.malwarebytes.org/)

... 

But even after using these, you still don't actually **know** that you aren't infected.
Malware detection/prevention is (mostly) a reactive industry.

The fact that you do actually bother to check with these shows that you yourself are not convinced that your careful behaviour is enough to prevent infection.   > **perspectoff said:**
> Hear hear.

When you market Windows to ''5-year-olds with crayons'', that's who buys it.

I've used Windows from the very beginning and have never had a virus (or trojan) that I know of. But I also don't allow scripts to run from websites (yeah, I don't watch ads, allow Javascript or Java, watch Flash except very selectively, allow ActiveX or other extensions) and have access controls on every hard drive and network device (including the router and wireless access points). 

...

I use Linux and have never had a virus (or trojan) that I know of.  
I do allow scripts, ads, Javascript, Java, Flash and other extensions.

---

### Post by jerenept on 2010-06-04
I like [this]("http://xkcd.com/463/") one...

How about [this]("http://xkcd.com/272/") as well?

---

### Post by Austin25 on 2010-06-04
1. Synaptic Package Manager can list all installed packages.
2. You can view all running processes with System monitor.
3. You would need an administrative password to install anything.
4. Malware programmers would rather go for the larger target audience of Windows.
5. If you are still worried, use a live cd session.

---

### Post by jrothwell97 on 2010-06-05
> **formaldehyde_spoon said:**
> But even after using these, you still don't actually **know** that you aren't infected.
Malware detection/prevention is (mostly) a reactive industry.

The fact that you do actually bother to check with these shows that you yourself are not convinced that your careful behaviour is enough to prevent infection.

What you're saying there is that people who are woken by noises in the night and go downstairs to investigate are unsure of whether or not they've locked the door.

Running Windows as a limited user (or even a power user) is much, much safer on XP or Server 2003. (Later versions with UAC make running as an administrator more viable.)

---

### Post by Shining Arcanine on 2010-06-05
> **Diluted said:**
> Web browser vulnerability?

That hardly seems like a Linux issue, but even if it was, what if it is not a client system or the user does not bother with web browsing?

---

### Post by forrestcupp on 2010-06-05
I got a virus once from running something called PC Defender because they made it appear to be an update to Windows Defender.  Even the icon and logo was similar.  I ignorantly ran something malicious, thinking it was something helpful.

How many of you have ever run a script in Linux that is made to make life easier without studying the code, even sometimes entering your password?  I know I have.  It's not that hard to make a malicious script; you just need an ignorant person to run it, just like a virus.

---

### Post by Shining Arcanine on 2010-06-05
> **forrestcupp said:**
> I got a virus once from running something called PC Defender because they made it appear to be an update to Windows Defender.  Even the icon and logo was similar.  I ignorantly ran something malicious, thinking it was something helpful.

How many of you have ever run a script in Linux that is made to make life easier without studying the code, even sometimes entering your password?  I know I have.  It's not that hard to make a malicious script; you just need an ignorant person to run it, just like a virus.

I do this all the time, mostly because there is too much code in Gentoo Linux's scripts to be able to inspect every line of it and also because they are an official part of the operating system.

---

### Post by Diluted on 2010-06-05
> **Shining Arcanine said:**
> That hardly seems like a Linux issue
It isn't, but that means switching to Linux isn't going to protect you from threats from the web. Web pages are (usually) cross-platform after all.

> **Shining Arcanine said:**
> but even if it was, what if it is not a client system or the user does not bother with web browsing?
E-mail clients? Whatever that will interact with untrusted code. The less popular an application is, the less likely it is going to be targetted.

---

### Post by Shining Arcanine on 2010-06-05
> **Diluted said:**
> It isn't, but that means switching to Linux isn't going to protect you from threats from the web. Web pages are (usually) cross-platform after all.


E-mail clients? Whatever that will interact with untrusted code. The less popular an application is, the less likely it is going to be targetted.

It is not the fault of the operating system if a user runs programs that contain security flaws and one of the security flaws is exploited.

Something like privilege escalation (after an attacker has managed to get into a system via a user's application) is a fault of the operating system, unless the system administrator does something stupid, like letting users use sudo without passwords or allowing users to use the system's package manager to install new software.

---

### Post by Diluted on 2010-06-05
> **Shining Arcanine said:**
> It is not the fault of the operating system if a user runs programs that contain security flaws and one of the security flaws is exploited.

Something like privilege escalation (after an attacker has managed to get into a system via a user's application) is a fault of the operating system, unless the system administrator does something stupid, like letting users use sudo without passwords or allowing users to use the system's package manager to install new software.
The operating system still has the potential to be compromised either way.

Would that answer your question as to how someone would hack the system you specified?

---

### Post by formaldehyde_spoon on 2010-06-05
> **jrothwell97 said:**
> What you're saying there is that people who are woken by noises in the night and go downstairs to investigate are unsure of whether or not they've locked the door.



Must simple statements always be transformed into bad analogies?  
If you had to check the success of your actions then you were unsure of the success of your actions.

---

### Post by jrothwell97 on 2010-06-05
> **formaldehyde_spoon said:**
> Must simple statements always be transformed into bad analogies?  
If you had to check the success of your actions then you were unsure of the success of your actions.

Does this mean, however, that Windows is insecure by design?

No, it doesn't. When misconfigured, yes, it's insecure. (This is something in particular I hate with XP: you can have unpassworded administrator accounts used day-to-day, and it's like running as root permanently on a Linux box.)

However, what you're saying is that the fact Frak checks his Windows box for malware implies that his box is insecure. Unfortunately, I don't see how this is a logical conclusion.

---

### Post by aysiu on 2010-06-05
> **jrothwell97 said:**
> 
However, what you're saying is that the fact Frak checks his Windows box for malware implies that his box is insecure. Unfortunately, I don't see how this is a logical conclusion. The daily checking doesn't mean it **is** insecure. But if it is secure then daily checking seems excessive. It's like constantly opening your refrigerator every hour to make sure your food didn't walk out on its own. If you're certain your food doesn't have legs and that your fridge door is securely closed, there isn't a need to check it that often.

Likewise, if you're sure your soap works and that you haven't touched anything dirty in the last few hours, there's no need to wash your hands ten more times just to make sure they're clean. That's obsessive-compulsive behavior.

---

### Post by formaldehyde_spoon on 2010-06-05
> **jrothwell97 said:**
> Does this mean, however, that Windows is insecure by design?

No, it doesn't. When misconfigured, yes, it's insecure. (This is something in particular I hate with XP: you can have unpassworded administrator accounts used day-to-day, and it's like running as root permanently on a Linux box.)

However, what you're saying is that the fact Frak checks his Windows box for malware implies that his box is insecure. Unfortunately, I don't see how this is a logical conclusion.

Please stop telling me what I am saying. Ask instead.

I didn't say Windows is insecure, by design or otherwise, nor did I imply it.
I didn't imply that anyone's system was insecure.

For the record I think Windows is less secure than Linux, but that doesn't necessarily mean it is insecure.

The point of what I wrote was what I wrote: the most ardent believers of "Malware on Windows is the Users Fault" know that even they cannot be sure of avoiding all malware.
From that you can draw your own conclusions.  I would say it means users can't be blamed for every infection on their system, and that using Window comes with an inherent risk from malware that's greater than the risk that Linux users face, no matter how careful you are.

---

### Post by Shining Arcanine on 2010-06-05
> **Diluted said:**
> The operating system still has the potential to be compromised either way.

Would that answer your question as to how someone would hack the system you specified?

It does not, because I never specified what it does. I only said what operating system runs on it.

---

### Post by sydbat on 2010-06-05
> **aysiu said:**
> It's like constantly opening your refrigerator every hour to make sure your food didn't walk out on its own. If you're certain your food doesn't have legs and that your fridge door is securely closed, there isn't a need to check it that often.I have seen fridges that made me question whether the food had legs or not...<insert throw-up smiley>

And to address a couple of the previous posts about web browser security - IE is still an integral part of the Windows OS, so if something is able to breach IE, it will breach Windows, even without user interaction. I know, I have seen it. 

However, other browsers (like Firefox) are not part of the Windows OS, so it is far less likely for web-based nasties to get far (unless the user tells it to). Same goes for all other OS's.

---

### Post by screaminj3sus on 2010-06-05
> **sydbat said:**
> I have seen fridges that made me question whether the food had legs or not...<insert throw-up smiley>

And to address a couple of the previous posts about web browser security - IE is still an integral part of the Windows OS, so if something is able to breach IE, it will breach Windows, even without user interaction. I know, I have seen it. 

However, other browsers (like Firefox) are not part of the Windows OS, so it is far less likely for web-based nasties to get far (unless the user tells it to). Same goes for all other OS's.

IE8 is actually very secure (and not as integrated with windows as it once was, but I guess you do still have a point), right up there with firefox (if you have UAC enabled) it uses a sandboxing tabs/ and separate tab processes like chrome.

There are plenty of valid criticisms of IE but it does not deserve the horrible security reputation from the ie6 days anymore. Same with windows7/vista which are MUCH more secure than XP and previous.

Hell I have to clean virus's and crap off friends and families computers all the time and not once have I ever had to clean a windows vista/7 computer yet.

[http://blogs.msdn.com/b/ie/archive/2008/03/11/ie8-and-loosely-coupled-ie-lcie.aspx](http://blogs.msdn.com/b/ie/archive/2008/03/11/ie8-and-loosely-coupled-ie-lcie.aspx)

---

### Post by del_diablo on 2010-06-05
> IE8 is actually very secure (and not as integrated with windows as it once was, but I guess you do still have a point)

It still automatically runs the GUI running root priviliges sort of. Which means its still fails security.
I have seen a computer who got infected trough IE8, it was amazing how much less problems i had from that user after i switched her to another browser.

---

### Post by screaminj3sus on 2010-06-05
> **del_diablo said:**
> It still automatically runs the GUI running root priviliges sort of. Which means its still fails security.
I have seen a computer who got infected trough IE8, it was amazing how much less problems i had from that user after i switched her to another browser.

And I've seen plenty of computers infected using firefox. My brother uses firefox and I've had to clean his pc of infection many times.

---

### Post by Diluted on 2010-06-05
> **Shining Arcanine said:**
> It does not, because I never specified what it does. I only said what operating system runs on it.
I'm afraid you're going to have to specify more, because I'm using an unspecified-target point of view. I'm not a hacker, so I can't tell you how a hacker targeting a specific computer would do. I don't think home users would need to worry about some random hacker trying to break into their systems anyway, unless someone has a grudge against them.

> **sydbat said:**
> IE is still an integral part of the Windows OS, so if something is able to breach IE, it will breach Windows, even without user interaction.
Really? I was under the impression that IE would run under the privileges of the user account (lower under Standard Users and higher under Administrators). I would be surprised if you can breach Windows simply by compromising a standard user IE session without using a privilege escalation vulnerability.

> **del_diablo said:**
> It still automatically runs the GUI running root priviliges sort of. Which means its still fails security.
Are you sure? I've just checked it out and it appears that my IE processes is owned by my standard user, not with Administrator or anything higher.

---

### Post by screaminj3sus on 2010-06-06
Yeah they don't know what they are talking about, IE8 does not "run the gui as admin" with uac enabled. it runs as a standard user.

---

### Post by aysiu on 2010-06-06
> **screaminj3sus said:**
> And I've seen plenty of computers infected using firefox. My brother uses firefox and I've had to clean his pc of infection many times. So the infection was through Firefox? Or he got infected while also using Firefox? The two are not the same.

While I know it's theoretically possible, I've never encountered anyone who has been infected *through* Firefox (unless you count using Firefox to search for and download a malicious .exe file, which you then decide to install yourself).

---

### Post by Frak on 2010-06-06
> **aysiu said:**
> So the infection was through Firefox? Or he got infected while also using Firefox? The two are not the same.

While I know it's theoretically possible, I've never encountered anyone who has been infected *through* Firefox (unless you count using Firefox to search for and download a malicious .exe file, which you then decide to install yourself).
I've heard of people getting infections while visiting a website using Firefox, though that was some time ago and the holes were fixed.

It's not like it can't happen, just unlikely.

---

### Post by screaminj3sus on 2010-06-06
Almost all of the infections I have to clean lately are Rogue AV programs that are installed because they were to stupid to click the "omg your computer has 1000 viruses scan now" crap. Those are a bitch to get rid of too :/

---

### Post by Shining Arcanine on 2010-06-06
> **Diluted said:**
> I'm afraid you're going to have to specify more, because I'm using an unspecified-target point of view. I'm not a hacker, so I can't tell you how a hacker targeting a specific computer would do. I don't think home users would need to worry about some random hacker trying to break into their systems anyway, unless someone has a grudge against them.

I am afraid that you will need to learn to hack with less, because hackers are not told much about the specifications of the systems they target. They can spend years doing little things because they do not have the slightest clue how to get into the systems. It is not until they have a breakthrough that it becomes publicized that they were trying to hack various systems in the first place.

---

### Post by Diluted on 2010-06-06
> **Shining Arcanine said:**
> I am afraid that you will need to learn to hack with less, because hackers are not told much about the specifications of the systems they target. They can spend years doing little things because they do not have the slightest clue how to get into the systems. It is not until they have a breakthrough that it becomes publicized that they were trying to hack various systems in the first place.
I'll say it once more, I'm not a hacker. All I'm telling you is how your system can be compromised within the threat model of common home users. If you are unlucky enough to be targeted specifically, I think this thread isn't going to be enough and you should seek additional advice.

If you really want answers as to how someone would hack a Linux system without knowing anything else, I suggest you ask someone within a dedicated hacking community, where there are people who are more knowledgeable than me.

---

### Post by Shining Arcanine on 2010-06-06
I am not asking how you would hack my system, because I am fairly certain that under ordinary circumstances, it cannot be done. There is a professor at my university that is an expert on this subject that I could ask about that, but I am confident enough that my system is secure that I do not plan to do that. The only potential issue at the moment is to man in the middle attacks on untrusted Wi-Fi connections, but there are even ways around that (involving a two-way authenticated VPN connection). The hypothetical system I mentioned (which was a type of server), is not a mobile system, so it does not suffer from man in the middle attacks under any reasonable circumstances. Someone would need to splice into the local network, the ISP or the internet backbone to do a man in the middle attack on it, which is unlikely.

Unless a user/system administration does something foolish, minimalist Linux distributions are really not hackable.

---

### Post by Diluted on 2010-06-06
> **Shining Arcanine said:**
> I am not asking how you would hack my system,
I must have missed the "tell me how would you hack it" part from your previous post then.

> **Shining Arcanine said:**
> There is a professor at my university that is an expert on this subject that I could ask about that, but I am confident enough that my system is secure that I do not plan to do that.
Better safe than sorry. Your professor may inform you of avenues you've missed or new types of attacks that is getting common.

---

### Post by Shining Arcanine on 2010-06-06
> **Diluted said:**
> I must have missed the "tell me how would you hack it" part from your previous post then.

It was a rhetorical question meant to make you realize that it is not possible unless I assist in the task.

---

### Post by Diluted on 2010-06-07
> **Shining Arcanine said:**
> It was a rhetorical question meant to make you realize that it is not possible unless I assist in the task.
I would appreciate it if you could say these things earlier, so we don't have to move the challenge from what appears to be a secure home computer, to a computer that is not a client system, to a computer that may or may not be running applications and finally, a server of an unspecific type. I'm sorry, but I just can't keep up with all the goal posts.

Not to mention that I'm supposed to learn to hack with even less information, in order to solve a challenge that is not possible without your assistance.

Realistically, nobody is going to try to hack your server, without knowing its value and without any incentives.

---

### Post by Shining Arcanine on 2010-06-07
The point is that as long as the user and system administrator do not provide avenues for hacking, a hacker will be unable to hack a Linux system. That is not the case with both Mac OS X or Windows, but it is the case with Linux distributions and the various flavors of BSD.

---

### Post by sydbat on 2010-06-07
> **shining arcanine said:**
> the point is that as long as the user and system administrator do not provide avenues for hacking, a hacker will be unable to hack a linux system. That is not the case with both mac os x or windows, but it is the case with linux distributions and the various flavors of bsd.qft.

---

### Post by Frak on 2010-06-07
> **Shining Arcanine said:**
> The point is that as long as the user and system administrator do not provide avenues for hacking, a hacker will be unable to hack a Linux system. That is not the case with both Mac OS X or Windows, but it is the case with Linux distributions and the various flavors of BSD.
That is the case with all systems, not just Linux and *BSD.

---

