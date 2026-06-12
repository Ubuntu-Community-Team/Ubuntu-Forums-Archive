---
title: "Outdated packages?"
date: 2011-08-01
forum: Recurring Discussions
---

### Post by Socob on 2011-08-01
Hello everyone,

Recently, I've come across quite a lot of programs where I noticed that the version in the repositories (using Synaptic or apt) seems to be annoyingly outdated even though a new version has been released ages ago. Examples I can name off the top of my head are Eclipse (package is still "Galileo"), Netbeans (still 6.9), git and Java (I haven't seen a JDK7 package yet). Yes, there's a lot of Java stuff, but that's just because I've been dealing with that a lot - I can remember other packages being outdated as well.

My question is: Is there any particular reason for this? Are the packages not updated due to bugs or incompatibilities? Should I perhaps add some kind of PPA to get newer versions? Or is it just that it takes a long time for these packages to get new versions?

---

### Post by jerrrys on 2011-08-02
the new software versions will appear in the next ubuntu release (hence, every 6 months).  if you do not wish to wait, then yes the PPA's are the way to go or even the developers site.

---

### Post by Socob on 2011-08-02
Oh, I didn't know there was a specific schedule like that for the packages as well. Then again, I get package updates all the time - are programs updated outside of the 6-month-schedule if it's just a minor update?

Also, I'm pretty sure Eclipse has had a new version out way longer than Ubuntu Natty. Is there any explanation for that?

---

### Post by jerrrys on 2011-08-02
i do not know or have an explanation for this or any of the other 30,000 packages found in the software center that are not totally up to date.  i would imagine the ubuntu maintainers for this package could give reason for this.  maintainer address are listed in properties in synaptic package manager.

---

### Post by BuddyThirteen on 2011-09-09
I was gonna start a similar thread.

It seems every time I have a problem with an app, I ask or google and people say "Upgrade to the newest version, that's not a problem anymore" and I find that I have to add a software-specific PPA for nearly every single program I have installed just to keep them updated. Is this really the way it's supposed to work?

Of course, if I'm unlucky, the software doesn't even have a PPA. Like Picard. I'm stuck with 0.12 because that's what's in the Repos, there's no software-specific PPA, and the method to update is a bit too complex for me.

I don't buy that the repos are only updated when Ubuntu is updated, because then there'd be no updates ever, instead of once a week or so.

---

### Post by ottosykora on 2011-09-09
well, outdated, many people say this, but one has to consider that each programm has to be packed for the particular distro, it has to be tested in all possible scenarios and if this has to be done for over 30000 programs, well this is big job.

It not about simply get it form whom ever and poste it on some sevrer.
Many programs need to be build as they come as source only and all dependencies have to be considered.

Then some people think they need all kind of alpha versions, bugy or not, but has to be the latest.

Example: Why to update java to version 7 if this has not even been released by the authors yet?
OK, someone needs to test some new software for compatibility, this is no problem, such people will be able to make their own package or build things from source.

---

### Post by BuddyThirteen on 2011-09-09
But I'm not talking about alphas or even betas. Standard stable releases aren't in the repos for months. Like the Shotwell bugfix that just released, you have to install the Yorba PPA to get it. And that's not even a major upgrade, just a bugfix.

---

### Post by Socob on 2011-09-09
@ottosykora:
I can see your points, but like BuddyThirteen, I'm not talking about the latest development versions or any alphas here. What I mean is that if a new stable version of a program is released, it shouldn't take months for that to appear in the repositories. As it's a stable version, I don't think a lot of testing would have to be done by the packagers - that would be the developers' job.

Also, the programs I've mentioned (Eclipse and NetBeans) are incredibly outdated. The version of NetBeans that's available as a package is over a year old, and the version of Eclipse is in fact **more than two years** old. Since then, it has had **two** major version upgrades. If that's not outdated, I don't know what is.

Concerning Java 7, I'm not sure what you mean by "not released by the authors". Java 7 was officially released on July 28th, but I do admit that that's not very long ago.

---

