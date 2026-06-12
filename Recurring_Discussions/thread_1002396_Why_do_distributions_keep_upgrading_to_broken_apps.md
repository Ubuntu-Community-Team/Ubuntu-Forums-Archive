---
title: "Why do distributions keep upgrading to broken apps?"
date: 2008-12-04
forum: Recurring Discussions
---

### Post by JKBurton on 2008-12-04
First the good news: After using Linux for years on the household server (used Redhat, Mandrake, Suse, switched to Ubuntu at Dapper), Ubuntu and I have finally reached the point where I'm eliminating Windows from all 6 of our household computers. And it feels good. Really, really good :)

But, there's something that's confused me for all 7 years of my Linux experience. Every single release of every distribution I've used will contain a few apps that have some significant previously-working feature that's now broken. 

The current one nagging at me is how Intrepid's Gnome won't save sessions. Now, Canonical uses saved sessions as a marketing point and this was a known bug, but some person there apparently decided it's more important to be on the latest release of Gnome than it was to have that working. Can anyone explain to me why that wasn't a bad decision?

And what were the Gnome developers thinking? Do they really not know that taking an existing function away is far more frustrating for the users than not getting a new one implemented? Do they not care, do they not do functional regression testing, or what?

I'm not flaming here, just hoping for a real explanation. I've been in IT over 30 years; been a developer, been a development team leader, and managed an app testing unit. When I look at the source code, it's clear many of these devs are better than I ever was. Yet in my entire career, I only delivered an app with this sort of bug one time, and I was EMBARRASSED! And not because my boss was upset, because it was unprofessional.

Please don't reply telling me to use lts versions, install down-level versions of packages and such. In my experience, Ubuntu lts has the same problems, and I know how to downgrade my packages. I just honestly do not see why this happens in the first place, and want to understand. Since I'm retired now, maybe I could even help out as a tester or something.

Thanks!

---

### Post by 3rdalbum on 2008-12-05
I will agree with this 100%. Don't break functions that were previously working! If you are removing features to streamline the program, reimplement the features if people complain! If you accidentally break a feature, then fix it and re-release as soon as you can.

To use a very small example, I wrote a program to deal with content on Sony Walkmans. It has had three different iterations. The first iteration was basic and dealt with video only. The second iteration added plugins and audio encoding. The third iteration removed the plugins and audio encoding and nobody complained, so I left them out. It did however introduce an incompatibility with some versions of ffmpeg that caused things to silently not work; as soon as I was notified of this problem, I fixed it and re-released.

Sure, my program is tiny compared to a full desktop environment like Gnome. But then, it has loads of developers and massive numbers of users who test these things and report bugs and regressions.

A similar thing that bugs me is when distributions decide to rip out and replace essential or headline applications. Ubuntu 6.06 introduced Beagle as the desktop search agent, to much fanfare.. During the development cycle for 7.04, Beagle was replaced with Tracker, and then Tracker became the headline feature.

Even worse is the situation with the printer setup program. Ubuntu 7.10 and earlier had a lovely, elegant, intuitive, incredibly Gnome-like program for adding printers. Ubuntu 8.04 replaced it with a complicated bohemoth created by Red Hat. Ubuntu 8.10 updated to a new version of the Red Hat program, that seemed to be a complete rewrite and bore little resemblence to the earlier version. It makes it impossible to help other users with their problems if every version of Ubuntu has an entirely different program for a particular function, because you have to remember three different interfaces and what versions of Ubuntu each interface has!

(Yes, I now use the CUPS web interface, which looks dated. I like that, it means that it hasn't changed every six months.)

Then there was Screens And Graphics. People wanted something like it for years, and finally Ubuntu developers write one. It's introduced in Ubuntu 7.10, and doesn't, er, work. Never mind, it works well enough in Ubuntu 8.04. The developers never updated it for the changes in Xorg, and it's not available for Ubuntu 8.10.

Give us some consistency please!

---

### Post by Tamlynmac on 2008-12-05
3rdalbum
JKBurton

Both of you have been members of the forum for quite a while and should know that the developers don't use the forum. Complaining on the forum with regards to development is fruitless. Should you really wish to either get involved or complain, I suggest you contact Canonical directly.

---

### Post by exploder on 2008-12-05
I agree with the original post. I wish I could say that reporting bugs helped to improve things but it has become almost pointless. I am not complaining, well maybe a little.:D

It is frustrating to find that new releases have less functionality than previous releases. Hardware that worked just fine before, no longer works and the same goes with applications. Using the previous release leaves the user "out in the cold" if they want updated applications to run in a previous release. 

What good are new features that do not work? One thing that has an impact on releases is that everything used to build the new release is at different stages of development. How do Ubuntu Developer's impact the development process? What do they actually develop is what I really want to know? Every bug report has the same answers: "we are a small group of developer's", "we can not fix everyones favorite bug", (My personal favorite response, "this is an upstream bug", you get the idea.

Sometimes things come together and a release is pretty good. Gutsy and Hardy were pretty nice releases, that is after a little time passed and things were updated. 

The most difficult thing to understand is why things are left broken through the entire life cycle of a release. It seems like once a new release is out the previous release is forgotten.How many new features have to be added before anything gets fixed? Why aren't newer bug fixed packages ever put into the main repos? Each release has planned obsolescence. (Doesn't that other OS do this?)

I ask these questions because I would like to see Linux used much more wide spread. The current method of development will not meet this goal. Things are just too buggy for large corporations to trust Linux to meet their needs. The company I work for reached that conclusion when they considered switching to Linux. The company was very serous, they were looking to save money. A good example of what they saw was Brasero, it was in the final release of Gutsy and of course did not work properly. Large corporations tend to test everything when they evaluate an operating system, they found too many very obvious bugs. The final word from corporate was that they would look at Linux in a few years and see if it improved. 

