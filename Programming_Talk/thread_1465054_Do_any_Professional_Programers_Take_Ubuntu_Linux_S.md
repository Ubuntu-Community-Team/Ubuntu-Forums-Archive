---
title: "Do any Professional Programers Take Ubuntu Linux Seriously?"
date: 2010-04-29
forum: Programming Talk
---

### Post by orphanlast on 2010-04-29
The reason why I'm posting this thread here is because I want to talk to some professional programmers because I'm kinda irritated with ubuntu right now. I spent two days trying to get a program that was said to be awesome... oh so cool and amazing (kdenlive) and all it did was crash. I couldn't do anything with it. I could watch one second of video on it, but I have video players that do much better than that.

After running into a few programs that have been less than stellar, I just want to ask if any professional programmers really take Linux or Ubuntu seriously?... If the answer is yes... maybe I might feel better with my operating system and get over this frustration faster...

I've been having a really rough go at learning this thing...

---

### Post by matthew.ball on 2010-04-29
> **orphanlast said:**
> I just want to ask if any professional programmers really take **Linux** or Ubuntu seriously?
I can't speak about Ubuntu specifically, but in terms of Linux the answer is a big yes.

While perhaps I'm not much of a professional programmer myself, I spend a lot of time with people who could be considered professional programmers (mostly senior academics* at my university in the computer science department), and everything is done with Linux here.

*When I say academics, this includes research *engineers* who do the programming.

---

### Post by orphanlast on 2010-04-29
I've read that 30% of Linux users tend to use Ubuntu. So if Linux is given serious consideration, I'd hope it'd be with what is currently considered the flagship of Linux.

In the last two days I've been learning about Software Repositories and spent about three days just trying to find out how to get Quicktime to work.

I finally got Quicktime to work, and I got the software repositories to work for me this time... but I don't know if I'll be able to resolve it again later on.

:)

Thanks

---

### Post by howlingmadhowie on 2010-04-29
> **orphanlast said:**
> The reason why I'm posting this thread here is because I want to talk to some professional programmers because I'm kinda irritated with ubuntu right now. I spent two days trying to get a program that was said to be awesome... oh so cool and amazing (kdenlive) and all it did was crash. I couldn't do anything with it. I could watch one second of video on it, but I have video players that do much better than that.

After running into a few programs that have been less than stellar, I just want to ask if any professional programmers really take Linux or Ubuntu seriously?... If the answer is yes... maybe I might feel better with my operating system and get over this frustration faster...

I've been having a really rough go at learning this thing...

it took you 2 days to open synaptic and double click kdenlive?

alternatively you could have done this:
```

sudo apt-get install kdenlive

```

---

### Post by Ascenti0n on 2010-04-29
I don't clearly understand what you are asking.

If you are asking does Linux have the same standard of software for manipulating various media, ie video editing, sound editing, image editing, then than answer is that the Linux platform is lacking.

But as your post is in the programming section, I assume you may also be asking, is Linux a good platform from programming, then the answer a resounding YES.

Linux is an awesome platform for programming, including web development. It's secure, fast and stable. It has a wide variety of free and capable editors and IDE's. It's also home the the greatest web server platform on the planet - Apache.

---

### Post by TheStatsMan on 2010-04-29
All serious computing done at research institutions I am aware (not saying all do, just all I am aware of) of are run on linux. I haven't used a super computer than runs on anything else.

I for one certainly find programming in (K)Ubuntu much more enjoyable and productive than programming in Windows. The tools are a lot better, it is far easier to use open source software, which in my opinion is very important. Comparing Linux to Windows as a programming tool is like comparing a Ferrari to a Toyota camry as a track car. More people have camrys but they sure as hell don't get around the track as quick as a Ferarri.

Edit: I just realised how stupid it was to describe Windows as a Camry. Camrys never break down, a Ford Pinto would be more appropriate.

---

### Post by orphanlast on 2010-04-29
> **howlingmadhowie said:**
> it took you 2 days to open synaptic and double click kdenlive?

alternatively you could have done this:
```

sudo apt-get install kdenlive

```

I'm not that stupid. 

For some reason my synaptic only had a really old version of kdenlive (And I tell my synaptic to refresh and to mark updates and "apply" multiple times, every single day). After having gone to kdenlive.org they state that all older versions before 7.7 have not been receiving updates and have degraded in their usefulness because of it. They suggest on their Ubuntu download page that you add a whole new repository to get it. I had to learn how to add repositories just to get a program that doesn't even work.

And there's no hardware problem, and no install problem.

---

### Post by CptPicard on 2010-04-29
> **orphanlast said:**
> They suggest on their Ubuntu download page that you add a whole new repository to get it. I had to learn how to add repositories just to get a program that doesn't even work.

And the problem in this is ... what? That is, it is some kind of an issue that you actually need to tell the package manager where to get something so it knows where to go get it so it can manage the system's dependencies automatically for you as it usually does?

---

### Post by cascade9 on 2010-04-29
OK....before I start this I will point out that I dont use kdenlive, and I'm not a big ubuntu user. 

What version of ubuntu are you using? If its 9.10, according to the kdenlive site, it should have 0.7.5 in the repos, if its 9.04 then 0.7.3, if 8.10 or 8.04 then 0.5. 

Which makes sense- 0.7.5 was released in 07/2009, so it was pretty current when 9.10 came out. (10/2009). 0.7.3 was 04/2009, so it was just realsed when 9.04 came out. 0.5 was released 07/2007, so it was pretty old with 8.04 and 8.10..but the next full (non-beta) release was 0.7, released 11/2008, so ti was too late to make it into 8.10 (and way to late for 8.04) so ubuntu was current with those releases as well. 

I dont know what version you are running...but IMO, I wouldnt call 0.7.3 'really old'. Not current, OK, agreed, but hardly 'really old'. If your using 8.10/8.04 and looking for current software, then IMO you either have a lot of work cut out for you, or you are using the wrong release.

> **orphanlast said:**
> For some reason my synaptic only had a really old version of kdenlive (And I tell my synaptic to refresh and to mark updates and "apply" multiple times, every single day). After having gone to kdenlive.org they state that all older versions before 7.7 have not been receiving updates and have degraded in their usefulness because of it. 

It wont matter how many times you refresh synaptic, its not going to make software magically apear in the repos. In general, apart from security fixes, once a version of ubuntu has been shipped, it tends to keep the version of whatever software it was shipped with. 

I had a look around the kdenlive site and didnt find any msg that said 'versions before 0.7.7 have degraded in usefullness'. What I did see was this (IMO rather overdone) -

> **OLD RELEASE, NO SUPPORT PROVIDED!**
This version of Kdenlive is deprecated. 'Deprecated' does not mean 'degraded'. 

> **orphanlast said:**
> They suggest on their Ubuntu download page that you add a whole new repository to get it. I had to learn how to add repositories just to get a program that doesn't even work.

And there's no hardware problem, and no install problem.

I wouldnt say there are no installation issues....there is obviosuly some fault. No idea what it is though. I also wouldnt be quite so quick to add repos, etc, just beause the version of program 'x' in your distros repos is slight older than the current release. 

IMO, somebody has tried to be 'helpful' with the ubuntu page on the kdenlive site. Have a look at the other distros pages- 