### Post by eric-yorba on 2011-09-09
> **BuddyThirteen said:**
> But I'm not talking about alphas or even betas. Standard stable releases aren't in the repos for months. Like the Shotwell bugfix that just released, you have to install the Yorba PPA to get it. And that's not even a major upgrade, just a bugfix.

Ubuntu 11.04 contains the Shotwell 0.9 series, Ubuntu 11.10 contains the Shotwell 0.11 series.  Only minor bugfix updates are accepted for each Ubuntu release, not releases that contain new features.

For that reason we provide a PPA for Ubuntu 11.04 users so they don't have to build from source to have the latest and greatest.

---

### Post by Socob on 2011-09-09
@eric-yorba:
Okay, I can see that, but that still doesn't explain programs that are outdated for years, like the ones I've mentioned. Or is it something specific about Eclipse and NetBeans that has caused problems so that they weren't included anymore?

---

### Post by BuddyThirteen on 2011-09-09
> **eric-yorba said:**
> Ubuntu 11.04 contains the Shotwell 0.9 series, Ubuntu 11.10 contains the Shotwell 0.11 series.  Only minor bugfix updates are accepted for each Ubuntu release, not releases that contain new features.

For that reason we provide a PPA for Ubuntu 11.04 users so they don't have to build from source to have the latest and greatest.
Thanks for the info. Am I the only one that thinks this is silly? I mean, sure, for default behavior (i.e., entry-level users) that's probably a good thing. Cuz if something crashes, they'll be all "Ubuntu sucks and crashes all the time!"

But there really should be an option in the settings for software center. Like on the updates tab where such a setting seems like it should exist. An option to get "New versions" rather than "bugfix releases" should be implemented.

---

### Post by ottosykora on 2011-09-09
>Concerning Java 7, I'm not sure what you mean by "not released by the authors". Java 7 was officially released on July 28th, but I do admit that that's not very long ago.<

it is up today not meant for general use apparently according to the java website.

Otherwise I think the authors and maintainers of particular programs should take care of the linux versions themselves. If they do not care, then who should do all the work. 
Under windows it is easy, there is only one version and so all has to be done only once.
Under linux, each distro has some different problems and sets up, this means preparing each single program for that particular distro. If the original authors do not care, then it is rather difficult to keep track of all.

The repository is getting so big, that I assume there is almost no way to have every single prograam under controll.

With some 'smaller' distros, there might be less choice, but all uptodate.

---

### Post by ottosykora on 2011-09-09
>But there really should be an option in the settings for software center. Like on the updates tab where such a setting seems like it should exist. An option to get "New versions" rather than "bugfix releases" should be implemented.<


but whre do you want take the 'new versions' from?

OK, if the original developer produces an updated version let say for 11.04 , he can send it to canonical and if it works on the system you will find it in repository.


But under linux unfortunately, the original developer has to produce then this version for: ubuntu 11.04, ubuntu 10.10, slax, mandriva, suse, fedora... who knows what elese.
We are here not in windows where one single version can be done and downloaded from the authors server.

See firefox. Under windows it is simple, only one single updater exists, this will simply download the deltas or even new version from the mozilla server, install , done.

This can not work under linux at all, therefore there is no updater build in. It has to be produced for each single distro separately.
This is this time not fault of canonical, this is basic problem of the linux folks in general, as the did never establish any common operating system valid for everyone.

---

### Post by Socob on 2011-09-09
@ottosykora:
If you mean java.com, then yes, Java 7 is not the default option there yet, but that doesn't mean that it's not available for "general use". What does "general use" even mean? I mean, things like the C++ compiler g++ are only used by developers, so of course, most people won't actively use it, but it's still up to date. Similarly, Java 7 is (currently) mostly used by developers, but that doesn't make it less legitimate. But anyway, that's not the point.

I'm not sure how the standard repositories are actually maintained, but considering that they're updated with every new release of Ubuntu, I suppose they're also maintained by Ubuntu. Can the developers of those programs even affect the standard repositories (if they want to take care of it themselves, as you say)? Of course, the developers could provide PPAs, but what's the point of having centralized standard repositories then?

