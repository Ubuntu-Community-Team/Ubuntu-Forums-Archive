---
title: "Is Ubuntu right for me?"
date: 2014-01-28
forum: Recurring Discussions
---

### Post by marius5 on 2014-01-28
I would like you, dear reader, to help me make a decision which can cost a lot of time and a lot of nerves.
I am trying to figure out, weather I should give ubuntu a shot or not. This problem of mine, of course, sound ridiculous - whats the problem, eh, just test it and see how it goes, write? Well, the problem is what I am doing with my computer... Here are the most common tasks that I do with my computer:
1. Listen to spotify(music) / watch videos(mostly through browser) (I really enjoy equalizers, and as I know, ubuntu doesn't have a good one)
2. Programming in Java, C++(Eclipse IDE for linux, maybe?), Android(Java)(Using android studio IDE)
3. Browse the web in general (studying, looking for information)
4. Make presentations, write documents
5. Communicating / social networking (Skype, Facebook)
6. Messing around with my phone (installing custom kernels, radios, roms)

I have tried windows 8 and windows 8.1 - its a horror movie (or at least was) for C++ developers who want to use boost libraries (it seems that you need to run as admin pretty much anything there in order to make it work). Currently I am running Windows 7 and it is fine. But what I really do like about Ubuntu (and OSX) is the global menu... Don't know why, but it is much more comfortable.

I have tried ubuntu 13.10 maybe two months ago. Used it for a week and at the end - I hated it for a couple of reasons:
1. It was very buggy and unstable. Used to constantly crash.
2. Sometimes my touchpad didn't work (this mostly occured when I used to turn off or on my touchpad with special button for it)
3. I was unable to connect to wireless networks in some places and was able to with Windows 7. (my laptop has intel wifi 1000bgn card, its a Msi fx600 laptop)
4. I was shocked that it was not that customizabile. (Don't know what canonical is thinking, but Linux should be all about customizability, security, speed, stability)
5. I have Samsung 840 evo series SSD which has neat features for windows (like rapid technology, etc) and yet Ubuntu does not even have a feature in control panel to enable or disable trimming...

So, I am asking for your tips, your experience on should I try Ubuntu? Will it run smooth in my daily usage and is it possible to get rid of these "bugs" that I have named? Maybe I should test other Ubuntu version (like 14.04, or maybe I should wait for it to be fully released and then try to switch?). Or maybe there is a better distro for me with global menu? Please, do not hesitate do give me as much tips and "experience talk" as possible.
Thank you very much!

---

### Post by bc.haynes on 2014-01-28
Hey, Welcome to the forums.
There is a post (I can not find it at the moment. I'm a noobie.) that is entitled "Ubuntu is not Windows" that can help you make up your mind. Perhaps one of the Forum Moderators could post a link to it.
I, for one, will not go back to Windows (too unsecure), but I am not a programmer and only use the computer to learn new things. I am a hobbyist, not a power user. Good luck with your search.

---

### Post by marius5 on 2014-01-28
> **bc.haynes said:**
> Hey, Welcome to the forums.
There is a post (I can not find it at the moment. I'm a noobie.) that is entitled "Ubuntu is not Windows" that can help you make up your mind. Perhaps one of the Forum Moderators could post a link to it.
Thanks. Going to search for it :) What is your personal opinion though? Edit: can't seem to find it...

---

### Post by mörgæs on 2014-01-28
Some of the bugs might be solved (or less severe) in X/Lubuntu. Worth a try before making up your mind.

---

### Post by robin7 on 2014-01-28
Something else to consider in your decision is **hardware compatibility**!   So click [here]("http://www.ubuntu.com/certification/") and what the Ubuntu Certified Hardware site says about your particular rig.

---

### Post by marius5 on 2014-01-28
Woah. never thought that ubuntu might not support (or fully support) certain laptops. As it turns my, my rare laptop, no surprises here, is not certified. Sweet :) I guess this answers a lot of my questions and I believe I will have to remain Windows user...

---

### Post by mörgæs on 2014-01-28
"Not certified" does by no means indicate that Buntu does not run on the hardware in question. My guess is that the most users here have non-certified gear.

---

### Post by Bucky Ball on 2014-01-28
*Thread moved to [I]**Recurring Discussions.***[/I]

Welcome. A question only you can answer. Best bet is to download some ISOs of various flavours (Ubuntu, Xubuntu, Lubuntu, Kubuntu), burn them to disk or USB and give them a try. You can try them all without installing. You can also run them as virtual machines using something like Virtualbox in Windows, avoiding the need to create install media. 

As for the Ubuntu bugs, try the rock solid 12.04 LTS (long-term support). Supported until April 2017, but directly upgradeable to 14.04 LTS when it comes out in April. 14.04 is not a good decision. It is testing and definitely not a good place to start unless you are looking to report bugs, get involved, and go on a steep learning curve.

Good luck. If Ubuntu is not right for you, [maybe another Linux distro is.]("http://distrowatch.com/")

PS: It is not that Ubuntu doesn't support certain laptops, it is that certain laptops don't support Ubuntu (or Linux). Nothing to do with Ubuntu if manufacturers don't play the game.

Having said that, don't think that because it doesn't have a little Linux penguin on the box alongside the mac and MS logos that it means it is not supported. I've got tons of stuff that is not 'certified' in that way and I email the company about why not when I plug their product in and it 'just works'. I've had non-certified hardware that has just worked in Linux, but I've had to jump through hoops with it in Windows. ;)

---

### Post by QIII on 2014-01-28
> **marius5 said:**
> Woah. never thought that ubuntu might not support (or fully support) certain laptops. As it turns my, my rare laptop, no surprises here, is not certified. Sweet :) I guess this answers a lot of my questions and I believe I will have to remain Windows user...

Hello!

Because there is a general and pervasive misunderstanding about such things, I would like to point out that it is not the case that Ubuntu (or any other distro) supports or does not support any laptop or individual component.

The relationship is the opposite -- the question is whether some piece of hardware supports Linux.  No matter what we would like, if an OEM does not, for instance, provide a Linux driver there is little the Linux community can do about it.  Open source developers try, with varying levels of success, to create open source drivers -- but they do so by trying to peer into a black box.  This is devilishly difficult since OEMs don't often provide proprietary information about their hardware.

Windows does not work with OEM XYZ's component due to any effort on the part of Microsoft.  OEM XYZ makes sure that their component works with Windows or they go out of business.  If they don't make it work with Linux, then they are only missing out on a piddlingly small share of the market.  It does not make good business sense to expend the same amount of resources on 2% of the market as they spend on 93% of the market.  One can hardly blame OEMs for making a wise business decision.

This is a fact of life in the Linux world.  If the OEM only provides a Windows driver and no developer is able to black-box a driver that works for Linux, that hardware is not likely to work well, or at all, with Linux.

The effect, of course, is the same:  You can't use OEM XYZ's component.  But it is not for want of trying on Linux' part.

---

### Post by Bucky Ball on 2014-01-28
^^^^
The above.

---

### Post by Bashing-om on 2014-01-28
marius5; Hi ! My five pounds worth.

I do have a programming background (somewhat limited) and I will attest that ubuntu is a programmer's dream system. Unreal how much direct support exist and the ease of workability - once you know how.

But as all have said, there is a steep learning curve, The referenced "reading material":
[http://ubuntuforums.org/showthread.php?t=2125370](http://ubuntuforums.org/showthread.php?t=2125370)
[http://ubuntuforums.org/showthread.php?t=2200144](http://ubuntuforums.org/showthread.php?t=2200144)
[http://ubuntuforums.org/showthread.php?t=2201432](http://ubuntuforums.org/showthread.php?t=2201432)
These guys say it so well.

On your wish list is nothing that 'buntu can not do, and in some respects better than any other. However, It do take the hosses to operate the high end ubuntu, the flagship edition, with all the bells, whistles and eye candy. It do take the the hardware in this instance. There are many many alternatives one may choose once you have established a knowledge base.
I am somewhat knowledgeable and I choose to install a base system and build the operating system I want. Absolutely beautiful - for what I want in MY operating system and what I use it for. Your mileage will vary. To start with, out of the box will serve nicely. In 'buntu the base system is all the same, just the desk top and applications differ. As advised, download several, and see what tickles your fancy the most.

And perhaps best of all, is the community at large and the great support structues. Anything and everything you want to know, all for the asking !

This is open source at it's best ->

[INDENT][INDENT][INDENT]there are no secrets
[/INDENT][/INDENT][/INDENT]

---

### Post by grahammechanical on 2014-01-28
Are you right for Ubuntu? That is the more important question.

---

### Post by BlinkinCat on 2014-01-28
> **grahammechanical said:**
> Are you right for Ubuntu? That is the more important question.

+1

- [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

---

### Post by robin7 on 2014-01-28
From what you describe what you want from your OS and what tasks you want to do, I think Ubuntu (or any of it's official flavors) would be good.  Just check for [hardware compatibility]("http://ubuntu.com/certification/") and proceed from there.

---

### Post by DuckHook on 2014-01-28
The link to "Linux is not Windows" intro:

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

Answering your questions in the order posed:

1. You will encounter annoyances with music and videos mainly revolving around codecs—restricted codecs must be installed as a separate conscious choice. This is not a problem for one with IT experience and usually just involves Googling. Obscure Windows-only codecs are a problem, but few use them.

2. Have never heard that programming is ever an issue in Linux (it is a geek's OS after all), but I'm not a programmer, so only going on hearsay.

3. Web browsing is no different to Windows and can be far safer.

4. If you must use Windows apps then this is a problem.

5. Skype works fine for some, but is awful for others. Do not expect MS to continue making any efforts to keep Skype compatible with any OS but their own. Other social networking works well with a large selection of apps to choose from.

6. Depends on the phone. Some will only allow jailbreaking/rooting with Windows tools.

Comments about your prior issues (again in order posed):

1. 13.10 is not for new users nor for those looking for stability. 12.04 serves that function. You should not be using a bleeding-edge version if you want stability.

2. ...don't turn off touchpad. Linux driver support does not match Windows driver support because vendors often don't even write Linux drivers, so it is written by Linux community (see QIII's post).

3. WIFI support is largely good but can be spotty depending on HW. Most WIFI is supported extremely well, but when it isn't, you must improvise.

4. Linux *is* highly customizable. The hundreds of distros in existence attest to this fact. Shouldn't conflate Ubuntu with Linux. Ubuntu is one distro that has chosen to position itself for general users who would only be confused and flustered if confronted with dozens of choices. If you want customization, then choose basic Arch or Gentoo and go nuts customizing to your heart's content. Just don't then complain about the accompanying complexity and obscurity; customization and complexity are two sides of one coin. Regarding Linux security, speed & stability over Windows, these are evident to anyone who has properly experienced and contrasted both OSes, but cannot be conveyed without experiencing over time for yourself.

5. It is true that Ubuntu/Linux requires a certain willingness to dig into the guts of the OS. Trimming must be turned on by editing a config file (fstab), but this is not especially difficult. However, if completely unwilling to work with command line and config files, then I agree that Ubuntu or any Linux distro for that matter is not for you.

What follows is a general observation—a meta-comment, if you will.

When I look back at my Windows experience, nothing came easy. Contrary to the accepted bromide, Windows was neither easy nor friendly. It was just that years under its solitary confinement had conditioned me into thinking that its limitations and failings were normal. When I now look back at how I meekly swallowed its bloat, registry cruft, slowdowns over time, memory leakage, malware, holes, defragging requirements, usage restrictions, activation requirements, not to mention its incessant BSoDs, I am struck by how easy it is to get people to normalize insanity.

If you want to learn Linux, especially at the level that you apparently do, the process will not be easy. People who tell you that it's easy are misleading you—perhaps with good intentions—but nevertheless doing you a disservice. You will have to learn new paradigms, metaphors and the dreaded command line. The difference is that, at the end of the learning curve, you will be using an OS that does not constrain you, does not insult your intelligence, does not try to lock you into captivity, and does not expect you to normalize insanity.

Your time, your effort, your choice.

---

### Post by DuckHook on 2014-01-28
My only point of disagreement with QIII's excellent post is a tiny one...> **QIII said:**
> ...One can hardly blame OEMs for making a wise business decision......perhaps a "short-sighted pragmatism", but not such a "wise" business decision. No business wants to rely on a single customer any more than it wishes to be confined to a single supplier. It gives the opposite party the power of life and death over you. It is in every business's own long-term interest to foster competition and alternatives in both suppliers and customers, even if such alternatives have small market shares. That's how all alternatives start out—small. It's only by supporting and nurturing sparks that you eventually get healthy flames.

In the general scheme of things, it doesn't cost OEMs much more to produce a Linux driver once they've committed themselves to writing one for Windows. Most certainly manage to do so for Macs. The real issue here is that monopolies suffocate choice and innovation by bullying or bribing their suppliers into erecting artificial barriers to entry against any perceived threat to their hegemony. This tactic is not constrained to MS. It happens in any monopoly/cartel throughout history, from pre-breakup ATT to Rockefeller's Standard Oil to the Renaissance guilds.

It's not easy breaking the vicious cycle, but we can all do our small part by giving our business to suppliers who have the balls to resist the threats/blandishments of the monopolies/cartels.

---

### Post by lykwydchykyn on 2014-01-28
I think you could be well served by some Linux distro or another, if you're willing to put in a little effort and accept that not every aspect is going to be the same.

Many people make the mistake of thinking that Ubuntu is the greatest distro and all others are a distant second.  Ubuntu is fine, but other distros have merits too.  I'm not sure it's the right distro for you.  Try a few; there's no rush.

---

### Post by marius5 on 2014-01-29
Huge thanks goes to all of you guys. This is very valuable and interesting information that you are sharing.
I have digged around a bit. I don't know if this is the right place to discuss other distors, but anyways... Debian, as I understood, is the best thing when it comes to stability. Also, others say that Elementary OS is worth a try.

---

### Post by craig10x on 2014-01-29
Debian stable may be stable but it has very old packages...ubuntu does an awful lot of refinement to debian and i think makes it a lot better...i have used debian based distros and always seem to come back to to ubuntu...

---

