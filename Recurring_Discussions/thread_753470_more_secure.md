---
title: "more secure?"
date: 2008-04-12
forum: Recurring Discussions
---

### Post by waggingwabbit on 2008-04-12
I hear that linux is supposed to be really secure or something, like you don't need an anti virus or firewall? is that true? Can't really see these things with your eyes... I've only used ubuntu for a day too, so far I don't really see any advantages over XP. having trouble trying to figure things out, having to type weird things into the terminal alot....why is it so hard to get things working properly? Is ubuntu really any more secure than XP? what advantages does ubuntu offer? so far I see alot of downs...

---

### Post by tamoneya on 2008-04-12
firewalls are still recommended but anti-virus is less necessary.  Some people recommend that linux users still use a virus scanner in order to prevent forwarding on viruses through emails and such.  Linux however doesnt have any viruses "in the wild".  This is primarily because of two reasons. 1) programs do not have root permissions unless they are given explicitly by means of su. 2) There is a much smaller percentage of linux desktops when compared to windows. 

Ubuntu by default though comes with adequate security for a desktop user.  if you are looking to start a server or something you should look into adding more.

---

### Post by Pogeymanz on 2008-04-12
Yes, Linux is much more secure, for several reasons:

1: File permissions. Linux has a different way of handling files than Windows. Windows passwords are much more superficial. Maybe someone else can explain this, as I'm sure I'll say something wrong. All Unix-based operating systems are this way and the file permissions is the main thing that makes Linux viruses an oxymoron.

2: Linux is open source. This means that if someone DOES find a security flaw, everyone can look at the code and figure out how to fix it. When someone finds a flaw in Windows, we have to wait for Mr. Gates's team for figure it out, rather than the whole community.

3: Windows accounts for 90-something% of all desktop computers. If you were going to write a virus, would you rather target 90% of people, or .5%?

4: All the programs you need are in official respositories, so you know that what you are installing is clean. When you go to a website and download their program, you have no way of knowing if they include spyware.

---

### Post by ibutho on 2008-04-12
Everything has a learning curve, so it takes time to master something new. The Unix security model generally makes Linux (and other Unix like systems) more secure than Windows (mainly because of the clear separation of users, groups and not working as an admin by default). There aren't any viruses out in the wild for Linux, but you still have to take the issue of security seriously. You definitely need a firewall and Linux ships with a built in firewall called iptables. You can install GUI frontends such as firestarter or guraddog to configure the firewall to your needs. Another thing you have to lookout for is rootkits. A couple of tools that can help with that are rkhunter and chkrootkit.

---

### Post by tamoneya on 2008-04-12
explanation of file permissions:
***Do not try what is listed in this quote box***
> Windows:  Go into C:/Windows/System32.  Hit ctrl-A delete. 
Linux:rm -rf / 
**DO NOT ATTEMPT THE ABOVE***

You will notice that windows will let you delete important system files since there are no restrictions on your permissions.  Linux however will fail unless you call it with sudo before it.  This is just an example and while this would never happen you should realize that this means that a virus can go an modify any windows file it wants.  In linux this is not true.

again DO NOT ATTEMPT THE COMMANDS IN THE QUOTE BOX

---

### Post by Tom--d on 2008-04-12
Just search in youtube Compiz!

---

### Post by Nathan. on 2008-04-12
I'm no expert myself, but I've read and been told that Linux is much more secure than Windows. I'm pretty sure you do need a firewall in place when using Linux, I use Firestarter myself. I find it surprising that you don't see any advantages compared to Windows. A big one is that everything is free unless you decide to donate, even then it's your own choice. I also like the idea of not supporting corporations like MS, who make shockingly low-quality products. Another biggie is that software is all open-source, so you can change or build upon software and perhaps improve it or have a better understanding of how it works.

Ubuntu installed and now works fine on my computer, I've had no problems so far. I think you'll find that if you put in the effort, you'll prefer Linux to Windows anyday.

---

### Post by djbsteart1 on 2008-04-12
When you first switch you do have a learning curve, but in the end it is worth it.

As for security, there are practically no viruses.spy/ad/mal/ware for Linux so you don't need the standard protection you do with windows, and you do need a firewall, however Linux has one built in which is all you need. Its called iptables. 
As for the terminal, you will find that you will end up doing the things you do in it graphically, just describing something like the help you have been receiving graphically is much harder, as system configurations change. Also, these tasks are often one offs, and with experience you will either learn to love the terminal, or just do them in another way.