The development process has to change. More emphasis needs to be placed on fixing bugs. We have a lot of things in our favor, no viruses, less maintenance, better security, better package management, Live CDs and a better selection of default applications. There are of course more good things than I have listed but there are obvious bugs. Evolution in Intrepid is terrible, Brasero can not handle DVDs without producing errors, system sounds do not all work, floppy drives are no longer supported, xorg can not figure out some monitor resolutions properly and a look in the general forum will reveal many more everyday issues.

The bottom line is quality has to come first. An honest commitment to quality would put Ubuntu or any other distribution on desktops. I am not singling out Ubuntu, all distributions seem to be released with outstanding bugs. How do you get quality standards improved? 

I wish I had answers to give to the original post.

---

### Post by Tamlynmac on 2008-12-06
> exploder
I wish I had answers to give to the original post. 

I'll reiterate - those answers will not be found on this forum. Anyone who has invested time on the forum should know that the developers don't use the forum.

> JKBurton
Please don't reply telling me to use lts versions, install down-level versions of packages and such.

As this statement indicates - some don't wish to address the issue of compulsive upgrading. Yet as with most software, upgrading should only be performed after identifying that the upgrade would actually enhance your system by improving functionality, stability, providing additional benefits and is compatible. IMHO it's the individual performing the upgrade that is responsible for assuring this criteria is met.

No where have I read that "Upgrading is Mandatory".

---

### Post by magmon on 2008-12-06
Well, I started with 8.10 so I cant complain about missing saved sessions, but its certainly a feature Id like to have.

---

### Post by exploder on 2008-12-06
> Tamlynmac 
I'll reiterate - those answers will not be found on this forum. Anyone who has invested time on the forum should know that the developers don't use the forum.

Maybe they should.

Until quality takes priority over release dates things will not improve. The distribution is becoming a "house of cards".

---

### Post by stinger30au on 2008-12-06
well if they didnt and everything worked just randy dandy 100% then no one would have anything to complain about and the fourms would not be here ;)

---

### Post by Tamlynmac on 2008-12-06
> exploder
Maybe they should.

You may wish to contact them and make that recommendation. I agree, that philosophy may have some merit. But like so many other issues in the world - no asked _me_.:smile:

However, IMHO this forum isn't the place to address issues or complaints with the developers. There's no benefit and it's truly non-productive, considering they don't participate. Obviously, directing statements, opinions or complaints at individuals who can't respond - is meaningless.

---

### Post by 3rdalbum on 2008-12-06
I realise that my post sounded like I was addressing it directly to the developers, but I was actually trying to solicit some sort of response from the community such as "Yes I agree" or "No, you're completely off the mark". If most Ubuntu users think the change of programs is necessary, then I'll quietly become a Debianian - in this instance Ubuntu obviously isn't for me. If lots of people agree, then I'll take it to the developers.

---

### Post by JKBurton on 2008-12-06
Yes, I was fully aware this wasn't a developer forum, but there isn't an appropriate one I'm aware of. Any particular distribution or app forum I addressed this to is likely to feel I'm singling them out, and so I'd provoke a hostile reaction. So this was a shot in the dark, to see if I got lucky and got an answer I could use...and also to make sure I didn't screw up my phrasing and say something flame-ish ;)

This isn't a Gnome problem or a Ubuntu problem, it's a problem that seems to be endemic to open source projects generally. Existing features that people have learned to depend on are released broken. It only happens to a tiny percentage of the apps each time, but every release of every distribution I've used (ummm, 15-20?) contains at least one broken pre-existing, important feature that frustrates thousands of people. And more to the point, every distribution has had at least one that frustrated me, personally. 

Bugs in new features are unavoidable. But new bugs in existing features simply should not happen. Because of the way Linux apps are built, typically depending on several layers of underlying libraries and kernel apis working right, proper testing is more important to us than in many other OSes. I always thought assembling all those pieces and testing them together was the distro's job. But I'm wondering now if that was a bad assumption. And in Ubuntu's case, I have no idea how much of that testing should be done by Debian, either.

Tamlynmac, with every release of every distribution demonstrating the problem, I don't see how that's connected to "compulsive upgrading", at least not by the end-users. I only upgrade my installed distributions when there's a bug-fix that's important to me. I do run a fresh install of new Ubuntu releases on a single machine here to decide whether to migrate the others. After all, Linux does keep getting better! But even then I don't upgrade; I wipe the root partition and reinstall. (Last time I tried upgrading an OS in-place to a new release was Windows for Workgroups 3.11, and I swore never again. <grin>)

---

### Post by Tamlynmac on 2008-12-06
> 3rdalbum 	 		**Re: Why do distributions keep upgrading to broken apps?**
 I realise that my post sounded like I was addressing it directly to the developers, but I was actually trying to solicit some sort of response from the community such as "Yes I agree" or "No, you're completely off the mark". If most Ubuntu users think the change of programs is necessary, then I'll quietly become a Debianian - in this instance Ubuntu obviously isn't for me. If lots of people agree, then I'll take it to the developers. 

Obviously, I misunderstood your intent. 
Good Luck Soliciting

---

### Post by exploder on 2008-12-06
JKBurton, what you wrote was very well expressed. I update packages when bugs are fixed, new features are a bonus. I agree that there really is no place to express the views in this thread to the developer's. I have tried in bug reports and in Brainstorm once.

The type of quality and flexibility we are seeking can only come from the top, Mark Shuttleworth himself. The same goes for any distribution. Quality and the ability to update packages in supported releases is possible, I can think of one distribution that has these qualities but I am not a KDE fan. (I bet someone knows what distribution I am referring to.)