---

### Post by ottosykora on 2011-09-09
The exact way how all is maintained will have to tell us one of the ubuntu mods here.

But: take synaptic and see how the files are listed there. If you have set up the correct repository, that means for 11.04 the natty etc then some packages have kind of ubuntu sign next to it.
Those are supposed to be set up by ubuntu (canonical) and tested for that particular distro version.

Those which have not the sign are packed for the ubuntu version, but not that way tested by canonical. 
This means they are packed by other people or companies etc and submitted to canonical to be included. It does not mean they do not work , in fact I did so far not met much what did not work straight out of the repository, but it exists.

Some authors provide kind of universal .deb files, meaning they should work on all debian derivates, but imagine , someone wants them to work in gnome2, the other one in KDE etc. Then you would have to either supply all the needed libs with the program (bringing half of the os with it) or make proper distribution version package.
And if such package is missing something in its list of dependencies, then the whole thing will fail or will at least behave differently in ubuntu 11.04 and ubuntu 10.10 etc.

Distribution authors will often package the most important programs. Canonical does really extremely lot in this direction.

But many programs are not distributed as directly installable packs.
Look at the firefox. OK it is just a zip file of this and that, if this works on a particular distro, we dont know. In fact I tried recently to run it on some older debian and have given up, the large number of libs I was asked to install separately was big.

---

### Post by eric-yorba on 2011-09-09
> **BuddyThirteen said:**
> But there really should be an option in the settings for software center. Like on the updates tab where such a setting seems like it should exist. An option to get "New versions" rather than "bugfix releases" should be implemented.

I'm pretty sure advanced users will either go find a PPA or just compile from source. Ubuntu makes both of those options relatively straightforward.

That said, there are distros that make this distinction.  It's all about maintaining the balance between stability and bleeding-edge features.

---

### Post by Socob on 2011-09-10
> **eric-yorba said:**
> I'm pretty sure advanced users will either go find a PPA or just compile from source. Ubuntu makes both of those options relatively straightforward.

That said, there are distros that make this distinction.  It's all about maintaining the balance between stability and bleeding-edge features.
Again, I wouldn't talk about "bleeding-edge features" when we're looking at versions which are over two years old. There are no PPAs, either, so every user would have to maintain the version on their own, which is just annoying.

---

### Post by Sicnarf on 2011-09-11
I was just finding out myself how to update programs in Ubunutu. I have 10.04. My questions are:

a) The way I understand it is in order to get the latest (or newer versions, not necessary latest) versions of programs is to upgrade to the latest version of Ubuntu which is 11.04?

b) Am I correct in my understanding that sometimes even if you have 11.04 you still won't get the latest versions of programs? just newer ones compared to when you have 10.04?

c) So the only way to upgrade every program to the latest version is through PPAs/source codes?

---

### Post by mue.de on 2011-09-11
> **BuddyThirteen said:**
> I was gonna start a similar thread.

It seems every time I have a problem with an app, I ask or google and people say "Upgrade to the newest version, that's not a problem anymore" and I find that I have to add a software-specific PPA for nearly every single program I have installed just to keep them updated. Is this really the way it's supposed to work?

I fully agree to your opinion and i wouldn't have that much trouble get my system working again (for two weeks now!), if even an KDE-developer gave me that advice, see -> [http://ubuntuforums.org/showthread.php?t=1842379](http://ubuntuforums.org/showthread.php?t=1842379)
Now the expected features aren't present in the programm but the whole system is damaged as a cause of using unsecure backport repositories !

---

### Post by snowpine on 2011-09-11
> **Sicnarf said:**
> I was just finding out myself how to update programs in Ubunutu. I have 10.04. My questions are:

a) The way I understand it is in order to get the latest (or newer versions, not necessary latest) versions of programs is to upgrade to the latest version of Ubuntu which is 11.04?

b) Am I correct in my understanding that sometimes even if you have 11.04 you still won't get the latest versions of programs? just newer ones compared to when you have 10.04?

c) So the only way to upgrade every program to the latest version is through PPAs/source codes?

