---
title: "Why Linux Isn't the Most Popular Operating System"
date: 2009-10-16
forum: Recurring Discussions
---

### Post by Penguin Guy on 2009-10-16
**In a nutshell:** There are too many variations, and although Linux has very good package management systems, it isn't enough.

Okay, first off I would like to say how much I love Linux - it opened up a whole new world in computing for me (BIOS, partitions, filesystems, and a whole lot more). However we all know it is not the most popular operating system - but exactly why isn't it? I believe it has quite a few main problems, mostly relating to incompatibility with itself:
[LIST]
[*]There are multiple installer package types (.deb, .rpm, .tgz, etc) - this means that packages are not very compatible between distributions.
[*]Programs handle stuff they shouldn't (Gnome handles the background, Gedit handles syntax highlighting, Firefox handles it's icons, etc) - this makes would-be-simple tasks such as setting the background or changing syntax coloring hell for programmers, and therefore such programs tend not to be very compatible between desktop environments.
[*][Settings are spread across different systems (/etc/default, gconf, etc).]("http://ubuntuforums.org/showthread.php?t=1381140")
[*]Branding: Ubuntu (most people I've talked to think it sounds weird), the Gimp (is this a joke?), and more.
[/LIST]

Linux lacks commercial software, to get commercial software on Linux we need to make it as easy as possible for companies to sell software on our repo's:
[LIST]
[*]Create 'FOSS' packages and a FOSS master-repo' - FOSS packages can be uploaded to the FOSS repo' and automatically be converted into various package types and distributed across multiple distributions.
[*]Make it possible to create installation CDs that are compatible between distrobutions.
[*]Introduce a commercial packages scheme - setting up a system that allows users to pay for packages should encourage companies like Adobe to port their packages to Linux. We could also add a donate feature to help support open-source packages. *- In Progress*
[/LIST]

I admit that one of the main reasons why Linux is not very popular is because of Windows' monopoly, but it *is* partly because Windows is better for the average user. What does everyone else think?

---

### Post by Eisenwinter on 2009-10-16
Why is this question asked 10 times a week, and always leads to the same thing of "it's your opinion, others may think otherwise"?

---

### Post by sydbat on 2009-10-16
> **Eisenwinter said:**
> Why is this question asked 10 times a week, and always leads to the same thing of "it's your opinion, others may think otherwise"?^^This^^

---

### Post by RiceMonster on 2009-10-16
> **Eisenwinter said:**
> Why is this question asked 10 times a week, and always leads to the same thing of "it's your opinion, others may think otherwise"?

People are on a mission to add as many threads to recurring discussions as possible

---

### Post by Tony Flury on 2009-10-16
Popularity is probably more down to availability - bear in mind most people buy a PC with MS Windows (or MAC OS) already pre-installed, and not many people are technically confident enough to think about installing Linux.

I am not sure I agree about your critique of the various applications but as Eisenwinter says it really all is a matter of opinion. At the end of the day the OS is a tool do either do productive work with, or to enable leisure activities. If it works for you then great. You will notice that flame wars on the internet are very rare on the subject of hammers, saws or screwdrivers, and they are just tools too.

---

### Post by Calmor on 2009-10-16
My view:

I guess I'm a little confused about Gedit handing syntax highlighting.  No part of the file itself is changed (the only thing I can think of is the tab width/spacing).  Highlighting is provided as a convenience, and many GUI text editors have this option.  In fact, I think Gedit is a little more graceful than some, as it allows you to select themes which are loosely based on built-in Ubuntu themes.

I think a large part of why Linux isn't more popular is the fact that it's hard to displace what everyone already knows well.  At this point, Microsoft is popular because everyone uses it.  Send someone an OpenOffice Writer file saved as .DOC with a bunch of custom-formatted tables and see if they like it.  Thus, MS Office is a de facto standard of business.  

Another issue is choices, options, and the requirement to know a bit about (or at least desire to know how to change) settings and the internal workings of your PC.  Windows made the computer accessible to nearly everyone.  Some can say Linux is working toward that as well, but there are still too many options, too many tweaks that need to be performed.  The general public doesn't want to decide if they want Gnome, KDE, XFCE, etc.  They don't want to guess if the hardware they buy will work.  They just want their computer to work.  This may not be all the fault of the Linux community (we have to reverse-engineer drivers, after all, since they're often not provided), but it's still a drawback.  Apple has addressed this by limiting the selection of both interfaces and hardware, even though the core system allows for much larger variances.  

The problems you list about package installer types is actually a little further than that - because Linux can be customized so many different ways, it's harder to release software that works on all systems.  Proprietary companies generally don't want to support a million variants of a product used by 1% of the total computer users.  Financially, it makes sense not to support Linux unless those types of users are your core market.  Intuit has refused to produce and market a Linux version of Quicken because it feels most of its users run Windows or Mac, and doesn't want to pay for R&D for Linux for minimal returns.

Part of why I love Linux is because I can change things, edit settings (or even the code if necessary), and do with it as I please.  But I'd say I'm in the minority.

---

### Post by sydbat on 2009-10-16
> **Tony Flury said:**
> Popularity is probably more down to availability - bear in mind most people buy a PC with MS Windows (or MAC OS) already pre-installed, and not many people are technically confident enough to think about installing Linux.

I am not sure I agree about your critique of the various applications but as Eisenwinter says it really all is a matter of opinion. At the end of the day the OS is a tool do either do productive work with, or to enable leisure activities. If it works for you then great. **You will notice that flame wars on the internet are very rare on the subject of hammers, saws or screwdrivers, and they are just tools too.**However, there are a lot of flame wars about tools...if you know what I mean...:P

---

### Post by maflynn on 2009-10-16
Lots of reasons why its not the most popular
1. windows comes with every pc by default, it works (sometimes barely) and the user doesn't need to go into CLI to configure/run stuff

2. OSX has a reputation of being rock solid, albeit bloated and works extremely well with the hardware

3. Linux is viewed by most people as an OS for hobbyists who like to muck around with the innards of the OS, compiling kernels and such.  Most typical users don't want to dig in that much.

4. Software/peripheral support.  I use LightRoom, there's really nothing comparable in Linux that gives me the same level organization for my images and non-destructive image editing capability.  When I want to print them, I do so on my Canon Pixma Pro9000 printer.  I am unable to find drivers for that printer on Linux

So you see there's lots of varied reasons and the list I produced is not comprehensive in any sense of the word.

---

### Post by Penguin Guy on 2009-10-16
> **Tony Flury said:**
> 
You will notice that flame wars on the internet are very rare on the subject of hammers, saws or screwdrivers, and they are just tools too.

That is because if you have a compatibility problem between your screwdriver and your screw, there is an easy solution: get a new screwdriver. When you switch between screwdrivers it's as easy as taking one out of the toolbox and putting another back in - you don't have to wait a few minutes rebooting.

> **Calmor said:**
> 
The problems you list about package installer types is actually a little further than that - because Linux can be customized so many different ways, it's harder to release software that works on all systems.  Proprietary companies generally don't want to support a million variants of a product used by 1% of the total computer users.

Exactly! My point is that we should allow customization, but in such a way that makes everything compatible. For example, you  could put your home directory at /admin/home if you wanted - but it would break everything - that is, if it were not for the $HOME variable. If Linux simply added more things like these, distro's would become far more compatible.

---

### Post by aysiu on 2009-10-16
> **maflynn said:**
> 
3. Linux is viewed by most people as an OS for hobbyists who like to muck around with the innards of the OS, compiling kernels and such.  Most typical users don't want to dig in that much. Well, to the extend Linux is viewed at all, this is true. Every person I meet in person (not on the forums or in blogs) who finds out I use Linux asks if I work in technology or if I'm a programmer. They're often shocked to find out neither applies to me.

---

### Post by Penguin Guy on 2009-10-16
> **aysiu said:**
> Well, to the extend Linux is viewed at all, this is true. Every person I meet in person (not on the forums or in blogs) who finds out I use Linux asks if I work in technology or if I'm a programmer. They're often shocked to find out neither applies to me.
I got the impression that lots of non-tech people use Ubuntu. You don't need to be a tech person, you just need to be open-minded and prepared to try new things. With other distro's this is not the case, specifically Arch.

---

### Post by aysiu on 2009-10-16
> **Penguin Guy said:**
> I got the impression that lots of non-tech people use Ubuntu. You don't need to be a tech person, you just need to be open-minded and prepared to try new things. With other distro's this is not the case, specifically Arch.
I'm the only Linux user I know in person who isn't also working tech professionally or programming.

I'm not saying other non-techies *can't* use Linux, only that they don't.

In my social circles, I'd say the #1 obstacle (apart from ignorance) is possession of an iPod Touch or iPhone.

---

### Post by RiceMonster on 2009-10-16
> **aysiu said:**
> I'm the only Linux user I know in person who isn't also working tech professionally or programming.

I'm not saying other non-techies *can't* use Linux, only that they don't.

It's true. I know a bunch of Linux users in real life and they're all involved in IT either through work or school.

---

### Post by JDShu on 2009-10-16
People use Microsoft file formats, and there is no motivation to change. If everyone magically started using open file formats, then I suspect Linux (and other OS's) would be much more widespread.

---

### Post by Penguin Guy on 2009-10-16
> **RiceMonster said:**
> It's true. I know a bunch of Linux users in real life and they're all involved in IT either through work or school.
I guess a new operating system seems a lot more interesting to a tech person than to any other person.

---

### Post by aysiu on 2009-10-16
> **Penguin Guy said:**
> I guess a new operating system seems a lot more interesting to a tech person than to any other person.
That makes sense, considering most people don't even know what an operating system is (or even a web browser).

---

### Post by NCLI on 2009-10-16
I think that's really the biggest problem for GNU/Linux: Most people don't care what OS they're using, *they just want it to work. *They don't want to tweak their computer, or replace the working environment they're comfortable in, and they really don't care all that much. We have to show them *why *they should want Linux, they're not going to find out that it is a worthy alternative on their own.

This has been said many times before here on this forum, but another big problem is that people don't realise that their computer could be much easier to work with than it is under Windows, or think they need to buy a Mac. Even relatively tech-savy people who know how to maintain a Windows system, keeping it up to date, tweaking it etc, don't know how to install an operating system.
I've helped many people I'd label as tech-savy who wanted Ubuntu, but didn't know how to make the PC boot from the CD-ROM drive!

Lastly, there's compatibility. Most mainstream hardware types works OOTB, but tablets, 3G modems and touchscreens are still problematic. However, software compatibility is by far the biggest problem. Wine is obviously working hard to fix this, but the best way is really to make Linux so big that companies can profit from porting their applications to it.

---

### Post by donkyhotay on 2009-10-17
People go to a store and just buy a computer. They don't care what it comes with, since MS uses it's leverage to force windows on every system it can thats all people know about. If they did buy a computer from a store with linux on it chances are they would call tech support upset that "it doesn't work" because they can't install MS office or some other proprietary program. Most people don't know that there are free alternatives (like open office) and when you try telling them they figure it has to be illegal/pirated or something because proprietary software companies have been beating the message that you should pay for all software into their heads for the last decade or more.

---

### Post by tcoffeep on 2009-10-17
> **donkyhotay said:**
> People go to a store and just buy a computer. They don't care what it comes with, since MS uses it's leverage to force windows on every system it can thats all people know about. If they did buy a computer from a store with linux on it chances are they would call tech support upset that "it doesn't work" because they can't install MS office or some other proprietary program. Most people don't know that there are free alternatives (like open office) and when you try telling them they figure it has to be illegal/pirated or something because proprietary software companies have been beating the message that you should pay for all software into their heads for the last decade or more.

People go to a store and just buy a computer, yeah. The rest of what you say, though, I have a problem with. MS doesn't use its leverage to force Windows on every system... no. You're wrong, there. Generally, the computers sold to consumers work. And they generally work with very little wrong with them. With linux, they'd need to do this, and do that, and do this and that. Mind you, not always. Sometimes it really does **just work**(tm)... just not very often.
People don't care what they use because what they use generally doesn't cause them any freakin' problems. If it did, a google search would give them every answer. Here's the really awesome part : Some people know there are *free* alternatives, but don't give a **** because they like supporting what they use. Freakin' crazy people, these days.

You know, I told my girlfriend's father about openoffice. He tried it, said it was ****, and reinstalled Microsoft Office. So, no. It's not misinformed people, all the time. It's called preference and taste.

Have a nice day.

-Dex

---

### Post by subdivision on 2009-10-17
> **tcoffeep said:**
> people go to a store and just buy a computer, yeah. The rest of what you say, though, i have a problem with. Ms doesn't use its leverage to force windows on every system... No. You're wrong, there. Generally, the computers sold to consumers work. And they generally work with very little wrong with them. With linux, they'd need to do this, and do that, and do this and that. Mind you, not always. Sometimes it really does **just work**(tm)... Just not very often.
People don't care what they use because what they use generally doesn't cause them any freakin' problems. If it did, a google search would give them every answer. Here's the really awesome part : Some people know there are *free* alternatives, but don't give a **** because they like supporting what they use. Freakin' crazy people, these days.

You know, i told my girlfriend's father about openoffice. He tried it, said it was ****, and reinstalled microsoft office. So, no. It's not misinformed people, all the time. It's called preference and taste.

Have a nice day.

-dex

+1

---

### Post by Penguin Guy on 2010-04-17
> **RiceMonster said:**
> It's true. I know a bunch of Linux users in real life and they're all involved in IT either through work or school.
Funnily enough, I know two people who use Linux in real life, and neither of them has anything to do with computers.

---

### Post by jrusso2 on 2010-04-17
Its not good enough.  Also there is no Microsoft Office, Adobe Photoshop or anything thats near as good as the applications people want on Linux.

---

### Post by jkxx on 2010-04-17
But what's "good enough"? Is it good enough if it has a functional desktop (check), multimedia capabilities (check), and internet connectivity (check)? Or are you talking about the less than ideal 3D experience - thanks to binary blobs and lack of support from various hardware vendors?

I'll dare guesstimate that most (or many?) people who think Photoshop and Office are the best haven't tried much else.

Here's why I think Linux isn't as popular as it could be:

1) External factors: Microsoft, Adobe, and the other big offenders. These companies have a habit of putting out closed-sourced software with little or no support on platforms they don't like. And then they go and patent things to prevent compatible clones from emerging. With such a hostile gang of big corps giving Linux (and other FOSS efforts) a hard time, the end result is not too surprising.

Oh and there's the hardware vendors that either release binary blobs only (hey Nvidia!) or don't even bother to make drivers for anything but Windows.

Linux has been responding to these with a 'best effort' solution and it's done quite well but there's only so much the devs can do in a situation like this.

2) Internal factors: Lack of compatibility and disorganization, particularly a Linux-centric problem. Currently there is no way to make one binary and have it work across different releases of one distro, much less across different distributions. There's a band-aid fix in the form of package managers and they help but the basic issue still stands. If you're a developer you must roll out a separate package for every distro you want to support. If you are a user, you must hunt down the build for your distro and hope one exists in the first place. Linux needs a common standard for executables and such. Even with DLL hell Windows is ahead here.

I probably missed something but this should be enough for a start.

---

### Post by Penguin Guy on 2010-04-17
Just had another though - branding (I'm looking at you, gimp :x).

---

### Post by jflaker on 2010-04-17
> **Penguin Guy said:**
> **In a nutshell:** There are too many variations, and although Linux has very good package management systems, it isn't enough.

There is only ONE Windows....Different levels of windows, but that is artificially crippled based on what you pay for.

I live variety.  It creates a bit of competition and makes for a better overall product (talking about actively developed distributions)

It isn't popular because there isn't millions of dollars in advertising available otherwise, Linux would be a consideration for the average user..

IBM has advertisements, but I haven't seen them except for on youtube.[URL="http://www.google.com/search?q=ibm%20linux&oe=utf-8&rls=com.ubuntu:en-US:official&client=firefox-a&um=1&ie=UTF-8&tbo=u&tbs=vid:1&sa=N&hl=en&tab=wv"]
http://www.google.com/search?q=ibm%20linux&oe=utf-8&rls=com.ubuntu:en-US:official&client=firefox-a&um=1&ie=UTF-8&tbo=u&tbs=vid:1&sa=N&hl=en&tab=wv[/URL]

I specifically like this one
[http://www.youtube.com/watch?v=KwEWxpOWOok]("http://www.youtube.com/watch?v=KwEWxpOWOok")
:lolflag:
and this one
[http://www.youtube.com/watch?v=0JqtMgiUaf4]("http://www.youtube.com/watch?v=0JqtMgiUaf4")

---

### Post by Odd-rationale on 2010-04-17
I think you have a valid point.

If a third-party software company wanted to support Linux, they would have to create .rpm's for Fedora and SuSE, and .deb's for Ubuntu and Debian. And maybe even others.

In addition, they would have to test it on all distributions they packaged for. Most don't have the resource to do so. What ends up happening is the app performs poorly (or sub-par) on Linux.

Take Google's Picassa for Linux, for example. It is simply the Windows version bundled with Wine!

By being so spread out, we have made it difficult for these company to support Linux the way they do Windows and Mac OSX.

Maybe it is about time we had one Linux distro? I really don't care if it ends up being Ubuntu, Fedora, openSUSE, or whatever. Because if we all synchronized our efforts together, I am sure that *that* distribution would be the best.

---

### Post by mspmsp on 2010-04-17
Love the new Ubuntu
Most popular, well...

I think it is still geeky, which I enjoy messing about with that stuff
but , no way would I allow my non tech family members to use it, unless I disconnected the phone, and didn't check my emails

Its lovely, and great, but technical

Ubuntu 10.04 is much easier to use. May never go back to windows 7
:KS

---

### Post by jflaker on 2010-04-17
> **Odd-rationale said:**
> I think you have a valid point.

If a third-party software company wanted to support Linux, they would have to create .rpm's for Fedora and SuSE, and .deb's for Ubuntu and Debian. And maybe even others.

In addition, they would have to test it on all distributions they packaged for. Most don't have the resource to do so. What ends up happening is the app performs poorly (or sub-par) on Linux.

Take Google's Picassa for Linux, for example. It is simply the Windows version bundled with Wine!

By being so spread out, we have made it difficult for these company to support Linux the way they do Windows and Mac OSX.

Maybe it is about time we had one Linux distro? I really don't care if it ends up being Ubuntu, Fedora, openSUSE, or whatever. Because if we all synchronized our efforts together, I am sure that *that* distribution would be the best.

I think that Ubuntu should support (and that would be, supporting it "Out of the box") all Linux software distribution methods....It would make Ubuntu THE distribution to use.

---

### Post by aysiu on 2010-04-17
> **jrusso2 said:**
> Its not good enough.  Also there is no Microsoft Office, Adobe Photoshop or anything thats near as good as the applications people want on Linux.
Not everyone can use Linux as their main OS, but there are more people who *could* use Linux for all they do than who actually *do* use Linux.

Application support is not the only issue or even the main one.

---

### Post by MisfitI38 on 2010-04-18
> **Penguin Guy said:**
> **In a nutshell:** There are too many variations, and although Linux has very good package management systems, it isn't enough.

Okay, first off I would like to say how much I love Linux - it opened up a whole new world in computing for me (BIOS, partitions, filesystems, and a whole lot more). However we all know it is not the most popular operating system - but exactly why isn't it? I believe it has quite a few main problems, mostly relating to incompatibility with itself:
[LIST]
[*]There are multiple installer package types (.deb, .rpm, .tgz, etc) - this means that packages are not very compatible between distributions.
[*]Programs handle stuff they shouldn't (Gnome handles the background, Gedit handles syntax highlighting, Firefox handles it's icons, etc) - this makes would-be-simple tasks such as setting the background or changing syntax coloring hell for programmers, and therefore such programs tend not to be very compatible between desktop environments.
[*][Settings are spread across different systems (/etc/default, gconf, etc)]("http://ubuntuforums.org/showthread.php?t=1381140")
[*]Branding: Ubuntu (most people I've talked to think it sounds weird), the Gimp (is this a joke?), and more
[/LIST]
I admit that one of the main reasons why Linux is not very popular is because of Windows' monopoly, but it *is* partly because Windows is better for the average user. What does everyone else think?

You are absolutely correct. However, I don't really mind that GNU/Linux is a niche OS and that each distro is a niche-within-a-niche.
I don't feel the need to advertise it, nor do I think that anyone is really missing out on anything by choosing another system.
It's just an OS.

---

### Post by Penguin Guy on 2010-04-18
> **MisfitI38 said:**
> You are absolutely correct. However, I don't really mind that GNU/Linux is a niche OS and that each distro is a niche-within-a-niche.
I don't feel the need to advertise it, nor do I think that anyone is really missing out on anything by choosing another system.
It's just an OS.
Hmm, good point, but I was thinking along the lines of hardware support - the more people who use Linux, the more drivers we'll have. Of course there are disadvantages as well, such as viruses, more help threads on the forums, etc.

---

### Post by 133794m3r on 2010-04-18
i'd love to have just one type of package for the files .deb, .rpm, .whatever i'd love for it to just be one.

If we're able to do that, there comes GNU/Linux being popular. Fix it, and it's done we've just tackled the NUMBER ONE biggest problem that software companies face when setting up a GNU/Linux version of their product. Now the second thing is that a lot of software companies feel that GNU/Linux users won't pay for software that they want everything to be FOSS so they don't see a reason to even attempt to make their product for them.

If we can somehow, get away from this image that we are willing to pay for some commerical apps when there's no real equivalent in the open source world at this time, then we'd have 3rd party commercial apps, that combined with everyone using one type of packages would make it a lot more simple. Gimp is an ok application but it lacks quite a lot of the functionality of Photoshop, and that seems to be the #1 app from windows that people site as their "i have to have it or i'll never go" application.

GNU/Linux distros band together and do this, i am sure that we shall be able to get everything that GNU/Linux users want.

---

### Post by kwacka on 2010-04-18
because Microsoft was there first, and used unethical sales techniques and underhand business practices to develop a virtual monopoly.

E.g. dealers HAD to sell Microsoft operating system with every computer sold, or they didn't get discounts.

Many schools still have to buy a MS license for every computer (including Macs) whether it runs MS or not.

Advertisments HAD (have?) to carry the '**** recommends Windows' stickers - or again no discounts.

Stealing other developers products e.g. Stac Electronics allowed MS to look at their 'Stacker' disk compression. Stacker refused their offer (we'll put it in DOS 6 and not pay you - being associated with us is great advertising for you) and found that MS's 'Drivespace' in DOS 6 used their algorithms. MS lost the case, but counter-sued (and won) because Stac had broken the EULA terms by reverse-engineering the code to find their work.

As L. Torvalds once said "Bill Gates can't tell me anything about computers and I can't tell him anything about business".

---

### Post by utnubuuser on 2010-04-18
I think linux is not the most popular OS because it's yet not commonly available pre-installed, and the vast majority of users have no clue it even exists.

---

### Post by swoll1980 on 2010-04-18
> **tcoffeep said:**
>  MS doesn't use its leverage to force Windows on every system... no.

That's some mis information if I ever seen any. Microsoft is notorious for using their leverage to force manufacturers into excluding other OSs and software from their machines. This is a fact, not an opinion. They have been found guilty of monopolistic business techniques several times in several countries. Say what you want about Microsoft, or Linux, but lets not pretend that the average user ever had a choice. You and Bill Gates would be the only two people in the world that believed that. The reason MS "works so good" is because the machines are built, and designed by companies that support a Windows environment, even then it's hit or miss half the time.

---

### Post by irishrick on 2010-04-18
I think Linux is catching up with MS.  All my computers are now Linux and I've talked most of my friends into using Ubuntu. If you look at the average user they do nothing to their computer except use it.  when they have problems they go to someone else to have it figured out so if you put Windows or Linux on for them and they can do their mail, surfing and messaging they are happy. I find the Linux machines I look after take up less of my time than the Windows machines I used to look after.  Without the threat of virus' or ad-ware there is far less to go wrong.

---

### Post by Shining Arcanine on 2010-04-20
> **Penguin Guy said:**
> There are multiple installer package types (.deb, .rpm, .tgz, etc) - this means that packages are not very compatible between distributions.

You can fix this by switching to a variant of BSD. Take your pick:

[http://www.dragonflybsd.org/](http://www.dragonflybsd.org/)
[http://www.freebsd.org/](http://www.freebsd.org/)

---

### Post by Meep3D on 2010-04-20
> **utnubuuser said:**
> I think linux is not the most popular OS because it's yet not commonly available pre-installed, and the vast majority of users have no clue it even exists.

This is actually a myth.

Windows 7 was beta'd early last year and showed a steadily increasing trend and surpassed Linux usage shortly after the release of RC1.  This is a pre-release OS that was not being sold or advertised by Microsoft.

Surely the people who were downloading and demoing Windows 7 are exactly the sort of people who are aware and capable of running Linux - especially so once you consider the LiveCD angle?  Yet over the last five or so years Linux has only seen an increase of ~50% in userbase (and is still hovering around the 1% mark).

Also I seriously doubt the 'lack of advertising' angle as just about anyone who is interested in tech on the internet has no doubt heard of Linux multiple times - in fact just about every single review of Windows 7 has people advocating Linux in the comments section.

---

### Post by Penguin Guy on 2010-04-20
> **Shining Arcanine said:**
> 
[QUOTE=Penguin Guy;8114563]There are multiple installer package types (.deb, .rpm, .tgz, etc) - this means that packages are not very compatible between distributions.


You can fix this by switching to a variant of BSD.[/QUOTE]
And BSD uses; **yet another** package type.

---

### Post by WinterMadness on 2010-04-21
its not popular because it gets in the users way.

I understand why, its mostly security.

Everyday people dont care about that. Whether or not linux users agree that it should be that way is irrelevant. 

Linux has gotten to the point where people who only need basic things would have the compatibility they require. Now it needs to be as user friendly. Ubuntu seems easy to us. However to someone like my mom, it would seem that the OS either doesnt work or its simply fighting you tooth and nail for every action.

She will not EVER go into the command line. Its  out of the question. Not even to turn into root

Its not far fetched to say many other people feel the same way. In fact, I know plenty

The linux community should at least try to provide a system for these kinds of people.

---

### Post by cespinal on 2010-04-21
My opinion: Lack of good ol corporate massive marketing campaigns...
Dats all

---

### Post by asddf on 2010-04-21
Social media is Ubuntus biggest chance, Facebook, Youtube, Twitter all those ways are Ubuntus biggest chance to making the big time.

People need to join the groups, post information on their accounts really get it out there.

---

### Post by iponeverything on 2010-04-21
> Why Linux Isn't the Most Popular Operating System

Other pressing questions:
- why am I not the centre of the known universe?
- if Doctor Who dropped his pen in a bar, would Gizmodo find it and be able to take it apart?
- is the desktop the only game in the never ending OS popularity contest?

Linux/GPL just is. It exist in parallel universe from commercial software. It can't be bought or sold or put out of business. It exists entirely on its own merits.

---

### Post by scania_gti on 2010-04-21
Popularity of Linux - its job for Microsoft users ;)
Because: more Linux - less price of Windows :D

---

### Post by beast2k on 2010-04-21
One aspect of "why is Linux not more popular than it is" that seems not to get mentioned much is $$$MONEY$$$  Microsoft has billions of dollars invested in this whole software business, they pay billions in taxes, create hundreds of thousands of jobs, last year Microsoft donated more money and resources to charity that Ubuntu and Mr. Shuttleworth ever will in their entire lives and Microsoft will literally do anything to protect their interests and  investment. Sometimes if another company has compatible interests such as Dell computers for example (or suse Linux?) Microsoft will work with this company to further their interests, after all, Dell does not want unhappy customers calling tech support with "how come I can't install [insert software name here] onto my computer" the windows operating system is a lot less troublesome to support. My point is we have no money, certainly not enough money to compete with Microsoft's billions, we as Linux users and developers must understand it will take a major event to unseat Microsoft as the dominant operating system provider to the world. Ubuntu if it grew 10 times larger in every way overnight this would still not even make Microsoft blink. In my opinion without some major event such as complete and total bankruptcy or financial meltdown it will NEVER be possible to make Linux the dominent operating system, The long awaited year of Linus is NEVER going to come EVER and Apple is not powerful enough to do it either that's why they sell ipods and iphones now. As for the OP's original question "Why Linux Isn't the Most Popular Operating System" people do not know what Linux is let alone how to use it just for fun ask somebody at work or school what Linux is and see the response you get, it will take a MASSIVE advertising campaign just to start letting people know what Linux is and nobody has that kind of money for a operating system that produces no financial returns. 
Instead of asking this question over and over again we need a productive conversation about how we can work with company's like Microsoft instead of against them.

---

### Post by Penguin Guy on 2010-04-21
> **beast2k said:**
> Instead of asking this question over and over again we need a productive conversation about how we can work with company's like Microsoft instead of against them.
Rather than asking a question I was putting forward my views (see original post), and seeing what other people thought. As for how we can work with microsoft, see [this]("http://ubuntuforums.org/showthread.php?t=1245159") post (unfortunately it has been locked because of the heated debate).

---

### Post by malspa on 2010-04-21
> **beast2k said:**
> One aspect of "why is Linux not more popular than it is" that seems not to get mentioned much is $$$MONEY$$$  [...] My point is we have no money, certainly not enough money to compete with Microsoft's billions[...]

Good post, beast2k, and good points made.  Perhaps MONEY is the MAIN reason that Linux isn't the most popular operating system!

---

### Post by beast2k on 2010-04-21
> **Penguin Guy said:**
> Rather than asking a question I was putting forward my views (see original post), and seeing what other people thought. As for how we can work with microsoft, see [this]("http://ubuntuforums.org/showthread.php?t=1245159") post (unfortunately it has been locked because of the heated debate).
Sorry Penguin Guy I wasn't referring to you necessarily when I said "asking the same question over and over" I was referring to all of us, Linux users in general. the fact of the matter is we need heated debate it's normally the first step to at least figuring out a direction or goal to work toward, or are we as a community just going to continue on wishing we were the dominant operating system ? One thing is true, whatever we are doing now (if anything) is not working as far as making progress toward at least becoming more popular. Somebody must do something different or things will never change, we need an idea or an edge over the competition.

---

### Post by Penguin Guy on 2010-04-22
I think the main problem is that there are too many distributions, and it's too hard work porting your software to all of them. We need some kind of master-repo' that can automatically port software to all the other repo's. The ability to sell your software would also be a good feature to have if we hope to gain commercial interest.

---

### Post by aysiu on 2010-04-22
> **Penguin Guy said:**
> I think the main problem is that there are too many distributions, and it's too hard work porting your software to all of them. We need some kind of master-repo' that can automatically port software to all the other repo's. The ability to sell your software would also be a good feature to have if we hope to gain commercial interest. That's *a* problem, but I don't see how that could be the *main* problem. After all, you don't have to create packages for every single distribution out there.

There are several easy solutions to this:

1. If your software is open source, provide the source downloadable and let the distributions themselves compile packages to distribute in the repositories.

2. If your software is closed source, you can create packages for the major distributions (that's what [Opera](http://www.opera.com/browser/download/?os=linux-i386&ver=10.10&local=y) and [Skype](http://www.skype.com/download/skype/linux/choose/) do, for example).

3. You can also just create a precompiled binary that isn't nicely packaged but that can run on pretty much any distro (Firefox from the Mozilla website or Google Earth, for example).

If I were a company that didn't want to do that much work, I would create a .deb for Ubuntu and an .rpm for Fedora and leave it at that.

---

### Post by Penguin Guy on 2010-04-22
> **aysiu said:**
> If I were a company that didn't want to do that much work, I would create a .deb for Ubuntu and an .rpm for Fedora and leave it at that.
Exactly my point, we need to help port stuff to the distro's that wouldn't normally get commercial packages (Arch, Suse, etc), because the more users who have access to the product, the more likely it is that companies will bother porting their stuff to Linux.

---

### Post by WolfyAU82 on 2010-04-22
The NT camp are catching on as to what makes a good OS.  Take a look at Windows 7, that is currently the best thing the NT camp (Commercial and Open Source Collective) has to offer.  Whereas the NX (Unix / Linux and all dirivitives) Camp...  Commercially, that would be a MAC.  Open Source, Ubuntu is one of NX's best offerings in my opinion.

---

### Post by prodigy_ on 2010-04-22
The problem is that people, when they speak about IT, easily mix up shiny marketing "changes" in press releases with real, substantial changes in technologies themselves. The latter are few and far between. Despite a very popular belief, IT sphere in a nutshell is **ultra-conservative**. Almost every revolutionary IT innovation that isn't backwards compatible is outright doomed even when the new technology is very progressive.

Just look closely at the history of x86 CPU architecture and you'll understand what I'm talking about.

Linux isn't different at all. In the IT paradigm *NIX systems were exclusively server-oriented for decades. And just 10 years ago the very idea of using Linux on a desktop was laughable. Today, it's still uncommon but many people take Linux seriously now.

Eventually, Linux will get the popularity it deserves. But we need to get rid of the whole stupid "Year of Desktop Linux" concept. Because it's not going to be this way. Changes in IT happen slowly, over **decades**, not over months.

---

### Post by JDShu on 2010-04-22
The reason that Linux is not the Most Popular Operating System, or even a Decently Popular Operating System, is because most people are big noobs who can't use Linux. So we should all feel happy about our intellectual superiority and leave it at that.

Actually, I think the biggest barrier is Microsoft Office and its formats. I can't see this situation changing. Oh well. Open Office being inferior doesn't help either.

---

### Post by Meep3D on 2010-04-23
> **JDShu said:**
> The reason that Linux is not the Most Popular Operating System, or even a Decently Popular Operating System, is because most people are big noobs who can't use Linux. So we should all feel happy about our intellectual superiority and leave it at that.

Actually, I think the biggest barrier is Microsoft Office and its formats. I can't see this situation changing. Oh well. Open Office being inferior doesn't help either.

There is absolutely no correlation between power and difficulty.  If something is hard to use or overly complex it is because the creator lacked the time or talent to make it easier and more approachable.  If something is harder to learn or use it does not automatically mean it is more powerful or 'better' - quite the opposite.

I would say that using something that does the same job as before but is much more complicated than what you are replacing hardly demonstrates 'intellectual superiority'.

---

### Post by Penguin Guy on 2010-04-23
> **JDShu said:**
> The reason that Linux is not the Most Popular Operating System, or even a Decently Popular Operating System, is because most people are big noobs who can't use Linux. So we should all feel happy about our intellectual superiority and leave it at that.
:D Your posts always make me laugh.

> **Meep3D said:**
> There is absolutely no correlation between power and difficulty.  If something is hard to use or overly complex it is because the creator lacked the time or talent to make it easier and more approachable.  If something is harder to learn or use it does not automatically mean it is more powerful or 'better' - quite the opposite.

I would say that using something that does the same job as before but is much more complicated than what you are replacing hardly demonstrates 'intellectual superiority'.
Well actually, most of the time [COLOR="Green"]complex = powerful[/COLOR]. This is because, quite often, simplicity restrains your intelligence. Try using nautilus (simple) to add a [FONT="Courier New"]~[/FONT] to the end of every file on your computer - it'd take years. Now try using the terminal to do it: [FONT="Courier New"]for file in `find /`; do mv "$file" "${file}~"; done[/FONT] - took me about 10 seconds. Complex is (usually) better, the only problem is that you have to put the time in to learn it. I think Linux uses a good balance between simplicity (easy but weak) and complexity (hard but powerful).

---

### Post by Meep3D on 2010-04-24
> Well actually, most of the time [COLOR="Green"]complex = powerful[/COLOR]. This is because, quite often, simplicity restrains your intelligence. Try using nautilus (simple) to add a [FONT="Courier New"]~[/FONT] to the end of every file on your computer - it'd take years. Now try using the terminal to do it: [FONT="Courier New"]for file in `find /`; do mv "$file" "${file}~"; done[/FONT] - took me about 10 seconds. Complex is (usually) better, the only problem is that you have to put the time in to learn it. I think Linux uses a good balance between simplicity (easy but weak) and complexity (hard but powerful).

And if you actually *did that* (and had permissions) your computer probably wouldn't boot.  The only reason that there isn't an inbuilt GUI tool to do it for you is because it's an extreme corner case that virtually nobody would ever need to do.  The fact that you didn't provide an actual practical real world example is telling.

Ultimatley most CLI's are a stones throw from a turing complete programming language, and developers use programming languages to create actual software for people to use.  If a common task is only possible with the CLI then the developers have failed to do their jobs.

Plus 30 seconds on Google gave me [http://www.nonags.com/nonags/fileren.html](http://www.nonags.com/nonags/fileren.html) (for Windows at least) which will do everything that you claimed in your example.

---

### Post by Jpenguin on 2010-04-25
> **tcoffeep said:**
> You know, I told my girlfriend's father about openoffice. He tried it, said it was ****, and reinstalled Microsoft Office. So, no. It's not misinformed people, all the time. It's called preference and taste.

Have a nice day.

-Dex


Most people don't even give the free stuff a chance, the fact is they are afraid of change

---

### Post by MisfitI38 on 2010-04-27
It isn't the most popular, and that is intentional. It is designed *by* computer scientists, software engineers, programmers, sysadmins and hobbyists *for* computer scientists, software engineers, programmers, sysadmins  and hobbyists. 
When are you going to get it.

---

### Post by aysiu on 2010-04-27
> **MisfitI38 said:**
> It isn't the most popular, and that is intentional. It is designed *by* computer scientists, software engineers, programmers, sysadmins and hobbyists *for* computer scientists, software engineers, programmers, sysadmins  and hobbyists. 
When are you going to get it. That's not the intent of everyone involved in Linux:
[https://bugs.launchpad.net/ubuntu/+bug/1](https://bugs.launchpad.net/ubuntu/+bug/1)

When are *you* going to get it?

---

### Post by MisfitI38 on 2010-04-27
> **aysiu said:**
> That's not the intent of everyone involved in Linux:
[https://bugs.launchpad.net/ubuntu/+bug/1](https://bugs.launchpad.net/ubuntu/+bug/1)

When are *you* going to get it?

2004 called; it wants its carrot back.
:)

---

### Post by vexxev on 2010-05-07
It has been said many times before, but people do not use Linux because it is not preloaded (in most places).  Just about every computer that is purchased is preloaded with some version of Microsoft Windows, or in the case of the Macintosh OS X.  The average user is not going to go out of their way to download a CD or DVD image of a Linux distro, burn it, and re-setup their computer.  It really doesn't matter how much better it might be, or how much more secure.  They're just simply not going to go through all that trouble.  If it were the other way around, and Linux was preloaded on the majority of computer being sold than Windows would be in the same boat Linux is in right now (not so much OS X.. Apple is in their own world).  

Hardware incompatibility, software not being cross platform, OS polish, and integration  all comes second to that one simple fact - Windows is already installed; not to mention they've paid for it.

Chances are all the other issues people have with hardware, and software would be next to non-existent if Linux was the OS of choice, and preloaded on all computers.  All of these software titles that people complain about not being available for Linux would have no choice, but to be available.  The question is if Linux was at this point today, would we be where we are right now?

---

### Post by aysiu on 2010-05-07
> **vexxev said:**
> It has been said many times before, but people do not use Linux because it is not preloaded (in most places).  Just about every computer that is purchased is preloaded with some version of Microsoft Windows, or in the case of the Macintosh OS X.  The average user is not going to go out of their way to download a CD or DVD image of a Linux distro, burn it, and re-setup their computer.  It really doesn't matter how much better it might be, or how much more secure.  They're just simply not going to go through all that trouble. I fully agree. Which means the solution to [Bug #1](https://bugs.launchpad.net/ubuntu/+bug/1) isn't "Let's make Linux easier to use" or "Let's improve the interface." The solution is to provide the open source equivalent to Apple.

It would have a lot of the same things Apple has--the ability to try out the computers in the store, hardware and software designed to go together (not just rebranded Asus or Dell laptops), no major hardware regressions in newer versions, a full ecosystem of guaranteed-to-work-together peripherals.

The major thing it would lack that Apple has is lock-in. You could still choose to install Linux on whatever computer you want and work out the issues yourself. But a simple out-of-the-box thoroughly tested and properly marketed physical product would be available to try and purchase.

---

### Post by vexxev on 2010-05-07
> **aysiu said:**
> 

The major thing it would lack that Apple has is lock-in. You could still choose to install Linux on whatever computer you want and work out the issues yourself. But a simple out-of-the-box thoroughly tested and properly marketed physical product would be available to try and purchase.


It wouldn't be a sudden change with droves of users deciding to purchase desktop hardware with Linux as the OS, but slowly Linux would become a real contender in the OS race.  Until the OS is being marked as a real option not just a decision for someone to make after purchasing a computer with a preloaded OS, but marked as a complete computer you can go to a store in your local mall, and purchase today it will not gain a notable percent of the market.  Apple does this (to an extent), and it still has a relatively small share in the OS market, imagine how much smaller it would be if OS X wasn't preloaded on any system, and Apple tried to market it as an after market option to install after you purchase a computer that for all practical purposes already has an OS (Windows) that pretty much accomplishes word processing, banking, web surfing, etc.  Now think of how much larger of a share Apple would have if they opened their OS up to other hardware models (I know they tried clones in the 90s, and it didn't work so well, but this can be managed).  Just as Apple would most likely gain a larger % of the market Linux could do this as well if Linux was opened up to all computers (it already is), and preloaded, and sold that way in stores on a mass level while being marketed in a way that keeps up with marketing of other operating systems (which it isn't).   

This could totally change the way people buy computers if it is done right (not the "buy Linux on an eMachine in the back of Walmart type campaign).  It could change the way the OS market is too, and shift the interest back to hardware if say you didn't have to choose between Apple's EFI Intel boards, and regular BIOS; Linux runs on both, and (hopefully) looks just as good by the time we get to this point as far as the aesthetics of the OS go.  Why buy expensive Apple branded (regular hard drive, RAM, etc with an Apple brand on the outside) systems, when you can buy something for less money with the same specs running an OS which is just as good at this point if not better than OS X?

The world as a majority is going to accept whatever is thrown at them so long as it is aesthetically pleasing to look at, easy to use, stable (or lack there of  when you look back at the OS timeline),  and accomplishes what they need.  No one in their right mind (except for those of us here, and on other forums like this) would even think about downloading Linux because as far as they can tell Windows, and MacOS is already getting the job done for them.  To truly bring open source to the world it has to be more than just here, and available.  It needs to be marketed as complete, and available to the average consumer in a form that they view as being a complete system.

This turned out a lot longer than I expected.  I'm not checking for typos because I'm ready to leave my office for the day.

---

### Post by beast2k on 2010-05-07
It seems that a key component of competing with any other operating system is our unity or lack of it. We as Linux users of all distros are stronger with all the distros united than we ever will be apart. [COLOR="Red"]There must be a way we can have our cake and eat it to[/COLOR], by that I mean have all the different distros and still have one distro to rally around. The general issue of all the different distros and package management systems etc etc is becoming the key element along with financing holding back our progress.

---

### Post by murderslastcrow on 2010-05-07
People expect to walk into a store and buy a computer, and as long as it runs the majority of programs out there (which Linux does- with Wine, you get more applications than available for Windows since you also have the majority of them). And most people would love to have an OS impervious to viruses, and since it's monetarily free, it wouldn't be so big of a deal to distribute it and have people buy Windows separately if they really need it.

Even though Linux is insanely easy to install these days, and to dual boot with, the majority of normal people have never installed an OS, so they think Linux is hard because it requires that step unless you buy online.

The simple fact is that, installing Ubuntu and most modern Linux distributions is by and far easier and faster than any other OS currently on the market. Not to mention you can run the OS and do stuff while it's installing, something no other OS offers.

As soon as Linux ends up on store shelves, even if it's only on netbooks, even if it's only as Google Chrome, it will start to steal away the market.

Many consumers argue that the reason they buy Windows instead of anything else is that they think Windows computers are the cheapest, so they'll deal with the issues so long as they have an OS of some kind, even if they think it's bad.

So having something that costs less and has less issues would be a big deal for most common users. They just have no idea it's out there. Kids listen to what the TV tells them, sorry to tell you. Not all of us are internet researchers.

The best way to get Linux into the mainstream besides using it and showing it to people in a friendly, non-intrusive manner, is to buy hardware from system76, Zareason, and especially DELL's Ubuntu offerings so they can expand them and advertise them more broadly, as well as any local stores that sell Linux goods.

That way it will be more obvious to manufacturers that it's a viable alternative and deserves just as much consideration as the company that keeps pushing them around, who I will not name.

---

### Post by infestor on 2011-06-20
i think the main reason is that windows & mac os users are actually satisfied with their os. so why bother?

---

### Post by DangerOnTheRanger on 2011-06-20
Windows users aren't usually satisfied after they're infected with their 42nd virus... :)

---

### Post by Robynsveil on 2012-02-20
Why? I don't think Linux cares about popularity. Linux users are happy with it (whatever distro they've settle on) and that's all that counts. I don't proselatize Linux: I use it because it works.

And smile quietly when Windows users whinge about system slow-downs, virus attacks, etc. Been there, done that, got the tattoo.

---

### Post by wapicke on 2013-04-16
> **Meep3D said:**
> This is actually a myth.



Also I seriously doubt the 'lack of advertising' angle as just about anyone who is interested in tech on the internet has no doubt heard of Linux multiple times - in fact just about every single review of Windows 7 has people advocating Linux in the comments section.

  Seriously, I didn't hear about LInux, until I seen it on a shelf at Hastings, back in 2000.  About four years later, I bought a copy, from the same store.  The only advertising that is seen in such tech forums, is those that are sought after.  Search engines automatically assume you want info about Windows, and custom builds your queary based on that assumtion.

---

### Post by cbeal5816 on 2013-08-01
Quite frankly, most people are too lazy and/or scared to try Linux.  Every computer they have ever owned has been loaded with Windows and they only do what they are told that they are allowed to do.  Honestly, I love Linux simply because I can do what I want to do.

---

### Post by RadicaX on 2013-08-02
No rule against Necro posting in these forums? Quite plainly, for me, and what I have seen, you get one person that can not use Itunes on Linux, then said person goes telling all the people, never get Linux it is horrible. They only do Email, Websurf, study, and youtube. Xubuntu has met all their needs. Probably help if they looked for programs to use, they do not though. (again, why would you, if all the stuff you needed was met?) Another family, they did not want Linux period, till their computer got some kind of set of viruses that prevented Windows from setting up. I just popped Linux on, and they loved it! Back in the Day, When Ubuntu was still like 7.04 or something, and I was a kid, I got a liveCD and tried it, I loved it, but my family would not have any of it. They were windows fans till they were forced to use Ubuntu, than they liked it after a while. And enjoy not having to worry about Viruses and spyware. 

Quite plainly. people have no clue what an OS/Web browser is, most of them just use whatever they have. Windows 8 for example, many people tell me how disgusted they are by it, but they use it because they have no clue of alternatives. Microsoft most think did something stupid by doing that to computers. (They did. ) But now they are ready for the wave of the future. (hand held computer phones really. ) Their mistake, was they did not have two OSs really going. Linux, it will survive regardless because it is so modular, you can just patch the sucker, boom ready for tablet phones and that is when desktops will be a thing of the past.

---