We have all seen once top rated distributions drop in popularity and even worse, vanish without a trace. We need all the annoying bugs resolved before adding more features that only half work. I could write a list of obvious bugs and regressions that need attention but we all know what they are. Does Cannonical really think they can ever be profitable with the current state of the OS? If they can't fix the obvious bugs like system sounds and burning DVDs to name a couple, why would anyone want to pay for support? 

Would a large corporation want to run an OS with such obvious bugs on their systems? Probably not. Have you ever compared the cost of Ubuntu support to Redhat and Novell? Ubuntu support is considerably higher and Redhat and Novell have better working products. Both Redhat and Novell add features when they are fully developed and tested to their business models. 

I am trying to illustrate the importance of quality not to bash Ubuntu. The number of non working and bug filled features keeps increasing with each new release. The release notes for Intrepid come right out and tell the user about some of the bugs present! The honesty is admirable but this does not build confidence in the operating system. What would happen if that other OS published similar release notes? What do we as Linux user's say when we find bugs in that other OS?

Quality is everything today, it is what makes or breaks any product no matter what the product is. The Japanese embraced QS-9000 and look what they have done with it! The Japanese buy their materials from other countries, build factories in other countries, produce high quality products and manage to outsell most competitors because they put quality above all else. I use this as an example because i was taught this in Business College and it really drives home the point.

I have worked in a Japanese and American transmission plants. The Japanese clean, vacuum and oil every single part of their transmissions. Every single rivet, spring, bolt, etc, has a dot to ensure it has been checked and each piece can be traced to the employee that was responsible. Make two mistakes and you are fired! The entire plant was climate controlled so rust would not form on any parts and sub assembly rooms are considered clean rooms. The American plant did non of this and defective transmissions were sometimes returned by the hundreds!

The same type of commitment should be applied to computer operating systems. I doubt everything could be flawlessly perfect but things could improve. How do you get anyone to listen?

---

### Post by Changturkey on 2008-12-06
Have every ubuntu user learn how to bugfix?

---

### Post by exploder on 2008-12-07
> Have every ubuntu user learn how to bugfix? 

Some do, that is how I have some system sounds.How does one go about learning to code? Things that work in one release are not transferable to another. The system is built with planned obsolescence.

---

### Post by Bios Element on 2008-12-07
> **exploder said:**
> Some do, that is how I have some system sounds.How does one go about learning to code? Things that work in one release are not transferable to another. The system is built with planned obsolescence.

What....are you going on about obsolescence? That's what the LTS is for...

---

### Post by cardinals_fan on 2008-12-07
Slackware and RHEL/CentOS are the only systems I've found that are consistently stable.

---

### Post by exploder on 2008-12-07
> What....are you going on about obsolescence? That's what the LTS is for...

The LTS release is good but there are never upgraded, bug fixed applications available. Gimp, OpenOffice, Brasero, and others and before you say "backports" the versions there are not current.

I go to getdeb for applications I need newer bug fixed versions of.

> Slackware and RHEL/CentOS are the only systems I've found that are consistently stable.

I completely agree! Redhat slowly adds refined packages. CentOS builds from Redhat's source code so CentOS is also a high quality distribution. Slackware takes a conservative approach as well and are known for quality standards.

---

### Post by 3rdalbum on 2008-12-08
> **exploder said:**
> Things that work in one release are not transferable to another. The system is built with planned obsolescence.

I don't think it's planned obsolescence, it's just a lack of planning that causes programs to jump in and out of Ubuntu as they become "the next big thing".

---

### Post by Darrell Lawrence on 2008-12-10
> **exploder said:**
> 

 Does Cannonical really think they can ever be profitable with the current state of the OS? If they can't fix the obvious bugs like system sounds and burning DVDs to name a couple, why would anyone want to pay for support? 

Would a large corporation want to run an OS with such obvious bugs on their systems? Probably not. Have you ever compared the cost of Ubuntu support to Redhat and Novell? Ubuntu support is considerably higher and Redhat and Novell have better working products. Both Redhat and Novell add features when they are fully developed and tested to their business models. 

I am trying to illustrate the importance of quality not to bash Ubuntu. The number of non working and bug filled features keeps increasing with each new release.


These are some very good points. Redhat has Redhat Enterprise Linux and Novell has Suse Linux Enterprise. These are stable, corporate level versions of Linux. Fedora is a proving ground for features that may get added to to RHEL later. Same for openSUSE and SLE.

Canonical has Ubuntu period. Corporations would probably go for the LTS versions because of the longer support cycle. That said, you have to release a product of enterprise level quality to compete. Same for small business. If you are going to use Linux it has to work very well.

And continuing to add applications that are broke to the latest releases - I just don't see the logic in doing this, whether it's Ubuntu, Fedora, openSUSE, etc. I can see were it would turn off new Linux users. If it's an application known to be broken, why not leave it out of the distribution until it's fixed?

Darrell

---

### Post by Tamlynmac on 2008-12-10
I continue to be at a loss for understanding. Written time and again on this forum is the adage "Use What Works For You", yet many of the ongoing complaints that are typical in this section refer to Canonical. They tend to express their aggression on the forum pointing out the obvious. I find it odd that individuals would rather be critical of Ubuntu on the forum than to address these issues directly with Canonical. I often wonder what the goal is. Is it simply to express their dissatisfaction or is it deliberate in an effort to impact other users?

Should any OS (Ubuntu or any other Linux distro) not meet your expectations or prove dysfunctional on your system, why continue to use it? If you truly wish to assist in the improvement of Ubuntu than logic would suggest you file bugs reports, contact Canonical and offer to get involved. Expressing one's opinion without commiting to or becoming involved in a solution seems nonproductive and I'm not certain would the intended goal is. We all have opinions, solutions on the other hand are more viable and IMHO harder to come by.

---

### Post by VON_CAPO on 2008-12-11
> **exploder said:**
> 
We have all seen once top rated distributions drop in popularity and even worse, vanish without a trace. 