The release number tells you the year and date of the release. So for example 10.04 = April 2010, 10.10 = October 2010, 11.04 = April 2011.

So if an application version was released May 2010 (for example) then you will not find it in the repositories for 10.04, only 10.10 or later.

The above applies only to the official Ubuntu repositories. You can choose to install later application versions from source or using a PPA.

---

### Post by ottosykora on 2011-09-11
It seems that still some people thing therms of windows latest versions of some ptograms.

Latest version of some program under linux is quite meaningless however.
There is no point having simply a new version of some program, as it will work under windows.
Yes , under windows, one only needs to look for latest version of that program, can install it, and that will work.

In linux, this is completely different. You need a version of that particular program *for that particular distribution*.

As said, some version of some browser for example has no value or meaning or does not say if it is latest or new or what ever, unless we talk about of that particular browser for that particular version of the distribution.

I found for example nice OCR tool in .deb format, apparently suitable for ubuntu. 
OK tried to install it, but this will work only under ubuntu 10.10 and definitely not under ubuntu 11.04.
Why?
Because ubuntu 11.04 contains the latest version of some particular text editor.
The OCR program however will work only with some older version of that text editor installed on the computer.

So one has to 'downgrade' that special text editor to the version contained in 10.10, which may break function of other programs in 11.04, and will so get a functionality of that OCR  in its latest form.

So  from this we can see, that trying to install 'the latests' version of something on a linux system is not best idea if this something latest was not explicitely prepared to run on exactly that version of the distribution.
If there is a version which is 2 years old for that distribution, then it may well have very good reasons, as later versions will not work with the current version of libraries etc.

We may have for example even some .deb package which will need definitely gnome3 libs to be able to run. How should this run on current versions of ubuntu when there are libs for gnome2 included?

One can try to build something from sources, but yes, the libs needed will have to be present on that system and this could mean either damaging whole system or set it even to some previous version for example.

Under windows, such problems do not come up often as all is done for one single version of an operating system, compatible for number of years.

---

### Post by ottosykora on 2011-09-11
> **Sicnarf said:**
> I was just finding out myself how to update programs in Ubunutu. I have 10.04. My questions are:

a) The way I understand it is in order to get the latest (or newer versions, not necessary latest) versions of programs is to upgrade to the latest version of Ubuntu which is 11.04?

b) Am I correct in my understanding that sometimes even if you have 11.04 you still won't get the latest versions of programs? just newer ones compared to when you have 10.04?

c) So the only way to upgrade every program to the latest version is through PPAs/source codes?

a) may be in general so, particularly for programs which are tested and packages prepared by ubuntu/canonical, but even it may not be absolutely true, as some programs in newer version may not run on higher versions of distribution 

b) mostly correct, you will probably get the newest version which can work on that particular distribution version

c) many program you can not upgrade to the latest version at all or just with many problems which could make your system unstable etc. 
The source can be compatible with that particular distribution version, but does not need to be. The author might want to have the program dependent on some exotic libs from some exotic distribution or programs of versions which will in turn not run on your distro, may ask you to install most of completely other desktop environment first before his program wants behave, or put other obstacles to it.

So forget what you know from windows, as download the latest version, install and you have the latest.

The author of that program does not know on which particular linux version are you going to use his work.

---

### Post by Sicnarf on 2011-09-12
> **snowpine said:**
> The release number tells you the year and date of the release. So for example 10.04 = April 2010, 10.10 = October 2010, 11.04 = April 2011.

So if an application version was released May 2010 (for example) then you will not find it in the repositories for 10.04, only 10.10 or later.

The above applies only to the official Ubuntu repositories. You can choose to install later application versions from source or using a PPA.

I see. Just as I have thought. Thank you!

> **ottosykora said:**
> a) may be in general so, particularly for programs which are tested and packages prepared by ubuntu/canonical, but even it may not be absolutely true, as some programs in newer version may not run on higher versions of distribution 

b) mostly correct, you will probably get the newest version which can work on that particular distribution version