Some things that Linux can do are far superior, a good place to look for customization is [www.gnome-look.org](www.gnome-look.org) for gnome of [www.kde-look.org](www.kde-look.org) for kde. Also, if you want to install software easily a good thing to look for are files that end in .deb these are debian package files which are akin to .exe files for windows. This will make installing software that is not in the repository easier.

And if you want to get some windows programs working, install wine, which implements the windows api, allowing them to run. 
For codecs, you might want the w32codecs, for stuff like this, see [www.medibuntu.org](www.medibuntu.org).

Other than this, just give it time, and you will find that Linux is worth the effort, however, if you find that ubuntu does not work for you, there are many other choices, a good place to look is [www.distrowatch.com](www.distrowatch.com). Or for discussions on them, the other os talk section of this forum is very good.

---

### Post by waggingwabbit on 2008-04-12
@Nathan
I really don't want to support the corporate either, but everything just seems to be made for windows...

I don't know how to modify these things though...it sounds really complicated. How do things get made to be compatible with ubuntu anyways? do we have to rely on regular people from the ubuntu community to do that?

------------------

so ubuntu isn't affected by viruses cuz they need to be run manually by the desktop owner? what about the possiblilty of being hacked or something where people can see what you do or have on the computer? is torrenting any safer on ubuntu? o.o 

how do i really learn how to use the terminal? so far I've been trying to get my tablet to work right, then my 3D to work (which still doesnt work) and trying to regain my sound which i somehow lost...All I'd been doing is typing things in that I've read on websites and not completely understanding exactly what or why I typed something in, and also some extra options/commands available...

---

### Post by djbsteart1 on 2008-04-12
The terminal will come with time, as for the packages, some are by the community, some are by companies like mozilla or limewire. When you talk about converting things from windows, its more that they were written for Linux as well. However programs written for windows can be run through wine. 
Part of using Linux is the community that goes around it, This is what makes it so special as well as the benefits that come with a more advanced system. I hope you manage to get your problems solved. 

The best way is to post in the forums, as there are so many users, most problems have answers already.

---

### Post by JoshuaRL on 2008-04-12
A couple of things about security:

[This is probably the best information on Ubuntu Security on the forum right now.](http://ubuntuforums.org/showthread.php?t=694198)  Now, that may change since we just got a Security Team, but it's still really good information.

Ubuntu and Linux are more secure by design and by style.  By design with the limited user access.  To get a virus to run on a standard Linux computer you'd need to get the user to:
1).  Download the malware
2).  Make executable
3).  Enable temporary root priviledges
4).  Run the malware.
That leaves malware and exploits almost purely to the realm of social engineering.

As far as it being secure because only ~1% of desktops use is, that is a falsity.  Most servers (and thereby most of the important information in the world) is run off of a Linux OS.  If there were a lot of exploits in Linux, even if only ~1% of desktop users were using it, you better bet crackers would be after Linux.  No question.

But it isn't unsecure.  Thousands of eyes look over the code and submit bugs and fixes.  The last major security flaw in Ubuntu was solved in less than 48 hours.  Microsoft is more around the weeks-to-months timescale.  All of this adds up to an OS that has no malware in the wild, and much less than 100 ever in existence.

And here's the problem with rootkits.  You need root access to install a rootkit.  So if you already have root access, then why mess with a rootkit?  Why not just take the info off of the computer and make it a zombie?  And if an OS has little to no vulnerabilities to exploit, how are you going to get root access?  Again, the attack vector being social engineering.

But your best security doesn't come from letting others make patches for you, its being informed.  Especially since the #1 attack vector for Linux must needs be through you.  [This link will help you learn about the terminal.](http://www.linuxcommand.org/)  Really good info there.  And if you're not sure about a command, ask here.  Wait for confirmation, and Google it.  Being informed is your best defense.

---

### Post by RTrev on 2008-04-13
> **waggingwabbit said:**
> I hear that linux is supposed to be really secure or something, like you don't need an anti virus or firewall? is that true? Can't really see these things with your eyes... I've only used ubuntu for a day too, so far I don't really see any advantages over XP. having trouble trying to figure things out, having to type weird things into the terminal alot....why is it so hard to get things working properly? Is ubuntu really any more secure than XP? what advantages does ubuntu offer? so far I see alot of downs...

Well, most of us have broadband these days, and almost all cable or DSL modems include NAT routers, so you're probably covered just in that re the firewall issue.