Quality is everything today, it is what makes or breaks any product no matter what the product is. 

I agree. 

Also, I have reached the point where I considerate to give a last try to a real stable distro or give up and to turn back to XP.

But, in the end, it is all about the Linux dependencies chaos = "the dynamic linking system". In theory looks beautiful and functional but in the real world results only in incompatibilities and breakage ... a endless nightmare.

---

### Post by lykwydchykyn on 2008-12-11
As much as Ubuntu gets touted as a "newbie" distro, I wonder what the real demographic of users looks like.  I used to use much more stable (as in using more mature code and longer release cycles) distros like Debian stable or SimplyMEPIS, but I switched to Ubuntu because I'm an impatient person who wants new toys every few months. 

There are downsides either way.  Look at Debian right now: Lenny was supposed to have been out in September, now they are 3 months behind the release date and a release is not in sight.  Why?  Because they have release-critical bugs that need to be fixed.  By the time Lenny goes stable, most Linux users will consider it stale; it will probably mostly get used on servers (that's where I use it).

With something as big and complex as GNOME, is there ever a 100% working release?  I mean, if the next upstream release patches 25 bugs, adds six highly-requested features, but includes 2 regressions -- what do you do as a distro?  Maybe you can backport some of the bugfixes, but probably not the features.  

I think all of this is symptomatic of open development.  If Linux were proprietary software, the "release" would probably be of Debian Etch vintage, and all the cool features we're enjoying in Intrepid and Jaunty would be under wraps.

---

### Post by Darrell Lawrence on 2008-12-11
> **lykwydchykyn said:**
> As much as Ubuntu gets touted as a "newbie" distro, I wonder what the real demographic of users looks like.  I used to use much more stable (as in using more mature code and longer release cycles) distros like Debian stable or SimplyMEPIS, but I switched to Ubuntu because I'm an impatient person who wants new toys every few months. 

There are downsides either way.  Look at Debian right now: Lenny was supposed to have been out in September, now they are 3 months behind the release date and a release is not in sight.  Why?  Because they have release-critical bugs that need to be fixed.  By the time Lenny goes stable, most Linux users will consider it stale; it will probably mostly get used on servers (that's where I use it).

With something as big and complex as GNOME, is there ever a 100% working release?  I mean, if the next upstream release patches 25 bugs, adds six highly-requested features, but includes 2 regressions -- what do you do as a distro?  Maybe you can backport some of the bugfixes, but probably not the features.  

I think all of this is symptomatic of open development.  If Linux were proprietary software, the "release" would probably be of Debian Etch vintage, and all the cool features we're enjoying in Intrepid and Jaunty would be under wraps.

Excellent post. I agree, it's symptomatic of open source development. There's a trade-off where you have rapid innovation with the caveat that there is the chance of less stability. What I was alluding to in my previous post is that Ubuntu with it's 6 month release cycle has to compete against RedHat's and Novell's Enterprise releases in the business world. That said, Canonical offers customized versions of Ubuntu to businesses if they want it.

I certainly hope they (Canonical) are successful and reach profitability in the next few years. 

Darrell

---

### Post by 3rdalbum on 2008-12-12
> **VON_CAPO said:**
> But, in the end, it is all about the Linux dependencies chaos = "the dynamic linking system". In theory looks beautiful and functional but in the real world results only in incompatibilities and breakage ... a endless nightmare.

All platforms, including Windows, have a dynamic linking system. That's what the first DL means in DLL.

The only time there are "incompatibilities" is when you try to use a bleeding-edge development version of a program on an older distro. The only time there's breakage is when you try to bypass the package manager and install all sorts of bleeding edge versions of libraries. In other words, it's not dependency chaos, it's "you're borking your system".

---

### Post by JKBurton on 2008-12-12
> **lykwydchykyn said:**
> I think all of this is symptomatic of open development.  If Linux were proprietary software, the "release" would probably be of Debian Etch vintage, and all the cool features we're enjoying in Intrepid and Jaunty would be under wraps.

I'd wondered about that point myself. The advances in desktop usability the last few years have been amazing. But while it makes sense to me we're always going to have new features that don't work right (particularly on less-common hardware), releasing a product with a preexisting feature broken just confuses the heck out of me.

I'm a power-user and clearly make more aggressive use of more features than a typical desktop user. But my gut feel says I spent more time moving from 7.10 to 8.10 and getting all my "stuff" working again, than I did learning Vista! Gut feelings aren't especially reliable, but if this one's close to true then consistency is way down in "unacceptable" territory.

But at the same time, 7.10 to 8.10 was an awesome improvement. Wine, VirtualBox, and hardware driver issues, for example, are so improved that I finally threw away the ability to dual-boot on our computers*. I also swapped my old VMware Workstation 5.5 for VirtualBox, rather than paying VMware $99 for an upgrade. :)

I guess it's just a trade-off we live with for now. If things don't settle down, maybe later I'll open up the premier OSS regression-testing lab...anybody wanna contribute to my Paypal?  :)  :)  :)

* Fear not, all that Vista training I did wasn't wasted. The more I learned about Vista, the more motivated I was to solve my problems and become "Windows free".

---

### Post by VON_CAPO on 2008-12-12
> **3rdalbum said:**
> All platforms, including Windows, have a dynamic linking system. That's what the first DL means in DLL.

The only time there are "incompatibilities" is when you try to use a bleeding-edge development version of a program on an older distro. The only time there's breakage is when you try to bypass the package manager and install all sorts of bleeding edge versions of libraries. In other words, it's not dependency chaos, it's "you're borking your system".

Let's see a current example:

Ubuntu v8.10 shipped with the library "libv4l-0 v0.5.0-3~intrepid1" causing breakage in the package Cheese (the green screen effect, bug #282473); this has been fixed a few days ago with the upgrade to "v0.5.6-1~intrepid1".

As you can see is not the user, but Ubuntu dev team who injects this kind of packages in the distro.

But, blaming the developers is not fair, the root of all evil resides in how Linux itself manage the libraries... yeap ... "everything is dynamically linked", and is right here where the hell broke loose.  
As soon as one dependency suffers a modification all the related packages are at risk of breakage. 

All of this can be easily avoided using "static linking" **as necessary** (all the required dependencies are already included into the binary package).

Obviously, a lot of opposition will surge, such as:
1- This is not the Linux way.
2- We have Synaptic, a living proof that dynamic linking works! 
3- Static linking is too heavy, the binary file have to include all the dependencies and its size will grow up too much.
4- Static linking is not efficient, if you have 3 static linked packages using GTK+ v2.14, you must load in RAM that GTK+ v2.14 three times, exhausting your RAM very fast.

People, let us be honest.
- Static packages have the real advantage that the motto "just works" will be fulfilled.
- Also, they could be able to run in Ubuntu 6.10, 7.04, 7.10, 8.04, etc; without the permanent necessity of recompilate the whole package every time a new Ubuntu version is released (of course, there will be always exceptions). 
- Today's machines have at least 2 Gigabytes of RAM, far more than enough to run almost any combination of static linked software.
- The excuse of "it is a waste of hard drive space" belongs to some period 20 years ago.
- Low end machines always can use Xubuntu, Synaptic and the official repository.

---

### Post by lykwydchykyn on 2008-12-12
I would think an idea compromise is to offer a system with a current set of packages every 18-24 months.  Then offer statically linked packages for applications that need to be updated.  This way, you only statically link GTK if your app requires features from a newer version of GTK.

Of course, I've tried to take that approach personally before and it doesn't always pan out.  But I think as Linux grows and becomes more accepted by ISV's and mainstream users, we'll see this kind of approach becoming more common.

I'm not a fan of the "computers are fast now, we don't need to worry about efficiency" approach to development.  That's why, with a 3 GHz dual core processor, it takes me just as long to launch an email client as it did 10 years ago with a pentium II.  This is why Vista is missing out on the netbook action.  Linux doesn't need to go that route.

---

### Post by VON_CAPO on 2008-12-12
> **lykwydchykyn said:**
> 
I'm not a fan of the "computers are fast now, we don't need to worry about efficiency" approach to development.  That's why, with a 3 GHz dual core processor, it takes me just as long to launch an email client as it did 10 years ago with a pentium II.  This is why Vista is missing out on the netbook action.  Linux doesn't need to go that route.
I think the idea is that you can take any email client version and make it work at once. Just when you more need it: Now!, without to investigate in a forum for a workaround, or to wait for a fix from the developer.

---

### Post by lykwydchykyn on 2008-12-12
> **VON_CAPO said:**
> I think the idea is that you can take any email client version and make it work at once. Just when you more need it: Now!, without to investigate in a forum for a workaround, or to wait for a fix from the developer.

Well, that's a bit of a false dichotomy; I'm suggesting a compromise between dynamic and static linking, because I suspect that if you created a whole system using static linking, it would run like a cow even on a "modern" system.  I'm simply pointing out that the idea of ignoring the need for efficiency on the grounds that computers are more powerful than they used to be is flawed.  Getting rid of dynamic linking whole-hog is not the answer.

---

### Post by VON_CAPO on 2008-12-12
Of course I agree the basic system must not be statically linked.
I am talking about the everyday applications, such as Totem, Brasero, Cheese.

---

### Post by cariboo on 2008-12-12
I read somewhere on these forums that we as Ubuntu users are the largest percentage of Gnome testers. I think it is a shame that there is no easy link to Gnome's bug tracker, so that the bugs we are experiencing can be reported to the source. I reported a bug in Network Tools, that was supposedly sent upstream, but that was when Hardy was in development, the problem is still there in Jaunty.

I haven't yet, but I will ask the Launchpad devs to provide an easy way to report bugs upstream, so that maybe some of the issues mentioned can be resolved a little quicker.

Jim

---

### Post by cardinals_fan on 2008-12-12
> **VON_CAPO said:**
> Let's see a current example:

Ubuntu v8.10 shipped with the library "libv4l-0 v0.5.0-3~intrepid1" causing breakage in the package Cheese (the green screen effect, bug #282473); this has been fixed a few days ago with the upgrade to "v0.5.6-1~intrepid1".

As you can see is not the user, but Ubuntu dev team who injects this kind of packages in the distro.

But, blaming the developers is not fair, the root of all evil resides in how Linux itself manage the libraries... yeap ... "everything is dynamically linked", and is right here where the hell broke loose.  
As soon as one dependency suffers a modification all the related packages are at risk of breakage. 

All of this can be easily avoided using "static linking" **as necessary** (all the required dependencies are already included into the binary package).

Obviously, a lot of opposition will surge, such as:
1- This is not the Linux way.
2- We have Synaptic, a living proof that dynamic linking works! 
3- Static linking is too heavy, the binary file have to include all the dependencies and its size will grow up too much.
4- Static linking is not efficient, if you have 3 static linked packages using GTK+ v2.14, you must load in RAM that GTK+ v2.14 three times, exhausting your RAM very fast.

People, let us be honest.
- Static packages have the real advantage that the motto "just works" will be fulfilled.
- Also, they could be able to run in Ubuntu 6.10, 7.04, 7.10, 8.04, etc; without the permanent necessity of recompilate the whole package every time a new Ubuntu version is released (of course, there will be always exceptions). 
- Today's machines have at least 2 Gigabytes of RAM, far more than enough to run almost any combination of static linked software.
- The excuse of "it is a waste of hard drive space" belongs to some period 20 years ago.
- Low end machines always can use Xubuntu, Synaptic and the official repository.
The problem isn't dynamic links.  The problem is the rush to get the latest and greatest to market.  Consider PulseAudio and the havoc it has caused.  Did it really need to be introduced so soon, when ALSA still works fine?

My machine has 1 gig of RAM, and my Slackware system (which has never had breakage from upgrading packages) uses 60 MB for a blank desktop.  My SliTaz system (too new for me to pass judgment on stability, but no problems so far) only uses 32 MB.  Don't assume that statically linking everything and forcing everyone to buy new machines is the answer.
> **lykwydchykyn said:**
> I would think an idea compromise is to offer a system with a current set of packages every 18-24 months.  Then offer statically linked packages for applications that need to be updated.  This way, you only statically link GTK if your app requires features from a newer version of GTK.

Of course, I've tried to take that approach personally before and it doesn't always pan out.  But I think as Linux grows and becomes more accepted by ISV's and mainstream users, we'll see this kind of approach becoming more common.

I'm not a fan of the "computers are fast now, we don't need to worry about efficiency" approach to development.  That's why, with a 3 GHz dual core processor, it takes me just as long to launch an email client as it did 10 years ago with a pentium II.  This is why Vista is missing out on the netbook action.  Linux doesn't need to go that route.
Brilliant post.

---

### Post by JKBurton on 2008-12-14
> **lykwydchykyn said:**
> I would think an idea compromise is to offer a system with a current set of packages every 18-24 months.  Then offer statically linked packages for applications that need to be updated.  This way, you only statically link GTK if your app requires features from a newer version of GTK.



I think that's a very interesting idea, lykwydchykyn!

---

### Post by solwic on 2008-12-17
> **jkburton said:**
> i think that's a very interesting idea, lykwydchykyn!

+1

---

### Post by zugu on 2008-12-19
This has been discussed over and over again on these forums and believe me, you're wasting your breath. It's not gonna happen in Ubuntu. "Serious" Linux distributions will not switch to this bundled way of packaging OS X and Windows are using.

The only notable *NIX distributions that are working towards "everything in a file/archive/folder" approach are PC-BSD and Gobo Linux.

I would personally love Gobo Linux to succeed and become the greatest Linux distribution ever, but that's not gonna happen in the foreseeable future.

Check [this]("http://gobolinux.org/?page=at_a_glance") out, it's an interesting reading about software packaging in GoboLinux and in operating systems in general.

Edit: [This]("http://brainstorm.ubuntu.com/idea/12137/") is what the Ubuntu community thinks about the Gobolinux approach.

---

### Post by VON_CAPO on 2008-12-20
> **zugu said:**
> This has been discussed over and over again on these forums and believe me, you're wasting your breath. It's not gonna happen in Ubuntu. "Serious" Linux distributions will not switch to this bundled way of packaging OS X and Windows are using.

The only notable *NIX distributions that are working towards "everything in a file/archive/folder" approach are PC-BSD and Gobo Linux.

I would personally love Gobo Linux to succeed and become the greatest Linux distribution ever, but that's not gonna happen in the foreseeable future.

Check [this]("http://gobolinux.org/?page=at_a_glance") out, it's an interesting reading about software packaging in GoboLinux and in operating systems in general.

Edit: [This]("http://brainstorm.ubuntu.com/idea/12137/") is what the Ubuntu community thinks about the Gobolinux approach.

I was not aware of Gobolinux, but it looks really promising. 
I already downloaded the live CD.

Also I took a look to the community opinion about Gobolinux, and the first comment that I read was "**please stop spamming brainstorm**"  :confused:
You are right about "wasting your breath", those people look like religious nuts, unable to consider anything different to their dogma.

---

### Post by lykwydchykyn on 2008-12-20
> **VON_CAPO said:**
> I was not aware of Gobolinux, but it looks really promising. 
I already downloaded the live CD.

Also I took a look to the community opinion about Gobolinux, and the first comment that I read was "**please stop spamming brainstorm**"  :confused:
You are right about "wasting your breath", those people look like religious nuts, unable to consider anything different to their dogma.

That's a bit unfair, don't you think?  What's being suggested here is not trivial, it involves starting everything over from scratch.  They might as well suggest porting Ubuntu to the Amiga kernel while they're at it.  I don't know what you do for a living, but imagine how you'd react if someone was repeatedly asking you to basically reinvent whatever you do or sell, all for very dubious and marginal benefits.

This really doesn't have a lot to do with statically linking apps; I guess I can see how doing a lot of static linking would require some kind of organization in /opt or some other tree designated for static apps.  But simply reorganizing the filesystem doesn't address the static vs dynamic issue.

---

### Post by VON_CAPO on 2008-12-20
Well, Last night I expend like 2 hours at the Gobolinx website plus an additional half at Brainstorm.

I assure you I was delighted to read how that bunch of developers pushed the idea of exercise their freedom to run any version of software beyond the limitations of the "Linux way".

They got rid of the package manager and a collateral consequence is a restructured filesystem. Because of every application is contained in its own directory the danger of incompatible libraries is gone.

Also, they tackled the problem of repackaging all the software using something called "Recipes". 
If I understood well, the user installs any desired software from source and all the required dependencies are automatically downloaded from their respective web sites.    

Sweet right? :P

---

### Post by lykwydchykyn on 2008-12-20
> **VON_CAPO said:**
> Well, Last night I expend like 2 hours at the Gobolinx website plus an additional half at Brainstorm.

I assure you I was delighted to read how that bunch of developers pushed the idea of exercise their freedom to run any version of software beyond the limitations of the "Linux way".

They got rid of the package manager and a collateral consequence is a restructured filesystem. Because of every application is contained in its own directory the danger of incompatible libraries is gone.

Also, they tackled the problem of repackaging all the software using something called "Recipes". 
If I understood well, the user installs any desired software from source and all the required dependencies are automatically downloaded from their respective web sites.    

Sweet right? :P

Well, that's great and all, but expecting ubuntu to go back to square one and retool everything to do it that way is absurd.  If the "gobo linux way" has real tangible benefits over the olde FHS, it will take off, people will switch to it, and we'll all be shiny happy people.  In the mean time, I'm happy to have distros stick as close to standards as possible.  


Frankly I find all the posturing about "freedom" on brainstorm and so forth a bit ridiculous.  As if Mark Shuttleworth is cackling and wringing his hands together saying "Hahaha!  Now everyone will have to put apps under /usr, and there's nothing anyone can do about it!"

---

### Post by Caraibes on 2008-12-20
I think you guys are just ripe for this following reading : [http://beranger.org/index.php?page=diary&2008/12/10/23/43/18-the-big-move-defecting-from-linu](http://beranger.org/index.php?page=diary&2008/12/10/23/43/18-the-big-move-defecting-from-linu)
;)

---

### Post by VON_CAPO on 2008-12-20
> **lykwydchykyn said:**
> Well, that's great and all, but expecting ubuntu to go back to square one and retool everything to do it that way is absurd.  If the "gobo linux way" has real tangible benefits over the olde FHS, it will take off, people will switch to it, and we'll all be shiny happy people.  In the mean time, I'm happy to have distros stick as close to standards as possible.  


Frankly I find all the posturing about "freedom" on brainstorm and so forth a bit ridiculous.  As if Mark Shuttleworth is cackling and wringing his hands together saying "Hahaha!  Now everyone will have to put apps under /usr, and there's nothing anyone can do about it!"

I think the fundamental idea about GNU is Freedom.

Also in a sense of versatility, freedom to install applications **À la carte** should be something normal, but it is not, we are locked to the packages tailored for a specific distro version and good luck if we try to install some uncommon application from source, the most likely result will be errors and breakage because of incompatible libraries.

Anyway, I believe I have nothing else to add, we both have divergent points of view and our little chat is degenerating towards to a non-constructive path.

---

### Post by lykwydchykyn on 2008-12-20
Sure freedom is the fundamental idea, I just think some folks are getting melodramatic about it.  It's not restricting your freedom for someone else NOT to do something for you. 

I have nothing against this stuff, my only point is that if it has merit, it will win out in the end.  That's the beauty of open-source: differentiation and natural selection.

---

### Post by zugu on 2008-12-25
> **lykwydchykyn said:**
> Well, that's great and all, but expecting ubuntu to go back to square one and retool everything to do it that way is absurd.  If the "gobo linux way" has real tangible benefits over the olde FHS, it will take off, people will switch to it, and we'll all be shiny happy people.  In the mean time, I'm happy to have distros stick as close to standards as possible.

Not even FHS is respected. That's the problem.

---

### Post by lykwydchykyn on 2008-12-25
> **zugu said:**
> Not even FHS is respected. That's the problem.

That is a problem.  I wish Debian would get in line with that (Ubuntu would follow, of course; they don't generally change what Debian does on that level).  Glaring example is the web root for apache: /var/www?  What the heck is that?  Of all places... /var?

Anyway, I checked out gobolinux some; I think I was wrong about it not being relevant to the issue.  I see what they're doing now, and it makes sense, much along the lines of what I was saying earlier.  So, sorry von_capo about not seeing where you were coming from.

I think part of the problem is, people tend to push what gobolinux is doing because it's "easier for users", but as their faq explains that's not really the point.  The point is more along the lines of what I was saying earlier:  separating the apps out of the main filesystem and statically linking them in their own namespace.  

I guess time will tell if it's a better arrangement.

---

### Post by zugu on 2008-12-27
> **lykwydchykyn said:**
> The point is more along the lines of what I was saying earlier: separating the apps out of the main filesystem and statically linking them in their own namespace.Exactly! And being easy to use is just a nice side effect of this separation.

---

### Post by lykwydchykyn on 2008-12-27
> **zugu said:**
> Exactly! And being easy to use is just a nice side effect of this separation.

Yeah, but when I look at (for example) what's going on over at brainstorm with this stuff, it seems like people are pushing the "side issue" more than the central issue.  

I mean, if I were an ubuntu dev, I would not react well to "change your entire system architecture because it will make the directory names easier to understand".  I might be more apt to consider "make an additional namespace in the directory structure to allow for the use of statically-linked binaries".  

The thing a lot of bandwagon folks are missing on this issue is that gobolinux doesn't get rid of the old FHS structure, it just adds on to it.  So, it's not really what a lot of the supporters (or detractors) seem to think it is.

---

### Post by zugu on 2008-12-28
Although for me and few other people what GoboLinux is doing seems like a logical step in dealing with software management on *NIX systems, most of the rest of the world sees this as a blasphemy. And I don't blame them, what we're discussing here is changing a fundamental "standard". Such a move would have consequences in almost the entire *NIX ecosystem.

It's not just a cosmetic redesign of FHS, it's rethinking software management in the free software world, although Windows and OS X have enjoyed the benefits of this approach for quite some time. There are advantages and disadvantages in relation to FHS and the "current" way of getting things done - I happen to be in the camp that believes the disadvantages are few enough that it's worth jumping ship altogether. But I'm part of a minority.

I don't think Ubuntu will ever change in this respect. Better said, I don't think Debian will ever change their package management framework. Ubuntu clearly can't afford the time and resources necessary to implement a GoboLinux-like filesystem, even if it wanted, and is dependent on Debian. While GoboLinux showed us it's possible, changing the "industry" won't be possible unless some big player finds their concept worthy of implementing. Thinking Red Hat or Novell might do it? No way in hell! It would break everything they have right now.

The momentum is too great to ignore, it's been building up for decades. Even if it strays them in the wrong direction, they'll make a conscious decision to ride the wave till the end.

I'm a "radical" when it comes to *NIXes, but at the same time I am a realist and I'm sad to conclude no big, meaningful change will occur.

---

### Post by lykwydchykyn on 2008-12-28
zugu, why does EVERYONE have to do it for it to be a useful idea?  Why can't a few like minded distros or spinoff distros do this, and if it's truly a better and more manageable way of doing it, it'll take off?  Ubuntu, RedHat, et al don't own Linux.  This way, we could see if it's truly a better approach.

---

### Post by zugu on 2008-12-29
Not everyone has to do it, but at least someone with a big name, someone who matters. And the big players won't, I explained above why not.

---

### Post by Sef on 2008-12-29
> This has been discussed over and over again on these forums.... 

Agreed.  Since this thread is neither a testimonial nor an experience, it has been moved to recurring discussions.

---

### Post by saulgoode on 2008-12-29
> **lykwydchykyn said:**
> Glaring example is the web root for apache: /var/www?  What the heck is that?  Of all places... /var?
/var and /tmp are the only directories which, under the FHS, are guaranteed to not be read-only. It would make no sense to keep dynamic data in directories which can't be modified or in a directory whose contents may be lost upon reboot.

---

### Post by Tamlynmac on 2008-12-29
> Sef 	 		**Re: Why do distributions keep upgrading to broken apps?**
 		 	Quote:
 	 	 		 			 				This has been discussed over and over again on these forums.... 			 		 	 	 
Agreed.  Since this thread is neither a testimonial nor an experience, it has been moved to recurring discussions. 	

Thank You. Do we really need to keep beating a dead horse???
+1

---

### Post by lykwydchykyn on 2008-12-29
> **saulgoode said:**
> /var and /tmp are the only directories which, under the FHS, are guaranteed to not be read-only.

Really?  
From FHS 2.3 [http://www.pathname.com/fhs/pub/fhs-2.3.html#SRVDATAFORSERVICESPROVIDEDBYSYSTEM](http://www.pathname.com/fhs/pub/fhs-2.3.html#SRVDATAFORSERVICESPROVIDEDBYSYSTEM)
> 
/srv contains site-specific data which is served by this system. 


Seems more appropriate to me.  /home would even be better, IMO.  I see nothing in FHS about /var/www.  

> 
Thank You. Do we really need to keep beating a dead horse???
+1 

Well, you don't have to.  I've found this conversation educational, and I've never discussed this topic with anyone before.  I don't mind it being moved to recurring discussions, but I don't see why I can't follow through with a conversation I find interesting.  Excuse me for polluting your Internet with redundant discussions.

---

### Post by Tamlynmac on 2008-12-30
> lykwydchykyn
Quote:
 	 	 		 			 				[SIZE=1]Thank You. Do we really need to keep beating a dead horse???
+1  			 		[/SIZE] 	 	 
Well, you don't have to. I've found this conversation educational, and I've never discussed this topic with anyone before. I don't mind it being moved to recurring discussions, but I don't see why I can't follow through with a conversation I find interesting. Excuse me for polluting your Internet with redundant discussions.

Keep in mind I didn't request or move this - Just agreed with it. If you really are dissatisfied with the action, I'd suggest you take it up with the mod. I don't believe anyone suggested that you can't continue the conversation (as you implied). Just not in this section of the forum. At least that's my interruption of the mod's statement.

---

### Post by lykwydchykyn on 2008-12-30
> **Tamlynmac said:**
> Keep in mind I didn't request or move this - Just agreed with it. If you really are dissatisfied with the action, I'd suggest you take it up with the mod. 

I believe I said already that I didn't care about it being moved in the slightest; what the mod did is fine and appropriate.  Discussions that happen over and over belong in recurring discussions.  No argument here.
> 
I don't believe anyone suggested that you can't continue the conversation (as you implied). 

re read your posts to this thread and tell me it doesn't come off that way?

---

### Post by MikeTheC on 2008-12-30
> **Tamlynmac said:**
> IMHO it's the individual performing the upgrade that is responsible for assuring this criteria is met.

No where have I read that "Upgrading is Mandatory".

Yeah, but just imagine if nobody ever bothered to upgrade.

Nothing directed at you personally, Tamlynmac, but that's simply an excuse too easily hid behind by those who write software or build hardware.

---

### Post by Tamlynmac on 2008-12-30
> MikeTheC
Yeah, but just imagine if nobody ever bothered to upgrade.
Nothing directed at you personally, Tamlynmac, but that's simply an excuse too easily hid behind by those who write software or build hardware.


I disagree.
Upgrading is optional (as in choice) not mandatory. Nowhere, did I imply upgrading isn't an option, simply pointed out the obvious. IMHO it is the responsibility of the installer to assure compatibility prior to installation. Generally speaking if I'm not satisfied with a product - I simply replace it with a different product. What's complicate? If 8.1 fails to function, either re-install a previous version or use a different product. Seems fairly simple to me. Nothing I've read or agreed to mandates upgrading or stipulates I must use the most recent version. Personally, I prefer the LTS versions.

Had you read my responses, I think it was obvious that my concerns had little to do with upgrading. They were targeted at people complaining about a product to a group that had no responsibility for or control of said product. I don't believe you will find the devs or the hardware mfgs. hiding in the forum.

> MikeTheC
re read your posts to this thread and tell me it doesn't come off that way? 	

I will quote myself: > I don't believe anyone suggested that you can't continue the conversation (as you implied). Just not in this section of the forum.
I also think the mods decision was appropriate. As for beating a dead horse, It's MHO that this topic has been discussed repetitively without resolution. The answers to most of these issues can only be found by addressing the devs.

I refuse to continue involvement with this conversation, as I previously stated "beating a dead horse". Enjoy your conversation and I wish both of you a Happy, Prosperous & Safe New Year.

---