[http://kdenlive.org/user-manual/downloading-and-installing-kdenlive/pre-compiled-packages/slackware-packages](http://kdenlive.org/user-manual/downloading-and-installing-kdenlive/pre-compiled-packages/slackware-packages)

0.7.7.1 

[http://kdenlive.org/user-manual/downloading-and-installing-kdenlive/pre-compiled-packages/mandriva-packages](http://kdenlive.org/user-manual/downloading-and-installing-kdenlive/pre-compiled-packages/mandriva-packages)

0.7/0.7.2

[http://kdenlive.org/user-manual/downloading-and-installing-kdenlive/pre-compiled-packages/gentoo-packages](http://kdenlive.org/user-manual/downloading-and-installing-kdenlive/pre-compiled-packages/gentoo-packages)

0.7.3

[http://kdenlive.org/user-manual/downloading-and-installing-kdenlive/pre-compiled-packages/debian-packages](http://kdenlive.org/user-manual/downloading-and-installing-kdenlive/pre-compiled-packages/debian-packages)

0.7.5 (on sid, which is wrong and out of date (last updated 04/2008  ), I know because I've checked sid and its actaully 0.7.7.1 now). 

Ubuntu 9.10 using 0.7.5 doesnt look qiute so 'old' anymore now, does it? 

Next time, I'd worry less about what the website says and just try the version in the repos. If you have issues with the version from there, then maybe try coming here and posting about it, or trying some 3rd party repo.

---

### Post by orphanlast on 2010-04-29
> **CptPicard said:**
> And the problem in this is ... what? That is, it is some kind of an issue that you actually need to tell the package manager where to get something so it knows where to go get it so it can manage the system's dependencies automatically for you as it usually does?

The problem was originally that I had no idea how to add software repositories. I know now, but it was a pain in the butt.

---

### Post by Bodsda on 2010-04-29
> **orphanlast said:**
> I'm not that stupid. 
 
For some reason my synaptic only had a really old version of kdenlive (And I tell my synaptic to refresh and to mark updates and "apply" multiple times, every single day). After having gone to kdenlive.org they state that all older versions before 7.7 have not been receiving updates and have degraded in their usefulness because of it. They suggest on their Ubuntu download page that you add a whole new repository to get it. I had to learn how to add repositories just to get a program that doesn't even work.
 
And there's no hardware problem, and no install problem.
 
you mean you added a non-standard repository to download an app not packaged by ubuntu developers, and are frustrated that it doesnt work?
 
You should probably try building from source and running the app from the terminal to find out why it crashed. Then you could debuig the issue and file a bug report to help others.
 
This should take an hour or two, max.
 
--
 
In response to the initial question, yes. Linux is taken very seriously as a programming platform and it is much easier to program on Linux then on Windows. I started programming on a Linux platform and when I tried to do the same on a Windows platform it was unbelievably frustrating.
 

Bodsda

---

### Post by orphanlast on 2010-04-29
> **cascade9 said:**
> OK....before I start this I will point out that I dont use kdenlive, and I'm not a big ubuntu user. 

What version of ubuntu are you using? If its 9.10, according to the kdenlive site, it should have 0.7.5 in the repos, if its 9.04 then 0.7.3, if 8.10 or 8.04 then 0.5. 

Which makes sense- 0.7.5 was released in 07/2009, so it was pretty current when 9.10 came out. (10/2009). 0.7.3 was 04/2009, so it was just realsed when 9.04 came out. 0.5 was released 07/2007, so it was pretty old with 8.04 and 8.10..but the next full (non-beta) release was 0.7, released 11/2008, so ti was too late to make it into 8.10 (and way to late for 8.04) so ubuntu was current with those releases as well. 

I dont know what version you are running...but IMO, I wouldnt call 0.7.3 'really old'. Not current, OK, agreed, but hardly 'really old'. If your using 8.10/8.04 and looking for current software, then IMO you either have a lot of work cut out for you, or you are using the wrong release.



It wont matter how many times you refresh synaptic, its not going to make software magically apear in the repos. In general, apart from security fixes, once a version of ubuntu has been shipped, it tends to keep the version of whatever software it was shipped with. 

I had a look around the kdenlive site and didnt find any msg that said 'versions before 0.7.7 have degraded in usefullness'. What I did see was this (IMO rather overdone) -

'Deprecated' does not mean 'degraded'. 



I wouldnt say there are no installation issues....there is obviosuly some fault. No idea what it is though. I also wouldnt be quite so quick to add repos, etc, just beause the version of program 'x' in your distros repos is slight older than the current release. 

IMO, somebody has tried to be 'helpful' with the ubuntu page on the kdenlive site. Have a look at the other distros pages- 

[http://kdenlive.org/user-manual/downloading-and-installing-kdenlive/pre-compiled-packages/slackware-packages](http://kdenlive.org/user-manual/downloading-and-installing-kdenlive/pre-compiled-packages/slackware-packages)

0.7.7.1 

[http://kdenlive.org/user-manual/downloading-and-installing-kdenlive/pre-compiled-packages/mandriva-packages](http://kdenlive.org/user-manual/downloading-and-installing-kdenlive/pre-compiled-packages/mandriva-packages)

0.7/0.7.2

[http://kdenlive.org/user-manual/downloading-and-installing-kdenlive/pre-compiled-packages/gentoo-packages](http://kdenlive.org/user-manual/downloading-and-installing-kdenlive/pre-compiled-packages/gentoo-packages)

0.7.3

[http://kdenlive.org/user-manual/downloading-and-installing-kdenlive/pre-compiled-packages/debian-packages](http://kdenlive.org/user-manual/downloading-and-installing-kdenlive/pre-compiled-packages/debian-packages)

0.7.5 (on sid, which is wrong and out of date (last updated 04/2008  ), I know because I've checked sid and its actaully 0.7.7.1 now). 

Ubuntu 9.10 using 0.7.5 doesnt look qiute so 'old' anymore now, does it? 

Next time, I'd worry less about what the website says and just try the version in the repos. If you have issues with the version from there, then maybe try coming here and posting about it, or trying some 3rd party repo.

I know those pages are supposed to be helpful but I guess I'm just supposed to struggle with interpreting what those are.

I don't know what to tell you other than my synaptic was displaying version 3 not 7.7.  It was way out of date. It was only when I added repositories that it said 7.7

---

### Post by orphanlast on 2010-04-29
> **Bodsda said:**
> you mean you added a non-standard repository to download an app not packaged by ubuntu developers, and are frustrated that it doesnt work? 

I used the repository that was recomended from the developers: [http://www.kdenlive.org/user-manual/downloading-and-installing-kdenlive/pre-compiled-packages/ubuntu-packages](http://www.kdenlive.org/user-manual/downloading-and-installing-kdenlive/pre-compiled-packages/ubuntu-packages)
 
>  You should probably try building from source and running the app from the terminal to find out why it crashed. Then you could debuig the issue and file a bug report to help others.
 
This should take an hour or two, max. That sounds cool.

And as soon as I find out how do do that, I think I will. I'm a noob at all this... never HAD to do any of this, so it's more than a little frustrating.

That's some of the reason why I made this thread... If the people that actually make programs think Linux matters then maybe this all might be worth it.

---

### Post by CptPicard on 2010-04-29
> **orphanlast said:**
> 
That's some of the reason why I made this thread... If the people that actually make programs think Linux matters then maybe this all might be worth it.

Just consider that most of the übergeeks have been thinking that Linux matters since the 90s. I've been a full-time Linux user since about 1998, and learned pretty much everything I know on it. It admittedly looks and feels like its users and developers -- they only care that it works for them, and this is why we get issues when the typical "end-user" from Windowsland comes over. 

They often eventually see the light though regarding things like why the package manager works the way it does for example :)

---

### Post by SledgeHammer_999 on 2010-04-29
> **orphanlast said:**
> The problem was originally that I had no idea how to add software repositories. I know now, but it was a pain in the butt.

It's not that difficult. You(and many others) have just got used to some other way.(the Windows way). Keep in mind that this is a different system and you'll have to learn how to use it. (It is not that different from other OSes).


> 
You should probably try building from source and running the app from the terminal to find out why it crashed. Then you could debuig the issue and file a bug report to help others.

This should take an hour or two, max. 

You don't have to compile it yourself. Nor do you have to mess with building sources at this stage(noob stage).

If you have kdenlive already installed, open a terminal, type "kdenlive" and hit enter. The program will load. Just do your usual work on the program until it crashes. Then examine the output of the terminal and make a thread at the appropriate forum section for help.

---

### Post by cascade9 on 2010-04-29
> **orphanlast said:**
> I know those pages are supposed to be helpful but I guess I'm just supposed to struggle with interpreting what those are.

I don't know what to tell you other than my synaptic was displaying version 3 not 7.7.  It was way out of date. It was only when I added repositories that it said 7.7

Version 0.3? o.O 

That was released 05/2006. I would guess that it would have been the version that came with ubuntu 6.06...what version are you using? 

BTW, I only linked to those pages to show that virtually none of the distros (non rolling release distros anyway) have 'old' versions of kdenlive.

---

### Post by nvteighen on 2010-04-29
> **CptPicard said:**
> Just consider that most of the übergeeks have been thinking that Linux matters since the 90s. I've been a full-time Linux user since about 1998, and learned pretty much everything I know on it. It admittedly looks and feels like its users and developers -- they only care that it works for them, and this is why we get issues when the typical "end-user" from Windowsland comes over. 

They often eventually see the light though regarding things like why the package manager works the way it does for example :)

Well, that's actually the reason why GNU/Linux is a system that works: it's developed by its own users, which means that the developers know exactly what people need from their computers. A totally different issue is the lack of resources GNU/Linux seemed to have suffered until these last years and which prevented some cool stuff to be ported/cloned into Free Software alternatives. GNU/Linux systems are build on features people do need and of course, package managers make it very easy to install/remove what you want with much more guarrantee of success than third-party software used my MS Windows.

The issue is that in order to keep this track, GNU/Linux "end-users" should engage a little more into the community and maybe not start developing and mantaining packages, but at least report bugs.

---

### Post by orphanlast on 2010-04-29
> **SledgeHammer_999 said:**
> It's not that difficult. You(and many others) have just got used to some other way.(the Windows way). 

I agree, it's not difficult to add repositories... but what's difficult is knowing how to find other repositories, then distinguishing if they're even reliable. Then there's the issue of if the program will even work...
 

 >  Keep in mind that this is a different system and you'll have to learn how to use it. (It is not that different from other Oses). 
 It's more work than the average OS. And sometimes I feel as though it's a comfortable OS, but when I work hard to understand something and to get a new program and it doesn't work... that's frustrating.




>  You don't have to compile it yourself. Nor do you have to mess with building sources at this stage(noob stage).

If you have kdenlive already installed, open a terminal, type "kdenlive" and hit enter. The program will load. Just do your usual work on the program until it crashes. Then examine the output of the terminal and make a thread at the appropriate forum section for help.Cool.
 

 > **cascade9 said:**
> Version 0.3? o.O 

That was released 05/2006. I would guess that it would have been the version that came with ubuntu 6.06...what version are you using? 
 

 9.10. I don't know why such an old version was showing up in my Synaptic. I am currently using Kdenlive 7.7 and it's the one that's crashing.

---

### Post by mmix on 2010-04-29
not yet x86, x86-64, but yes, other cpu platform like arm, ppc, mips, tilera, ...

embedded linux stuff on the hardware.

on x86/x86-64, reactos will have better an opportunity, IMHO.

---

### Post by Reiger on 2010-04-29
Do professional programmers take Linux seriously? Umm: what are the employees of Red Hat, Canonical, Novell, Oracle, IBM, Intel, Google? A boy scout club? :confused:

If the yardstick is software that &#8220;does not work right after you did what you always used to do&#8221; then by the same logic we could ask whether or not Professional Programmers take Windows or Mac OS X seriously.

---

### Post by orphanlast on 2010-04-29
> **Reiger said:**
> Do professional programmers take Linux seriously? Umm: what are the employees of Red Hat, Canonical, Novell, Oracle, IBM, Intel, Google? A boy scout club? :confused:

If the yardstick is software that &#8220;does not work right after you did what you always used to do&#8221; then by the same logic we could ask whether or not Professional Programmers take Windows or Mac OS X seriously.

C'mon... working with a software repository is nothing like what I used to do.

I know Google is jumping on the Linux wagon, but they're not working with conventional distros. I'd hope that with one of the biggest companies jumping on board there will me more attention planted on other distros and the possibility of faster improvement, customization, and universal use.

Microsoft is a software company and they develop more than just windows and many of their programs are industry standard... think excel and you instantly think "spreadsheet"

Mac also has some amazing software. Personally, I don't use a Mac but I've had the chance to play around with an ipad (which I know isn't the same, but much of the software on the ipad is developed from Apple). iworks was kinda cool and I could see it really getting the job done. The itouch (and iphone) is the most successful MP3 player with the market, with the most application support than anything else in the entire market, be it for MP3 players or Cell phones (this includes the Linux based Android phones which were created under a good philosophy but a terrible business model. Google also has contracted with other companies to make sub par phones. Take the mytouch, which I own... it's a piece of crap).

Anyways... it's the Internet and software that make the world go round when it comes to operating systems. You can have an amazing operating system and have it be completely incompatible with absolutely everything but its own material and websites specifically designed for it. It can be the most secure, the most brilliant. The most sound code... hell -- it could even be self aware. But if it would always remain like that, it doesn't matter how amazing it is to its own self worship. No one would want it. So I think software IS a good measuring stick.

---

### Post by slavik on 2010-04-29
> **orphanlast said:**
> C'mon... working with a software repository is nothing like what I used to do.

I know Google is jumping on the Linux wagon, but they're not working with conventional distros. I'd hope that with one of the biggest companies jumping on board there will me more attention planted on other distros and the possibility of faster improvement, customization, and universal use.

Microsoft is a software company and they develop more than just windows and many of their programs are industry standard... think excel and you instantly think "spreadsheet"

Mac also has some amazing software. Personally, I don't use a Mac but I've had the chance to play around with an ipad (which I know isn't the same, but much of the software on the ipad is developed from Apple). iworks was kinda cool and I could see it really getting the job done. The itouch (and iphone) is the most successful MP3 player with the market, with the most application support than anything else in the entire market, be it for MP3 players or Cell phones (this includes the Linux based Android phones which were created under a good philosophy but a terrible business model. Google also has contracted with other companies to make sub par phones. Take the mytouch, which I own... it's a piece of crap).

Anyways... it's the Internet and software that make the world go round when it comes to operating systems. You can have an amazing operating system and have it be completely incompatible with absolutely everything but its own material and websites specifically designed for it. It can be the most secure, the most brilliant. The most sound code... hell -- it could even be self aware. But if it would always remain like that, it doesn't matter how amazing it is to its own self worship. No one would want it. So I think software IS a good measuring stick.
"Industry" standard is technically ODF ... OOXML is as well, but it's a horrible standard which is not implemented anywhere.

When I think Excel, I don't think spreadsheet. Thinking Excel -> Spreadsheet is what gets us into trouble where we start using the brand name as the description of the product (band-aid anyone? it's an adhesive bandage). Obviously, this isn't how everyone thinks about it, but the point is that we (people) don't tend to think about the tools, but about the solutions.

As for professional programmers taking Ubuntu seriously ... they take it as seriously as Red Hat, or SUSE, or any other distro.

The point is that if you are a large company, you either buy Sun, IBM, HP itanium/risc or someone who has x86 based hardware (HP/Dell usually) and put Linux on it. Most of the time, Windows is there only because of some specific use/limitation (library, active directory, exchange).

If it's a server, chances are it's Unix/Linux (Unix meaning Solaris, AIX, HPUX. Linux is mostly Red Hat). I can tell you this from personal professional experience.

---

### Post by orphanlast on 2010-04-29
>  Obviously, this isn't how everyone thinks about it, but the point is that we (people) don't tend to think about the tools, but about the solutions. I would agree with that. But I might just Google it after I take an Apirin. Lol. (Instead of research the matter after taking an analgesic bit of medicine called acetylsalicylic acid.) ... Okay, enough stupid humor.

>  I can tell you this from personal professional experience.Awesome. Really, thanks.

 What do you think of Ubuntu 10.04? I really like the fact that I can click on a file type that this thing doesn't recognize and can't play and it'll find it like Visa did. Oh yeah!

No more googling for two days in order to play a file type like quicktime again!

---

### Post by CptPicard on 2010-04-30
Your mistake, that is a very typical one, is imagining that Linux is supposed to be a "business model" that aims for selling stuff to Joe Sixpack. It's not. It's a collection of code and a a bunch of people hacking on that code because they feel it's worthwhile to do so, plus some industry sponsors for certain projects.

These programmers care about Linux because it's an open platform and a completely transparent tool for what they do. Whether it auto-recognizes some filetype is totally peripheral to that goal.

Technically speaking, the Linux model has been very successful. This was most apparent in the 90s when Windows was a crashy piece of ... without any features of what you'd typically associate with what deserves to be called an operating system. WinXP caught up a little, but Windows still is far too "person at desktop with mouse"-centric to be a proper, flexible, networked multiuser OS.

And I don't understand the package manager complaints... I mean, your typical Linux installation consists of a multitude of user-chosen packages that have their dependencies. In the Windows world you would have to go on the web to download the right installers, click on them, install them... isn't the Linux approach just obviously totally superior? :confused:

---

### Post by orphanlast on 2010-04-30
> **CptPicard said:**
> 
And I don't understand the package manager complaints... I mean, your typical Linux installation consists of a multitude of user-chosen packages that have their dependencies. In the Windows world you would have to go on the web to download the right installers, click on them, install them... isn't the Linux approach just obviously totally superior? :confused:

To a degree... the process of downloading a program on Windows was, by and large, the same every time. Click a button that says Download, download the installer, install the installer, delete the downloader... or keep it, whatever.

But I've had some strange interactions with the software repositories. Some really outdated stuff just appeared in it and that's what got me to look for more software repositories, yet everyone tells me that it didn't have that outdated information, but I know what I saw... can't explain it.

Also, if you're just looking for a program on Windows, you'll be able to find it, almost without a doubt, but sometimes the synaptic package manager just simply won't. Even 10.04 (as awesome as it is) doesn't have songbird. I'm going to need to reinstall that sucker.

---

### Post by ajackson on 2010-04-30
> **orphanlast said:**
> Also, if you're just looking for a program on Windows, you'll be able to find it, almost without a doubt,
Only if it has a Windows version, you try finding a Windows version of synaptic. Also have you considered looking for a linux equivalent to the software you are after? Sometimes another program can do just as good a job as application *X*.

> **orphanlast said:**
> but sometimes the synaptic package manager just simply won't. Even 10.04 (as awesome as it is) doesn't have songbird. I'm going to need to reinstall that sucker.
So the package manager doesn't contain packages for every single program ever created, shocking isn't it. But people can create PPA that can be added to fix some of the gaps and take care of dependancies, sure you start running the risk of incompatible versions cropping up but you get that under Windows as well.

Edit: One quick search throws up debs for Songbird [http://www.getdeb.net/app/Songbird](http://www.getdeb.net/app/Songbird) took all of about 10 seconds to find it.

---

### Post by CptPicard on 2010-04-30
> **orphanlast said:**
> To a degree... the process of downloading a program on Windows was, by and large, the same every time. Click a button that says Download, download the installer, install the installer, delete the downloader... or keep it, whatever.

The process of installing something on Linux is the same every time. Tell the package manager to install it. Done. What if on Windows your program has dependencies?

> 
Also, if you're just looking for a program on Windows, you'll be able to find it, almost without a doubt, but sometimes the synaptic package manager just simply won't.

If there's a working package for your distribution, it will be in the repos (this is very much the case for Debian at least). It really is equivalent to the situation where, for Windows, you simply wouldn't have the software -- but on Linux you still have the option of even source-compilation, should you need that...

---

### Post by conradin on 2010-04-30
The Linux Users I know are just turning their attentions to ubuntu. The Real hackers seem to use REHL or some sort of RPM based derivative. Indeed, there are more packages out there for REHL. Additionally, I feel the Hacker culture is stronger with REHL, when it comes to tinkering with code, science, research, and custom hardware. 

The strength of Ubuntu is its rapid development, and growing community. 
My recommendation is to try another video editor if you have a problem with one. I use Pitivi. Open Shot is also allegedly very good though I haven't really tested it yet.

I should ask what video hardware you  have, and are you running the KDE environment?

---

### Post by CptPicard on 2010-04-30
> **conradin said:**
> The Linux Users I know are just turning their attentions to ubuntu. The Real hackers seem to use REHL or some sort of RPM based derivative. Indeed, there are more packages out there for REHL. Additionally, I feel the Hacker culture is stronger with REHL, when it comes to tinkering with code, science, research, and custom hardware. 


IMO Red Hat is more of the distribution that is being pushed at "Enterprise" users... Debian is probably the most solid "community project" that you tend to see on "hackers'" machines.

But, certainly choice of distribution is not that indicative of who is a hacker and who is not...

---

### Post by sujoy on 2010-04-30
why would the hackers buy RHEL when they can get the same stuff with Fedora/CentOS/ etc etc..?

---

### Post by orphanlast on 2010-04-30
> **ajackson said:**
> Only if it has a Windows version, you try  finding a Windows version of synaptic. Also have you considered looking  for a linux equivalent to the software you are after? Sometimes another  program can do just as good a job as application *X*. 
    
    When I had Windows, I never wanted a Linux program. Honestly, I barely  even acknowledged the existence of Linux. It was that one operating  system that I had heard about in the 1990's as being really difficult to  use and that I'd read a little about when I'd go to stumbleupon.com and  just stumble on the net for a little while.
    
   >  So the package manager doesn't contain packages for every  single program ever created, shocking isn't it.     Not a shock either way. I don't know what to expect out of this thing. I  was hoping that it would retrieve compatible versions of the program  being looked for or something like that. Oh well.
    
    >  But people can create PPA that can be added to fix some of the  gaps and take care of dependancies, sure you start running the risk of  incompatible versions cropping up but you get that under Windows as  well.     Is that done by just going to SYSTEM>ADMIN>SOFTWARESOURCES and  just adding something into the "OTHER SOFTWARE" tab?
    
    >  Edit: One quick search throws up debs for Songbird [http://www.getdeb.net/app/Songbird](http://www.getdeb.net/app/Songbird)  took all of about 10 seconds to find it.    Oh yeah, I got it now.
   
   > **CptPicard said:**
> The process of installing something on Linux is  the same every time. Tell the package manager to install it. Done. What  if on Windows your program has dependencies? 
   
   If it's not in the repository it can be different and three times more  complicated if it really wants to be.
  
  There have been about four or five times I've downloaded a program  outside of a repository and directly from the developer's website. How  that went was (and this is with linux) was: I'd download a compressed  file, I'd extract it into the /user/ file and it starts working. That's  kinda cool
  
  But if it's something like GnoMenu ([COLOR=Red]The next sentence in black text was only true a about an hour ago. It was pretty much inevitable. I HAD to get another Repository... or PPA... What's the difference from the two? Is a Repository a more official list of programs and a PPA is just a list of programs made by one specific group? [/COLOR]which I'm currently working on but  didn't have to with 9.10) then I download the compressed from here file  [https://launchpad.net/gnomenu](https://launchpad.net/gnomenu) with the green button to the right. I then  extract it... and it's a hidden file, but it looks different. Usually  it would show up as ".GnoMenu" instead of just "GnoMenu," it doesn't  show up as an "add to panel" icon... in fact its as though it's not  there at all. So I play around with the readme file and make sure that I  have the other programs that are needed to get it to work, but it's  just not working. Maybe I'm missing one... or two... I'll figure it out.
  
  And sometimes, like my old install of KdenLive, even if it worked after  install, there was something bad happening to get it to crash within the  first fifteen seconds of it being used every single time.
  
  So there's a little more involved with Linux. I've never had to worry  about incompatibility with Windows... I don't know where that's coming  from, but I'm sure I'd have faced those sorts of frustrations had I  wanted to use Linux programs in Windows.
  
 > **conradin said:**
>  My recommendation is to try another video  editor if you have a problem with one. I use Pitivi. Open Shot is also  allegedly very good though I haven't really tested it yet. 
 
 Will do
 
>  I should ask what video hardware you  have, and are you  running the KDE environment  Graphic card: GeForce 9800 GTX+
 
 Mother board: Biostar G31-M7 TE
 
I don't think I have a KDE environment... I think I'd need to have  Kubuntu. I have the Main Gnome release 10.04 (I had to look at the  Ubuntu Pocket Guide to answer that one.)

---

### Post by CptPicard on 2010-04-30
> **orphanlast said:**
> When I had Windows, I never wanted a Linux program. Honestly, I barely  even acknowledged the existence of Linux.

So now that you're on Linux, you are expecting for everything to automagically work the same as on Windows?

    
> I  was hoping that it would retrieve compatible versions of the program  being looked for or something like that. Oh well.

It manages your dependencies excellently regarding your current system. Better than anything else in existence.
    
       
> 
   If it's not in the repository it can be different and three times more  complicated if it really wants to be.

The repositories are already far easier than anyone has the right to expect them to be.

>   
  There have been about four or five times I've downloaded a program  outside of a repository and directly from the developer's website. How  that went was (and this is with linux) was: I'd download a compressed  file, I'd extract it into the /user/ file and it starts working. That's  kinda cool


Do you actually understand what goes into making anything work on any computer?
  
>   
  And sometimes, like my old install of KdenLive, even if it worked after  install, there was something bad happening to get it to crash within the  first fifteen seconds of it being used every single time.

Well, you probably had something incompatibable underlying it. See above.
  
> 
  So there's a little more involved with Linux. I've never had to worry  about incompatibility with Windows... I don't know where that's coming  from, but I'm sure I'd have faced those sorts of frustrations **had I  wanted to use Linux programs in Windows**.

Come on! If you had wanted to use these programs on Windows, *they would never have worked to begin with!*.

The reason why you do not have to worry about incompatibility with Windows is that those pieces of software are written for Windows. On Linux, it is naturally different.

---

### Post by orphanlast on 2010-04-30
> **CptPicard said:**
> So now that you're on Linux, you are expecting  for everything to automagically work the same as on Windows? 
 
 The reason I made this thread is because I knew it's  different. I was trying to adapt and I was getting frustrated and wanted  to know if all this effort was worth it. With the new version of Ubuntu  out and how it now operates, I'd say that it works far more comfortably  than it did and I'm happy with that. Also, some programmers have spoken  up and mentioned that it is something taken very seriously. So that's a  big plus.
 
>  It manages your dependencies excellently regarding your  current system. Better than anything else in existence. My current system. Lol. Is that a potshot at my hardware? lol.

You would know if it was better than anything else in existence better  than I would, so I'll take your word for it. I think one of the biggest  things is that I don't know any programs on Linux. I keep asking long  term Linux users what they think are the best programs and they never  really answer... so even though there's a long list of programs on  Synaptic, it's hard to pick and choose what programs to get and those  that aren't for me. There's usually a ten word summary of the program  but sometimes the summary just doesn't explain what the program is for  the layman, so I have to go out and research what these programs are  for. 

I'll admit that there's tons of programs in the Synaptic and that's  cool. But what's not cool is having to do tons of research on every  program I'm not going to enjoy and finding the rare program that I find  of interest. 
 
>  The repositories are already far easier than anyone has the  right to  expect them to be. I'm sure that in the 1990's they were either a pain in the *** or none  existent and you had to type it all in the terminal.
 
 >  Do you actually understand what goes into making anything work  on any  computer?  I'm not really criticizing Ubuntu or Linux. I'm just voicing some  frustrations with it because I admittedly don't understand it. I'll  answer that question honestly too. No. I don't.  I'm sure it's a real  pain.

>  Come on! If you had wanted to use these programs on Windows, *they   would never have worked to begin with!*. Most, yes. But Gimp is compatible with Windows and Mac. I'm sure other open source (originally Linux) programs have been made universal like Gimp. That's basically what I was referring to.

>  The reason why you do not have to worry about incompatibility with  Windows is that those pieces of software are written for Windows. On  Linux, it is naturally different.Naturally different as in there's all the other distros based off or different programs and such?

---

### Post by soltanis on 2010-04-30
Not to beat a dead horse, but are you complaining about something being difficult to install?

Please.

There's plenty of stuff hard to install on any system. Personally I prefer a single Debian package registry to the Windows system registry. Difference: one works, the other degrades over time, destabilizes your system, and forces you to reinstall many times.

Do professional programmers take Linux seriously? Absolutely. Do you realize how much easier it is to write software for Linux when compared to Windows and OS X? Mac is seriously the worst -- you get the choice of, Xcode, and oh yeah, Xcode -- and perfectly fine Python applications that I have written that ran beautifully on Linux and Windows, even, Mac OS X refused to grok. For absolutely no good reason that I can think of besides "Steve Jobs doesn't want you to use your computer."

Sounds a lot like "Bill Gates doesn't want you to use your computer" with the difference being Steve Jobs has a company that can actually write software.

---

### Post by TheStatsMan on 2010-04-30
> **orphanlast said:**
> When I had Windows, I never wanted a Linux program. Honestly, I barely  even acknowledged the existence of Linux. It was that one operating  system that I had heard about in the 1990's as being really difficult to  use and that I'd read a little about when I'd go to stumbleupon.com and  just stumble on the net for a little while.
  Surely if you are programming then anything useful on the web is open source, closed source code is simply not going to do you any good. Now if you want to use an open source library then your life is going to be a hell of a lot easier on linux than it is on Windows. Say you want ATLAS for instance. You can simply go the repositories and click on ATLAS. If you want you can compile from source, without too much stress. Now go try getting it to work on Windows. There are so many useful libraries out there that are simply a headache for the Windows user that are trivial to obtain for the linux user.  I think you are coming on here with the Window's mindset and wondering why things work different than Windows. A lot of people come on here asking for something like Visual Studio. Obviously, if you come in with that mind set nothing is going to quite work like Visual Studio. If you get an IDE that is imitating Visual Studio the it is likely that it is going to be worse than Visual Studio. Now if you are open minded and you have a shot at the Linux way of programming, then you may realize that Visual Studio is not quite as good as you thought it was. You begin to see how inefficient the Windows way of coding is and why linux does things in a certain way.  Now you seem to be commenting on the overall experience of linux rather than the programming aspect. All I can say is Linux is not Windows. You can't expect the second you start using Linux you are going to be using if flawlessly. You have been learning to get around the annoyances in Windows for years and now they are second nature. De-fragmenting the hard drive, virus scanners, spyware scanners, messing with the registry, Googling for software and deciding not to get it because it costs money, maybe pirating software, hitting control-alt-delete all the time to shutdown software, rebooting a million times when installing some new, maybe even updates, having only one virtual desktop, searching for drivers, etc, etc. These things are second nature and taken for granted.

---

### Post by orphanlast on 2010-04-30
> **soltanis said:**
>  There's plenty of stuff hard to install on any system. 

I'm saying I don't understand it all and that's making it more complicated than it really is. But the only thing I've ever seen difficult to install on Windows was something like a Bittorrent, one big plus is that, for so long as I have Linux, I don't need to mess with that ever again.

---

### Post by soltanis on 2010-04-30
> **TheStatsMan said:**
> having only one virtual desktop, searching for drivers, etc, etc.

I can't stand Windows anymore and I can barely stand Macs because of the multiple desktops thing. They've become such a second nature for me (along with tiling windows). Speaking of which, I laugh every time I see Windows 7 commercials, especially the one about the "snap" feature.

Yeah Windows. Quite a feature. You learned how to snap windows to the side of the desktop. I've been working on 4+ things at once for multiple years with something I call dwm (granted, dwm isn't for normal people).

Anyways, what's the issue here, besides random OS bashing?

---

### Post by orphanlast on 2010-04-30
> **soltanis said:**
> I can't stand Windows anymore and I can barely stand Macs because of the multiple desktops thing. They've become such a second nature for me (along with tiling windows). Speaking of which, I laugh every time I see Windows 7 commercials, especially the one about the "snap" feature.

Yeah Windows. Quite a feature. You learned how to snap windows to the side of the desktop. I've been working on 4+ things at once for multiple years with something I call dwm (granted, dwm isn't for normal people).

Anyways, what's the issue here, besides random OS bashing?

What's DWM?

Macs have Multiple Desktops like Linux's Virtual Desktops these days.

But, yeah, I AM getting used to some things in Ubuntu that are really nice and I wouldn't want to go back... I just wish I understood everything.

---

### Post by soltanis on 2010-04-30
DWM is the "Dynamic Window Manager." It's a tiling minimalist window manager, so you have all your windows tiled out instead of floating over and under each other. All it really supports is drawing windows, closing them, moving them from desktop 1-9, and opening xterm. (It also gets out of your way, which I like -- let's you focus on the program instead of the decorations).

The real kicker is that it's great for working side by side on multiple things at once. Unlike in floating window managers, even with multiple desktops, you can really get things done. If you ever had multiple monitors, its a similar concept, but it doesn't take two monitors to do it.

Mac's multiple windows are a rather limited implementation of compositing. Not anything like what Compiz can achieve (then again, Compiz crashes).

---

### Post by slavik on 2010-04-30
> **soltanis said:**
> DWM is the "Dynamic Window Manager." It's a tiling minimalist window manager, so you have all your windows tiled out instead of floating over and under each other. All it really supports is drawing windows, closing them, moving them from desktop 1-9, and opening xterm. (It also gets out of your way, which I like -- let's you focus on the program instead of the decorations).

The real kicker is that it's great for working side by side on multiple things at once. Unlike in floating window managers, even with multiple desktops, you can really get things done. If you ever had multiple monitors, its a similar concept, but it doesn't take two monitors to do it.

Mac's multiple windows are a rather limited implementation of compositing. Not anything like what Compiz can achieve (then again, Compiz crashes).
there is also awesome.

I tend to use terminator for multiple terminals :)

---

### Post by hulyanmakabayan on 2010-04-30
Maybe this question is for professional programmers to answer. And since I'm not one, what I'm about to say is as good as anyone's opinion here.

Your frustrations with kdenlive is understandable. To the average Joe, multimedia manipulation in linux  hasn't reached the level of sophistication that many commercial applications are at already. For professional level of work ... by that I mean the kind where you charge people money for, MacOS softwares tend to lead the pack. It's their heritage. 

Linux started with internet service software as a  strong base. I still cringe at the thought of using Windows web server to this day. In this area of software, I'm pretty convinced a number of professional programmers are taking the level very, very seriously. Not because it pays well, but in a Bobby Jones Jr. - amateur kind of way. (Apologies for the reference to golf). top-notch work for a song and the privilege to contribute to the internet.

I've been using linux since 1997 mostly in server mode. Got bit by the ubuntu bug about 5 years ago and still at it.  Really:  Firefox, Openoffice,vlc and Gimp. I still find it the best desktop for my use.

Maybe kdenlive in ubuntu is not the best for you. Go back to Windows and some commercial software if your livelihood depends on it. No, get thee a Mac! Prepare your checkbook too.

But check out the open source world from time to time. They get better.

Take to your genre, and get the best you can afford. But remember that only fools mock Picasso because he couldn't draw "properly" like Michaelangelo.

---

### Post by TheBuzzSaw on 2010-05-01
I am a professional programmer.

I take Ubuntu/Linux seriously.

Any questions?

---

### Post by slavik on 2010-05-01
> **TheBuzzSaw said:**
> I am a professional programmer.

I take Ubuntu/Linux seriously.

Any questions?
answer answered, thread closed. ;)

---

### Post by TheStatsMan on 2010-05-01
> **slavik said:**
> there is also awesome.

I tend to use terminator for multiple terminals :)

 Terminator is good. The latest version of Kubuntu does things like windows snapping together, without the need for a more advanced windows manager.  Just wait until the day when Windows gets multiple desktops. They will have it all over adds like they invented it.

---

### Post by TheStatsMan on 2010-05-01
> **orphanlast said:**
> What's DWM?

Macs have Multiple Desktops like Linux's Virtual Desktops these days.

But, yeah, I AM getting used to some things in Ubuntu that are really nice and I wouldn't want to go back... I just wish I understood everything.

 It just goes how to show Steve Jobs patent crusade is at the moment. Could the man be any more unethical. He is starting to make Bill Gates look like a saint.

---

### Post by ajackson on 2010-05-01
> **orphanlast said:**
> I think one of the biggest  things is that I don't know any programs on Linux. I keep asking long  term Linux users what they think are the best programs and they never  really answer... so even though there's a long list of programs on  Synaptic, it's hard to pick and choose what programs to get and those  that aren't for me. There's usually a ten word summary of the program  but sometimes the summary just doesn't explain what the program is for  the layman, so I have to go out and research what these programs are  for. 
OK so the descriptions in synaptic range from good to rubbish, so you have to do independent research into what a particular program does. Is there some magical thing in Windows that tells you exactly what a program does? Didn't think so.

As to what are the best programs, there is no answer to that unless you get specific. For example Firefox is an excellent web browser but pretty rubbish for desktop publishing; does that make it a good application or bad? If you want to do DTP it is a very bad choice.

> **orphanlast said:**
> 
I'll admit that there's tons of programs in the Synaptic and that's  cool. But what's not cool is having to do tons of research on every  program I'm not going to enjoy and finding the rare program that I find  of interest. 
Again how do you know about Windows applications? Were you born with an amazing knowledge of every single application created for Windows or did you have to find out about them somehow?

> **orphanlast said:**
> I'm not really criticizing Ubuntu or Linux. I'm just voicing some  frustrations with it because I admittedly don't understand it. I'll  answer that question honestly too. No. I don't.  I'm sure it's a real  pain.
Did you not have to learn how Windows works? If you did is it that unreasonable that you'd have to learn how a different OS works?

---

### Post by Max Destruction on 2010-05-01
I am certainly not a professional programmer but I think in a lot of ways GNU/Linux is as good or better than Windows. But there are certain areas where it lags drastically, and they are to do with applications (the GNU part)-Games and Video-processing for two. It's just so unlikely that volunteer programmers are going to be able to compete with the highly paid teams. I highly doubt GNU will ever be able to produce something like Visual Studio...but that's ok. It doesnt really need to. I think computing is evolving to a virtual machine model anyway..so in the future the operating system will become less and less relevant.

---

### Post by CptPicard on 2010-05-01
> **Max Destruction said:**
> It's just so unlikely that volunteer programmers are going to be able to compete with the highly paid teams. I highly doubt GNU will ever be able to produce something like Visual Studio...but that's ok. It doesnt really need to.

It is actually interesting that such a vast body of open code actually exists considering that it's based on small increments by mostly volunteer contributors. The idea that you need a paid team working on a closed product to make it good seems very questionable to my mind...

It really is about needs, not capabilities. Hackers do not really care about or bother with eye-candy or having multimedia work out of the box or whatnot. What they have cared about in Linux from the start is to have a solid, open base for an operating system and to have good tools they can use to work on technical problems... those problems that interest them.

>  I think computing is evolving to a virtual machine model anyway..so in the future the operating system will become less and less relevant.

And what that virtual machine actually runs on seems to be something Linux-based in most cases...

---

### Post by P4man on 2010-05-01
> **orphanlast said:**
> 
But, yeah, I AM getting used to some things in Ubuntu that are really nice and I wouldn't want to go back... I just wish I understood everything.

Interesting to read through this thread and how your opinion seems to evolve as you gain more knowledge.

Id just point out you had rough start by picking one of the few area's where linux software is still weak: video editing. And to make things worse, the KDEnlive in the repositories prior to 10.04 has been out of date and horribly unstable (I know, Ive been there). its improved dramatically since (as you probably noticed) and id say its now a contender for products like imovie or windows moviemaker. its no premiere yet, and at the moment, linux has no (free) software that comes close. 

That is probably about to change though, with lightworks being opensourced:
[http://ostatic.com/blog/powerful-video-editor-lightworks-released-as-open-source](http://ostatic.com/blog/powerful-video-editor-lightworks-released-as-open-source)
I hope that will make premiere  look like a silly and buggy and incredibly overpriced piece of software. But we aint there yet.

Besides video editing, there are other well known sore points like games, and to some extent photoshop (gimp comes close for most uers, but not quite there for "pros's").

That doesnt mean there is no professional quality programs for linux. Far from it. Much of the best software i run under windows is opensource software that is also (and often originally) native to linux, like openoffice, thunderbird, firefox, VLC, smplayer, inkscape, lyx, php/apache/mysql... I could go on.

But if you're someone depending on specific windows-only apps like Premiere, Visual Studio, dreamweaver or photoshop, simple fact is windows will serve you better.

---

### Post by Max Destruction on 2010-05-01
> **CptPicard said:**
> It is actually interesting that such a vast body of open code actually exists considering that it's based on small increments by mostly volunteer contributors. The idea that you need a paid team working on a closed product to make it good seems very questionable to my mind...

It really is about needs, not capabilities. Hackers do not really care about or bother with eye-candy or having multimedia work out of the box or whatnot. What they have cared about in Linux from the start is to have a solid, open base for an operating system and to have good tools they can use to work on technical problems... those problems that interest them.



And what that virtual machine actually runs on seems to be something Linux-based in most cases...

Indeed indeed. 

I've pretty much switched completely to Linux gnu these days. Thus far the only things that I've found to be lacking compared to the proprietary competition are: 

Adobe products. Gimp is good enough to make me not miss photoshop and inkscape is 80% of Illustrator. But Dreamweaver, InDesign, After Affects, Premiere .. gnu is a looong way away from this standard.

Visual Studio.  (which as you said, is kinda not really the Linux way anyway)

Games (i couldn't care less)

For the rest I find Linux to be superior in all ways.

---

### Post by P4man on 2010-05-01
> **Max Destruction said:**
>  After Affects, Premiere .. gnu is a looong way away from this standard.


Maybe not as long as you (and I) previously thought;
[http://ostatic.com/blog/powerful-video-editor-lightworks-released-as-open-source](http://ostatic.com/blog/powerful-video-editor-lightworks-released-as-open-source)

---

### Post by Max Destruction on 2010-05-01
> **P4man said:**
> Maybe not as long as you (and I) previously thought;
[http://ostatic.com/blog/powerful-video-editor-lightworks-released-as-open-source](http://ostatic.com/blog/powerful-video-editor-lightworks-released-as-open-source)

thats really good news, will be a great boost for open source!

i should also add that im really impressed with blender. very professional-like quality.
those developers should be given trophies.

---

### Post by P4man on 2010-05-01
Blender seems to be amazing indeed, but I just cant get my head around its interface. I tried a few times, and got far enough to be thoroughly impressed, but its not compatible with my brain lol.

---

### Post by Max Destruction on 2010-05-01
> **P4man said:**
> Blender seems to be amazing indeed, but I just cant get my head around its interface. I tried a few times, and got far enough to be thoroughly impressed, but its not compatible with my brain lol.

Have you tries 3dsmax. maya, or any of those other 3d rendering programs? ..they are all insanely complicated, it's the nature of the beast :p

---

### Post by Penguin Guy on 2010-05-01
I am no professional programmer, but I've programmed on both Windows and Linux, so my opinion does have *some* merit.

I find that whether Linux is better for programming or not really depends on your preferences. Programming on Windows is more commonly done through an IDE where all the tools you need are grouped together in one program. Whereas programming on Linux usually takes a more modular approach and is usually done by editing text files using any text editor you want, then running the program in the terminal. I find that the Windows approach is better for beginner programmers as it gives them a lot of debugging tools and assistance when programming.

However, I personally prefer the Linux approach because it gives me the freedom to use whatever text editor I want, whereas with Windows I am forced to use the text editor that the IDE chooses - although I must admit that Windows' IDEs usually have better syntax highlighting than most Linux text editors.

NOTE: The above is just the usual way things are done. You can still use a text editor + terminal to program in Windows, just as you can use an IDE to program in Linux.

---

### Post by P4man on 2010-05-01
> **Max Destruction said:**
> Have you tries 3dsmax. maya, or any of those other 3d rendering programs? ..they are all insanely complicated, it's the nature of the beast :p

I grew up using 3d studio (way back in the dos days. Think it was like version 2.0. I remember I had 4Mbyte ram and the program actually claimed to need 8 which cost a fortune and I couldnt afford it). I actually won a legal copy of  3d studio 3.0 (I think?) in a contest (my submission was created with 3ds, but they were kind enough not to ask questions lol).  

Later i picked up again with 3d max under NT and that wasnt too hard to adapt too. Not been doing much if any 3d since, but I tried blender a year or two ago and couldnt find my way. I might well have the same problem in 3d max now, Im getting old i guess :)

---

### Post by Max Destruction on 2010-05-01
> **P4man said:**
> I grew up using 3d studio (way back in the dos days. Think it was like version 2.0. I remember I had 4Mbyte ram and the program actually claimed to need 8 which cost a fortune and I couldnt afford it). I actually won a legal copy of  3d studio 3.0 (I think?) in a contest (my submission was created with 3ds, but they were kind enough not to ask questions lol).  

Later i picked up again with 3d max under NT and that wasnt too hard to adapt too. Not been doing much if any 3d since, but I tried blender a year or two ago and couldnt find my way. I might well have the same problem in 3d max now, Im getting old i guess :)

ahhh ok so you know what you are doing then :D my i find them all equally confusing. :p i am just learning the physics engine this last week. very nice.

---

### Post by orphanlast on 2010-05-01
> **hulyanmakabayan said:**
>  Your frustrations with kdenlive is understandable. To the average Joe, multimedia manipulation in linux hasn't reached the level of sophistication that many commercial applications are at already. 
 

 Well as fast as Linux seems to be getting at catching up with the market, I think skies are starting to look blue. I was really irritated with Ubuntu 9.10 when I made this thread. I had no idea it would get this much attention.
 

 Just off hand and off topic... does anyone know of a good program that's similar to Adobe Audition? (I don't know much with Adobe Audition, but I do like messing with sounds – manipulating, editing, etc.)
 

 >  Maybe kdenlive in ubuntu is not the best for you. Go back to Windows and some commercial software if your livelihood depends on it. No, get thee a Mac! Prepare your checkbook too. 
 

 Nah. The most I'd do on that regard is place virtualbox on my computer and mess with windows and mac that way.

>  But check out the open source world from time to time. They get better. 
 

 Ubuntu 9.10 vs 10.04 No contest. 10.04 is amazing in comparison. So yeah, I kinda jumped in at the right time to see just how dramatic the change tends to get.

>  Take to your genre, and get the best you can afford. But remember that only fools mock Picasso because he couldn't draw "properly" like Michaelangelo.


 I've only seen a few paintings from Picasso that I could actually appreciate. But yeah, proper art isn't always good art.
 

 > **TheBuzzSaw said:**
> I am a professional programmer.

I take Ubuntu/Linux seriously.

Any questions?


 Short simple and to the point. Awesome. Would you say it'd be worth my time to learn all that there is about Linux? I'm about midway (hopefully) through a transition from a life long use of Windows to Linux. It's not the easiest thing in the world. Just simply because there's concepts that I've never considered before that this Operating System presents to the table.
 

 > **TheStatsMan said:**
> It just goes how to show Steve Jobs patent crusade is at the moment. Could the man be any more unethical. He is starting to make Bill Gates look like a saint.
 

 I wouldn't say that, I've never used a Mac. But I'd agree that Steve Jobs likes to make everything a big Crusade and “DESTINY”. When a tech blogger got his hands on the next iphone and showed it to the world Steve Jobs treated it like it was a Military operation and he was the President of the United States. That poor guy.
 

 My thoughts are, if Linux users want people to know about Linux, what it's capable of they need to be doing some serious promotioning. There's plenty of ways to do it for free. For example, blogging. There's also a way to get political about it. Schools. Why spend hundreds of thousands of dollars on software releases when you can give the kids a free operating system, an interest in programing, and free programs? Where's the downside? It promotes Ubuntu. It also makes a valuable point.
 

 Personally. Even though I've been extremely frustrated with my transition to Linux, and because I currently don't know how to do any programing, I've been trying to do my part in blogging about it. (The more you blog, the more Linux shows up in Google searches.)
 

 If anyone is interested in seeing at least one blog I've made about Ubuntu look here [http://hubpages.com/hub/Ubuntu-Description-And-Review](http://hubpages.com/hub/Ubuntu-Description-And-Review)
 

 > **ajackson said:**
> OK so the descriptions in synaptic range from good to rubbish, so you have to do independent research into what a particular program does. Is there some magical thing in Windows that tells you exactly what a program does? Didn't think so. 
 

 There's advertisements, if not on television, then they're advertised everywhere on the Internet.

>  Again how do you know about Windows applications? Were you born with an amazing knowledge of every single application created for Windows or did you have to find out about them somehow? 
 

 Not to complain about Synaptic (because this really isn't one) but it would be nice to pop on there, and since it's somewhat like a store, why wouldn't it have advertisements for the programs there? … let it give you a chance to type in your interests and it gives suggestions based off of what tags might have been placed on the programs...  
 

 Advertisement is really a good way of letting people know what program does what and how good it is – BUT I know that Linux doesn't sell anything and so advertisements aren't really avaliable because of the lack of funds, but there should be some internal free simple ways to search.  
 

 Another way I've found programs of interest is if a friend starts playing with one and it piques my interest. But no one even remotely around me every uses Linux. So I'm forced to see my friends and see these advertisements and ask people “Is there a program like THAT?” on Linux... Doing something like that would make it so that less people would compare Linux to something else and recognize it more for being its own animal.

>  Did you not have to learn how Windows works? If you did is it that unreasonable that you'd have to learn how a different OS works?
 
If we're using the the word “learn” in the conventional sense, I'd say “no”. I don't recall learning how to speak, but I guess I did, otherwise I wouldn't be speaking and writing in English. I learned Windows much the same way. It's just what I did.  It wasn't really a thought process or effort behind it.
 

 > **P4man said:**
> Interesting to read through this thread and how your opinion seems to evolve as you gain more knowledge. 
 

 Well, I made the stubborn decision to stick it out 'till the end. This thread was just to ask if it was going to be a bitter end.

>  And to make things worse, the KDEnlive in the repositories prior to 10.04 has been out of date and horribly unstable (I know, Ive been there). its improved dramatically since (as you probably noticed) and id say its now a contender for products like imovie or windows moviemaker. its no premiere yet, and at the moment, linux has no (free) software that comes close. 
 

 Do you know of an “unfree version”?
 

 By the way. I love how your avatar is Linux taking a dump. I just wish the toilet said “Microsoft” on it or something.

>  That is probably about to change though, with lightworks being opensourced:
[http://ostatic.com/blog/powerful-video-editor-lightworks-released-as-open-source](http://ostatic.com/blog/powerful-video-editor-lightworks-released-as-open-source)
I hope that will make premiere look like a silly and buggy and incredibly overpriced piece of software. But we aint there yet. 
 

 Awesome.


 >  Besides video editing, there are other well known sore points like games, and to some extent photoshop (gimp comes close for most users, but not quite there for "pros's"). 
 

 Oh yeah. I'm strictly photoshop and bothered with that. But I'll be using Virtualbox for that one.
 

 >  That doesn't mean there is no professional quality programs for linux. Far from it. Much of the best software i run under windows is opensource software that is also (and often originally) native to linux, like openoffice, thunderbird, firefox, VLC, smplayer, inkscape, lyx, php/apache/mysql... I could go on. 


 Oh oh! Please do.
 

 What's lyx, php, apache, mysql.
 

 >  But if you're someone depending on specific windows-only apps like Premiere, Visual Studio, dreamweaver or photoshop, simple fact is windows will serve you better.
 

 I'm coming to terms with not using windows programs.
 
Thing is... when you make the transition from Windows to Mac, there's learning curve but all the industry standard programs will be able to make the transition (like photoshop) but that's not true with Linux. But, again, that's what virtualbox is for. I really hope we see some serious development from virtualbox.
 

 > **Max Destruction said:**
>  i should also add that im really impressed with blender. very professional-like quality.
those developers should be given trophies.
 

 Again, not to poke at any flaws of the Synaptic manager, but it gets me to wonder why there's not a 5 star rating system? There should be some sort of benefit for someone making a high quality program. It may not be financial but it should be able to boost their resume or something.
 

 Maybe if Synaptic were to count how many downloads were made for the programs and how good the star ratings are. Maybe there might be some sort of public recognition from Ubuntu that gives for that site... Maybe an official message that they might be able to receive stating that Ubuntu has found that their applications go far and above what's expected... or something. It doesn't have to be expensive, but it can still be something.
 

 I'm sorry if I'm talking about serious alterations to serious programs from a point of ignorance. I know that's probably what I sounds like and it's not really intended. I'm just talking about how I personally think it might be able to improve and give incentives to developers.
 

 (Thanks for mentioning Blender. I'm going to mess around with that one).
 

 I'm sure there's nothing like Zbrush yet though. But that's okay... I don't use Zbrush anyways.
 

 I mentioned blogging earier to promote Linux. If more people were to jump on board then I'm sure there's be a new and bigger group of programmers ready to contribute with the added mass of users. Some of these frustrations might be able to disappear through time.

---

### Post by P4man on 2010-05-01
>  Not to complain about Synaptic (because this really isn't one) but it would be nice to pop on there, and since it's somewhat like a store, why wouldn't it have advertisements for the programs there? … let it give you a chance to type in your interests and it gives suggestions based off of what tags might have been placed on the programs...  
 
Ubuntu software center is rather new and replaces a gnome program that actually had more features, like a popularity rating. They are working hard on it though, im sure it will get improved quickly, and some of the things you suggest are already in there, like the featured applications. You have seen the ubuntu software center, right? In the applications menu.


>  Do you know of an “unfree version”?
 
yes, but they are not for sale in bestbuy. Lightworks is one, there are some other hollywood studio grade packages you cant just buy (unless your name is Steven Spielberg).

 > 
 Oh yeah. I'm strictly photoshop and bothered with that. But I'll be using Virtualbox for that one.
 
Ive used photoshop for like 10 years. I still struggle a bit with gimp (withdrawal symptoms), but there is precious little it cant do. Here, a small teaser:
[http://www.youtube.com/watch?v=6OOYnZyY2rs&feature=related](http://www.youtube.com/watch?v=6OOYnZyY2rs&feature=related)


>  What's lyx, php, apache, mysql.
 
google on them :)
> 
 I'm just talking about how I personally think it might be able to improve and give incentives to developers.
 

Lets be real here. Developers need to eat. Best incentive is money. Not because they are greedy bastards but only if they get enough money to not need a daytime job can they really move projects forward. So donate a few bucks to the projects you need/like most and that are not sponsored by novell, canonical or oracle.

more and similar suggestions here:
[http://www.youtube.com/watch?v=YoYL4R3Te2s](http://www.youtube.com/watch?v=YoYL4R3Te2s)

---

### Post by CptPicard on 2010-05-01
orphanlast, I read your blog post and can't help but feel that you simply lack a lot of the  context behind the history of Linux and relevant OS concepts... you seem to base your views mostly on what the user sees. Of course, the really interesting bits of an operating system are somewhere entirely different, and on Linux it is instructive to understand that the entire graphics system is actually a completely separate collection of user-space processes that don't have much to do with the kernel itself.

This is quite different from, for example, Windows, that was so awfully unstable back in the day exactly because it was a shoddy graphical shell on top of DOS underpinnings, without any form of critical kernel parts' protection from other stuff running on the machine... architecturally it was so incredibly stupid that it didn't deserve to be called an "operating system". The Windows NT architecture that evolved to XP resolved a lot of these issues, which is why the BSODs became much more rare.

Now, at this point you really must go hit Wikipedia and read about the history of UNIX. In the old days, Unices were "Real Operating Systems", which appropriate user management, multitasking, networking, kernel/userspace process separation, memory protection and so on. These Real Operating Systems were also closed-off and horribly expensive because they ran on big machinery in basements and so on.

However, of course Real Hackers didn't like what they were seeing in "consumer" OSes and wanted their own UNIX, so Stallman started the GNU project which was still lacking the kernel when one was finally written for it in the form of Linux. So here we now had a pretty robust open UNIX implementation while the best-selling consumer OS was light-years behind in functionality.

So in this sense I kind of die a little when someone comes and proclaims that Linux is "catching up in the marketplace". It's Windows that has caught up in many under the hood things. The user toys that are getting prettier these days are relatively insignificant from the technical perspective, although I can understand that the end-user may see things differently.

Considering that my own "professionalism" in programming was initially learned in the 1990s, I can't understate the significance of having had the chance to run my own UNIX throughout that time. I honestly wonder what would have come of me if I had been programming only on Windows back then...

---

### Post by orphanlast on 2010-05-01
> **P4man said:**
> . 

Ubuntu software center is rather new and replaces a gnome program that actually had more features, like a popularity rating. They are working hard on it though, im sure it will get improved quickly, and some of the things you suggest are already in there, like the featured applications. You have seen the ubuntu software center, right? In the applications menu.


I was thinking about the Ubuntu Software Center when I wrote that. I like how it's much like the Android Market/App store. I still haven't seen any "featured items" but I wish there was a way to give the programs the star rating and even leave comments on there. But I just assumed that might actually be on the way. People also tell me that it's still kind of in he beta stages.

When I was more of a noob than I am now, that's what I thought was the only way to download programs on Ubuntu. I tried Fedora out for two hours and decided that I didn't like it simply because it didn't have an easy-to-find Software Repository like the Software Center. So I went back to Ubuntu. When I told someone here that that's what I was using they suggested Synaptic... sounded like no one takes the Software Center seriously though. I don't know why they suggested that I, as a noob use Synaptic. Even now, I think the software center is far more visual and comfortable. I also like the changes they made with the update. 

>  yes, but they are not for sale in bestbuy. Lightworks is one, there are some other hollywood studio grade packages you cant just buy (unless your name is Steven Spielberg). 
 

 Wouldn't that just be a kick in the Windows and Mac OS if Spielberg used Linux?  
 

 So if I just googled Lightworks I'd be able to find a place where I can buy and download it?
 

 >  Ive used photoshop for like 10 years. I still struggle a bit with gimp (withdrawal symptoms), but there is precious little it cant do. Here, a small teaser:
[http://www.youtube.com/watch?v=6OOYnZyY2rs&feature=related](http://www.youtube.com/watch?v=6OOYnZyY2rs&feature=related) 
 

 I actually knew about that but I've never been able to get it to look the way I've wanted my image to look at. But I'm sure I'm doing something wrong on the menu.
 

 My biggest complaint is that it doesn't appear as though Gimp has anything like a Vector Mask, I like how you can “erase without permanently erasing” (as a precaution, if you need to revisit the same project again.) You can't play around with the levels with a vector mask or anything like that either. So any changes to the hues and color saturations are all permanent alterations to the pixels.
 

 I also like photoshop's means to morph objects. It's as simple as making a selection, CTRL+T, right click select morph, click and drag to morph the object whatever shape you want.
 

 Gimp seems to only have the imorph filter where you just roughly eye it. Which isn't as exact, forces you to do necessary morphs, which mutilates pixels and asks for more repetition of a process that shouldn't take very long. But if you have suggestions that can get Gimp to do those things, I'm open to that. If I could just do those things, I'd be happy settling with Gimp.

>  Lets be real here. Developers need to eat. Best incentive is money. 
 If you have a good word from the biggest Linux distro for developing a great program that is downloaded thousands or tens of thousands of times annually and gets an average star rating of four or five that would boost a resume. That resume could play a big part in landing a developer in a job that gets them the money you're talking about. Currently they don't even have THAT incentive. The only incentive they have (right now) is to make their operating system what they thing an operating system should be and making programs that do as they'd personally like them to be... that's a good incentive, but why not try and do more?  
 

 I like how developers leave “donate” buttons on their programs. But that's not an award. And what's an award anyways? It's not monetary. It's a piece of metal or shiny plastic. It's a resume builder.
 

 That's what I'm suggesting.
 

 >  Not because they are greedy bastards but only if they get enough money to not need a daytime job can they really move projects forward. So donate a few bucks to the projects you need/like most and that are not sponsored by novell, canonical or oracle.

more and similar suggestions here:
[http://www.youtube.com/watch?v=YoYL4R3Te2s](http://www.youtube.com/watch?v=YoYL4R3Te2s)


 Thanks for the link. I'm looking at it now.

---

### Post by TheStatsMan on 2010-05-01
> **CptPicard said:**
> 
So in this sense I kind of die a little when someone comes and proclaims that Linux is "catching up in the marketplace". It's Windows that has caught up in many under the hood things. The user toys that are getting prettier these days are relatively insignificant from the technical perspective, although I can understand that the end-user may see things differently.


The whole notion that linux is catching up is not a sensible thing to say on here, particularly in the programming section. From our perspective Linux is a long way ahead, which is why we use it. Whilst, I like the whole idea of opensource software, if a proprietary product is better then I would use it. Linux is not simply for poor people who don't want to spend any money on an OS.  

The 'toys' that the user gets are now pretty fantastic, particularly for the KDE users. Lucid is a really strong distribution.  In my opinion whilst we have always had the advantage under the hood,  the UI (particularly in Kubuntu 10.04) is also a step ahead of the competition. It is just marketing where Linux fails. 

Take android for instance, it has been a huge success. Two reasons, marketing from Google and the fact that someone else is setting up the linux system for the user.

---

### Post by P4man on 2010-05-01
> **orphanlast said:**
> I still haven't seen any "featured items" 

Maybe the orange isnt bright enough?

[[img]http://www.ubuntu-pics.de/thumb/55675/screenshot_002_C21RzN.png[/img]](http://www.ubuntu-pics.de/bild/55675/screenshot_002_C21RzN.png)
 
> 
 Wouldn't that just be a kick in the Windows and Mac OS if Spielberg used Linux?  
 
AFAIK a lot of hollywood companies like industrial light and magic already run linux, and have for many years.
> 
 So if I just googled Lightworks I'd be able to find a place where I can buy and download it?

?
 
> But if you have suggestions that can get Gimp to do those things, I'm open to that. If I could just do those things, I'd be happy settling with Gimp.

Non destructive editing is coming with the next release (which wont be here before the end of the year mind you), but the other things you mention, I dont know.

> 
 I like how developers leave &#8220;donate&#8221; buttons on their programs. But that's not an award. And what's an award anyways? It's not monetary. It's a piece of metal or shiny plastic. It's a resume builder.
 
Well, you can always come work here, give up your day job, whatever your skills Ill find you a job,  and ill pay you as many rewards as you want. Deal?

talented software developers are worth a lot of money. Its rather simple, the guys writing KDEnlive or gimp can start working for Adobe tomorrow. They are people like anyone else with a mortgage, a family, and a long wishlist. Sure some award might be nice, but the guy developing Gimp IIRC collected like $20.000 in donations in a year (from the clip you are watching now, correct me if i remember wrong).  You think an ubuntu award will prevent him from joining adobe for a 5x higher paycheck? I wouldnt count on it.

---

### Post by CptPicard on 2010-05-01
> **TheStatsMan said:**
> Whilst, I like the whole idea of opensource software, if a proprietary product is better then I would use it.

Fully agreed, I am not ideological about FOSS. But I do find it very "nice" that the concept of a "freely extensible open body of work" can function in our day and age where it seems like some people can't even fathom that such a thing could be :)

> 
The 'toys' that the user gets are now pretty fantastic, particularly for the KDE users.

Yes -- I have always been a KDE guy exactly because KDE had the architecture right from the start. KIOslaves and KParts, for example...
 been a huge success. Two reasons, marketing from Google and the fact that someone else is setting up the linux system for the user.[/QUOTE]

---

### Post by sventek on 2010-05-01
hi Orphanlast
you mentioned that you finally got Quicktime to work?  How did you do that, if I may ask because I have been trying to do that for like a year now.?  thanks

---

### Post by ajackson on 2010-05-01
> **orphanlast said:**
> If we're using the the word “learn” in the conventional sense, I'd say “no”. I don't recall learning how to speak, but I guess I did, otherwise I wouldn't be speaking and writing in English. I learned Windows much the same way. It's just what I did.  It wasn't really a thought process or effort behind it.
Congratulations you've mastered the art of learning without using thought processes, medical science would like your brain :)

Learning by trial and error is still learning, learning by being taught in a classroom is also learning. Using the conventional sense of the term "learn" you learnt how to use Windows, you learnt how to read and write English. About the only things you didn't learn are the stuff that is hard wired in your body (boring stuff like breathing, getting your heart to pump, etc).

As for seeing advertisements on the internet, surely that can apply to non-Windows stuff as well, can you finally admit that you learn about software by doing some form of research whether it is a Windows app or a Linux app?

---

### Post by steveneddy on 2010-05-01
After reading the first three pages of this thread, here is the impression that I get from the OP merely from his/her replies:

1. really needs to get to know how Linux/Ubuntu works before trying to install software

2. Needs to ask questions before jumping into the deep water

3. The applications offered with Ubuntu are not developed by Ubuntu developers - they are owned by the respective developers - kdenlive devs are not Ubuntu devs

4. OP needs to realize that Linux is merely an operating system and Ubuntu is merely a collection of OS and applications

5. Linux/Ubuntu is NOT Windows. OP needs to learn to do things the Linux way and not expect every OS to operate like Windows.

My opinion on Windows:

Windows is marketed to the least common denominator and most people have only used Windows and due to that situation these people that have used Windows for many years think that the Windows way of doing things is the only way.

Using Linux of any type will make the end user learn many new ways of using the PC and maybe even learn something about computers.

Windows is designed like a toy and operates in the same way. IMHO, Windows is a poor example of an operating system.

To the OP: Take the time to learn to the Linux way and forget everything you learned in Windows.

You may do better by running Ubuntu in VirtualBox under Windows until you get a better handle on Ubuntu.

Ubuntu/Linux isn't hard, just different. The learning curve is steep. Linux is not for everyone. Use the OS that you feel the most comfortable with.

*****************

To address your issue with kdenlive - try different versions of kdenlive or upgrade/downgrade the OS until you find a combination that works for you. I am still on Intrepid 8.10 because this combination of OS and applications works for me at this time. The latest Ubuntu release isn't the best choice for every person/hardware/application choice.

The great thing about Linux is choice. You can choose the OS version, applications, GUI style and an endless list of other options to suit your needs. You just need to spend some time getting to know Linux and Ubuntu before trashing the developers.

---

### Post by orphanlast on 2010-05-01
> **sventek said:**
> hi Orphanlast
you mentioned that you finally got Quicktime to work? How did you do that, if I may ask because I have been trying to do that for like a year now.? thanks


 Wow, a year? And I thought I had it rough having to look for two days.
 
Uhh... if you have Ubuntu 10.04 it does all the work for you. All that you have to do is go to Apple.com, or any website where it plays quicktime, and right now there's a big picture of the imaxipad, fortunately with no blood on it... yet...  
 

 Anyways, click on the ipad picture, then click on the &#8220;Watch the Guided Tour&#8221; link. Then it'll have a picuture of an ipad and a cup of coffie next to it. Click on that. If you have 10.04 then Ubuntu will automatically notice that you're trying to open a file that it doesn't recognize. It'll offer to find and download the software that'll get it to run properly (much like Vista *the sound of Angel Chiors*). If you're streaming Quicktime videos you'll get video but you won't get audio. Right click on the video when it starts playing all muted. It'll give you the option of playing it on &#8220;Movie Player&#8221;. So you'll be able to watch online Quicktime, but you have to do it sort of ghetto with another program.
 

 If you don't have Ubuntu 10.04 then this is what you do. Go to Synaptic and download &#8220;Gecko Media Player&#8221;. I think it's got a much needed codec that'll help with that. Why does Ubuntu not have that in the first place? Because of national and international copy write restriction laws.
 

 > **P4man said:**
> Maybe the orange isnt bright enough? 


 That's all bright and colorful. Lol. Actually I only spent a brief moment or two on it since the upgrade to 10.04. So no, I didn't notice because I was just skimming over it. 
 
(By the way, I asked you if I would be successful in buying something online if I googled it because I didn't want to get stuck in a wild goose chase LOOKING but not finding).

>  Non destructive editing is coming with the next release Good! It'd be awesome if it had the panoramic option but that's getting too hopeful. Virtualbox is still great. Lol... I know it sounds like I just keep expecting all sorts of things, but I'm really not... I'd love to spend money on the Gimp project especially... but there's a bit of a fear that I might spend money on a project that might go a direction I don't want it to be going. And so I'd start pissing and moaning that I'm a financial contributor and start doing something like a special interest group and make demands or pull funding. Lol.... but then again it's open source. So that might be less likely to happen.
 

 >  Well, you can always come work here, give up your day job, whatever your skills Ill find you a job, and ill pay you as many rewards as you want. Deal?  Well, as long as it's part time, flexible hours, and has to do with Graphic Design, I'm in. Freelance work with a few trophies would be awesome. I don't know about quitting the day-job thing though. Freelance work would be hard while relying on begging out in the streets and the occasional five dollars for cleaning someones massive yard.
 

 Are you saying most linux developers devote their entire life for Linux and barely get paid? They QUIT their day job?
 

 Pay IS nice, but someone made the remark that the developers should have gotten some recognition with a reward. I was just thinking on paper as to how we could give that reward out to the people that have done a great job.
 

 As soon as I'm not having to deal with a bankruptcy I'll be sure to donate some money to the best programs. By any chance, and I'm assuming you're programing stuff, what are you currently working on?

>  talented software developers are worth a lot of money. Its rather simple, the guys writing KDEnlive or gimp can start working for Adobe tomorrow. They are people like anyone else with a mortgage, a family, and a long wishlist. Sure some award might be nice, but the guy developing Gimp IIRC collected like $20.000 in donations in a year (from the clip you are watching now, correct me if i remember wrong). You think an ubuntu award will prevent him from joining adobe for a 5x higher paycheck? I wouldnt count on it. Yeah, you're probably right. That'd be like your biggest competitor deciding to work for you. I perceived that possibly the developers might work on these programs as a hobby or on their time off because they were passionate about making their operating system THEIR operating system and sharing it with others in a fully open system. But it looks like many of them are wanting to make their living off the donations. I admit, that would be hard to work with. The only thing that I think would be the easiest way of getting that done would be "Getting as many people to use Linux as possible," even if that means doing what steveneddy calls appeasing the "lowest common denominator" and making it "operate like a toy". (This isn't a criticism of Linux or Ubuntu, as is. I'm just saying, the best way of getting more donations and bigger donations is getting more people to donate and use the product by getting them to feel like it's what they need or want. If there's a way to get the settings on Ubuntu to be so simplistic that my grandma could use it, awesome.)

 > **ajackson said:**
> Congratulations you've mastered the art of learning without using thought processes, medical science would like your brain  :smile: 
 
 &#8230; lol. There just wasn't an effort to set out and learn it. It's just what was done. I couldn't conceive doing things any other way because that's how you get the computer to do it. The same as I just can't think of any other way of communicating this in English. It's the only language I know... and that's just how things are done... for me, and this part of the country.

>  Learning by trial and error is still learning, learning by being taught in a classroom is also learning. Using the conventional sense of the term "learn" you learnt how to use Windows, you learnt how to read and write English.  I'm sure you can't tell me how you learned your native language. So would it be fair to say that you learned how to write and possibly program computers through the same effort and method? Personally, I'd say no. My earliest memories only extend to the point to where I was already speaking. My parents bought a computer and I grew up playing with the mouse on windows 3.1 (lol).  
 

 I guess, like learning a native language it was mostly &#8220;mokey see monkey do&#8221; where as this is all independent research through the school of hard knocks.
 

 >  About the only things you didn't learn are the stuff that is hard wired in your body (boring stuff like breathing, getting your heart to pump, etc).  Those aren't boring. Those are awesome. If I could control all those things I'd be a happy camper and I'm sure most people would. I'd tell my digestive system just what to do with that five pounds of ice cream I ate &#8211; send stuff that to the pooper! I'd only have one annual haircut. Never, or hardly ever, need to clip my stupid nails. I wouldn't grow hair in my arm pits. I'd get rid of my useless male nipples. I'd find some way to distribute some sort of cleaning bodily fluid to make sure I'd never have to brush my teeth and I'd work out a way to give myself telescopic vision. I'd totally take the Linux approach to my body. Lol.


 >  As for seeing advertisements on the internet, surely that can apply to non-Windows stuff as well, can you finally admit that you learn about software by doing some form of research whether it is a Windows app or a Linux app? I wouldn't call watching someone else do it research. That's spoon feeding. And what do you mean &#8220;finally admit&#8221;. I didn't know we'd been talking about that for a long time. 
 

 Whatever, I guess I learned windows. But in my defense, I learned it in a more simplistic environment through a completely different structure and it's just HOW IT WAS DONE the same as speaking English is just HOW IT'S DONE in my life.
 

 Dude, where's John Sherridan when you need him?  
 

 > **steveneddy said:**
> Windows is marketed to the least common denominator and most people have only used Windows and due to that situation these people that have used Windows for many years think that the Windows way of doing things is the only way. 
 

 Well... the lowest common denominator doesn't always mean &#8220;wrong&#8221; or &#8220;bad&#8221; either, most especially if that means Linux will get quite a bit more exposure and approval. It would become the standard. But, to show that that's not entirely what I'm promoting, take a look at this blog I posted a week or two before I made this threat titled &#8220;Why You Need Ubuntu&#8221;: [http://hubpages.com/hub/Why-You-NEED-Ubuntu-Linux](http://hubpages.com/hub/Why-You-NEED-Ubuntu-Linux) . There can be aspects or packages for Linux that can appease those people to shut them up and have more intensive parts for the more advanced user.
 

 During my first week on Ubuntu 9.10 I was downloading all sorts of programs from the Ubuntu Software Center and I thought I was downloading cute applications. I had no idea that the whole thing was oriented around free software until I read the Ubuntu Pocket Guide.


 >  You can choose the OS version, applications, GUI style and an endless list of other options to suit your needs. You just need to spend some time getting to know Linux and Ubuntu before trashing the developers. I sure hope I'm not just trashing developers. I am planning on learning Ubuntu 10.04 all the way, and have plans on learning programing as a hobby and Linux has sort of inspired that desire. It started with my POS Android phone though (It's a mytouch, that's why it's a POS) and that's still Linux.
 

 I'm learning. And I feel like I'm slowly getting comfortable with Linux. I'm primarily going to stick it out with Ubuntu simply because it's where most Linux users are and as long as people are settling with one distro it means that Linux will start having standardized formats for stuff. That would get us further away from incompatibility issues, I think.

---

### Post by Samhain13 on 2010-05-02
OT:

> **P4man said:**
> more and similar suggestions here:
[http://www.youtube.com/watch?v=YoYL4R3Te2s](http://www.youtube.com/watch?v=YoYL4R3Te2s)

Thanks for the link. I found the Resynthesizer in the Lucid repositories, playing with it now. :guitar:

---