c) many program you can not upgrade to the latest version at all or just with many problems which could make your system unstable etc. 
The source can be compatible with that particular distribution version, but does not need to be. The author might want to have the program dependent on some exotic libs from some exotic distribution or programs of versions which will in turn not run on your distro, may ask you to install most of completely other desktop environment first before his program wants behave, or put other obstacles to it.

So forget what you know from windows, as download the latest version, install and you have the latest.

The author of that program does not know on which particular linux version are you going to use his work.

Now I know. So that's why even really new versions of apps don't come with the newest Ubunutu. I installed firefox 6.0.2 on 10.04 and I was amazed that 11.04 only comes with firefox 4. So that explains it.

So those source codes that you get from the internet are sort of a hit-or-miss thing when installing them on your machine?

---

### Post by ottosykora on 2011-09-12
>So those source codes that you get from the internet are sort of a hit-or-miss thing when installing them on your machine?<

they will require certain other programs to be present in correct version on your machine. 
If you can provide those, then all is fine. If not, you can not install it at all or it will simply not run.

I have a printer driver in source, this will need an rather old versions of some libs to compile at all. I have to get those libs first as they will not be included in any current version of ubuntu for example.

If you have a package from the ubuntu repository and it is marked as being supplied by canonical, then it is tested, will install the needed libs from canonical repository during the installation and all will work.

If you have just some program from somewhere from internet, you may need to install hundreds of program libs before you can use that program.

If you have just the source of the program, then during the compile it needs to find the libs , if not , it will not compile but the compiler will tell you that you need this and that first.

---

### Post by eric-yorba on 2011-09-12
> **ottosykora said:**
> It seems that still some people thing therms of windows latest versions of some ptograms.

Latest version of some program under linux is quite meaningless however.
There is no point having simply a new version of some program, as it will work under windows.
Yes , under windows, one only needs to look for latest version of that program, can install it, and that will work.

That's simply not the case. An application made for Windows 7 won't run on Vista.

Microsoft devotes an incredible amount of resources to maintaining backward compatibility on Windows, yes. But there's no support for *forward* compatibility.

---

### Post by Socob on 2011-09-12
> **ottosykora said:**
> It seems that still some people thing therms of windows latest versions of some ptograms.
Wanting the latest version of a program is in no way thinking "in terms of Windows". There's a point to new software versions: new features and bugfixes. Trying to get the latest (stable) version of a program should be the obvious instict for anyone.

> **ottosykora said:**
> 
In linux, this is completely different. You need a version of that particular program *for that particular distribution*.
Distributions really don't differ that much. Yes, there are different package systems and so on, but if you look at the actual programs (e.g. if you compile from source instead of using .deb/.rpm/... packages), it really only depends on what libraries you have installed.

> **ottosykora said:**
> 
As said, some version of some browser for example has no value or meaning or does not say if it is latest or new or what ever, unless we talk about of that particular browser for that particular version of the distribution.
Again, it doesn't really depend on the distribution. All you need are the dependencies. I don't see why people make such a big deal out of the whole distribution thing.

> **ottosykora said:**
> 
I found for example nice OCR tool in .deb format, apparently suitable for ubuntu. 
OK tried to install it, but this will work only under ubuntu 10.10 and definitely not under ubuntu 11.04.
Why?
Because ubuntu 11.04 contains the latest version of some particular text editor.
The OCR program however will work only with some older version of that text editor installed on the computer.
That's a very specific case. Generally, it's not a good idea for a program to rely on another, independently maintained program, especially if both programs interact while running. You have the same issue on Windows (my example: "MiniLyrics" and "iTunes" [or any other supported media player] - if you don't have an appropriate combination of versions, both programs will crash or behave unpredictably). This really has nothing to do with Linux, but is a general issue of compatibilities of interacting, independent programs.

> **ottosykora said:**
> 
So  from this we can see, that trying to install 'the latests' version of something on a linux system is not best idea if this something latest was not explicitely prepared to run on exactly that version of the distribution.
If there is a version which is 2 years old for that distribution, then it may well have very good reasons, as later versions will not work with the current version of libraries etc.
Again, this is not really a Linux issue - every system has to deal with dependencies. Also, the programs in question are Java programs that ship with all the needed libraries included, so I doubt it's that (I'd still appreciate if anyone could solve that mystery, though).

