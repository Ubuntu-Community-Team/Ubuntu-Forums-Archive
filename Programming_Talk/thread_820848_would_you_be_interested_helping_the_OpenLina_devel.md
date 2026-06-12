---
title: "would you be interested helping the OpenLina development?"
date: 2008-06-06
forum: Programming Talk
---

### Post by madjr on 2008-06-06
well, Openlina is rather new and breakthrough project aimed at **unifying the software install experience in Linux (all versions)**.

Openlina wants to make the **download / installation and usage** of FOSS fast and simple on any platform/distro. 

Something which may have seemed impossible just a year or two ago.

A big problem affecting linux as it has fragmented over time.

hardware vendors are divided in the distros they're using:

Asus = Xandros
Dell = Ubuntu
HP = SUSE
Lenovo = SUSE
Acer = linpus linux
Intel = Mandriva (intel classmate)
OLPC = Fedora
Everex = gOS
etc. = etc....

this big fragmentation of versions is a big problem... for users, software developers and maintainers alike.

It'll bring some order in the distro jungle.

"***Linafy once and run in any distro.***"


find out more at
[http://www.openlina.com/](http://www.openlina.com/)

and forums:
[http://openlina.org/forum/index.php](http://openlina.org/forum/index.php)


the project is at a good point right now but **we need more smart programmers with good ideas and many people to test/request features** (both developers and users).

a Developer kit will also be available.

they will also implement kernel partitioning for Linux hosts, which will allow **near-native performance** if you are already running Linux

Even support for the native package manager.

Apart from that it'll also be cross-platform.

as linux usage grows this project will become increasingly more important.

---

### Post by pmasiar on 2008-06-06
This looks like Holy Grail - so quite possible is not feasible, otherwise people would did it long time ago.

Who from Linux gurus is on board? There are phones and website but no names. Suspicious. Some  private company?

---

### Post by madjr on 2008-06-06
> **pmasiar said:**
> This looks like Holy Grail - so quite possible is not feasible, otherwise people would did it long time ago.

Who from Linux gurus is on board? There are phones and website but no names. Suspicious. Some  private company?

like everything in FLOSS = not enough programmers, testers or maintainers.

[I]**Q: How can I contribute to the LINA project?**
A: LINA is a **community-driven project**. Contributions can include anything from documentation, to bug fixes, to brilliant new features. We will launch the community site at [www.openlina.org](www.openlina.org) in June 2007 when we release the LINA source code.[/I]


their big aim is to promote the usage (ease download and installation) and development of FOSS (make it easier for GPL developers to get their software working everywhere fast and easy).

here's a sample of the software installer they created:
[http://openlina.org/wiki/index.php/LINA_Apps_on_Linux](http://openlina.org/wiki/index.php/LINA_Apps_on_Linux)

[IMG]http://openlina.org/wiki/images/e/ed/Linux-nano-install-screen.png[/IMG]

---

### Post by samjh on 2008-06-06
> **pmasiar said:**
> This looks like Holy Grail - so quite possible is not feasible, otherwise people would did it long time ago.

Who from Linux gurus is on board? There are phones and website but no names. Suspicious. Some  private company?Names are very clear for all to see: [http://www.openlina.com/about.html](http://www.openlina.com/about.html)

The project has been around for a while: [http://www.openlina.org/](http://www.openlina.org/)

They were participants in OSCON 2007: [http://conferences.oreillynet.com/pub/w/58/exhibitors.html](http://conferences.oreillynet.com/pub/w/58/exhibitors.html)

I don't care much for this project.  There are others like Autopackage which has been around longer and perhaps is better supported by developers.  However, research should take place before negative comments.

---

### Post by Alasdair on 2008-06-06
Just what we need for linux, windows style installers. Why would anyone want to go to a website, download an installer and run through 6 steps of an installation wizard when they can just type 'sudo apt-get xyz'. Maybe I'm just not getting it, but it seems like the only real point in this is for running linux apps on windows.

But there's a few flaws even with that:

[LIST]
[*]It seems like it only supports terminal apps/web apps natively.
[*]Anything else (apparently) needs to be ported/modified to work on their LINA layer thingy. Plus GTK is the only toolkit that works. Oh and no 3d.
[*]It currently only supports C and C++ apps...
[*]... which run 2x slower under LINA. ([http://www.openlina.org/faq.html](http://www.openlina.org/faq.html))
[*]They then tell us there is no performance overhead. ([http://www.openlina.org/howitworks/howitworks.html](http://www.openlina.org/howitworks/howitworks.html))
[*]Its GPL'd but apparently they've patented some parts of it. Why? They say we can write apps for it without worrying, but they could sue you for copying it's code. That alone should make the whole thing unattractive for open source programmers. 
[*]They don't seem to have any detailed information on how it actually works. I'd imagine thats what most people would be interested at this stage of the project, but it seems like their website is trying to sell us a free product.
[/LIST]
All in all it just seems inferior to what we have already in linux, and it's limited language and library support means it would probably be easier to just write cross-platform code from the get-go rather than target LINA (which no users will have anyway). Sorry if that all sounded too harsh, but I honestly see nothing to get exited about here.

---

### Post by samjh on 2008-06-06
> **Alasdair said:**
> Its GPL'd but apparently they've patented some parts of it. Why? They say we can write apps for it without worrying, but they could sue you for copying it's code.The project existed before the code was released under GPL.  So obviously it was a proprietary product, and they appropriately patented some aspects of it.  This is not unusual.

Also patents do not operate on the code itself, but the concept or idea behind it.  Code itself is protected by copyright, which in this case is the GPL.  This company needs to clarify where developers and the FOSS community stand in relation to the patent-encumbered parts of the project.

---

### Post by pmasiar on 2008-06-06
> **samjh said:**
> Names are very clear for all to see: [http://www.openlina.com/about.html](http://www.openlina.com/about.html)


I said "linux gurus". No name is obviously recognizable, at least by me :-) even if I do not claim to know many experts, but anyway...

It looks like some proprietary idea did not worked well, and they are trying to salvage it by going GPL. Synaptic is good enough for me :-)

---

### Post by Mr.Macdonald on 2008-06-06
No, if LINA is going to make Linux installers like Windows than I don't like it. The problem with the installers is that, if we go to a site and download it than how can we know to trust it. This could also lead to alot more commercial Linux products (which I completely oppose) by allowing people to go search Google for their desired software and then purchasing the installer.

If we push for a major repository that all linux can use (does GNU already do this??) and all packages are put up there then we will be unified. Back in my Windows days, all the software that i wanted was scattered across the internet. In Ubuntu its all right were i want it.


[SIZE="3"]If I got the whole LINA wrong[/SIZE]

If i misunderstood the Lina goal than i am sorry. But i still don't want Windows style installers. Maybe a nice GUI configure tool but not installers.

---

### Post by madjr on 2008-06-07
> **samjh said:**
> 

I don't care much for this project.  There are others like **Autopackage** which has been around longer and perhaps is better supported by developers.  However, research should take place before negative comments.

it's not the same as autopackage. It'll be better integrated with the system.

most of the time i used autopackage it didn't work.

and there been barely any updates or progress for over a year. I hope they are not dead..

still they seem to focus on similar goals, so competition might be good.

> **Mr.Macdonald said:**
> 


[SIZE="3"]If I got the whole LINA wrong[/SIZE]

If i misunderstood the Lina goal than i am sorry. But i still don't want Windows style installers. Maybe a nice GUI configure tool but not installers.

yea i would say you got it wrong.

it will be **integrated with the package manager**.

will be same as **.debs** , but universal.

> **Mr.Macdonald said:**
> 
If we push for a major repository that all linux can use (does GNU already do this??) and all packages are put up there then we will be unified.

that would be ideal but may never happen, not only the software in linux is fragmented, the minds too. Every distro just wants to dominate and do stuff their way even if that means "reinventing the wheel".

with Openlina an "universal repository" may be possible.

this is why they need people to give feedback and ideas, so they can add them to the roadmap (if these are realistic of course)

---

### Post by madjr on 2008-06-07
> **samjh said:**
> The project existed before the code was released under GPL.  So obviously it was a proprietary product, and they appropriately patented some aspects of it.  This is not unusual.

Also patents do not operate on the code itself, but the concept or idea behind it.  Code itself is protected by copyright, which in this case is the GPL.  This company needs to clarify where developers and the FOSS community stand in relation to the patent-encumbered parts of the project.

i think this answers the patent

[I]**Q: What license is LINA released under?**
A: The type of license you need depends on how you plan to use LINA. If you simply wish to run code packaged for LINA, the LINA platform is available under the GNU General Public License, Version 2. If you wish to use the LINA programming libraries and the LINA compiler to create applications that run on our platform, LINA is also available under the **GPL**, as long as you make any code you write using our tools available to the public under the terms of the GPL. **If you wish to create LINA applications without making your source code available to the public, the LINA programming libraries and compiler may be used under the terms of our commercial license.** Please contact us directly for more information.[/I]



they push for FLOSS

---

### Post by madjr on 2008-06-07
> **Alasdair said:**
> Just what we need for linux, windows style installers. Why would anyone want to go to a website, download an installer and run through 6 steps of an installation wizard when they can just type 'sudo apt-get xyz'. Maybe I'm just not getting it, but it seems like the only real point in this is for running linux apps on windows.

But there's a few flaws even with that:

[LIST]
[*]It seems like it only supports terminal apps/web apps natively.
[*]Anything else (apparently) needs to be ported/modified to work on their LINA layer thingy. Plus GTK is the only toolkit that works. Oh and no 3d.
[*]It currently only supports C and C++ apps...
[*]... which run 2x slower under LINA. ([http://www.openlina.org/faq.html](http://www.openlina.org/faq.html))
[*]They then tell us there is no performance overhead. ([http://www.openlina.org/howitworks/howitworks.html](http://www.openlina.org/howitworks/howitworks.html))
[*]Its GPL'd but apparently they've patented some parts of it. Why? They say we can write apps for it without worrying, but they could sue you for copying it's code. That alone should make the whole thing unattractive for open source programmers. 
[*]They don't seem to have any detailed information on how it actually works. I'd imagine thats what most people would be interested at this stage of the project, but it seems like their website is trying to sell us a free product.
[/LIST]
All in all it just seems inferior to what we have already in linux, and it's limited language and library support means it would probably be easier to just write cross-platform code from the get-go rather than target LINA (which no users will have anyway). Sorry if that all sounded too harsh, but I honestly see nothing to get exited about here.


you got wrong some concepts. But am no expert or part of the dev team.

you can ask the developers themselves at their forum
[http://openlina.org/forum/index.php](http://openlina.org/forum/index.php)

about the performance, they will implement kernel partitioning for Linux hosts, which will allow **near-native performance** if you are already running Linux

also, **sudo apt-get xyz**, has some **problems** that are getting increasingly noticable. Specially the Repo freeze on each version.

here is an example of my situation:
[http://ubuntuforums.org/showpost.php?p=5127017&postcount=230](http://ubuntuforums.org/showpost.php?p=5127017&postcount=230)

anyway, if You didn't ever had a similar issue then it's understandable that you don't support it or have the correct concept.

the target of Lina is not really current linux savvy users (us geeks). It's target is windows users who just purchased a linux powered computer or device (i.e. netbooks).

it's a project aimed at linux's future, so it's still under heavy dev. More choices and solutions is always better than none.

it will make the life or average joe, mom and pop easier. Even if all 3 are running different linux versions.

Not everyone uses ubuntu. In fact is not even pre-installed on any of the popular netbooks... yet.

---

### Post by samjh on 2008-06-07
> **madjr said:**
> it's not like autopackage. It'll be better integrated with the system.

most of the time i used autopackage it didn't work.

and there been barely any updates or progress for over a year.

still they seem to focus on similar goals, so competition might be good.

Autopackage released 1.2.5 last month.

It's true that Autopackage has issues.  But if Lina aims to create a decentralised packaging and distribution system, it will have similar issues, not all of which is technical.  Politics has a heavy hand in the fragmentation of Linux packages.

---

### Post by madjr on 2008-06-07
> **samjh said:**
> Autopackage released 1.2.5 last month.

It's true that Autopackage has issues.  But if Lina aims to create a decentralised packaging and distribution system, it will have similar issues, not all of which is technical.  Politics has a heavy hand in the fragmentation of Linux packages.

they released an update :confused:

wow thats good to hear. For many months they seemed dead and their website has been constantly down, in fact is down now.

---