Linux machines are a very small "attack surface" compared to MS and Apple, so few people bother to write viruses for us.

Linux enforces privileges quite well, so unless someone does something silly like surfing the web from their root account, most exploits cannot work on the Linux machine.

HTH,
Bob

---

### Post by hyper_ch on 2008-04-13
> **RTrev said:**
> Linux machines are a very small "attack surface" compared to MS and Apple, so few people bother to write viruses for us.

I disagree with that... numbers of installation doesn't equal to malware on it

---

### Post by djbsteart1 on 2008-04-14
> **RTrev said:**
> Well, most of us have broadband these days, and almost all cable or DSL modems include NAT routers, so you're probably covered just in that re the firewall issue.

Linux machines are a very small "attack surface" compared to MS and Apple, so few people bother to write viruses for us.

Linux enforces privileges quite well, so unless someone does something silly like surfing the web from their root account, most exploits cannot work on the Linux machine.

HTH,
Bob

As has been said above over 70% of servers are on linux, and this is what the real hardcore viruses would go for, so user base has nothing to do with it.

---

### Post by SunnyRabbiera on 2008-04-14
Trust me though Linux has come a long way over the last few years, these days the terminal isnt as needed as it used to be.
as for linux being more secure then windows... you bet!

---

### Post by RTrev on 2008-04-14
> **djbsteart1 said:**
> As has been said above over 70% of servers are on linux, and this is what the real hardcore viruses would go for, so user base has nothing to do with it.

Well, I'm thinking of the huge botnets.  A friend watched the traffic Storm was producing, and concluded tentatively that it looked like the guy was spending the first few days of each week replacing bots he had lost, and then for the remainder of the week he was renting out the fleet to the highest bidder.  Seemed logical.  Probably how most of the big criminal botnets works.

Now we all know Linux machines are more secure than Windows ones, but if a larger percentage of people began running Linux don't you think these bot herders would focus their devious minds of ways to compromise them?

Linux itself seems very secure, but I have to wonder about all of the add-on junk like Flash, Java, Javascript, the browsers, the number of users who would end up running as root because it was easier in their view, and so on.

I'm not arguing that Linux isn't head and shoulders above inherently broken systems like Windows.. just that we haven't *really* come under attack yet except for the servers.. but I'd argue that they are a different game.  Mostly not run by end users, and so on.

One of the maxims of security is that you can't *claim* security, you have to *prove* it.

Now maybe I'm wrong (it happens often) but if the percentage of Linux machines were to rise to 25% of the market, I'd bet we start seeing exploits aimed at them, and some of the exploits would work.

Bob

---

### Post by hyper_ch on 2008-04-14
> **RTrev said:**
> Now we all know Linux machines are more secure than Windows ones, but if a larger percentage of people began running Linux don't you think these bot herders would focus their devious minds of ways to compromise them?

Most servers run linux and the servers would be much more interesting that home computers...  because they are on the big pipes and because they have also business secrets...

So, how comes linux servers don't get hijacked this often? Because even if you manage to find a security issue in an application you still are very limited... by default if you can find a loophole on windows you own the whole machine...

So while the benefits of owning the linux servers would be a lot more rewarding it seems that the "return of investements" on owning windows are much larger...

So, even if there was a larger userbase on linux by owning just one application you still are far away from owning the whole computer and so it's not worth the effort as long as there are so many easy preys out there.

---

### Post by RTrev on 2008-04-14
> **hyper_ch said:**
> 
So, how comes linux servers don't get hijacked this often?

Good points, Hyper.  Do we have any solid data about how often they *do* get hijacked?  A quick search didn't turn up much in the way of that.

Thanks,
Bob

---

### Post by hyper_ch on 2008-04-14
> **RTrev said:**
> Good points, Hyper.  Do we have any solid data about how often they *do* get hijacked?  A quick search didn't turn up much in the way of that.

Thanks,
Bob

Search M$.... they will publicate hijacking of Linux servers in order to demonstrate how bad those are ^^

---

### Post by djbsteart1 on 2008-04-15
True about the servers, and yes it will be interesting to see what happens when the market share increases. I agree that exploits will be seen, but I doubt that they will be Linux's fault. And even if there are exploits anywhere in any Linux code, I'm sure the devs will be able to stay on top.
Also, the servers are where real attacks go, the ones on desktops are just trying to be annoying. So I would guess that we would know about it if there were problems in the servers. Microsoft would have let the world know by now.

---