> **ottosykora said:**
> 
We may have for example even some .deb package which will need definitely gnome3 libs to be able to run. How should this run on current versions of ubuntu when there are libs for gnome2 included?
The package would name gnome3 as a dependency and install it if needed, separate from gnome2. Problem solved.

---

### Post by ottosykora on 2011-09-13
>The package would name gnome3 as a dependency and install it if needed, separate from gnome2. Problem solved.<

yes, sure, but where does it take it from? It needs some kind of place where to get the ready made libs , that means in our linux terms, the repository of the particular distro will keep it ready, or in case of debian based distros, one can go to the debian server and obtain each single lib with all the version numbers etc one by one and place them where they should go.

If the program needs then the gnome3 libs, it has to be packaged so, that it will go automatically and fetch the gnome3 from somewhere. Then yes, you are right.
But this is not the case if you just pick some random program from somewhere.

So if I take the firefox latest version, try to install it on my older debian, it will simply not do anything at all as dozens of libs are missing and they all have to be provided in the correct version. Debian server will not install those libs automatically.

There are even 'universal' .deb of firefox around, they mostly work on ubuntu, will less often work on real debian, as the installer has no way to obtain the libs automatically.

This is now where people like ubuntu devs will start work and prepare a package which will ask for those libs AND they will same time make sure those libs are on their server folder belonging to that particular distro, this way making sure that some 'outside' app does not fetch some old libs and breaks the system.

This I would say is the difference between the 'big' distros like ubuntu and some small experimental once.
Take some of the basic linux distros, like DSL and see if some packet can trigger the installation of gnome3 libs to it. Probably not, as most of it will not be placed on their servers anyway.


There were some people trying to make portable apps for linux. Well it was nice idea, as for windows such thing exists for long time. 
But with windows, everything is backwards compatible about 10 years, programs build for windows will simply run on every current version of windows and very little has to be provided by the program itself.

Under linux, this ended up in few programs only, packed with all possible needed libs in the case those were not installed local and not available for immediate download.
To make such program to work over number of distros, all dependencies has to be provided with the program, making it very big in size.

In windows, you supply the program itself, compiled in some recent tool for that and it is simply compatible. 


As far as latest(stabele) version of a program, you are right, I would in this context here on linux,  add to it 'for my operating system'.

So latest (stable) version for ubuntu 11.04 

as this would differentiate to possibly newer version available for some other operating system (other distro for example)
as it would not make much sense to have the latest (stable) version of something, but the dependencies can not be met or just with less perfect version of some libs of provided by the distro author.

---

### Post by yooozy on 2011-09-13
lot of interesting talk here :)  

I think there's a  smart tool in Synaptic but I'm not sure it will do the job:

Settings > Preferences >general
reloading outdated packages - automatically

can anyone confirm

---

### Post by Socob on 2011-09-13
> **yooozy said:**
> Settings > Preferences >general
reloading outdated packages - automatically

can anyone confirm
There is indeed such an option, but that's not what the topic is about. The option you mentioned just ensures that Synaptic refreshes and gets the latest package information available. What I mean, however, is that the packages themselves are outdated - there simply are no packages for version 3.7 of Eclipse because nobody's created them. I'm still trying to find out why that is, since Eclipse (and even NetBeans) have a very significant level of popularity among developers.

---

### Post by dniMretsaM on 2011-09-13
> **Socob said:**
> There is indeed such an option, but that's not what the topic is about. The option you mentioned just ensures that Synaptic refreshes and gets the latest package information available. What I mean, however, is that the packages themselves are outdated - there simply are no packages for version 3.7 of Eclipse because nobody's created them. I'm still trying to find out why that is, since Eclipse (and even NetBeans) have a very significant level of popularity among developers.

Yeah, someone should indeed package the latest Eclipse. I might give it a go. I've been looking to learn to package programs anyway.

---

