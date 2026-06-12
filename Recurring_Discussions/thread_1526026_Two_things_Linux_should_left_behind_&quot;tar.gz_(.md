---
title: "Two things Linux should left behind: &quot;tar.gz (compiling)&quot; and &quot;sudo apt-get install&quot;"
date: 2010-07-07
forum: Recurring Discussions
---

### Post by alexan on 2010-07-07
quit with tar.gz for general distribution: let the tar.gz to their only use = collect source to compile/study. --- evolute to ---> deb or deb+rpm or (even better) deb repository for latest ubuntu release.


sudo apt-get install:
[alt]+[f2] > apt:/[namepackage]
let apt-get usage for specific techy needs.. and move forward to human logic friendliness.

---

### Post by RiceMonster on 2010-07-07
I don't get it, this is pretty much already the case.

tarballs are used for source code, or in some cases for distro agnostic binaries.

There is already GUI options in most distros for installing software. Software Centre, PackageKit, YaST, etc.

---

### Post by Redache on 2010-07-07
In short: No.

At length: using compressed source is the best way to have distribution neutral source code, it doesn't matter what distribution you have as long as you meet the dependency requirements then the application will compile and run.

What would you prefer? a downloadable binary that can contain anything?.

---

### Post by koenn on 2010-07-07
> **alexan said:**
> quit with tar.gz for general distribution: let the tar.gz to their only use = collect source to compile/study. --- evolute to ---> deb or deb+rpm or (even better) deb repository for latest ubuntu release.


sudo apt-get install:
[alt]+[f2] > apt:/[namepackage]
let apt-get usage for specific techy needs.. and move forward to human logic friendliness.


In ubuntu,
compiling from source tarbals has been replaced by the distribution of compiled programs in .deb packages, and
'sudo apt-get install" has been replaced with synaptic and software center.

There,
done.

---

### Post by nothingspecial on 2010-07-07
> **alexan said:**
> quit with tar.gz for general distribution: let the tar.gz to their only use = collect source to compile/study. --- evolute to ---> deb or deb+rpm or (even better) deb repository for latest ubuntu release.


sudo apt-get install:
[alt]+[f2] > apt:/[namepackage]
let apt-get usage for specific techy needs.. and move forward to human logic friendliness.

No.

That`s not the point.

---

### Post by Warpnow on 2010-07-07
I'm also going with:

No.

---

### Post by alexan on 2010-07-07
> **RiceMonster said:**
> tarballs are used for source code, or in some cases for distro agnostic binaries.

The probleam are, indeed, the "cases" of distro agnostic software distributor. I mean, it's fine to put tar.gz... but what the propose to put _only_ tar.gz?
It's a subethical choice: you want promote freedom by forcing *everyone else* to follow your way of freedom.

The "network" of dependencies provided by deb/rpm would look the exe/msi a really obsolete way to provide software.
> **Redache said:**
> In short: No.

At length: using compressed source is the best way to have distribution neutral source code, it doesn't matter what distribution you have as long as you meet the dependency requirements then the application will compile and run.
In short, No. You don't only need to meed the dependencies, you need many layer of dependencies to look after
Example: the software/resource to compile (useless stuff you could remove once installed... but remain there "forever"), the right +vesion of the dependencies and many little "extra" you may find in the README or INSTALL file (place your bet: one (or both) of these two file contain the "true" info to have your software.
tar.gz should mainly aimed to distro maintainer developer: if someone want to "push his/her software" try anything else but deb/rpm/repositories it's just pointless.


> **Redache said:**
> What would you prefer? a downloadable binary that can contain anything?.
When a friend of mine ask to me: "it's easy install software (ie: nerolinux) in linux?"
I would simple prefer answer: "yes".
> **koenn said:**
> In ubuntu,
compiling from source tarbals has been replaced by the distribution of compiled programs in .deb packages, and
'sudo apt-get install" has been replaced with synaptic and software center.

There,
done.

See RiceMonster and Redache: what you're talking about don't even exist! (just joking)

Seriously: the software you see in software manager is bring there by the effort of some people who download/compile/_clean the source code_ to make it run smooth in Ubuntu/Fedora&co.

If there was some sort of really rational standard (and "not only" tar.gz is not), the work of these cool people would be a lot more easily.
The maintainer of Fedora repository can see the rules of Ubuntu (which is opensource) bring 100 new software delivered in deb, for lucid lynx, is more easly than open 100 different README (just an example)

---

### Post by wyliecoyoteuk on 2010-07-07
So you are saying :
lose the choice.
Linux is about choice, lots of it. you don't need to use tarballs if you don't want to, and developers don't have to supply anything but source if they don't want to.
The main reason for there only being a tarball is because no-one has got around to converting it to a binary, either because no-one with the skills to do so is interested, or has the time.

---

### Post by RiceMonster on 2010-07-07
> **alexan said:**
> but what the propose to put _only_ tar.gz? It's a subethical choice: you want promote freedom by forcing *everyone else* to follow your way of freedom.

Because the distros are expected to package it and distribute it within their own repositories anyway.

> **alexan said:**
> If there was some sort of really rational standard (and "not only" tar.gz is not), the work of these cool people would be a lot more easily.
The maintainer of Fedora repository can see the rules of Ubuntu (which is opensource) bring 100 new software delivered in deb, for lucid lynx, is more easly than open 100 different README (just an example)

So what you really want is a standard package format? LSB already says it's rpm, but clearly not everyone agrees that's the way it should be. Not to mention packages can still be incompatible across distributions.

---

### Post by Penguin Guy on 2010-07-07
I see what you mean - time is wasted converting between source code, [FONT="Courier New"].deb[/FONT], [FONT="Courier New"].rpm[/FONT] and other formats. Someone should create a master package format that can easily and automatically export to all other package formats. The closest thing to this is Python's [FONT="Courier New"]setup.py[/FONT].

---

### Post by Redache on 2010-07-07
> but what the propose to put only tar.gz? It's a subethical choice: you want promote freedom by forcing everyone else to follow your way of freedom.


I would like to point out that subethical isn't a word, you are not below ethics, you are unethical.

I also disagree with your point, most distributions do convert these source tarballs into easy to install packages. Maybe you feel distro's should update package repositories more frequently?. With a 6 month release cycle I think this is an unnecessary step to take as most applications will take that long to become stable releases.

---

### Post by koenn on 2010-07-07
> **RiceMonster said:**
> 
So what you really want is a standard package format? LSB already says it's rpm, but clearly not everyone agrees that's the way it should be. Not to mention packages can still be incompatible across distributions.
... so what we reallyneed to fix this is a unified package format, a unified set of conventions about which file goes where, unified configs and defaults for all available software, ... a Grand Unified Linux Distro. 


which way to Recurring ?

---

### Post by Johnald The Robot on 2010-07-07
> **alexan said:**
> It's a subethical choice: you want promote freedom by forcing *everyone else* to follow your way of freedom.

So what you're saying is that to be free we should give up other choices and go for one instead?

In that case can I just throw in my two cents and say if ubuntu does this then I suggest that the "tar.gz (compile)" way should be the one we use to install stuff. I mean I've learnt a lot from compiling programs to compile other programs. It's part of the linux experience. 

Some people might say it's hard but think about it, wasn't it hard to walk or ride a bike or do long division? Sure having the source code in .tar.gz is a little trickier but after a few times it will more or less be second nature and you could probably compile and run software on any linux! 

This is the only way to be free! Forcing people to use ONE way to install software instead of giving harder and *subethical* choices.

---

### Post by alexan on 2010-07-07
> **Johnald The Robot said:**
> So what you're saying is that to be free we should give up other choices and go for one instead?
No
What's the index of a book?
A "stuff" that you find (usually) at the start of book.
You take a book, open it and go to the first pages knowing you'll find it. It a very basic/simple rule... "simplicity" it's the way the index of books works.
I've "always" the book with all its content... but the book with the index (a easy, clear and simple way to _superficially_ access to the contenent) allow you browse quickly different tomes looking for the chapter you need. Any writer think about his/her tale.. and don't care about giving you "quick access" to jump over his/her work.

This is not good. This is why *editors* _always_ force an index in the books

tar.gz are these book without the index: read the manual of the manual.. then you *discover* how use the book.

That's all I am talking about.
Tar.gz is welcome for it's propose: share source code, help distro maintanier, programmer and other specific propose.
What's tar.gz _its not_... is for distribute software.

Programmer who prefer use tar.gz is like a poet which refuse the index for his/her book (too "closed" for his "free mind"). The result, is a book which readers will keep closed (and will download exe/msi)

---

### Post by koenn on 2010-07-07
you're still barking up the wrong tree

if you've come across software that is not packaged for your distro, talk to the distro maintainers to package it.

A general plea against tarbals  like the one you started with, is completely besides the question.

---

### Post by Crunchy the Headcrab on 2010-07-07
I don't even get what you're talking about.  I'm going to see everyone's "no" and raise them a "wtf"?  It sounds like you're bent on forcing developers to distribute software in a way that you see fit AND causes additional work for them.

---

### Post by Bachstelze on 2010-07-07
> **alexan said:**
> 
That's all I am talking about.
Tar.gz is welcome for it's propose: share source code, help distro maintanier, programmer and other specific propose.
What's tar.gz _its not_... is for distribute software.

Programmer who prefer use tar.gz is like a poet which refuse the index for his/her book (too "closed" for his "free mind"). The result, is a book which readers will keep closed (and will download exe/msi)

The developers of a piece of software and the maintainers of a distribution are usually different people. If the developers don't release a tarball, how on Earth are the distributors supposed to get the source and build packages from it?

---

### Post by Johnald The Robot on 2010-07-07
So you're saying it should be easy? Well nothing's really stopping you going taking the easy route, although I did think my tar.gz idea was good.

Also I don't understand your analogy. It could be because ubuntu can't run exe/msi or it could be because it wasn't in english I'm not sure....

A better analogy is saying that software are like fish. There are big fish and there are small fish and sometimes fish can smell. Fish come in different shapes and textures too e.g. a jellyfish is like made of jelly and a trout is made of ... erm fish bits. Anyway some people like different fish and like to do different things with fish, just like with software it's different and everyone has different preference in software (fish). Someone who doesn't like a certain way of software distribution is like someone who doesn't like fish that come in a tin can because the fish were brought up in *subethical *conditions. Some people like tinned fish though but it's hard to get fish out of a tin (like it's hard to get software out of tar.gz).

The point of this is that ubuntu is a free area with different fish for everyone which you can choose which fish you want to have . I mean without all freedom of choosing what fish we prefer we'd be stuck with... uh I dunno.. lets say smoked mackrell cause I really don't like smoked mackrell. Not all fish are smoked mackrell.

---

### Post by v1ad on 2010-07-07
apt-get ftw.

as easy as it gets.

---

### Post by aysiu on 2010-07-07
> **alexan said:**
> quit with tar.gz for general distribution: let the tar.gz to their only use = collect source to compile/study. --- evolute to ---> deb or deb+rpm or (even better) deb repository for latest ubuntu release. It's already been quit. .tar.gz files are not for general distribution. They're for developers to package for general distribution.

If I want to install software, I don't go to that software maker's website to download .tar.gz. That's what the Ubuntu developers do. They package the compiled source code *for me* so I can just install software through the repositories.


> sudo apt-get install:
[alt]+[f2] > apt:/[namepackage]
let apt-get usage for specific techy needs.. and move forward to human logic friendliness. Again, already happened. *apt-get* is there for specific techy needs. Anyone else can use Synaptic Package Manager or Ubuntu Software Center.

---

### Post by Penguin Guy on 2010-07-07
I never package my programs - I can't be bothered. Since you're so passionate about this however, feel free to package them for me: [https://launchpad.net/~joshbrown](https://launchpad.net/~joshbrown)

The point I am making is that it's not the programmer's duty to package their programs any more than it is yours. In fact, seeing as they've written the program for _free_, maybe someone else should do their part? If you've never packaged a program I don't think you can truly comprehend the amount of time the packaging process takes - again I urge you to have a go, perhaps then you will see why so many programs remain unpackaged.

You must also take into consideration that programs must be packaged separately for each package manager. This is why the programmer usually makes the [FONT="Courier New"].tgz[/FONT], and other people, from their respective package managers, package it.

---

### Post by SunnyRabbiera on 2010-07-07
Firstly tar.gz is there to be a neutral format for all linuxes to deal with, not all deal in debs or RPM's

Secondly sudo apt-get install is only there for profiling, use synaptic it does the same thing.

---

### Post by Penguin Guy on 2010-07-07
> **Johnald The Robot said:**
> software are like fish. There are big fish and there are small fish and sometimes fish can smell. Fish come in different shapes and textures too e.g. a jellyfish is like made of jelly and a trout is made of ... erm fish bits. Anyway some people like different fish and like to do different things with fish, just like with software it's different and everyone has different preference in software (fish). Someone who doesn't like a certain way of software distribution is like someone who doesn't like fish that come in a tin can because the fish were brought up in *subethical *conditions. Some people like tinned fish though but it's hard to get fish out of a tin (like it's hard to get software out of tar.gz).
Ahh - *now* it makes sense.

---

### Post by YeOK on 2010-07-07
Wow, I've read some threads in my time but this has to be the most surreal. I mean, tar.gz compared to an index in a book ? 

tar.gz can't be replaced. You can not even compare a source release to a .rpm or .deb, not even the same thing. Upstream releases software, they release as source code tar.gz, binary packages are the domain of downstream.

---

### Post by Simian Man on 2010-07-07
This is one of the biggest threats to the open source world: people getting involved and vocal when they have *no god-dam idea* what they're talking about.

---

### Post by Bachstelze on 2010-07-07
> **Simian Man said:**
> This is one of the biggest threats to the open source world: people getting involved and vocal when they have *no god-dam idea* what they're talking about.

Big +1.

---

### Post by Dustin2128 on 2010-07-07
> **alexan said:**
> No
What's the index of a book?
A "stuff" that you find (usually) at the start of book.
You take a book, open it and go to the first pages knowing you'll find it. It a very basic/simple rule... "simplicity" it's the way the index of books works.
I've "always" the book with all its content... but the book with the index (a easy, clear and simple way to _superficially_ access to the contenent) allow you browse quickly different tomes looking for the chapter you need. Any writer think about his/her tale.. and don't care about giving you "quick access" to jump over his/her work.

This is not good. This is why *editors* _always_ force an index in the books

tar.gz are these book without the index: read the manual of the manual.. then you *discover* how use the book.

That's all I am talking about.
Tar.gz is welcome for it's propose: share source code, help distro maintanier, programmer and other specific propose.
What's tar.gz _its not_... is for distribute software.

Programmer who prefer use tar.gz is like a poet which refuse the index for his/her book (too "closed" for his "free mind"). The result, is a book which readers will keep closed (and will download exe/msi)

I don't really see your analogy but I disagree strongly with you on the last point. distributing in tar.gz format allows the programmer  to distribute to all distros because all the end-user has to do is compile it for his or her system, something the vast majority of linux users don't mind doing. In fact, I've had *less *difficulty at times compiling from source than using the repository. Removing choice will ***_not_ ***improve the operating system, it will destroy it. I don't know about you but I personally would never install a binary from anyone I don't trust quite a lot (NGD, google, those are the only sources I've installed from) and swapping from tarballs to binaries would make linux tenfold more vulnerable to malware imho. I still think this is another one of those 'linux should be more like windows' threads though,  I'd stick it in recurring.
> **Simian Man said:**
> This is one of the biggest threats to the open  source world: people getting involved and vocal when they have *no  god-dam idea* what they're talking about.
+ 9001

---

### Post by jwbrase on 2010-07-07
> **Bachstelze said:**
> The developers of a piece of software and the maintainers of a distribution are usually different people. If the developers don't release a tarball, how on Earth are the distributors supposed to get the source and build packages from it?

Well, what I think he's advocating is that developers distribute debs and rpms of their programs alongside tarballs. Which, frankly, I do somewhat sympathize with. 

Devs devving for Linux seem to be in love with distributing source-only tarballs, with the only way to get a binary being to either get it through your distribution's repository (if it's in there) or to compile it yourself. FOSS devs on Windows, OTOH, tend to release a zip of the precompiled program (which is actually my favorite distribution format), or an MSI (not my favorite format, but better than compiling from source if you don't want to modify the program). In fact, it's possible to find programs nominally developed primarily for Linux where a source tarball and a precompiled Windows zip/MSI are available on the project's homepage, but no precompiled Linux binary.

It's not even really the tarball that's the problem, it's what the tarball contains, namely, nothing but source. A combined source/binary tarball, or the availability of a binary tarball (or, for bonus points, *.deb or *.rpm) along side the source one would be excellent. 

But where the OP is mixed up is that this isn't a (mal)feature of Linux, simply a very infuriating habit of a whole ton of developers.

---

### Post by Penguin Guy on 2010-07-07
> **simian man said:**
> this is one of the biggest threats to the [s]open source[/s] world: People getting involved and vocal when they have *no god-dam idea* what they're talking about.
+ &#8734;

---

### Post by Stancel on 2010-07-07
Chrome uses deb for installation.
Guess what Firefox uses? Tar.

Yet the file for Windows Firefox is an exe. 

I know some people like to rant about n00bs but the truth is, if you want the programs to be easily installed, you should use something that actually installs the program. Deb is comparable to exe, while tar is comparable to a zip file.

If Firefox released their browser in Windows under a zip file, people would be so pissed off.

---

### Post by aysiu on 2010-07-07
> **Stancel said:**
> Chrome uses deb for installation.
Guess what Firefox uses? Tar.

Yet the file for Windows Firefox is an exe. 

I know some people like to rant about n00bs but the truth is, if you want the programs to be easily installed, you should use something that actually installs the program. Deb is comparable to exe, while tar is comparable to a zip file.

If Firefox released their browser in Windows under a zip file, people would be so pissed off.
But the way to install Firefox on Linux is through the package manager. The way to install Firefox on Windows is going to the Firefox website.

I don't need to get the Firefox .deb from Mozilla when I can get it through the Ubuntu repositories.

---

### Post by Bachstelze on 2010-07-07
> **Stancel said:**
> Chrome uses deb for installation.
Guess what Firefox uses? Tar.

Yet the file for Windows Firefox is an exe. 

I know some people like to rant about n00bs but the truth is, if you want the programs to be easily installed, you should use something that actually installs the program. Deb is comparable to exe, while tar is comparable to a zip file.

If Firefox released their browser in Windows under a zip file, people would be so pissed off.

Mozilla is a non-profit, and Google is.. well, we know about Google. If Google can hire someone to build packages for every distro out there, more power to them. Maybe Mozilla can't (just a guess).

Either way, why do you care about how Mozilla distributes Firefox for Linux? As was said countless times, building distro-specific packages is the distributor's job. Microsoft don't build EXEs for Firefox, so the Mozilla guys have to do it themselves. I'm sure they'd rather not, it makes that much more time available for improving the software.

---

### Post by jwbrase on 2010-07-07
> **YeOK said:**
> Upstream releases software, they release as source code tar.gz, binary packages are the domain of downstream.

Upstream has to at least have the copy they decided worked well enough that the program could be released. Can't they just shove that into the tarball with the source?

---

### Post by Dustin2128 on 2010-07-07
> **Stancel said:**
> Chrome uses deb for installation.
Guess what Firefox uses? Tar.

Yet the file for Windows Firefox is an exe. 

I know some people like to rant about n00bs but the truth is, if you want the programs to be easily installed, you should use something that actually installs the program. Deb is comparable to exe, while tar is comparable to a zip file.

If Firefox released their browser in Windows under a zip file, people would be so pissed off.

Ah, but linux users and windows users are two totally different sets of people. Do you know how pissed off I am that chrome *didn't *release a tarball for me to compile (at least that I can find...)? Quite pissed off, can't install it on some of the non deb/rpm distros I use, which are many. Sure there are workarounds like slackbuilds but it'd be so much easier if they, like almost every other linux software provider in the world, released in a tarball *as well*.

---

### Post by Rey117 on 2010-07-07
> **Simian Man said:**
> This is one of the biggest threats to the open source world: people getting involved and vocal when they have *no god-dam idea* what they're talking about.

+ 1 chuck norris

---

### Post by koenn on 2010-07-07
> **Stancel said:**
> Chrome uses deb for installation.
Guess what Firefox uses? Tar.

Yet the file for Windows Firefox is an exe. 

I know some people like to rant about n00bs but the truth is, if you want the programs to be easily installed, you should use something that actually installs the program. Deb is comparable to exe, while tar is comparable to a zip file.

If Firefox released their browser in Windows under a zip file, people would be so pissed off.

what aysiu said.
+ I'm posting from a Firefox on Ubuntu. I've never seen a Firefox tarbal in my entire life. 

and, also, there's still quite a bit of software for Windows that is released as a zip archive. Just saying. 

I agree with the "This is one of the biggest threats to the open source world: people getting involved and vocal when they have no god-dam idea what they're talking about."

---

### Post by aysiu on 2010-07-07
> **Dustin2128 said:**
> Ah, but linux users and windows users are two totally different sets of people. Do you know how pissed off I am that chrome *didn't *release a tarball for me to compile (at least that I can find...)? Quite pissed off, can't install it on some of the non deb/rpm distros I use, which are many. Sure there are workarounds like slackbuilds but it'd be so much easier if they, like almost every other linux software provider in the world, released in a tarball *as well*. Don't they release Chromium as source?
[http://code.google.com/chromium/](http://code.google.com/chromium/)

---

### Post by DrMelon on 2010-07-07
Good luck trying to run this past FOSS fanatics.
Not to mention, there is a deb for firefox. I don't see the issue.

---

### Post by aysiu on 2010-07-07
> **DrMelon said:**
> Good luck trying to run this past FOSS fanatics.
Or even just anyone who understands how software works.

---

### Post by Dustin2128 on 2010-07-07
> **aysiu said:**
> Don't they release Chromium as source?
[http://code.google.com/chromium/](http://code.google.com/chromium/)
They did but I still can't find what I'm looking for, found one 'source code tarball' but it was implausibly large, over 700Mb so I didn't download it. Show me the tarball!

---

### Post by jwbrase on 2010-07-07
> **aysiu said:**
> But the way to install Firefox on Linux is through the package manager. The way to install Firefox on Windows is going to the Firefox website.

I don't need to get the Firefox .deb from Mozilla when I can get it through the Ubuntu repositories.

For Firefox, we don't. For, say, [Be the Wumpus]("http://bethewumpus.sourceforge.net/"), it sure would be convenient if upstream gave us the most rudimentary of binary packages, as there is no downstream. 

> **Bachstelze said:**
> Mozilla is a non-profit, and Google is.. well, we know about Google. If Google can hire someone to build packages for every distro out there, more power to them. Maybe Mozilla can't (just a guess).

A tarball of the author's copy of the binary would probably work on most Linux machines, at least for small programs for a single user (simply create a folder in your home directory and unpack it there). A single *.rpm would be even better, and could be converted with Alien to *.deb format at a pinch, before the Debian and Ubuntu repositories caught up. 

> 
Either way, why do you care about how Mozilla distributes Firefox for Linux? As was said countless times, building distro-specific packages is the distributor's job.

But I'm not looking for a package fine-tuned for my distro unless the program absolutely requires such fine-tuning to work, which is not my experience with most packages. I'm just looking for a working Linux binary that I don't have to compile myself.

---

### Post by aysiu on 2010-07-07
> **jwbrase said:**
> For Firefox, we don't. For, say, [Be the Wumpus]("http://bethewumpus.sourceforge.net/"), it sure would be convenient if upstream gave us the most rudimentary of binary packages, as there is no downstream. Well, the real solution is actually for there to be a downstream.

> 
But I'm not looking for a package fine-tuned for my distro unless the program absolutely requires such fine-tuning to work, which is not my experience with most packages. I'm just looking for a working Linux binary that I don't have to compile myself. Then you're the minority. If you're a typical end-user, use the repositories to install software. If you're a geeky hacker type, compile the source yourself. The in-between is a niche market.

---

### Post by alexan on 2010-07-07
> **koenn said:**
> you're still barking up the wrong tree

if you've come across software that is not packaged for your distro, talk to the distro maintainers to package it.
Not much logical; if I need a software which is not packaged.. I simply compile it for me. I know how do it... obviously even before know I can talk with such things called "maintainers"

I am talking about simplification; things not intended for me.. but for "accessibility" to everyone.
Wait (or ask) for the work maintainers is just to make things more involved.

A maintainer for every distro, it doesn't sound logical to me.

> **Bachstelze said:**
> The developers of a piece of software and the maintainers of a distribution are usually different people. If the developers don't release a tarball, how on Earth are the distributors supposed to get the source and build packages from it?

Maybe the developers should be are... or should have, just their own distributors? then put their software in the "index" which can be universally accessed by the same way...
not waiting, asking for every new software/version to check the README?

> **aysiu said:**
> It's already been quit. .tar.gz files are not for general distribution. They're for developers to package for general distribution.

If I want to install software, I don't go to that software maker's website to download .tar.gz. That's what the Ubuntu developers do. They package the compiled source code *for me* so I can just install software through the repositories.
If the software maker do this job by itself... it will be ready "instantaneously" for all the distro.
What I am say is this:
_add_ option for download the .deb package = wise software maker
let only tar.gz = some-maintainer-will-care-about-it software maker (also say: "I don't make preference" (probably: "I don't care really")

> **Penguin Guy said:**
> The point I am making is that it's not the programmer's duty to package their programs any more than it is yours. In fact, seeing as they've written the program for _free_, maybe someone else should do their part?
You know, there's free/opensource software for windows too.. it's near _always_ .exe for windows.
How do you explain this?
Give a look there:
[http://www.mozilla.com/en-US/firefox/all.html](http://www.mozilla.com/en-US/firefox/all.html)
exe dmg... and.... tar.bz
*no preference given*, eh?

> **SunnyRabbiera said:**
> Firstly tar.gz is there to be a neutral format for all linuxes to deal with, not all deal in debs or RPM's
You're talking about such things called "linuxes"... obviously not "linux users" anyway.
> **Simian Man said:**
> This is one of the biggest threats to the open source world: people getting involved and vocal when they have *no god-dam idea* what they're talking about.

Democracy works this way: there's no need of approval for people get "vocal". 

> **Dustin2128 said:**
> I don't really see your analogy but I disagree strongly with you on the last point. distributing in tar.gz format allows the programmer  to distribute to all distros because all the end-user has to do is compile it for his or her system, something the vast majority of linux users don't mind doing. In fact, I've had *less *difficulty at times compiling from source than using the repository. Removing choice will ***_not_ ***improve the operating system, it will destroy it. I don't know about you but I personally would never install a binary from anyone I don't trust quite a lot (NGD, google, those are the only sources I've installed from) and swapping from tarballs to binaries would make linux tenfold more vulnerable to malware imho. I still think this is another one of those 'linux should be more like windows' threads though,  I'd stick it in recurring.
If you go to firefox website to download your software.. you'll see exe, dmg, tar.gz and *everything else* removed.
Winodows user: you had to double click
Apple user: you had to double click (or drag&drop? I don't quite remeber)
Linux user: check README > check dependencies > check the right version > check INSTALL > ./configure > make > sudo make install.

The difference in linux is that for every...distro (while apple/win are made for every...people).
Not fair, not rational. **_ADD_** the option of tar.gz to deb/rpm.. but don't cut out deb/rpm.


> **jwbrase said:**
> Well, what I think he's advocating is that developers distribute debs and rpms of their programs alongside tarballs. Which, frankly, I do somewhat sympathize with. 

Devs devving for Linux seem to be in love with distributing source-only tarballs, with the only way to get a binary being to either get it through your distribution's repository (if it's in there) or to compile it yourself. FOSS devs on Windows, OTOH, tend to release a zip of the precompiled program (which is actually my favorite distribution format), or an MSI (not my favorite format, but better than compiling from source if you don't want to modify the program). In fact, it's possible to find programs nominally developed primarily for Linux where a source tarball and a precompiled Windows zip/MSI are available on the project's homepage, but no precompiled Linux binary.

It's not even really the tarball that's the problem, it's what the tarball contains, namely, nothing but source. A combined source/binary tarball, or the availability of a binary tarball (or, for bonus points, *.deb or *.rpm) along side the source one would be excellent. 

But where the OP is mixed up is that this isn't a (mal)feature of Linux, simply a very infuriating habit of a whole ton of developers.

Thanks for putting what I was trying to say... but in proper english this time :KS

---

### Post by aysiu on 2010-07-07
> **alexan said:**
> 
A maintainer for every distro, it doesn't sound logical to me. Scouring websites for .exe files doesn't sound logical to me.

Package managers are easy to use because you don't have to worry about tracking things down. All the software appears to be in one place.

---

### Post by jwbrase on 2010-07-07
> **aysiu said:**
> Well, the real solution is actually for there to be a downstream.

Unfortunately, not something the end user can control. I use alot of small-time FOSS programs I find on the Internet (in fact, since they introduced me to the FOSS culture, the FOSS community on Windows is probably largely responsible for the fact that I now use Linux), and many of these simply do not have a downstream. When they do have a binary tarball, or any kind of package, it usually works well regardless of what distro it was compiled under. Source tarballs tend to fail to compile once out of every 3 or 4 tries, and to do so in a way I am unable to remedy with my knowledge once in every 5 or 6. 

> 
 Then you're the minority. If you're a typical end-user, use the repositories to install software. If you're a geeky hacker type, compile the source yourself. The in-between is a niche market.

It's not what I want to do with the programs, it's the type of programs I run, and I wish developers would keep in mind the actual status of their program in deciding how to distribute it (If there aren't any distros that know you exist, it's probably good to package the program, at the very least as a binary tarball, rather than wait for the distros to find and package you). 

When the programs I'm using are in the repositories, I use that. When I actually wish to edit the source code (fairly rare), I compile from source. When I find a program on the 'net that's not in the repositories, I'll use a binary tarball or generic package if it's available, otherwise I compile from source and cross my fingers.

Now, unlike the OP, I do *not* see this as a problem with Linux, only with the habits of many developers for Linux.

---

### Post by Dustin2128 on 2010-07-07
> **alexan said:**
> 
Winodows user: you had to double click
Apple user: you had to double click (or drag&drop? I don't quite remeber)
Linux user: **sudo apt-get install firefox**
There, fixed it for you. 

If a user is using a distro without a package manager, the user probably is not afraid of compiling software from source. Otherwise, 98% of all software for ubuntu is in the repository. Certainly all the major software.

---

### Post by alexan on 2010-07-07
> **aysiu said:**
> Scouring websites for .exe files doesn't sound logical to me.

Package managers are easy to use because you don't have to worry about tracking things down. All the software appears to be in one place.

Indeed, the perfect equilibrium that only linux could only achieve today is a .deb which install package and repositories.
It give the perfect flexibility of both words
Also it would reduce the work of the maintainer of all the README stuff.

But the tar.gz addiction (when given as _only choice_) it's the worst of both words: Scouring websites... then Scouring again for dependencies&stuff

---

### Post by Dustin2128 on 2010-07-07
> **alexan said:**
> Indeed, the perfect equilibrium that only linux could only achieve today is a .deb which install package and repositories.
It give the perfect flexibility of both words
Also it would reduce the work of the maintainer of all the README stuff.

But the tar.gz addiction (when given as _only choice_) it's the worst of both words: Scouring websites... then Scouring again for dependencies&stuff
Look at it from a developer's perspective. You have your source code, your program's tested, it runs well. However, it has 1 or 2 dependencies that can not be resolved via the package manager (maybe it depends on another program you've developed that's also in tar.gz format). So, you don't put it in .deb format, you put it in a tar.gz format where anybody using any distro can compile it, and its dependencies (any descent software writer will have links to or host the dependencies on their sites) and run it on their system.

---

### Post by jwbrase on 2010-07-07
> **aysiu said:**
> Scouring websites for .exe files doesn't sound logical to me.

Well, if you're looking for something for a specific purpose, as a Windows user, you get used to it. When you adopt Linux, you generally do take up the habit of searching the repositories first, then searching if you can't find anything there. But I find as many programs because there's a link to them on some website I'm reading on a related topic as I do because I was actively looking for something to do their job. So once I'm actually looking at a program's website, it would be convenient and be able to download and unzip/install it without having to compile it.

> 
Package managers are easy to use because you don't have to worry about tracking things down. All the software appears to be in one place.

Once again, all well and good for programs actually in the repositories.

---

### Post by jwbrase on 2010-07-07
> **Dustin2128 said:**
> Look at it from a developer's perspective. You have your source code, your program's tested, it runs well. However, it has 1 or 2 dependencies that can not be resolved via the package manager (maybe it depends on another program you've developed that's also in tar.gz format). So, you don't put it in .deb format, you put it in a tar.gz format where anybody using any distro can compile it, and its dependencies (any descent software writer will have links to or host the dependencies on their sites) and run it on their system.

And while you're at it, since you had to have a binary to test the program and determine that it runs well, why not throw it into the tarball with the source code? That way the user can just unpack the program, along with any dependencies that you've written, and not worry about compiling. If it works for the end user, great! If not, they'll have to try compiling, but at least they'll give you credit for trying.

---

### Post by juancarlospaco on 2010-07-07
I dont understand.

You can Compile tar.gz on Windows too, and is more difficult.
You can install things with commands on Windows too, and is more difficult.

---

### Post by odiseo77 on 2010-07-07
I think that, even if there was a unified packaging format for binaries across the 100% of distros around (.deb, .rpm. or a format not created yet), there are so many different distros with different library versions, that it would be impossible to make it work in all of them. Besides this, I don't see any problem with debs, rpms and repositories at all; in fact it's easier to install software from the repositories (either through apt-get, aptitude, synaptic, or any other software management program from any distro) than going to every single site, downloading it (in binary form) and installing it (windows like).
As for sources and source packages, I don't see the point of "leaving them behind", it's simply impossible; if for example I use a distro for which there's not a given program in the repositories, I rather have a source tarball to compile and install it than not having anything at all. Anyway, nowadays, people can find thousands of packages on the repositories of the most popular distros (and the not so popular too), so it's rare when users are "forced" to compile.

---

### Post by WinterMadness on 2010-07-07
sudo apt-get install is good for newbies because when they ask for help we can just tell them to copy and paste and not deal with the "i dont see that option" thing.

I often fall into that category, so I much prefer the command line in all honesty.

---

### Post by chriswyatt on 2010-07-07
An easy way of installing programs across distributions does exist, Yabause uses it:

[http://autopackage.org/](http://autopackage.org/)

I do agree it's nice when the developers supply a nice easy way of installing their software, but as was mentioned before it's down to the developer.

---

### Post by mamamia88 on 2010-07-07
don't think i've ever had to compile anything and sudo apt-get install is so easy why get rid of it?

---

### Post by chriswyatt on 2010-07-07
I love package management, it's one of the best features of Linux and one of the main reasons why I abandoned my cluttered Windows partition.

---

### Post by KdotJ on 2010-07-07
Another good old post about "what's wrong with linux"

You're not forced to use tarball, or apt-get in the terminal. You have plenty of other options, and the basic "average" user will get by with no problems without using tarballs or apt-get, they would get on just as well even if they had no idea what they were

---

### Post by MCVenom on 2010-07-07
I think the OP has missed the point of almost every darn response to this thread. Therefore I will make it clear:

[SIZE=7][COLOR=DarkRed]***[SIZE=6]THE REPOSITORIES, UBUNTU SOFTWARE CENTER AND SYNAPTIC ALLOW EASY SOFTWARE INSTALLATION. YOU DON'T HAVE TO SCOUR THE WEB FOR RANDOM BINARIES. NOW, WHAT'S WRONG WITH THE REPO'S?!?!?!?!?![/SIZE]***[/COLOR][/SIZE]> **Simian Man said:**
> This is one of the biggest threats to the open  source world: people getting involved and vocal when they have *no  god-dam idea* what they're talking about.

Honestly.

---

### Post by Legendary_Bibo on 2010-07-07
What if there was some sort of super intelligent application that would take your source code find and download any dependencies needed, package it with the source code, and package it into a format that the deb or rpm or whatever installer will detect and be able to read it. AND it gives a person a gui way of adding or disabling features, like flagging in Gentoo, and it gives you the benefits of Gentoo! The GODLIKE package!!

---

### Post by dragos240 on 2010-07-07
So that means only debian distros can get programs. And that all other distros should perish?

---

### Post by marshmallow1304 on 2010-07-08
> **Dustin2128 said:**
> Do you know how pissed off I am that chrome *didn't *release a tarball for me to compile (at least that I can find...)?

Debian to the rescue!
[http://packages.debian.org/source/sid/chromium-browser](http://packages.debian.org/source/sid/chromium-browser)

---

### Post by murderslastcrow on 2010-07-08
I'm pretty sure they have ways of automatically compiling and installing software from tar.gz. Tarball doesn't sound too attractive, though.

If we all start adopting Packagekit and reworking it into different interfaces (like the USC) and include alien by default, the packages won't even matter anymore. However, most software is readily available anyway.

Don't take away the ability to type in commands to install stuff. It's very important, especially for troubleshooting a system in case X goes weird or something. And it's nice if it's quicker for you in some instance. Obviously not saying we should use it exclusively- that's plain moronic. Variety, choice, that's what Linux is all about. And we've made it pretty freaking convenient to have those choices.

---

### Post by Dustin2128 on 2010-07-08
> **marshmallow1304 said:**
> Debian to the rescue!
[http://packages.debian.org/source/sid/chromium-browser](http://packages.debian.org/source/sid/chromium-browser)
Thanks! just what I was looking for.

---

### Post by Dayofswords on 2010-07-08
> **alexan said:**
> 

sudo apt-get install:
[alt]+[f2] > apt:/[namepackage]
let apt-get usage for specific techy needs.. and move forward to human logic friendliness.

someone explain how that is more logical? it's much much shorter and that be just human laziness, but it sacrfices features...

plus apt:[packagename] is already implement in firefox on ubuntu

---

### Post by Methuselah on 2010-07-08
Why do some many people come in here and demand that options be removed?
Why should one be bothered by the mere existence of a capability one does not have to use?

Use Ubuntu Software Centre since nobody is forcing you to type apt-get install into a terminal.
Let those functions remain for people doing the kind of tasks for which they are useful.

---

### Post by Gregorybekkers on 2010-07-08
UHm.. :O
No..

sudo (security reasons that you don't have to login as su)
apt-get install ( to install you applications..)

If you don't want to use it. don't use it.

use Ubuntu software center (or some of the others)

it have to be there anyway. since not everyone want to use the GUI for all the stuff.
think about servers, scripts. 
and just people that know more about linux (belive me it goes faster)

so NO :)

---

### Post by doorknob60 on 2010-07-08
> **Legendary_Bibo said:**
> What if there was some sort of super intelligent application that would take your source code find and download any dependencies needed, package it with the source code, and package it into a format that the deb or rpm or whatever installer will detect and be able to read it.

Like Makepkg in Arch? That combined with the AUR and Yaourt means I have NO custom compiled software on my system. (It's all controlled by my package manager). It's great :) I've made quite a few of my own AUR packages though, but then after you make it it's still controlled by th package manager, which is nice, and most software is already in the repos or AUR already.

---

### Post by Legendary_Bibo on 2010-07-08
> **doorknob60 said:**
> Like Makepkg in Arch? That combined with the AUR and Yaourt means I have NO custom compiled software on my system. (It's all controlled by my package manager). It's great :) I've made quite a few of my own AUR packages though, but then after you make it it's still controlled by th package manager, which is nice, and most software is already in the repos or AUR already.

I've looked at what it takes to go from source --> .deb

It hurt my head. I can see why the devs don't like doing it, but I mean if you've done it several times then shouldn't it get easier the more you do it?

---

### Post by Barfleur on 2010-07-08
> **wyliecoyoteuk said:**
> So you are saying :
lose the choice.
Linux is about choice, lots of it. you don't need to use tarballs if you don't want to, and developers don't have to supply anything but source if they don't want to.
The main reason for there only being a tarball is because no-one has got around to converting it to a binary, either because no-one with the skills to do so is interested, or has the time.

I agree, choice is the way to go, let there be an open Carte Blanche, it's all about freedom and Linux is Free like the wind or the air we breath.

---

### Post by Penguin Guy on 2010-07-08
> **alexan said:**
> [QUOTE=Penguin Guy;9560328]The point I am making is that it's not the programmer's duty to package their programs any more than it is yours. In fact, seeing as they've written the program for _free_, maybe someone else should do their part?You know, there's free/opensource software for windows too.. it's near _always_ .exe for windows.
How do you explain this?
Give a look there:
[http://www.mozilla.com/en-US/firefox/all.html](http://www.mozilla.com/en-US/firefox/all.html)
exe dmg... and.... tar.bz
*no preference given*, eh?[/QUOTE]
A [FONT="Courier New"].exe[/FONT] takes 1 minute, a [FONT="Courier New"].deb[/FONT] takes a few hours.

---

### Post by Viva on 2010-07-08
It is already the case with most software. tar.gz is for package mantainers, apt-get for advanced users, software center for regular users.

---

### Post by alexan on 2010-07-08
I'll try to simplify my reply responding to jump over the "hot" and looping points, sort of FAQ

Q: *Why you do want remove the tar.gz?*
A: What's to remove is the "*tar.gz addiction*". tar.gz (with source README and INSTALL file in it) are _great_ for what its supposed to do. What is _not_ supposed to do, is to distribute software.

Q: *Why make preference RPM/DEB packages/you want disadvantages other distro*
A: Alien package show that's it's possible migrate packages, this software can be improved and bug/fixed when compatibility problem are faced. The difference is that a maintainer who try want "translate" .deb package for his/her distro had to bugfix a single package.. in order to bring _ALL_ Ubuntu repositories (thousands of software) in his/her distro.
A maintainer with tar.gz had just thousands of README to READIT.

Q: *It's already this way, its already happening*
A: No, it is not. As this thread show there's still big affection to tar.gz as the ONLY way to developers distribute their software.

---

### Post by Paqman on 2010-07-08
Compiling has already been left behind on distros that use binary package managers. There's no reason you should be compiling anything on Ubuntu, except in the *extremely* rare case that you have a piece of mission-critical software that isn't available as a package. Personally I haven't compiled anything in years.

---

### Post by mobilediesel on 2010-07-08
> **alexan said:**
> I'll try to simplify my reply responding to jump over the "hot" and looping points, sort of FAQ

Q: *Why you do want remove the tar.gz?*
A: What's to remove is the "*tar.gz addiction*". tar.gz (with source README and INSTALL file in it) are _great_ for what its supposed to do. What is _not_ supposed to do, is to distribute software.

Q: *Why make preference RPM/DEB packages/you want disadvantages other distro*
A: Alien package show that's it's possible migrate packages, this software can be improved and bug/fixed when compatibility problem are faced. The difference is that a maintainer who try want "translate" .deb package for his/her distro had to bugfix a single package.. in order to bring _ALL_ Ubuntu repositories (thousands of software) in his/her distro.
A maintainer with tar.gz had just thousands of README to READIT.

Q: *It's already this way, its already happening*
A: No, it is not. As this thread show there's still big affection to tar.gz as the ONLY way to developers distribute their software.

What is this I don't even

---

### Post by 3rdalbum on 2010-07-08
So what you're saying is that these things should be left behind, but retained for people who want them. Dude, you can't have it both ways, and it's obvious that you don't know the purpose of these things that you criticise.

---

### Post by Legendary_Bibo on 2010-07-08
> **3rdalbum said:**
> So what you're saying is that these things should be left behind, but retained for people who want them. Dude, you can't have it both ways, and it's obvious that you don't know the purpose of these things that you criticise.

I thought tar.gz was just a compression format like .zip. :confused:

---

### Post by Paqman on 2010-07-08
> **3rdalbum said:**
> it's obvious that you don't know the purpose of these things that you criticise.

+1

I would say troll, but looking at the OP's other posts they seem sincere.

---

### Post by 3rdalbum on 2010-07-08
In Ubuntu circles, .deb or a PPA/repository IS the preferred format.

Debs and RPMs can be converted, but may lose some of their more advanced features.

As a developer I only distribute Debs. If anyone complains, I can always learn how to make RPMs. No complaints yet.

Source code can be compiled for any platform though, so it's really the lowest common denominator. An AMD64 deb doesn't do you any good on x86 or ARM, for obvious reasons.

---

### Post by MooPi on 2010-07-08
I only use apt-get and also NO !!!!! This is sorta the reason for our freedom, an ability to use what form we prefer. Besides if your on a server platform without a GUI, apt-get is necessary.

---

### Post by RiceMonster on 2010-07-08
> **doorknob60 said:**
> Like Makepkg in Arch? That combined with the AUR and Yaourt means I have NO custom compiled software on my system. (It's all controlled by my package manager). It's great :) I've made quite a few of my own AUR packages though, but then after you make it it's still controlled by th package manager, which is nice, and most software is already in the repos or AUR already.

I don't know about making a deb (I haven't done it yet), but making an rpm is about just as easy as making a pacman package. The process isn't drastically different either.

> **alexan said:**
> I'll try to simplify my reply responding to jump over the "hot" and looping points, sort of FAQ

Q: *Why you do want remove the tar.gz?*
A: What's to remove is the "*tar.gz addiction*". tar.gz (with source README and INSTALL file in it) are _great_ for what its supposed to do. What is _not_ supposed to do, is to distribute software.

The whole README thing you keep pointing out is driving me crazy. This is how you compile software 99% of the time:
```
./configure # install any dependecies is says you don't have
make
su -c 'make install' # or on Ubuntu, sudo make install
```

It's not that complex, and you don't need to spend hours studying that little README file. Most of the things that are going to make an RPM spec file, and PKGBUILD, or Debian rules more complex, is usually not something in the README file, but distro specific patches and modifications.

> **alexan said:**
> Q: *Why make preference RPM/DEB packages/you want disadvantages other distro*
A: Alien package show that's it's possible migrate packages, this software can be improved and bug/fixed when compatibility problem are faced. The difference is that a maintainer who try want "translate" .deb package for his/her distro had to bugfix a single package.. in order to bring _ALL_ Ubuntu repositories (thousands of software) in his/her distro.
A maintainer with tar.gz had just thousands of README to READIT.

Alien is a hack. As far as I know, it doesn't always work 100%.

> **alexan said:**
> Q: It's already this way, its already happening
A: No, it is not. As this thread show there's still big affection to tar.gz as the ONLY way to developers distribute their software.

Type this into a terminal:
```
yes "Install software from the repos, not from the developers website"
```

---

### Post by chriswyatt on 2010-07-08
I didn't know about the yes command.  If only Homer knew about this command in the episode "King-size Homer" ;)

---

### Post by MisfitI38 on 2010-07-08
> **Crunchy the Headcrab said:**
> I don't even get what you're talking about.  I'm going to see everyone's "no" and raise them a "wtf"?  It sounds like you're bent on forcing developers to distribute software in a way that you see fit AND causes additional work for them.

I see your 'wtf' and raise you a 'rofl'.

BTW, tar.gz is a combination of a tar archive further compressed using the gzip algorithm.
What did it ever do to you?

---

### Post by SunnyRabbiera on 2010-07-08
> **Legendary_Bibo said:**
> I thought tar.gz was just a compression format like .zip. :confused:

You know what, there is a big piece of hypocrisy from the OP here on compressed formats.
On windows not all software comes in a .exe installer, it comes in a .msi and a .zip folder sometimes.

For me the OP is either too lazy to do some homework on why we still have command lines and software in compressed formats like tar.gz and wants linux to be as much like windows as possible like most ignorant newcommers.

---

### Post by GeneralZod on 2010-07-08
> **chriswyatt said:**
> I didn't know about the yes command.  If only Homer knew about this command in the episode "King-size Homer" ;)

He'd have *more than* tripled his productivity! :)

---

### Post by koenn on 2010-07-08
> **alexan said:**
> 
Democracy works this way: there's no need of approval for people get "vocal". 

and that's a major flaw in the democratic system. 

However, that is besides the point, because free software isn't a democracy.

---

### Post by Penguin Guy on 2010-07-08
This thread is complete bull, the OP has no idea what a [FONT="Courier New"].tgz[/FONT], [FONT="Courier New"].exe[/FONT] or [FONT="Courier New"].deb[/FONT] file actually is and certainly has no idea of what it takes to convert between the three. His posts have been completely illogical and irrational - and as can be seen from the response to this thread, the idea will never happen, so I see no point in discussing the matter further.

> **alexan said:**
> Democracy works this way: there's no need of approval for people get "vocal". 
Vocalism hasn't got anything to do with democracy, perhaps you're thinking of freedom of speech?

---

### Post by mamamia88 on 2010-07-08
dude these things are what i love about linux.  haven't ever had any software i needed to compile and everything i need is in the repos or a ppa.  when adding from a ppa i just use commands sudo add-apt-repository (insert name of repo here), sudo aptitude update, sudo aptitude install "name of program".  then all my software is automatically updated with update manager.  with windows and every other non linux based os you have to update ever piece of software manually.  i think linux has it right here. and even when things come in a tar.gz archive usually they have some kind of binary that runs and you create a link to it in your applications menu

---

### Post by koenn on 2010-07-08
> **Legendary_Bibo said:**
> I've looked at what it takes to go from source --> .deb

It hurt my head. I can see why the devs don't like doing it, but I mean if you've done it several times then shouldn't it get easier the more you do it?

it's not all that hard, and there are tools tools for it
 Distributions combine and configure those tools into  tool-chains and build farms : you throw in source code on one end, packages come out of it at the other end. 

That way is far more efficient than having each developer package his one program into several packages, each having to conform with several specifications of different distros for multiple CPU architectures, etc etc etc

Also, being a programmer doesn't necessarily make you good at, or even interested in, system administration. A lot of what packaging is about, has to do with system administration : where do the config files go, where doe the executables go, which libraries(-versions) will be present 
in the OS,  what account will this service run as, etc. N


So it makes sense the let devs dev, and let packagers package 
That also happens to be the way Open Source, as a development method, works : it's essentially loosely managed distributed collaboration.

---

### Post by Half-Left on 2010-07-08
Well in the end, it's down to the distro. Ubuntu and others don't install GCC dev tools and such by default as people might know already.

It's probably been already said but it's about choice and shouldn't be removed.

---

### Post by sh1ny on 2010-07-08
> **Penguin Guy said:**
> This thread is complete bull, the OP has no idea what a [FONT="Courier New"].tgz[/FONT], [FONT="Courier New"].exe[/FONT] or [FONT="Courier New"].deb[/FONT] file actually is and certainly has no idea of what it takes to convert between the three. His posts have been completely illogical and irrational - and as can be seen from the response to this thread, the idea will never happen, so I see no point in discussing the matter further.


Vocalism hasn't got anything to do with democracy, perhaps you're thinking of freedom of speech?

Strongly agree with this.

@OP - you won't get .exe format that will work in every linux out there. First - go ahead and read how it all started, back to Stallman and where/why linux came to be. Then read how each distro differs from the other ( or just start by understanding file formats and the differences between them ) and why there can't be a universal format for all of them and why developers release .tar.gz archives with **source code**. Then this discussion might have a point. Currently it does not.

Cheers.

---

### Post by mamamia88 on 2010-07-08
i don't mind tar.gz as long as they give detailed instructions in readme file on how to install and not some generic instructions.  wish they would include a runtobuild file like in sleepisdeath to make it super easy

---

### Post by alexan on 2010-07-12
> **sh1ny said:**
> Strongly agree with this.

@OP - you won't get .exe format that will work in every linux out there. First - go ahead and read how it all started, back to Stallman and where/why linux came to be. Then read how each distro differs from the other ( or just start by understanding file formats and the differences between them ) and why there can't be a universal format for all of them and why developers release .tar.gz archives with **source code**. Then this discussion might have a point. Currently it does not.

Cheers.
You won't get any .exe format that will work with every windows out there. But still it's widely used OpenSource project like Firefox... you can find even a .msi of it.
So, your point may had be right, but it is not in this discussion.
It is not about "removal" of tar.gz... but the removal of the *tar.gz mindset*.

You can release software in deb and rpm.. and then leave tar.gz for its very propose: when someone want to open the trunk of his car.


"You had to assemble the car when you get at home"?
Then what should be RMS, an IKEA prophet?

---

### Post by red_Marvin on 2010-07-12
Developers spend days and hours working on software because they want to. They are also nice enough to share it. They have no obligations whatsoever to make sure it is served on a silver platter.

---

### Post by alexan on 2010-07-12
> **red_Marvin said:**
> Developers spend days and hours working on software because they want to. They are also nice enough to share it. They have no obligations whatsoever to make sure it is served on a silver platter.
They are the same developer which make the stuff for windows..



in exe and over a silver platter.

---

### Post by marshmallow1304 on 2010-07-12
> **alexan said:**
> They are the same developer which make the stuff for windows..



in exe and over a silver platter.

If there were hundreds of Windows distros all with different standards for software management, they wouldn't.


I don't understand why this is so difficult.  Why should open source developers have to decide which distros for which to package?  Which architectures?  What if I'm on PPC?  A deb or rpm for i386 won't help much.

---

### Post by mrdusty on 2010-07-12
I agree about the tar balls, but as a real newbie, I like to use  the synaptic method and am not above apt-get as my alternative. Use both of them.
Maybe my 63 year old mind just hangs in the middle of a tz install.  Maybe it's a hairball between my ears??

---

### Post by alexan on 2010-07-13
> **marshmallow1304 said:**
> If there were hundreds of Windows distros all with different standards for software management, they wouldn't.


I don't understand why this is so difficult.  Why should open source developers have to decide which distros for which to package?  Which architectures?  What if I'm on PPC?  A deb or rpm for i386 won't help much.

So, the software developer which distribute .deb and .rpm packages won't help much their product?

deb(mostly) and rpm(slight less) ARE actually used standard which cover a more huge number of distros (derivative&co) than any other "tar.gz" propose.

Currently tar.gz is _used_ for its real propose when give together with deb/rpm (share source or compress folder while maintain filesystem's hierarchy) *OR* _force_ user to "not set any preference".

Again (over again): it is not about remove the tar.gz, but give the right priority to simple and fair distribution of software ("deb/rpm/tar.gz" "deb/tar.gz" or "repository with debs and sourcecodes (in deb)")

---

### Post by ajackson on 2010-07-13
> **alexan said:**
> You won't get any .exe format that will work with every windows out there. But still it's widely used OpenSource project like Firefox... you can find even a .msi of it.
Yes lets compare an organisation with teams of paid developers with most open source software that is written and maintained by small groups (often only one person) of volunteers doing it as a hobby.

> **alexan said:**
> You can release software in deb and rpm.. and then leave tar.gz for its very propose: when someone want to open the trunk of his car.

"You had to assemble the car when you get at home"?
Then what should be RMS, an IKEA prophet?
You can't compare a car with an open source project.

Yes the developer can produce debs, rpms and whatever package formats there are but it all takes time. I would prefer that developers spend their, often limited, time on developing and fixing bugs. If some of them release compiled packages that is a bonus but with Linux a source tarball is a universal way of supplying your piece of software.

The more popular pieces of software end up with compiled packages being created by other people, which in turn end up in repositories - a natural evolution in open source software.

If you start demanding that developers have to produce binaries for every distro out there most will turn around and stop developing the software because it's not worth the hassle of dealing with ungrateful people who want everything on a silver platter.

OP here is a challenge, develop a piece of software by yourself, keep improving it and also make sure that you create binary packages for all Linux distros. When you do that **then** you can take the high-ground about software distribution.

Put up or shut up.

---

### Post by RiceMonster on 2010-07-13
> **alexan said:**
> deb(mostly) and rpm(slight less) ARE actually used standard which cover a more huge number of distros (derivative&co) than any other "tar.gz" propose.

Actually, deb is not a standard, and rpm is according to lsb. tar.gz is like a zip file. It's just a way of packaging and compressing multiple files. It has no "purpose".

Just give it up already. If you don't want to extract a tarball, install from the damn repos. Why is that such a hard concept? I'm willing to bet you have never created a deb or rpm, because you continue to show you have no idea about how the packages work.

---

### Post by jerenept on 2010-07-13
Compiling from source is what makes it "Linux" and not "MacOS".

It makes us faster, more lean and more open and free. If you don't like it, install from the repositories.

---

### Post by alexan on 2010-07-13
> **ajackson said:**
> Yes lets compare an organisation with teams of paid developers with most open source software that is written and maintained by small groups (often only one person) of volunteers doing it as a hobby.
Both windows, mac and linux have opensource software and paid developers: tar.gz is _forced_ by some only on linux


> Yes the developer can produce debs, rpms and whatever package formats there are but it all takes time. I would prefer that developers spend their, often limited, time on developing and fixing bugs. If some of them release compiled packages that is a bonus but with Linux a source tarball is a universal way of supplying your piece of software.
So... in order to spare "human power resource time" let's divide the work, pushing hundred of distro maintanier to compile the same stuff over and over again (multiplied updates, multiplied distros).

> The more popular pieces of software end up with compiled packages being created by other people, which in turn end up in repositories - a natural evolution in open source software.
Mozilla is not by the same idea, of course they *want to be* delivered by default with _any_ distro: so why risk to make "preferences"

> If you start demanding that developers have to produce binaries for every distro out there most will turn around and stop developing the software because it's not worth the hassle of dealing with ungrateful people who want everything on a silver platter.
I am just grateful to the developers, tar.gz are quite boring but I know how manage them, so... personally, is not a big issue.
Things get differently when are no longer *personal*. If a friend of mine (or a work colleague) ask me if install software in linux it's easy as windows.. I can tell him that's more easy than windows/mac?
Yes, if all the software he need it's in the repository, otherwise *I lied* to him.


> **ajackson said:**
> OP here is a challenge, develop a piece of software by yourself, keep improving it and also make sure that you create binary packages for all Linux distros. When you do that **then** you can take the high-ground about software distribution.

Put up or shut up.
I don't program software, I make comics.
I use the english language in my comics even if I am not that good with this language. This, because I want to *give some hope* to my comic, not because someone is *begging* for that.
The factual standard language in Internet is "english", by translating my comics in english I grant the try to reach greater number of eyes. It cost me time, but in this way I give better hopes for my "software".

> **RiceMonster said:**
> Actually, deb is not a standard, and rpm is according to lsb. tar.gz is like a zip file. It's just a way of packaging and compressing multiple files. It has no "purpose".
Deb it's a *factual* standard thanks to Ubuntu. Ubuntu had to tanks its success tanks to Linux users choices.
in the end, DEB is now a democratically established standard. "we" elected DEB as standard because "we" did chose Ubuntu.

> **RiceMonster said:**
> Just give it up already. If you don't want to extract a tarball, install from the damn repos. Why is that such a hard concept? I'm willing to bet you have never created a deb or rpm, because you continue to show you have no idea about how the packages work.

What many seems to fail to realize.. it's that this is not a *personal need* for me.
I can install/use tar.gz on fly witout any glimpse. Please be aware of that.

> **jerenept said:**
> Compiling from source is what makes it "Linux" and not "MacOS".

It makes us faster, more lean and more open and free. If you don't like it, install from the repositories.
All software I _didn't_ compile run faster, lean, open and free than MacOS. This is thanks to linux community *and* stuff like tar.gz.

"Providing _only_ tar.gz" is not what make linux software run flof (fast,lean,open,free), it's just a subethical choice to say "we're not windows/mac"
Which is, IMHO, stupid.
again tar.gz had it's own, essential, propose.. and that propose is not deliver software on the main stream.

---

### Post by koenn on 2010-07-13
> **alexan said:**
> Providing _only_ tar.gz is ... a subethical choice to say "we're not windows/mac"
now, if you could just get that idea out of your had and actually listen to what people are trying to explain to you, you might eventually begin to understand something about software development and distribution.

---

### Post by aysiu on 2010-07-13
> **alexan said:**
> Both windows, mac and linux have opensource software and paid developers: tar.gz is _forced_ by some only on linux Nothing is forced.

You are misrepresenting or misunderstanding the distribution model.

.tar.gz is source code the programmer releases to distribution packagers.

.deb and .rpm are packages the distribution releases to the end user.

The .tar.gz isn't forced, because the end user does not see the .tar.gz. The end user just goes to the Ubuntu Software Center or Synaptic Package Manager and installs what software she wants (software already packaged).

What you're complaining about is like going to a factory and complaining that there are raw materials at the beginning of the assembly line instead of just picking up the finished product at the end of the assembly line.

As a Linux **user** your primary means of installing software should be through the package manager. Only Linux packagers or Linux power users with special needs should go to the program's home page to download the source code.

---

### Post by Chame_Wizard on 2010-07-13
Leaving ```
apt-get
```behind?

Blasphemy.:popcorn:

---

### Post by mobilediesel on 2010-07-13
> **alexan said:**
> What many seems to fail to realize.. it's that this is not a *personal need* for me.
I can install/use tar.gz on fly witout any glimpse. Please be aware of that.

Then why the troll?
[ATTACH]163331[/ATTACH]

---

### Post by ajackson on 2010-07-13
> **alexan said:**
> So... in order to spare "human power resource time" let's divide the work, pushing hundred of distro maintanier to compile the same stuff over and over again (multiplied updates, multiplied distros).
The developer has supplied the piece of software. If distro managers want to spend their time producing compiled packages that is up to them.

> **alexan said:**
> If a friend of mine (or a work colleague) ask me if install software in linux it's easy as windows.. I can tell him that's more easy than windows/mac?
Yes, if all the software he need it's in the repository, otherwise *I lied* to him.
Well the majority of the software he needs can be obtained via repositories, so you haven't lied. 

> **alexan said:**
> I don't program software, I make comics.
I use the english language in my comics even if I am not that good with this language. This, because I want to *give some hope* to my comic, not because someone is *begging* for that.
You don't supply your comics in cbz format, why not, why are you forcing people to have to read it via a web browser? You see you are just providing the source and not a "compiled" package yourself.

---

### Post by alexan on 2010-07-14
> **aysiu said:**
> The .tar.gz isn't forced, because the end user does not see the .tar.gz. The end user just goes to the Ubuntu Software Center or Synaptic Package Manager and installs what software she wants (software already packaged).

...if a maintainer had time to bring it on Ubuntu
...if a maintainer had time to bring it on Fedora
...if a maintainer had time to bring it on OpenSuse
...if a maintainer had time to bring it on Gentoo
...if a maintainer had time to bring it on Android
....
repeat for every version/update.



> **aysiu said:**
> What you're complaining about is like going to a factory and complaining that there are raw materials at the beginning of the assembly line instead of just picking up the finished product at the end of the assembly line.
Then, I suggest you to re-read what I do wrote; not polemic, but sincerely true. I know my english is quite bad: if you point to me the exact words I'd use to give this idea.. I can learn and fix, improving my english too.



> **aysiu said:**
> As a Linux **user** your primary means of installing software should be through the package manager. Only Linux packagers or Linux power users with special needs should go to the program's home page to download the source code.

This collide with: "*Nothing is forced*"
Anyway, I am not talking about a "general enforcement"... but a *tar.gz mindset enforcement* which affect only some software/driver developers (providing msi, zip, exe for windows.. and then only tar.gz for linux).

> **ajackson said:**
> The developer has supplied the piece of software. If distro managers want to spend their time producing compiled packages that is up to them.
This mean what?
some sort of "deserved" punishment for every distro maintainer of linux?
If microsoft want to make it's own repository, they had just to download bunch of exe and upload somewhere.
.exe is not more "standard" than ubuntu/debian .deb


> **ajackson said:**
> Well the majority of the software he needs can be obtained via repositories, so you haven't lied. 

yeah, I've "mildly" lied (or "I've said a mildly truth" if you prefer :P ).

> **ajackson said:**
> You don't supply your comics in cbz format, why not, why are you forcing people to have to read it via a web browser? You see you are just providing the source and not a "compiled" package yourself.
You know, It is not a bad idea at all!
But I was providing only the compiled version, I'll rework a bit the website, but for now. Here's the first episode:


Planet Run, episode 1, ver 0.0.1
cbz
[http://www.megaupload.com/?d=R9EYW9OI](http://www.megaupload.com/?d=R9EYW9OI)
[http://rapidshare.com/files/406870358/planet.run.episode.1.cbz](http://rapidshare.com/files/406870358/planet.run.episode.1.cbz)
[http://hotfile.com/dl/54737209/a0b262f/planet.run.episode.1.cbz.html](http://hotfile.com/dl/54737209/a0b262f/planet.run.episode.1.cbz.html)


[http://www.megaupload.com/?d=W6AKVRR9](http://www.megaupload.com/?d=W6AKVRR9)
[http://rapidshare.com/files/406870707/planetrun.episode1.tar.gz](http://rapidshare.com/files/406870707/planetrun.episode1.tar.gz)
[http://hotfile.com/dl/54737486/f5fec46/planetrun.episode1.tar.gz.html](http://hotfile.com/dl/54737486/f5fec46/planetrun.episode1.tar.gz.html)


The cbz contain the PNGs (which manage better the greyscale with loseless quality.. and they are undisclosed standard with jpg and gif )
the tar.gz contain the xcf as I did them.
I could had provide cbr in jpgs.. but providing the tar.gz give you the freedom to convert loseless quality for anything (but money) you wish.

---

### Post by ajackson on 2010-07-14
> **alexan said:**
> ...if a maintainer had time to bring it on Ubuntu
...if a maintainer had time to bring it on Fedora
...if a maintainer had time to bring it on OpenSuse
...if a maintainer had time to bring it on Gentoo
...if a maintainer had time to bring it on Android
....
repeat for every version/update.
Oh dear do you think the same people do that for every distro?

> **alexan said:**
> This mean what?
some sort of "deserved" punishment for every distro maintainer of linux?
Where do I say it is a punishment?

> **alexan said:**
> .exe is not more "standard"
Tell me you are kidding, tell me you don't really believe that? Any credibility your argument might have had has just gone up in flames as you now show that you don't understand what an exe is.

> **alexan said:**
> yeah, I've "mildly" lied (or "I've said a mildly truth" if you prefer :P ).
The world isn't black and white, you could probably find windows software that is supplied as source only - using your logic you would have lied if you said windows was easy to install stuff on.

> **alexan said:**
> 
You know, It is not a bad idea at all!
But I was providing only the compiled version, I'll rework a bit the website, but for now. Here's the first episode:
Thank you for falling into the trap I laid, the cbz format is just another compression format (like zip, tar.gz, tar.bz2) in fact cbz is the same as a zip, cbg is the same as a tar.gz. So by supplying your comics in a cbz format you are forcing people to use the "source" for your comics.

But you think that making it available as cbz file is a good idea, you are forcing the user to install software that can read/process those files, kind of like a dependency you could say.

---

### Post by red_Marvin on 2010-07-14
> **alexan said:**
> ...if a maintainer had time to bring it on Ubuntu
...if a maintainer had time to bring it on Fedora
...if a maintainer had time to bring it on OpenSuse
...if a maintainer had time to bring it on Gentoo
...if a maintainer had time to bring it on Android
....
repeat for every version/update.

The alternative is that you have to substitute 'maintainer' for 'developer'. There are often subtle differences between different distros, e.g. what a dependency package is named, where what kind of files are stored. There is a basic standard for the latter, but there are still a number of different traditions that the developer should not have to investigate for ecach distro.

What you are insisting is that each dairy farmer should also have their own factory for putting the milk into cartons and bottles, because there are people preferring bottled milk, and those who wants cartons.

---

### Post by RiceMonster on 2010-07-14
> **alexan said:**
> ...if a maintainer had time to bring it on Ubuntu
...if a maintainer had time to bring it on Fedora
...if a maintainer had time to bring it on OpenSuse
...if a maintainer had time to bring it on Gentoo
...if a maintainer had time to bring it on Android
....
repeat for every version/update.

Which is not a difficult process at all. Further proof you know nothing about packaging. It's far easier distro packaging teams to package it for their distro than for a developer to package it for every distro.

> **alexan said:**
> This mean what?
some sort of "deserved" punishment for every distro maintainer of linux?
If microsoft want to make it's own repository, they had just to download bunch of exe and upload somewhere.
.exe is not more "standard" than ubuntu/debian .deb

Punishment? If you're maintaining a distro, you know you will be compiling lots of software into packages. The fact of the matter is that a lot of distros will add patches to the software they provide, which means they would have to build a package anyway.

Your theory that packaging is such a difficult process for distro maintainers but simple for developers is highly amusing.

---

### Post by alexan on 2010-07-14
> **ajackson said:**
> Oh dear do you think the same people do that for every distro?
If you have the time, feel free to check what I am trying to say; not only what you do need to reply.


> **ajackson said:**
> Where do I say it is a punishment?
"*If microsoft want to make it's own repository, they had just to download bunch of exe and upload somewhere.*"
Still there: developers (the same which develop stuff for linux) use a standard which greatly simplify the life of Microsoft if they wanted to make something like linux.
If a developer release tar.gz only, expect that part of the work (compiling) should be done by distro-maintaner. Thus, the same developer feel like to compile his work for windows user.
more manual work is required on the shoulder of the distro mainaner: linux, punishment.
This is not your say, its mine.


> **ajackson said:**
> Tell me you are kidding, tell me you don't really believe that? Any credibility your argument might have had has just gone up in flames as you now show that you don't understand what an exe is.
(Setup.)exe IS the standard to distribuite software like water is the standard to clean your car. There are other *primary* use of water... but still the people wash their car with it ;)



> **ajackson said:**
> The world isn't black and white, you could probably find windows software that is supplied as source only - using your logic you would have lied if you said windows was easy to install stuff on.
There aren't just black, white and gray areas, there are things called, "proportions".

> Thank you for falling into the trap I laid, the cbz format is just another compression format (like zip, tar.gz, tar.bz2) in fact cbz is the same as a zip, cbg is the same as a tar.gz. So by supplying your comics in a cbz format you are forcing people to use the "source" for your comics.

But you think that making it available as cbz file is a good idea, you are forcing the user to install software that can read/process those files, kind of like a dependency you could say.

cbz is a very good standard because it's open (based upon a open source compression); you didn't even notice that I haven't used cbr (fairly more common, since offer better compression of the JPGs file)?

BTW: do you know which format compression use .deb pacakges?

yes, tar.gz (with others) :shock: :popcorn:

anyway, there also aviable cb7 (7zip) and cbt (tar) formats.
This is not about to find the "best format in the universe".. but find a simple and handy one.. for everyone.



> **red_Marvin said:**
> What you are insisting is that each dairy farmer should also have their own factory for putting the milk into cartons and bottles, because there are people preferring bottled milk, and those who wants cartons.

Again, I am talking about a work that's _already done_, provide compiled (bottled milk) is something developer are already doing.... for windows and mac.
We talk about the same developers which provide source and binary for winmac.. and tar.gz only for linux.

Due all respect to linux choice.. but still unfair against it.

---

### Post by DrMelon on 2010-07-14
Before you start telling people what needs to be done to an operating system, how about actually being legible? I can't understand a word you're saying.

---

### Post by red_Marvin on 2010-07-14
> **alexan said:**
> Again, I am talking about a work that's _already done_, provide compiled (bottled milk) is something developer are already doing.... for windows and mac.
We talk about the same developers which provide source and binary for winmac.. and tar.gz only for linux.

Due all respect to linux choice.. but still unfair against it.

Installing on linux and windows are different beasts altogether, so it is not not work already done. Read about the differences between static and dynamic linking.

---

### Post by alexan on 2010-07-14
> **red_Marvin said:**
> Installing on linux and windows are different beasts altogether, so it is not not work already done. Read about the differences between static and dynamic linking.


Looks like you're imply that's not possible. This has nothing to do with all everything I am trying to tell about.

.deb and .rpm are already available and working for mostly linux user, distro derivatives&co.

---

### Post by MCVenom on 2010-07-14
> **alexan said:**
> Looks like you're imply that's not possible. This has nothing to do with all everything I am trying to tell about.

.deb and .rpm are already available and working for mostly linux user, distro derivatives&co.
alexan... To be perfectly honest, you don't know what you're talking about, I'm not trying to insult you, but simply stating that you should read up more on this subject before trying to debate it further. A *.deb and an *.exe are completely different. Different in the way they're created, different in what they actually do, and different in the way their respective OS handles them. 

Furthermore, open source software is distributed in an easy way through the repos; if you need to use something outside them, fine. At this point, and speaking from experience, it usually is in a PPA somewhere. If not, you might find a *.deb package. I've found plenty of out of repo software available as either format. Can't find it in the repos? Hellbent on getting it in a *.deb? Try [http://www.getdeb.net]("http://www.getdeb.net/") . It's probably there. If you are seeing so many tarballs (and I can't believe that it seems that no one has said this in the regard that *.debs/PPAs are more available than OP thinks), I'm sorry, you're probably doin' it wrong.

If at this point you *still* can't find it (highly unlikely), obviously no one bothered to package it (rather rare, once again) and you'll have to compile it. Nine times outta ten it's:

```
sudo make
sudo make install
```And nothing more. But, for some software it might be more complex. Still, you don't lose more than fifteen minutes compiling it. Personally though, I only ever had to touch one tarball, and that was for a driver on an old computer I was setting up.

Alexan, may I ask what brought this on? I think you simply have not been looking in the right places for some of this software. What have you had to compile?

---

### Post by ajackson on 2010-07-14
> **alexan said:**
> If a developer release tar.gz only, expect that part of the work (compiling) should be done by distro-maintaner. Thus, the same developer feel like to compile his work for windows user.
more manual work is required on the shoulder of the distro mainaner: linux, punishment.
So all windows executables are created by the developers are they? No windows software is supplied as source code only is it?

> **alexan said:**
> (Setup.)exe IS the standard to distribuite software like water is the standard to clean your car. There are other *primary* use of water... but still the people wash their car with it ;)
What does washing a car have to do with software distribution?

setup.exe is a common filename for windows based installers, so is install.exe but then setup.msi is also a fairly common way of installing windows software. An exe file is more than just an installer, have [read]("http://en.wikipedia.org/wiki/Exe") on what an exe file actually is.

> **alexan said:**
> BTW: do you know which format compression use .deb pacakges?

yes, tar.gz (with others) :shock: :popcorn:
Well :shock: that means that your argument to use debs to get away from a tar.gz mindset is complete nonsense as according to yourself a deb uses tar.gz compression, so using a deb helps reinforce the tar.gz mindset that you hate so much :shock: :popcorn:

> **alexan said:**
> This is not about to find the "best format in the universe".. but find a simple and handy one.. for everyone.
What you mean like using some of the standard compression formats like tar.gz to distribute software? That is simple and handy for everyone (you try installing a deb on a system that uses rpm packages).

> **alexan said:**
> Again, I am talking about a work that's _already done_, provide compiled (bottled milk) is something developer are already doing.... for windows and mac.
We talk about the same developers which provide source and binary for winmac.. and tar.gz only for linux.
Again you seem to think that every software developer has teams of people working with them, they don't. My software is a one-man setup, I don't have the time or resources that someone like Mozilla has to provide a compiled binary package in every format known to man.

> **alexan said:**
> Due all respect to linux choice.. but still unfair against it.
Unfair would be if the software in question was not available.

You don't understand software development, you don't understand package creation, you don't understand what an exe is, you don't understand that all software is not created by large organisations. Do yourself a favour and learn about those things, I know you won't so I won't waste any more time trying to get you to understand pretty simple concepts, perhaps it is the language barrier causing some of the confusion I don't know but you speak English better than I do whatever your native language is.

---

### Post by alexan on 2010-07-15
> **ajackson said:**
> So all windows executables are created by the developers are they? No windows software is supplied as source code only is it?
Proportions, don't forget the *Proportions*


> **ajackson said:**
> What does washing a car have to do with software distribution?
Take your time, there's no haste.



> **ajackson said:**
> Well :shock: that means that your argument to use debs to get away from a tar.gz mindset is complete nonsense as according to yourself a deb uses tar.gz compression, so using a deb helps reinforce the tar.gz mindset that you hate so much :shock: :popcorn:
Tar.gz offer nothing but compression
deb (or rpm) offer compression and the whole structure to manage dependencies, updates and lot of things that with tar.gz should be done manually... open a README file.


> **ajackson said:**
> What you mean like using some of the standard compression formats like tar.gz to distribute software? That is simple and handy for everyone (you try installing a deb on a system that uses rpm packages).
deb/rpm aren't just compression format but, like cbz or jpg, specific format to solve easily a specific function: distribute, update and install software packages.

tar.gz is not, tar.gz it's just a, non invasive, compression format that you can use whatever you wish.. but only with the right proficiency/knowledge

> **ajackson said:**
> Again you seem to think that every software developer has teams of people working with them, they don't. My software is a one-man setup, I don't have the time or resources that someone like Mozilla has to provide a compiled binary package in every format known to man.
Well, simply: mozilla has time and/or resource to *provide compiled binary package in every format known to man*... but still stick with tar.gz


> **ajackson said:**
> Unfair would be if the software in question was not available.

You don't understand software development, you don't understand package creation, you don't understand what an exe is, you don't understand that all software is not created by large organisations. Do yourself a favour and learn about those things, I know you won't so I won't waste any more time trying to get you to understand pretty simple concepts, perhaps it is the language barrier causing some of the confusion I don't know but you speak English better than I do whatever your native language is.

I think this close the discussion (with you). Where I am wrong, and where you are.. will be pretty obvious to reader's eye.

---

### Post by mobilediesel on 2010-07-15
> **alexan said:**
> Proportions, don't forget the *Proportions*



Take your time, there's no haste.




Tar.gz offer nothing but compression
deb (or rpm) offer compression and the whole structure to manage dependencies, updates and lot of things that with tar.gz should be done manually... open a README file.



deb/rpm aren't just compression format but, like cbz or jpg, specific format to solve easily a specific function: distribute, update and install software packages.

tar.gz is not, tar.gz it's just a, non invasive, compression format that you can use whatever you wish.. but only with the right proficiency/knowledge


Well, simply: mozilla has time and/or resource to *provide compiled binary package in every format known to man*... but still stick with tar.gz




I think this close the discussion (with you). Where I am wrong, and where you are.. will be pretty obvious to reader's eye.

[IMG]http://dl.dropbox.com/u/1055489/mobilediesel/lolwut.jpg[/IMG]

---

### Post by louis--taylor on 2010-07-15
> Where I am wrong, and  where you are.. will be pretty obvious to reader's eye.I agree! Sadly, with the opposite effect to the one you intended...

---

### Post by iponeverything on 2010-07-15
> **alexan said:**
> quit with tar.gz for general distribution: let the tar.gz to their only use = collect source to compile/study. --- evolute to ---> deb or deb+rpm or (even better) deb repository for latest ubuntu release.


sudo apt-get install:
[alt]+[f2] > apt:/[namepackage]
let apt-get usage for specific techy needs.. and move forward to human logic friendliness.


Leave behind compiling.. humm. Open source is about the source - about the ability freely modify, improve and customize the source. Compiling is the turning that source into machine readable code. 

A compressed archive just happens to be most portable ways of distributing source.  

It could be that you're using the wrong OS..

---

### Post by alexan on 2010-07-15
> **louis--taylor said:**
> I agree! Sadly, with the opposite effect to the one you intended...

I don't want "convert" anyone to my thoughts. I can safely handle opposing views; anyway, you're not offering any point of view other than show the "believing in your belief"

> **iponeverything said:**
> Leave behind compiling.. humm. Open source is about the source - about the ability freely modify, improve and customize the source. Compiling is the turning that source into machine readable code. 

A compressed archive just happens to be most portable ways of distributing source.  

It could be that you're using the wrong OS..

Leave behind the *imposition* of compiling, anyway: tag.gz it's not only about compile... sometime they contain binary files.
What I do suggest, is _add_ an option when come to just deliver software. A deb/rpm option to show linux don't lacks in standards when they are required.

---

### Post by MCVenom on 2010-07-15
> > **alexan said:**
> Looks like you're imply that's not possible. This  has nothing to do with all everything I am trying to tell about.

.deb and .rpm are already available and working for mostly linux user,  distro derivatives&co.
alexan... To be perfectly honest, you don't know what you're talking  about, I'm not trying to insult you, but simply stating that you should  read up more on this subject before trying to debate it further. A *.deb  and an *.exe are completely different. Different in the way they're  created, different in what they actually do, and different in the way  their respective OS handles them. 

Furthermore, open source software is distributed in an easy way through  the repos; if you need to use something outside them, fine. At this  point, and speaking from experience, it usually is in a PPA somewhere.  If not, you might find a *.deb package. I've found plenty of out of repo  software available as either format. Can't find it in the repos?  Hellbent on getting it in a *.deb? Try [http://www.getdeb.net]("http://www.getdeb.net/") . It's probably there. If you  are seeing so many tarballs (and I can't believe that it seems that no  one has said this in the regard that *.debs/PPAs are more available than  OP thinks), I'm sorry, you're probably doin' it wrong.

If at this point you *still* can't find it (highly unlikely),  obviously no one bothered to package it (rather rare, once again) and  you'll have to compile it. Nine times outta ten it's:

```
sudo make
sudo make install
```And nothing more. But, for some software it  might be more complex. Still, you don't lose more than fifteen minutes  compiling it. Personally though, I only ever had to touch one tarball,  and that was for a driver on an old computer I was setting up.

Alexan, may I ask what brought this on?** I think you simply have not been  looking in the right places for some of this software. What have you  had to compile?**alexan, do you plan to answer my post at any point? :P

---

### Post by louis--taylor on 2010-07-15
> Leave behind the *imposition* of compiling, anyway: tag.gz it's not  only about compile... sometime they contain binary files.
What I do suggest, is _add_ an option when come to just deliver  software. A deb/rpm option to show linux don't lacks in standards when  they are required.

As has been stated many time throughout this thread, if you are coming into contact with so many source packages, you are doing something horribly wrong. A small example: My father uses Ubuntu/Fedora exclusively and gets along with no problems; he does not even know what a source package, or indeed what .tar.gz compression is.

The easy GNU/Linux way, and for that matter, most UNIX systems such as the bsds and OpenSolaris use a **package manager** to add, remove and manipulate software. You **do not** have to download anything, or even look at the software's project website, if the software is packaged for your distribution.

---

### Post by alexan on 2010-07-15
> **BlackOtaku said:**
> alexan, do you plan to answer my post at any point? :P

> **BlackOtaku said:**
> alexan... To be perfectly honest, you don't know what you're talking about
This is not the starting line of someone that want replies. Anyway, in 13 pages something always jump.

> **BlackOtaku said:**
> A *.deb and an *.exe are completely different. Different in the way they're created, different in what they actually do, and different in the way their respective OS handles them.
also *.dmg are completely different.
But commonly you find *.deb, (setup).exe and *.dmg on _the same website_ for the _same software_ to be donwloaded&installed.

The problem is when you find (only) exe, dmg and... tar.gz.

> **BlackOtaku said:**
> Furthermore, open source software is distributed in an easy way through the repos; if you need to use something outside them, fine. At this point, and speaking from experience, it usually is in a PPA somewhere. If not, you might find a *.deb package. I've found plenty of out of repo software available as either format. Can't find it in the repos? Hellbent on getting it in a *.deb? Try [http://www.getdeb.net](http://www.getdeb.net) . It's probably there. If you are seeing so many tarballs (and I can't believe that it seems that no one has said this in the regard that *.debs/PPAs are more available than OP thinks), I'm sorry, you're probably doin' it wrong.
obviously you don't even know what I am saying, here from my first (1st) post of this thread:
"*--- evolute to ---> deb or deb+rpm or (even better) deb repository for latest ubuntu release.*"
You're simply taking for *granted* that someone will browse the software you are looking for you (before of you) and will compile and keep updated for you. I am just saying that the people who develop software should do for linux what they are already doing for windows: compile and provide a compiled version.
Why a developer shouldn't do this? becouse he don't think it worth the time to "serve on a silver plate his work"... after all he's already "serving on golden plate, while standing on four and wiggle his tail for windows" :P


> **BlackOtaku said:**
> If at this point you still can't find it (highly unlikely), obviously no one bothered to package it (rather rare, once again) and you'll have to compile it. Nine times outta ten it's:... and if someone is left out... "who cares", isn't?
If all developers (expecially those with the "big software") start make their part (the same thing they are actually doing for win/mac.. nothing more or less); it will be more unlikely that some big&little get "cut out".

---

### Post by louis--taylor on 2010-07-15
> If all developers (expecially those with the "big software") start make  their part (the same thing they are actually doing for win/mac.. nothing  more or less); it will be more unlikely that some big&little get  "cut out".If I thought that the software that I write (sneaky advertising: [https://launchpad.net/taylortype](https://launchpad.net/taylortype)) was useful for enough people and it was stable enough, I would simply file a Request For Package bug against Debian. Soon enough, it would appear in most Debian based distribution.

If the software you want to install is not in the repositories, it is most likely unstable, too new to have made it into the repositories or not of interest to many people

> ... and if someone is left out... "who cares", isn't?What software are you actually talking about? Do you really have any examples?

---

### Post by alexan on 2010-07-15
> **louis--taylor said:**
> If I thought that the software that I write (sneaky advertising: [https://launchpad.net/taylortype](https://launchpad.net/taylortype)) was useful for enough people and it was stable enough, I would simply file a Request For Package bug against Debian. Soon enough, it would appear in most Debian based distribution.

If the software you want to install is not in the repositories, it is most likely unstable, too new to have made it into the repositories or not of interest to many people
Some "big" software developer for linux use give aviability of deb packages without wait debians guy make the job for them; for example Opera, which host its own repositories: stable and unstable.
With the deb package already provided by Opera the distro maintainer (fedora, ubuntu, opensuse etc..) are relief from some extra job.. giving the opportunity to "little" software like yours to care about.
if you too do this job, the "human horsepower" in debian/fedora/suse's factories can be used elseway to improve their distro. Or work to refine their "adherence" to a common standard.

> **louis--taylor said:**
> What software are you actually talking about? Do you really have any examples?

Take it just as example (you can find rakarrak in the repositories):
[http://rakarrack.sourceforge.net/dl.html](http://rakarrack.sourceforge.net/dl.html)

---

### Post by MCVenom on 2010-07-15
> **alexan said:**
> This is not the starting line of someone that want replies. Anyway, in 13 pages something always jump.


also *.dmg are completely different.
But commonly you find *.deb, (setup).exe and *.dmg on _the same website_ for the _same software_ to be donwloaded&installed.

The problem is when you find (only) exe, dmg and... tar.gz.


obviously you don't even know what I am saying, here from my first (1st) post of this thread:
"*--- evolute to ---> deb or deb+rpm or (even better) deb repository for latest ubuntu release.*"
You're simply taking for *granted* that someone will browse the software you are looking for you (before of you) and will compile and keep updated for you. I am just saying that the people who develop software should do for linux what they are already doing for windows: compile and provide a compiled version.
Why a developer shouldn't do this? becouse he don't think it worth the time to "serve on a silver plate his work"... after all he's already "serving on golden plate, while standing on four and wiggle his tail for windows" :P


... and if someone is left out... "who cares", isn't?
If all developers (expecially those with the "big software") start make their part (the same thing they are actually doing for win/mac.. nothing more or less); it will be more unlikely that some big&little get "cut out".
Well, considering that you obviously have no desire to admit that you do not know what you are talking about, allow me to be frank.

Sit down, shut up, and listen, okay? I *know* what you want, I *know* what you're thinking, I *get* your point. But you are operating on a flawed premise, and a complete lack of understanding here. Developers are not going to listen to someone who has clearly shown that they don't care to understand the system in place.

Alexan, I'm not trying to be mean to you, I don't mean to insult you. But it's not your English you need to work on, it's your debate skills. As much as it seems you'd like to remain ignorant of how open source software is developed and distributed on Linux systems, you can't do so and expect for the people who do know to take you seriously. There's a quote 'Don't teach your grandparents to suck eggs'. I suggest you look it up.

Furthermore, I have a theory on why you can't tell us the software you've had to compile;

> **mobilediesel said:**
> [IMG]http://ubuntuforums.org/attachment.php?attachmentid=163331[/IMG]

---

### Post by MCVenom on 2010-07-15
> **louis--taylor said:**
> What software are you actually talking about? Do you really have any examples?

> **alexan said:**
> Take it just as example **(you can find rakarrak in  the repositories)**:
[http://rakarrack.sourceforge.net/dl.html](http://rakarrack.sourceforge.net/dl.html)


[IMG]http://img404.imageshack.us/img404/7227/lolwhuttranslated384267dn3.jpg[/IMG]

---

### Post by nothingspecial on 2010-07-15
I`m unsubscribing from this thread now because it has gone on too long and I stand by my original statement which was simply

> **nothingspecial said:**
> No.

That`s not the point.

And frankly, I`m getting annoyed at the constant emails informing me of the conversation going round and round in circles.

@ alexan - I respect the way you continue to disagree with the majority amicably. I really do. Cheers.

---

### Post by MCVenom on 2010-07-15
I too am unsubscribing from this thread; it's now clear nothing good can come of it.

I saw a quote somewhere (I think on these forums) that said this:

> Significantly advanced incompetence is indistinguishable from malice.

---

### Post by alexan on 2010-07-15
BlackOtaku, I want help you to not get too disturbed by my post: welcome in my ignore list. :KS

> **nothingspecial said:**
> @ alexan - I respect the way you continue to disagree with the majority amicably. I really do. Cheers.

No problem at all, I like challenge my "belief".. I just wish others would be feel like to try the same... sometime.

---

### Post by apmcd47 on 2010-07-15
I really should not get into this debate, but ...

Am I missing something? We should not be using "sudo apt-get install" but you want all software packaged as debs which use "sudo apt-get install" ...

Surely the real reason Windows developers supply their products in binary format is that the compiler for Windows is an optional extra, and costs money, to boot. "My software is free but you will have to pay Microsoft £50 to compile it" won't wash with most users. Ditto Macintoshes.

Now, if I were to develop a nice package of some sort, I *could* package it up as an Ubuntu deb but that rather limits my audience. Instead, if I offer the source I widen my audience to several distributions of Linux, not to mention other variants/clones of Unix. And if somebody were to say to me "hey, great software - mind if I create an RPM?" I'd be delighted and would offer to host that package on my server.

Andrew

---

### Post by KiwiNZ on 2010-07-15
There was something that should have been left out ..... closure

I have just fixed that ..... Thread closed

---

