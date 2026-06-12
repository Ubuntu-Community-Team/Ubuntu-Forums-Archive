---
title: "Why I think Linux will fail on the desktop"
date: 2008-10-06
forum: Recurring Discussions
---

### Post by shadoweva00 on 2008-10-06
I've studied all the things that annoy me about Linux, and come to the conclusion that if open source will succeed on the desktop it will need a new kernel to be written. To be professional and thorough in describing why I think that, I have started a blog: [http://whydesktoplinuxwillfail.blogspot.com/]("http://whydesktoplinuxwillfail.blogspot.com/")

So far I've described the community, and package managers. The next post will probably be about driver licensing or the kernel, and then some posts responding to your angry comments.

---

### Post by Canis familiaris on 2008-10-06
I am sorry but there is no proper technical explanation on what is bad with the kernel itself.
Could you specify?
Is it because it's Monolithic? Development Method?

Personally I don't think anything is wrong with the kernel itself.

---

### Post by -Rick- on 2008-10-06
What do package dependencies have to do with the kernel again?

"http://whydesktoplinuxwillfail.blogspot.com/"
Hasn't failed me in the ~4 years that I'm using Linux on the desktop...

---

### Post by shadoweva00 on 2008-10-06
> **Anurag_panda said:**
> I am sorry but there is no proper technical explanation on what is bad with the kernel itself.
Could you specify?
Is it because it's Monolithic? Development Method?

Personally I don't think anything is wrong with the kernel itself.

Excluding the possibility of another incident like the paid developers tweaking it for servers and the ruining video on average desktops, there isn't anything wrong with it. It's how it is used that is the problem. As long as you have a Unix clone the desktop will be somewhat thrown together using existing software and dependency messes will always ensue. (i just dealt with one today: libaw6 somehow equals libxaw6, and I was told i would need openmotif in the first place...) If unix compatibility is canned, a desktop standard without an incredible heavy reliance on dependencies can be achieved. I'm saying you need a new kernel and GUI that ships with it. It would be possible to agree to a standard for desktops on Linux that would also remove the need for dependencies, but look how well all the distros have agreed on package managing itself. They would never agree to a standard desktop without dependencies for applications.

Config files: in theory these should never be touched, in practice: have a wacom tablet? The typical user must never have to edit these files by hand, like they wouldn't have to edit them on the competition. The fact that they exist means they will have to be hand edited if some unusual new piece of hardware is installed.

---

### Post by RiceMonster on 2008-10-06
> **shadoweva00 said:**
> Excluding the possibility of another incident like the paid developers tweaking it for servers and the ruining video on average desktops, there isn't anything wrong with it. It's how it is used that is the problem. As long as you have a Unix clone the desktop will be somewhat thrown together using existing software and dependency messes will always ensue. (i just dealt with one today: libaw6 somehow equals libxaw6, and I was told i would need openmotif in the first place...) If unix compatibility is canned, a desktop standard without an incredible heavy reliance on dependencies can be achieved. I'm saying you need a new kernel and GUI that ships with it. It would be possible to agree to a standard for desktops on Linux that would also remove the need for dependencies, but look how well all the distros have agreed on package managing itself. They would never agree to a standard desktop without dependencies for applications.

Config files: in theory these should never be touched, in practice: have a wacom tablet? The typical user must never have to edit these files by hand, like they wouldn't have to edit them on the competition. The fact that they exist means they will have to be hand edited if some unusual new piece of hardware is installed.

Mac OSX is a decendant of UNIX and POSIX complaint, and none of these "problems" you're talking about apply to it. I don't see how any of, or most of what you're saying has to do with the UNIX.

Actually, none of this has much to do with the kernel either. Go use Windows.

---

### Post by shadoweva00 on 2008-10-06
> **-Rick- said:**
> What do package dependencies have to do with the kernel again?

"http://whydesktoplinuxwillfail.blogspot.com/"
Hasn't failed me in the ~4 years that I'm using Linux on the desktop...

It's the downsides of package dependencies, they are directly tied to using Unix kernels. If you want universal single file installs that work on every OS distro under the name, they have to go. The only way they will is if the Unix kernel is abandoned for desktops since the same old software will just be ported to it and give the same experience with the same problems.

---

### Post by shadoweva00 on 2008-10-06
> **RiceMonster said:**
> Mac OSX is a decendant of UNIX and POSIX complaint, and none of these "problems" you're talking about apply to it. I don't see how any of, or most of what you're saying has to do with the UNIX.

Actually, none of this has much to do with the kernel either. Go use Windows.

They have strict enough control over the hardware and software so that the average user will never have to deal with the problems. Their control gives them control of what the desktop is, while Linux distros would never agree on that. It all has to do with how the kernel is used. It's a fine kernel, but it's basically politically impossible to get people bring desktop systems up to par with the competition because they can't agree.

The kernel also has licensing problems, as in broadcom. It's a bit of a problem that we can't support the most common wireless cards, and it would be better for the users if we just conceded on the need to license drivers under a specific license.

---

### Post by -Rick- on 2008-10-06
> **shadoweva00 said:**
> It's the downsides of package dependencies, they are directly tied to using Unix kernels. If you want universal single file installs that work on every OS distro under the name, they have to go. The only way they will is if the Unix kernel is abandoned for desktops since the same old software will just be ported to it and give the same experience with the same problems.
Packages running on multiple distros are possible already, but with some work (Nixstaller tries to simplify that part .. *cough*).

I don't see why throwing away years of work (kernel) is going to make any dependency problems away. Especially since dependencies are rarely on the kernel itself.

But if you want a Unix like OS without (many) dependencies, try Syllable [[link]]("http://web.syllable.org/pages/index.html")

---

### Post by chungy on 2008-10-06
> **shadoweva00 said:**
> It's the downsides of package dependencies, they are directly tied to using Unix kernels.

1. Last time I used Windows, it had a worse dependency problem.  If you install software, there's no neat repository to take care of everything automatically.  "You're missing MSXML2!" - wait, don't I have MSXML6 installed?  Oh, it's not backwards compatible.  Have to google for MSXML2 and download and install.  Start the original program's setup again.  Rinse and repeat.
2. No, the dependencies thing is not tied into the kernels in any way.  You can happily have every application be a static binary.  The downside, of course, is that all your applications will become significantly larger both on disk and in RAM, because you just eliminated shared libraries.

---

### Post by basenvironment on 2008-10-06
when will it fail? I want to be ready...

Shouldn't it of failed already? What is taking so long?

What exactly is failure anyway?

Are motorcycles a failure too? They haven't replaced cars...only offered a alternative to them.

---

### Post by shadoweva00 on 2008-10-06
> **chungy said:**
> 1. Last time I used Windows, it had a worse dependency problem.  If you install software, there's no neat repository to take care of everything automatically.  "You're missing MSXML2!" - wait, don't I have MSXML6 installed?  Oh, it's not backwards compatible.  Have to google for MSXML2 and download and install.  Start the original program's setup again.  Rinse and repeat.
2. No, the dependencies thing is not tied into the kernels in any way.  You can happily have every application be a static binary.  The downside, of course, is that all your applications will become significantly larger both on disk and in RAM, because you just eliminated shared libraries.

1. Hardly any windows software ever needs a dependency is the problem with that statement, all good software takes care of this during the install.

2. Having to store massive repositories on a server for each distro is better? Making the application huge is better? Shipping a kernel with a desktop that includes shared libraries sounds like the best solution to me (and again, also politically impossible on unix clones because no one would ever agree.)

---

### Post by damis648 on 2008-10-06
Seriously... no offense, what are you talking about? I see nothing that could make it fail.

---

### Post by SunnyRabbiera on 2008-10-06
The linux kernel is not the issue here, by all accounts its the most versatile kernel out there today thanks to contributors everywhere.
Linux is ready for the desktop in my eyes, but the desktop isnt ready for linux.

---

### Post by Canis familiaris on 2008-10-06
> **shadoweva00 said:**
> 1. Hardly any windows software ever needs a dependency is the problem with that statement, all good software takes care of this during the install.

2. Having to store massive repositories on a server for each distro is better? Making the application huge is better? Shipping a kernel with a desktop that includes shared libraries sounds like the best solution to me (and again, also politically impossible on unix clones because no one would ever agree.)

No offense based but you are getting the concepts wrong, totally wrong.

---

### Post by shadoweva00 on 2008-10-06
> **SunnyRabbiera said:**
> The linux kernel is not the issue here, by all accounts its the most versatile kernel out there today thanks to contributors everywhere.
Linux is ready for the desktop in my eyes, but the desktop isnt ready for linux.

My main point is that the desktop will never be ready, so it's time to move on to something else that frees us from the current desktop software mess by killing compatibility with these old programs, and taking the politics the developers wont overcome out by shipping with a GUI.

---

### Post by DrMega on 2008-10-06
I agree with what I read in the OP's blog.

There have been many occassions when I've installed something from the repositories and it hasn't worked, and I've had to work out what dependancies are missing. That said, the same is true in Windows.

I agree with the comments about the Linux community. Mostly everyone is a decent bunch, but nobody is prepared to pause for a moment and just consider if criticism is justified.

As for the kernel, the only thing I would change is that I'd give it a consistent API so that hardware firms could release one Linux version of their closed source drivers, knowing that their closed source driver simply makes API calls to talk to the kernel. The Linux community often criticise hardware firms for not realising Linux drivers, or not developing them properly, but if a firm has signed confidentiality agreements protecting elements of code in an attempt to conceal certain details about their hardware, which may use parts that they bought from another firm, then their hands are tied.

---

### Post by Barrucadu on 2008-10-06
I've just looked at your blog, and one thing struck me - drivers don't *have* to be open source, so what's open source got to do with Broadcom? And please explain what the kernel has to do with package managers - I'm hopelessly confused on that.

---

### Post by Canis familiaris on 2008-10-06
> **DrMega said:**
> 

As for the kernel, the only thing I would change is that I'd give it a consistent API so that hardware firms could release one Linux version of their closed source drivers, knowing that their closed source driver simply makes API calls to talk to the kernel. The Linux community often criticise hardware firms for not realising Linux drivers, or not developing them properly, but if a firm has signed confidentiality agreements protecting elements of code in an attempt to conceal certain details about their hardware, which may use parts that they bought from another firm, then their hands are tied.


But is it the problem of the **kernel**?

---

### Post by DrMega on 2008-10-06
> **Anurag_panda said:**
> But is it the problem of the **kernel**?

The bit that you've quoted me on has nothing to do with the kernel, but instead relates to other points raised by the OP.

However the bit that you *didn't* quote me on has everything to do with the kernel.

---

### Post by Canis familiaris on 2008-10-06
> **DrMega said:**
> The bit that you've quoted me on has nothing to do with the kernel, but instead relates to other points raised by the OP.

However the bit that you *didn't* quote me on has everything to do with the kernel.

Wrong Part Quoted. Corrected.

My Question Remains.

Lack Unification/Consistent API is the side effect of the license. I don't see any downside of the kernel here.

---

### Post by Mr. Picklesworth on 2008-10-06
Shadow, I think you are talking about the GNU operating system, not Linux. The kernel has nothing to do with Unix, package management or GUIs. It is certainly Unixish, but it can survive without GNU.

In fairness, it is a bit different with Windows, where a lot of strange functionality is packed into the kernel. Out here, practically everything - including GUIs and package management - is done in userspace.

Adding on to that, switching kernels with an open source desktop is absolutely trouble-free. Honest. Take a look at BSD, for example, which is perfectly happy with GNOME desktops and just about all of the software we are used to out here. All you need is a ginormous source tree, a compiler and GNU make. Go ahead, download the latest version of Hurd and build your own open source desktop on top of that. There may be some problems since the software is built and tested on Linux, but if you're fine with the whole userspace stack there shouldn't be much to worry about. File any bugs upstream.

---

### Post by shadoweva00 on 2008-10-06
> **Barrucadu said:**
> I've just looked at your blog, and one thing struck me - drivers don't *have* to be open source, so what's open source got to do with Broadcom? And please explain what the kernel has to do with package managers - I'm hopelessly confused on that.

I'll admit I can't find very detailed materials on the broadcom situation that seem to be accurate and non contradicting, once I find them I'll make a post to it to clarify. Since everyone here doesn't seem to understand my point that package managers and dependencies are linked to the unix kernels I'll make that the subject of my next post to the blog.

---

### Post by Twitch6000 on 2008-10-06
> **shadoweva00 said:**
> Since everyone here doesn't seem to understand my point that package managers are linked to the unix kernels I'll make that the subject of my next post to the blog.

No we are simply denying it because you are incorrect and not knowing what you are talking about.

Do you even realize Linux is not based on Unix?(it is just Unix Like)

It is based on Minix...

Read for yourself right here -

[http://en.wikipedia.org/wiki/Linux](http://en.wikipedia.org/wiki/Linux)

Edit: Oh and you should read this too about the GNU project <.<.

[http://en.wikipedia.org/wiki/GNU_Project](http://en.wikipedia.org/wiki/GNU_Project)

---

### Post by SunnyRabbiera on 2008-10-06
So in short are you blaming the unix like structure of linux?
You know the NT and other windows kernels are not much better.

---

### Post by Canis familiaris on 2008-10-06
And I doubt any known kernel will resolve these issues. Will FreeBSD? Will Solaris? Will XNU? Will the Windows Kernel?

---

### Post by DrMega on 2008-10-06
> **Anurag_panda said:**
> Wrong Part Quoted. Corrected.

My Question Remains.

Lack Unification/Consistent API is the side effect of the license. I don't see any downside of the kernel here.

Consider this scenario. I work as a software developer for a large firm that makes, say, graphics cards. We make the best graphics cards in the world. In order to achieve this, we buy in chips from another manufacturer who has told us that the details of how their chips work is a closely guarded secret and they don't want the info to go into the public domain. My boss has made me sign a confidentiality agreement not to disclose any source code that might give us clues how the chips work. I get asked to write the driver for that card.

I start with Windows. As long as it is a 32 bit version of Windows from 98 upto XP, it doesn't matter. I have the same API calls. I can release closed source drivers without breaching my contract and getting sued.

I then move onto Linux. I find that there's no consistent API. What am I to do? The Linux community will criticise my company if I don't produce Linux compatible driver, but if I give them a full featured one that they can compile, then I'll be in breach of my contract and will get sued. I reach a compromise, and realise a cut down version, with some elements omitted where it would breach the confidentiality agreement, and again the Linux community criticise my company because the Linux version isn't as full featured as the Windows one.

So you see, all for the lack of a consistent API, commercial organisations simply can't give us everything they give to Windows users, so we'll always be a few paces behind Windows when it comes to hardware compatibility.

---

### Post by Canis familiaris on 2008-10-06
> **DrMega said:**
> Consider this scenario. I work as a software developer for a large firm that makes, say, graphics cards. We make the best graphics cards in the world. In order to achieve this, we buy in chips from another manufacturer who has told us that the details of how their chips work is a closely guarded secret and they don't want the info to go into the public domain. My boss has made me sign a confidentiality agreement not to disclose any source code that might give us clues how the chips work. I get asked to write the driver for that card.

I start with Windows. As long as it is a 32 bit version of Windows from 98 upto XP, it doesn't matter. I have the same API calls. I can release closed source drivers without breaching my contract and getting sued.

I then move onto Linux. I find that there's no consistent API. What am I to do? The Linux community will criticise my company if I don't produce Linux compatible driver, but if I give them a full featured one that they can compile, then I'll be in breach of my contract and will get sued. I reach a compromise, and realise a cut down version, with some elements omitted where it would breach the confidentiality agreement, and again the Linux community criticise my company because the Linux version isn't as full featured as the Windows one.

So you see, all for the lack of a consistent API, commercial organisations simply can't give us everything they give to Windows users, so we'll always be a few paces behind Windows when it comes to hardware compatibility.
I see your point. However the fact that there is the lack of consistent API is the side-effect of GPL and other open source licenses. There are multiple competing standards and since there are so many standards and none is agreed unanimously, thus resulting in disunification. 
Is there a technical limitation of the kernel? NO.
If Microsoft's kernel was licensed under GPL (impossible scenario, I know but for sake of debate let's assume), and assuming there was no kernel such as Linux already, there would have been the same problem in Windows.

---

### Post by NoWayBill on 2008-10-06
oops

---

### Post by Twitch6000 on 2008-10-06
*deleted*

---

### Post by cardinals_fan on 2008-10-06
> **Twitch6000 said:**
> Good point good point
Although Linux does have three API's(this is if I know whhat API's are) they are RPM,DEB,and TAR.gz.

All you would need to do is simply make a rpm for red hat distros and a deb for Debian distros.Then if you must a tar.gz for others(which you might not be allowed due to a breach).

Also with windows their api might be coming to an end with windows 7 as they are changing some things and no longer having back ports and such.

I do understand your point though.
[http://en.wikipedia.org/wiki/Api](http://en.wikipedia.org/wiki/Api)

@OP: Let me know when you have a beta of this remarkable new operating system ready.  It might be fun to test.

---

### Post by smoker on 2008-10-06
> **shadoweva00 said:**
> My main point is that the desktop will never be ready, so it's time to move on to something else that frees us from the current desktop software mess by killing compatibility with these old programs, and taking the politics the developers wont overcome out by shipping with a GUI.

don't know about anyone else, but my desktop is just fine, maybe i'm lucky not to have experienced the above.

---

### Post by Twitch6000 on 2008-10-06
> **cardinals_fan said:**
> [http://en.wikipedia.org/wiki/Api](http://en.wikipedia.org/wiki/Api)

@OP: Let me know when you have a beta of this remarkable new operating system ready.  It might be fun to test.

Thank you for the information >.>.

---

### Post by Sorivenul on 2008-10-06
cardinals_fan, thanks for providing that link, I believe it is very helpful in relation to this topic.  

@OP: Please do specify about the package management in your next post.  After reading all the questions and answers here as well as the blog I'm no closer to understanding why Linux is not ready for the desktop.

My desktop and laptop systems run many different Linux distributions, as well as others, and have no problem.  My GUI's are perfectly functional despite the fact I use a different one on nearly every system, and I have no problem with any package management, and no problems with dependencies. However, I understand this may not be the case for every user.  

I don't understand what is implied in your definition of shared libraries, as it doesn't seem to fit the classic definition I have learned which is outlined fairly well [HERE]("http://tldp.org/HOWTO/Program-Library-HOWTO/shared-libraries.html").

The following may also be of interest:
[An interesting view on dependencies]("http://osnews.com/story/7922")
[More goodness from Wikipedia]("http://en.wikipedia.org/wiki/Dependency_hell")

I'll be looking forward to the next blog post.

---

### Post by Mr. Picklesworth on 2008-10-07
The reason why dependencies can't be handled in a "standard desktop has all of these at this version" kind of way is also the reason why open source desktops are a good idea. Each component there is developed by a different independent project. This means that the desktop can not be owned by, and thus we never become dependent on any one entity. It has the downside that things are tougher to control and fragmented. Keep in mind that the fragmentation is by design and, without it, the Linux desktop loses its soul.
Fascinating innovations like Debian package management stem from the issues presented.

(One possible fix for "everything in Ubuntu is 6 months out of date," speaking of which, would be a user-friendly way to subscribe to special updates for applications, which could add to sources.list a specialized Launchpad PPA type service for the latest stable versions of specific applications).

---

### Post by 3rdalbum on 2008-10-07
Dude, the Linux kernel can support programs that are dynamically linked (i.e. dependencies) as well as those that are static linked.

There are fundamental good reasons why it's better to have the libraries seperate rather than compiled-into the programs:

1. If multiple programs on your computer use the same library, you only need to download ONE copy of the library, which means less disk wastage and less to download
2. If there is a security flaw in a library, you can install a new patched version of it and immediately all programs that use the library will be secured.
3. Old programs can benefit from speed improvements and bug fixes from new versions of libraries, without the program developers needing to do any additional work

Look at DVDStyler. On Windows, it's static-linked, and is an 8mb download. On Linux, it's dynamic-linked and the Debian package automatically pulls in the dependencies. It's a 700kb download. Sure, the libraries might be 7mb, but if you've already got them you don't need to download them again!

There are small deficiencies in package management on Linux, but you don't even seem to know the things that really ARE issues. Stick to the repositories until you lose your training wheels.

---

### Post by 3rdalbum on 2008-10-07
> **DrMega said:**
> Consider this scenario. I work as a software developer for a large firm that makes, say, graphics cards. We make the best graphics cards in the world. In order to achieve this, we buy in chips from another manufacturer who has told us that the details of how their chips work is a closely guarded secret and they don't want the info to go into the public domain.

I then move onto Linux. I find that there's no consistent API. What am I to do? The Linux community will criticise my company if I don't produce Linux compatible driver, but if I give them a full featured one that they can compile, then I'll be in breach of my contract and will get sued.

Nvidia and ATI make the best consumer-level graphics cards in the world, and they release Linux drivers. You wanna know how they do it, even while they license software and hardware from other manufacturers?

It's simple. They write their drivers closed-source, and distribute them as precompiled binaries. There is a little open-source wrapper that they also make that contains no licensed technology, which just converts symbols and functions from the kernel into things that the driver understands. The wrapper is compiled against the kernel headers package.

All the licensed technology is still closed-source and able to be included in a Linux driver, and the Linux driver can contain as many features as the Windows one.

The reason why graphics card drivers have not achieved feature-parity with Windows is because Nvidia and ATI don't give enough resources (money, time and manpower) to the teams developing the drivers for Linux. ATI (AMD) has said that it will be fixing this situation soon.

---

### Post by DrMega on 2008-10-07
> **Anurag_panda said:**
> I see your point. However the fact that there is the lack of consistent API is the side-effect of GPL and other open source licenses. There are multiple competing standards and since there are so many standards and none is agreed unanimously, thus resulting in disunification. 
Is there a technical limitation of the kernel? NO.

Of course it is a technical limitation. The politics that created the situation do not change the fact that the result is a technical limitation. If I take two of the wheels off my car following a row with someone about how many wheels a car should have, the fact that my car has only two wheels is still a technical limitation regardless of the reason I did it.

> **3rdalbum said:**
> Nvidia and ATI make the best consumer-level graphics cards in the world, and they release Linux drivers. You wanna know how they do it, even while they license software and hardware from other manufacturers?

It's simple. They write their drivers closed-source, and distribute them as precompiled binaries. There is a little open-source wrapper that they also make that contains no licensed technology, which just converts symbols and functions from the kernel into things that the driver understands. The wrapper is compiled against the kernel headers package.

All the licensed technology is still closed-source and able to be included in a Linux driver, and the Linux driver can contain as many features as the Windows one.

The reason why graphics card drivers have not achieved feature-parity with Windows is because Nvidia and ATI don't give enough resources (money, time and manpower) to the teams developing the drivers for Linux. ATI (AMD) has said that it will be fixing this situation soon.

All true. However it has been said on this very forum that you can't guaruntee that something prepared for one distro will compile on all others. Without a consistent Linux API, a developer can't test his drivers on, say, Ubuntu and then release them with confidence that they'll work on Fedora, SUSE, Puppy and all the hundreds of others. If users of one of those distros then complains that such and such a company writes buggy drivers for Linux, then again they get bad press.

Hardware people are in a no win situation as far as Linux is concerned. A consistent API would massively help the open source movement. I don't expect anyone to agree with me, because in the past when I and others have made the same point we get told "no you're wrong, its perfect" from people on the very same forums where people kick off because of some hardware incompatibility or because they can't get some application to compile from source. The same forum where we get regular threads about the imminent demise of Microsoft Windows, posted up by users who (like me) use an operating system that is reported to have about 2% of the desktop share.

---

### Post by kaldor on 2008-10-07
I only see two problems with Linux in general; Technical Support and compatibility.

Yes, yes, Ubuntu DOES have technical support for a pretty high price, and not everyone uses Ubuntu. If Linux wants to get up there with Mac and Windows it needs to have more companies to support it. Hewlett Packard says they have Linux support(1-800-HP-LINUX), but I do not believe it is very well known. People should not have to google/search for everything they need to learn. This just forces people away from Linux and FOSS.

Compatibility is an issue that to some will not matter, as everything they need might be FOSS. But to others who want to play games etc, this can be a hassle. Wine does not work well for games in my experience. Linux needs to become more well known so that people would actually make games for Linux. ID software makes games for Linux as well as Windows. Quake 1, 2, 3 and 4 all have Linux versions. Hardware also seems to be an issue to some people. I myself have never had a problem with hardware compatibility. I must have just gotten lucky with the computers I buy. But I do hear that wireless is a huge problem to a lot of people.


Linux is not a fully developed OS yet. I agree with what the Original poster said about the community. But, besides that, I do not see why Linux can't lead. People just do not give it a chance. Some people say "LINUX SUCKS! GET WINDOWS!" when they have never even touched a Linux computer or even looked it up in their life. Those that do not complain about how much it sucks because you have to be a "nerd" to use Linux, usually do not know about it. Linux needs one good commercial distro (Canonical could advertise?) that would get the message out there.

---

### Post by Canis familiaris on 2008-10-07
> **DrMega said:**
> Of course it is a technical limitation. The politics that created the situation do not change the fact that the result is a technical limitation. If I take two of the wheels off my car following a row with someone about how many wheels a car should have, the fact that my car has only two wheels is still a technical limitation regardless of the 
reason I did it.

Let's agree to disagree on the debate that "it's a technical limitation" :)

> 
All true. However it has been said on this very forum that you can't guaruntee that something prepared for one distro will compile on all others. Without a consistent Linux API, a developer can't test his drivers on, say, Ubuntu and then release them with confidence that they'll work on Fedora, SUSE, Puppy and all the hundreds of others. If users of one of those distros then complains that such and such a company writes buggy drivers for Linux, then again they get bad press.
I think Linux would *never* get the uniformity. It has such a license and reputation, there would be constant derivatives and imcompatibilities.
Though we have OpenSolaris which has a consistent API. Personally I feel it's very promising.

---

### Post by basenvironment on 2008-10-07
> **basenvironment said:**
> when will it fail? I want to be ready...

Shouldn't it of failed already? What is taking so long?

What exactly is failure anyway?

Are motorcycles a failure too? They haven't replaced cars...only offered a alternative to them.

bump....could use some answers, please

---

### Post by handy on 2008-10-07
The OP was flame bait.

---

### Post by DrMega on 2008-10-07
> **Anurag_panda said:**
> I think Linux would *never* get the uniformity. It has such a license and reputation, there would be constant derivatives and imcompatibilities.
Though we have OpenSolaris which has a consistent API. Personally I feel it's very promising.

I agree, and I think it actually *should* be the way, that we get lots of choice in distros. However one of those choices could be a standard API layer that some distro creators might choose not to have. Much in the same way as there is no desktop standard or graphical standard, pretty much all distros I've tried use the Xorg x-server jobby to handle all graphics and IO. There are many applications that *require* an x-server to be running, many that *require* certain standard libraries etc. Why can't we have an API layer that is optional, but gives driver writers everything they need to write realiable binary drivers for their hardware, on the assumption that all the latest distros will either have that layer by default, or can have it installed as an option?

> **handy said:**
> The OP was flame bait.

I don't think it was intended that way. I think the OP's motive was to push forward Linux. I think in his blog he raised some very valid points. You don't need to look any further than this forum to see evidence of some of his claims. Take a look in the 'Testimonials' section and find some threads from people who had little or no luck and you won't be searching long before finding claims that it was all the thread starters fault and that everything works great.

---

### Post by basenvironment on 2008-10-07
Is it going to fail in like one year or closer to ten years? If someone is sure it will fail they should be able to provide some time frame.

---

### Post by DrMega on 2008-10-07
> **basenvironment said:**
> Is it going to fail in like one year or closer to ten years? If someone is sure it will fail they should be able to provide some time frame.

I don't agree with the OP when he claims Linux will fail, but I think people are getting too hung up on this one point in what he said. Not agreeing with this one point doesn't make the rest of his points invalid though.

Also, I saw no definition for failure in this context. Perhaps the OP meant that it will fail to capture a majority market share on the desktop, in which case I have to agree based on how things are at the moment. If on the other hand 'failure' means losing its current share or failing to gain any ground, then the evidence speaks for its self that this isn't true.

---

### Post by shadoweva00 on 2008-10-07
First, I know it will never "fail" because it's open source. It would be nearly impossible to kill an open source product, just take it as irony and move on.

Secondly I tried to answer the how the kernel is related to dependencies question, but I can't seem to write something that I feel does a good enough job of explaining it. Here it is anyway: [http://whydesktoplinuxwillfail.blogspot.com/2008/10/unix-compatable-kernels-and.html]("http://whydesktoplinuxwillfail.blogspot.com/2008/10/unix-compatable-kernels-and.html")

---

### Post by DrMega on 2008-10-07
> **shadoweva00 said:**
> First, I know it will never "fail" because it's open source. It would be nearly impossible to kill an open source product, just take it as irony and move on.

Secondly I tried to answer the how the kernel is related to dependencies question, but I can't seem to write something that I feel does a good enough job of explaining it. Here it is anyway: [http://whydesktoplinuxwillfail.blogspot.com/2008/10/unix-compatable-kernels-and.html]("http://whydesktoplinuxwillfail.blogspot.com/2008/10/unix-compatable-kernels-and.html")

I've had a read of your latest addition to your blog. While I agree with the sentiment of what I think you're saying, I can't agree with the detail.

The choice of desktop environment has little or nothing to do with the dependancies issue you raised, nor has it anything to do with laziness when choosing a desktop environment or other software. I use the Gnome desktop, but use many apps that were meant for KDE and some that were meant for Xfce. They all run fine under Gnome.

I think the dependancies issue arises at the packaging stage (if installing from packages), where the person or persons that built the dependancy list in the package made some incorrect assumptions and/or didn't test the install of their package on a fresh install of the OS. I can't really see an easy way round that problem, and it is a problem that also exists in Windows.

When compiling from source, the dependancies issue takes on a new level of complexity. The source may not have been aimed at any particular distro, and may have been developed and tested on a different distro, on which it may have compiled and ran without issues.

What could be done to combat the problem is if error messages (both compile time and run time) were a bit more meaningful, and if some sort of consistent standard format for such error messages was adopted. If that happened then a simple app could be developed that could import the error messages and automatically resolve the dependancies by downloading whatever was missing. In the case of Ubuntu the dependancies are usually there in the repos, but it can sometimes be difficult trying to determine what's missing based on rather cryptic messages.

None of these issues are to do with the kernel or the desktop environment.

One issue that *is* kernel related, as I've mentioned before, is the lack of a consistent API. If there was a consistent API, consistent across the major distros at least, then commercial developers might be more inclined to produce decent hardware drivers for Linux, which is one of the major drawbacks to Linux based OS's in my mind. This API could be something that is actually in the kernel itself, or equally it could be implemented as an optional extra layer much as the X-server is. That way nobody would lose any freedom of choice, they could choose a distro without the API if they wanted to, but for those that had the API, they would have a distro that developers, commercial or whatever, could target their software at knowing that it will in fact run.

---

### Post by shadoweva00 on 2008-10-07
> **DrMega said:**
> I've had a read of your latest addition to your blog. While I agree with the sentiment of what I think you're saying, I can't agree with the detail.

The choice of desktop environment has little or nothing to do with the dependancies issue you raised, nor has it anything to do with laziness when choosing a desktop environment or other software. I use the Gnome desktop, but use many apps that were meant for KDE and some that were meant for Xfce. They all run fine under Gnome.

I think the dependancies issue arises at the packaging stage (if installing from packages), where the person or persons that built the dependancy list in the package made some incorrect assumptions and/or didn't test the install of their package on a fresh install of the OS. I can't really see an easy way round that problem, and it is a problem that also exists in Windows.

When compiling from source, the dependancies issue takes on a new level of complexity. The source may not have been aimed at any particular distro, and may have been developed and tested on a different distro, on which it may have compiled and ran without issues.

What could be done to combat the problem is if error messages (both compile time and run time) were a bit more meaningful, and if some sort of consistent standard format for such error messages was adopted. If that happened then a simple app could be developed that could import the error messages and automatically resolve the dependancies by downloading whatever was missing. In the case of Ubuntu the dependancies are usually there in the repos, but it can sometimes be difficult trying to determine what's missing based on rather cryptic messages.

None of these issues are to do with the kernel or the desktop environment.

One issue that *is* kernel related, as I've mentioned before, is the lack of a consistent API. If there was a consistent API, consistent across the major distros at least, then commercial developers might be more inclined to produce decent hardware drivers for Linux, which is one of the major drawbacks to Linux based OS's in my mind. This API could be something that is actually in the kernel itself, or equally it could be implemented as an optional extra layer much as the X-server is. That way nobody would lose any freedom of choice, they could choose a distro without the API if they wanted to, but for those that had the API, they would have a distro that developers, commercial or whatever, could target their software at knowing that it will in fact run.

The choice of desktop does not matter, they've been made to be very compatible with each other. The problem lies in what needs to be done to compete, ship a desktop with the kernel. If these desktops are used, it'd just be a disaster. (think about what the people will do, competing package managers...) Also, the first time I install a KDE app on GNOME, it seems to need at least 300MB of KDE code to run according to the dependencies. Not exactly fine in my opinion.

The dependency problem you describe could also be solved with shipping with a desktop. Just like windows and mac, very few people would need to have any sort of dependencies installed. If someone forgets, they would find out quickly since the majority of systems would have hardly any "dependencies" installed. Sort of like gtk installs on windows, hardly anyone needs it, and sometimes it's just packages as part of the program.  

In other words, it's time to kill the problem with firepower.

---

### Post by marsmissionaries on 2008-10-07
Simply Put: You're a moron.

---

### Post by aysiu on 2008-10-07
We're up to over 40 posts, and I still haven't seen any link between the OP's criticisms about dependency problems and the Linux kernel, so I've retitled the thread. I've also moved it to Recurring Discussions, based on the content (not the original title) of the thread and the name of the blog linked to in the original post.

---

### Post by DrMega on 2008-10-07
> **shadoweva00 said:**
> The choice of desktop does not matter, they've been made to be very compatible with each other. The problem lies in what needs to be done to compete, ship a desktop with the kernel. If these desktops are used, it'd just be a disaster. (think about what the people will do, competing package managers...) Also, the first time I install a KDE app on GNOME, it seems to need at least 300MB of KDE code to run according to the dependencies. Not exactly fine in my opinion.

The dependency problem you describe could also be solved with shipping with a desktop. Just like windows and mac, very few people would need to have any sort of dependencies installed. If someone forgets, they would find out quickly since the majority of systems would have hardly any "dependencies" installed. Sort of like gtk installs on windows, hardly anyone needs it, and sometimes it's just packages as part of the program.  

In other words, it's time to kill the problem with firepower.

What you seem to be suggesting is that the choice should be taken away from the user.

When you install KDE on Ubuntu, if memory serves me right, a load of KDE apps come with it. That's probably why it is such a large download, but the user has chosen to do that. I can't see how that can be detrimental in any way, unless I'm missing your point completely?

If it is size of downloads you're concerned about, lets consider some facts. Ubuntu fits on a CD, and from a clean install you already have your kernel, desktop and some popular apps. Windows Vista comes on a DVD and all you get is the OS.

In your argument, you suggest that the choice of desktop should be forced upon the user and shipped with the kernel. It is in most distros, but then there are some cli only distros. All of which can be tailored and added to. So if you are saying that success lies in choosing a desktop and sticking with it, then Ubuntu and others have done that with Gnome or KDE or whatever other DE they started with. As a KDE app will run in Gnome or Xfce and vice versa, I don't see that limiting the choice would add anything of value (in fact it would take away, for example I personally don't like KDE but some people love it).

---

### Post by chungy on 2008-10-07
> **shadoweva00 said:**
> Secondly I tried to answer the how the kernel is related to dependencies question, but I can't seem to write something that I feel does a good enough job of explaining it. Here it is anyway: [http://whydesktoplinuxwillfail.blogspot.com/2008/10/unix-compatable-kernels-and.html]("http://whydesktoplinuxwillfail.blogspot.com/2008/10/unix-compatable-kernels-and.html")

I'm going to pick apart the second paragraph very carefully because it contains the roots for much of your other misinformation.

> The first thing that needs to be considered is installing software on Mac and Windows doesn't usually involve dependencies.
Actually, yeah it does.  The difference between Mac OS X and Windows, is that the former has package managers and can resolve dependencies automatically (like most Linux distros!), and the latter usually requires the user to supply dependencies manually (sometimes in a friendly "You are missing Microsoft Visual Basic runtimes, please install at http....", but far more often as a "Missing DLL: VBRUN60.DLL" with little information on how to resolve).  Mac OS X even has entire repositories to provide nearly the same software found in Debian/Ubuntu.

> It is very simple, their kernel ships with their desktop.
For Mac OS X, this is simply untrue.  Cocoa and applications under it are in no way tied into the kernel.  Go look up Darwin for an operating system without Cocoa; it's not some silly hack either, it's official from Apple.  For Windows NT, bad design decisions ended them up there;  NT 3.1 didn't have it integrated, but NT 3.5 did (the execs wanted it to compete with Unix/X11's speed, which runs entirely in user space).

> The developers aren't allowed to stray much from how the makers want the programs to be made.
For Mac OS X, there's some recommended guidelines, but none of it can be forced.  Plenty of applications break traditional conventions; although for the most part, it's GNOME/KDE software doing this.  For Windows, there really is no such thing as guidelines even, hell even Microsoft Office breaks any shred of established consistency.  To say that developers aren't allowed to stray is blatantly false.

> By shipping with a desktop, they have eliminated the user's need to deal with dependencies and created a de facto standard of single file universal installs.
No to both accounts.

> Now, why isn't it possible to do this on Linux or any other Unix compatible kernel?
It is, and it already exists.  You want single-file installs, download a pre-packaged .deb or .rpm; if your desired software doesn't provide them, ask for it, they're the most widely used package formats on the planet.  Actually, most of the time you won't be straying away from the repositories provided to you via APT/Yum, they contain almost everything anyone ever wants, and all the dependencies are handled in a much better and easier fashion than either OS X or Windows.

---

### Post by BLTicklemonster on 2008-10-07
Linux is succeeding on my desktop, it's Windows that failed.

---

### Post by handy on 2008-10-07
> **BLTicklemonster said:**
> Linux is succeeding on my desktop, it's Windows that failed.

:lolflag:

We've done it again BLT!?

---

### Post by BLTicklemonster on 2008-10-07
Dude, we're like ... gross or something.

:lolflag:

---

### Post by shadoweva00 on 2008-10-07
> **chungy said:**
> I'm going to pick apart the second paragraph very carefully because it contains the roots for much of your other misinformation.


Actually, yeah it does.  The difference between Mac OS X and Windows, is that the former has package managers and can resolve dependencies automatically (like most Linux distros!), and the latter usually requires the user to supply dependencies manually (sometimes in a friendly "You are missing Microsoft Visual Basic runtimes, please install at http....", but far more often as a "Missing DLL: VBRUN60.DLL" with little information on how to resolve).  Mac OS X even has entire repositories to provide nearly the same software found in Debian/Ubuntu.

And that resolving dependencies windows is practically never needed, and not that hard to figure out. A few searches for Mac, dependencies, and package managers, seem to say that Mac doesn't have any real problems in this area either. And those debian/ubuntu repositories is clearly just to cater to those linux users who want to use their old programs.


> **chungy said:**
> For Mac OS X, this is simply untrue.  Cocoa and applications under it are in no way tied into the kernel.  Go look up Darwin for an operating system without Cocoa; it's not some silly hack either, it's official from Apple.  For Windows NT, bad design decisions ended them up there;  NT 3.1 didn't have it integrated, but NT 3.5 did (the execs wanted it to compete with Unix/X11's speed, which runs entirely in user space).

Ships doesn't remotely mean integrated, it just means that it comes with it. If the desktop comes with it, then the developers can't stray. While linux has gtk, qt, etc...



> **chungy said:**
> For Mac OS X, there's some recommended guidelines, but none of it can be forced.  Plenty of applications break traditional conventions; although for the most part, it's GNOME/KDE software doing this.  For Windows, there really is no such thing as guidelines even, hell even Microsoft Office breaks any shred of established consistency.  To say that developers aren't allowed to stray is blatantly false.

No one uses huge amounts of dependencies in their software, clearly they were able to force people to use single file installs, and only use the native GUI capabilities. If they didn't, those developers wouldn't have users since the competition would provide.


> **chungy said:**
> It is, and it already exists.  You want single-file installs, download a pre-packaged .deb or .rpm; if your desired software doesn't provide them, ask for it, they're the most widely used package formats on the planet.  Actually, most of the time you won't be straying away from the repositories provided to you via APT/Yum, they contain almost everything anyone ever wants, and all the dependencies are handled in a much better and easier fashion than either OS X or Windows.

A terrible work around, also meaning we need huge software repositories for every distro. If the desktop experience is to be unified, everyone has to agree on a standard package format, and there is no chance that will happen.

In final, you seem to only think about the system and the programs, the actual user and user experience seem to be a mile away from your thoughts. Are you thinking about why Mac and Windows have so much market share and Linux can't break 1% even with Vista? The big guys ship their kernel with a desktop, and this provides an experience that just works without any need for dependency handling for the vast majority of users and makes those single file universal installs possible.

---

### Post by shadoweva00 on 2008-10-07
> **aysiu said:**
> We're up to over 40 posts, and I still haven't seen any link between the OP's criticisms about dependency problems and the Linux kernel, so I've retitled the thread. I've also moved it to Recurring Discussions, based on the content (not the original title) of the thread and the name of the blog linked to in the original post.

I believe the title you choose doesn't have that much to do with the thread. After all the blog is about what would be needed for open source operating systems to move forward and why, not "why Linux will fail."

---

### Post by aysiu on 2008-10-07
> **shadoweva00 said:**
> If the desktop experience is to be unified, everyone has to agree on a standard package format, and there is no chance that will happen. It won't happen in the way you're thinking it might happen (a committee is formed, and people argue back and forth and come to a consensus through discussion), but it still could happen in another way. If one distro (Ubuntu or Fedora or Mandriva) becomes extremely popular in the preinstalled consumer laptop/netbook/desktop sector, it will be the *de facto* standard for packaging.

You may think me biased as a Ubuntu user and forum moderator, but my gut is telling me if that ever happens, it'll be Ubuntu that comes out on top in this regard, and if commercial vendors start making only .deb packages that are Ubuntu-compatible, then .rpm will just die off naturally.

---

### Post by aysiu on 2008-10-07
> **shadoweva00 said:**
> I believe the title you choose doesn't have that much to do with the thread. After all the blog is about what would be needed for open source operating systems to move forward and why, not "why Linux will fail."
Your blog's url *is* [http://**whydesktoplinuxwillfail**.blogspot.com/](http://whydesktoplinuxwillfail.blogspot.com/). That's why I retitled it this way.

If you want, I can retitle it *Suggestions for improving open source operating systems*.

---

### Post by cardinals_fan on 2008-10-07
> **Anurag_panda said:**
> 
Though we have OpenSolaris which has a consistent API. Personally I feel it's very promising.
Perhaps you should read the API link I posted.  It might be educational.
> **shadoweva00 said:**
> 
The dependency problem you describe could also be solved with shipping with a desktop. Just like windows and mac, very few people would need to have any sort of dependencies installed. If someone forgets, they would find out quickly since the majority of systems would have hardly any "dependencies" installed. Sort of like gtk installs on windows, hardly anyone needs it, and sometimes it's just packages as part of the program.  

After all, there aren't any Linux distributions that ship with a desktop environment installed.  GNOME doesn't actually come with Ubuntu; that must just be my imagination.

---

### Post by Mr. Picklesworth on 2008-10-07
shadoweva00, I don't doubt that you have a valid point to make, but I am fairly confident that you are using the wrong words to explain it.

I gather from your writings that you think it would be a good idea to cram a desktop environment into a kernel, because developing software in a modular way permits fragmentation.
However, it is well known that doing that is bad practice. That limits the user to one shell, which means the operating system is not flexible. No longer could the same kernel power a high-end server as powers a desktop. What about users on unusual setups, like blind people, who would want to use specialized interfaces?
It is also a disaster waiting to happen as far as security is concerned. The kernel runs with permission to do whatever it wants with a system; one wrong move and it can actually start damaging hardware. In any modern operating system, (including Windows) software like the desktop environment runs in userspace. The toplevel window manager, your web browser, the session manager and even X window system (as well as any exploited security flaws) follows the same set of rules imposed by the kernel. Pull open the GNOME system monitor, flip to the Processes tab and use View All Processes and View Dependencies for a really impressive picture.

What exactly does cramming a desktop environment into a kernel gain that an official [standard base]("http://www.linuxfoundation.org/en/LSB") does not? What about the efforts of [FreeDesktop.org]("http://www.freedesktop.org/"), which are being adopted widely for all sorts of user interface components?

It's not that I deny there are problems, but I am having a lot of trouble understanding :/


As for unification, here's how it works:

A disproportionate number of projects put their weight behind a specific desktop environment for the sake of releasing completely amazing products that totally shine because of their laser-sharp focus. (Instead of being kludgey fits-all messes). Enough really amazing products and the result is organic.
That is why my own little software fiddlings are now done in Vala, specifically with GNOME technologies and a note that they are shooting for Ubuntu but "should work on most distros with the GNOME desktop."

No, we can't just tell the universe "use this new operating system, you fools!". What happens, just as we have learned over the years from the amazing tale of Linux's growth, is that development as a whole gravitates towards progress, not empty words. If a particular fragment of the free software ecosystem shows unprecedented *progress*, a particularly large following grows around it. If not, people keep trying their own paths. It's as simple as that.

---

### Post by qazwsx on 2008-10-07
Those depency are there because open source programs may potentially share more stuff. I wouldn't like If I had 125325323 same qt libraries installed in my system.

Sometimes even unoffical repositories offers static packages based completely on open source (like this one [http://www.bunkus.org/videotools/mkvtoolnix/downloads.html](http://www.bunkus.org/videotools/mkvtoolnix/downloads.html)).

Maybe few more exceptions  could be nicer but not certainly in full scale. I don't like that kind of bloat.

Another way is to install huge amount of different stuff as default. Again unnecessary bloat.

And official repositories will quarantee better security.

Standard package format is nonsense. For example you just  can not use Debian Woody repositories in your fresh Ubuntu install. ;) Linux isn't binary  compatibile across distributions. And it is free to modify so that will remain.

---

### Post by sicofante on 2008-10-07
> **aysiu said:**
> It won't happen in the way you're thinking it might happen (a committee is formed, and people argue back and forth and come to a consensus through discussion), but it still could happen in another way. If one distro (Ubuntu or Fedora or Mandriva) becomes extremely popular in the preinstalled consumer laptop/netbook/desktop sector, it will be the *de facto* standard for packaging.

You may think me biased as a Ubuntu user and forum moderator, but my gut is telling me if that ever happens, it'll be Ubuntu that comes out on top in this regard, and if commercial vendors start making only .deb packages that are Ubuntu-compatible, then .rpm will just die off naturally.
Totally agreed. While we can't expect Linux developers to come to an agreement on standards, we can expect one distro to prevail over the rest. I'm also betting on Ubuntu, but wouldn't care if it was any other, as long as there's a clear winner. That will never kill lesser distros, it will just make commercial developers look at a single major one and stop the current mess. (BTW, IMO Mark Shuttleworth's best asset is his ability to please -or at least not upset- upstream developers enough while making strong design decisions that make Ubuntu unique.)

---

### Post by chungy on 2008-10-07
> **qazwsx said:**
> Linux isn't binary  compatibile across distributions.

Actually, for the most part, it is.  That's what the Linux Standards Base is for.

---

### Post by cardinals_fan on 2008-10-07
> **qazwsx said:**
> 
Standard package format is nonsense. For example you just  can not use Debian Woody repositories in your fresh Ubuntu install. ;) Linux isn't binary  compatibile across distributions. And it is free to modify so that will remain.
Actually, Linux **is** binary compatible across distros.  Packages don't represent the actual binary executables.

---

### Post by Sorivenul on 2008-10-07
> **cardinals_fan said:**
> After all, there aren't any Linux distributions that ship with a desktop environment installed.  GNOME doesn't actually come with Ubuntu; that must just be my imagination.

Arch doesn't come with a GUI by default.  So many choices, so much functionality I don't know what to do with myself!  Maybe I'll opt out of the bloatware this install...  
;)

---

### Post by shadoweva00 on 2008-10-07
> **aysiu said:**
> Your blog's url *is* [http://**whydesktoplinuxwillfail**.blogspot.com/](http://whydesktoplinuxwillfail.blogspot.com/). That's why I retitled it this way.

If you want, I can retitle it *Suggestions for improving open source operating systems*.

Nah, people seemed to have stopped reading thoroughly so I'm giving up on the thread. (And the blog was marked as spam from an automated system as well so I'll wait till I fix that.)

> Totally agreed. While we can't expect Linux developers to come to an agreement on standards, we can expect one distro to prevail over the rest. I'm also betting on Ubuntu, but wouldn't care if it was any other, as long as there's a clear winner. That will never kill lesser distros, it will just make commercial developers look at a single major one and stop the current mess. (BTW, IMO Mark Shuttleworth's best asset is his ability to please -or at least not upset- upstream developers enough while making strong design decisions that make Ubuntu unique.)

I doubt one will ever prevail, since they're open source they can all just re use whatever code makes the other distros popular while keeping all the stuff they disagree on.

---

### Post by cardinals_fan on 2008-10-07
> **Sorivenul said:**
> Arch doesn't come with a GUI by default.  So many choices, so much functionality I don't know what to do with myself!  Maybe I'll opt out of the bloatware this install...  
;)
I know, but Arch, Slackware, Gentoo, etc. serve a niche group.  I happen to be part of that niche, but a niche it remains.  My point was that the OP's complaint about distros not including a desktop is confusing.

---

### Post by aysiu on 2008-10-07
> **shadoweva00 said:**
> 
I doubt one will ever prevail, since they're open source they can all just re use whatever code makes the other distros popular while keeping all the stuff they disagree on. Well, to a certain extent, you're correct. There will never be only one distro. And whatever distro is most popular can always be forked. But if Ubuntu became the standard home consumer distro, all other distros that wanted to take advantage of Ubuntu's popularity would have to be directly binary compatible with Ubuntu.

Ubuntu uses .deb files, not .rpm files. It's not so easy to just make Ubuntu an .rpm-using distro.

---

### Post by Daishiman on 2008-10-08
Well, I've taken the time to read your posts, and while I think your intentions are good, you've missed the point so thoroughly that it's been right under your nose and you didn't even realize it.

Let's start with the first post: 
> The very first reason I have to why desktop Linux will fail is the community behind it.
I know you didn't mean it as a troll, but c'mon, your writing and persuasion skills should be a heck of a lot better than that!
The very FIRST thing that you're claiming is that the very first issue with Linux is with the people who use it and create it. That will get you nowhere, especially since it's because of those users, not despite them, that Linux has a market share that went from nil to millions of users.

Actually, I take it back. I take that as an insult. Most Apple users I know are pretentious twits whose computing interests are nowhere near as deep as most Linux user's, and considering most of them, they simply swallow up whatever Steve Jobs sells as the Next Great Thing. Never mind the planned obsolescence of their platform, their completely closed development model, and the fact that their EXTREMELY limited niche doesn't cater to even a tenth of what most Linux users need. And remember, Linux's users are also scientists, embedded developers, programmers, and people who do real computing. Home users are users as well, but they're not the only ones who have a stake on the matter.

And Windows users? Well, considering that being a MS users means that if your needs don't resemble Microsoft's you're out of luck, that should speak for itself.

> . The need for dependencies, the commercial development tweaking the kernel for servers, drivers that just have to be open source*. all of these things are problems that need to be talked about and solved, but if the community can't admit problems and get involved fixing them nothing will change and Linux will stay at the bottom of market share reports.


No, see, the thing is that they're problems to YOU. You're after market share; the devs and users are after something that works for them. And what works for them is not necessarily what gets the most market share.
As a user of Free Software, an open platform is a requirement. If hardware companies have a problem with that, tough. The thousands of Thinkpads and Dells running Ubuntu don't seem to have much of an issue. It seems that, actually, most vendors are pretty much OK with open drivers. The problem stems from a matter of culture.
What you fail to notice is that the requirement for openness drives away very, very few vendors, and inertia will eventually make them cater to the needs of the increasingly larger and vocal Linux user base. By demanding closed drivers you only further the problem. Theo DeRaadt (not the nicest guy around) petitioned several wireless device makers to release driver specs and got most of them. Greg Kroah-Hartman did the same and he got excellent results.
FWIW, Solaris has had a stable kernel API for eons, and most hardware fails miserable on SunOS unless it's been certified by Sun to run there.
Have you ever had to track down drivers for a Windows machine when you don't get them included in a CD? The last time I had to do that I literally spent 5 hours searching for one on the Internet, and I had to remotely install it for a friend giving her directions over the phone. Had she had Linux her hardware would have been automatically configured, or at most I'd SSH to her machine and do it as if it was my own system.
Most Windows users don't service their machines; they pay a tech to do it for them. Your argument for saying closed OSes do this better are weak at best.
Let's not even talk Apple hardware. It's as flaky as any other, and you're definitely NOT servicing it yourself.
No other operating system has ever supported as many devices out of the box as Linux, so I'd say that proprietary vendors are doing it wrong and FOSS developers are on the right.

Let's go on to your second post:
> Sure a package manager is supposed to take care of them all, but if you've installed an IDE on Ubuntu recently you know it doesn't take care of build-essential and the correct version of automake. On top of that errors like "make sure gtk+2.0 development files are installed" mean going to the package manager and looking for arbitrarily renamed packages. It could be gtk+2.0-dev or libgtk2dev, or...

You are seriously claiming this is a problem?
Have you ever programmed in your life?
You have to download development dependencies for every other system. Want to develop with third party libraries for .NET? Gotta download them, but forget about them being automatically updated for patches. Want to target a particular architecture or library? You have to download it as well.
Oh wait, you actually have to get a DVD full of 2 gigs of god-knows-what to install Visual Studio. I still don't know what those 2 gigs are for, since they do remarkably little for such bloat.
The Linux nomenclature is clear and it is trivially easy to download development packages, and you can be sure that they will work. If not, Synaptic has a great search function that gives you a hand.
If you want complete software, here's your solution: go to Applications -> Add/Remove. An ordinary user does not need to go further. If you're doing development, you can handle the "pain" of knowing dependencies.
Regular users do not compile their software. That applies to every platform. You're ultimately complaining because something that Linux can do that other operating systems cannot because it's not meant to be exposed to regular users, is difficult!

> The much bigger issue here is that the typical user thinks dependencies are obsolete technology.

You have no idea what you're talking about. Everyone I know of finds automatically dependency resolution fantastic. I haven't heard of anyone having it fail for their use. When I tell nontechnical users that my OS updates itself, they are amazed.
Are Windows and OS X outdated because they can't automatically upgrade software without running a huge bloated monitor in the systray constantly phoning home?

As for the difference in package managers, it's trivial and irrelevant. Regular users use Ubuntu. Period. I have never had to recommend anything else to ordinary users. And considering all package managers have graphical frontends that work the same and do the same, the internal mechanics don't matter to anyone except developers. And for that you have distro packagers to help out, in a well documented process. The development overhead for running in multiple distros is, IMO, trivial. You do a generic version and distros will customize it to their system.
As for proprietary vendors, they manage just fine installing their things in /opt, like they should. Never fails.

I won't bother replying about the differences in desktops. All desktops support all applications, and they look quite spiffy. Don't like GTK/QT applications? Then why do you stand Symantic products with their ugly and bloated UI, Office 2007 looking unlike anything else in Windows, AVG with its own widget set, etc?
Inconsistent desktops are at most a mild annoyance. Irregular UIs have never prevented anyone from being productive on any platform. Even the biggest of the whiners has to recognize that different versions of Apple OSes have different looks and changes in functionality that far surpass your default Gnome desktop.

Again, ordinary users simply DO NOT have dependency issues. If they should, they ought to file a bug. The one dependency error I ever had on my desktop was due to a badly packaged interal IBM application, and that was the developer's fault. 
Speaking of installers, may I remind you that Windows depends on the hideous POS that is the registry, which is never fully cleaned up when software is uninstalled. Same with OSX, a lot of static libraries are simply not cleaned up and remaining crufting up the system. Never mind the antiviruses that install kernel hooks and will complain for the end of times if you ever had a reboot in the middle of the uninstallation process for an app. I once had a Norton app fail to install properly and my system never came back up.

After thinking it over, your posts reek of troll. You mention things you FEEL are problems, yet no one seems to be truly driven away by them. Linux has other barriers of adoptions, but your points are not it.

It seems to me you've never developed for Linux, never administered a serious Linux setup, and you've never had exposure to how those things are done in other platforms.

I've developed in Java, PHP, Python, and I'm a professional .NET developer. Visual Studio is a great IDE, but not great enough to make me quit developing for Linux and attempting to convince my team to keep compatibility with Linux systems. The dev environment for Linux is just fantastic. A little fragmented, perhaps, but when you need to do pro work your options are clear. The hobby alternatives that are iffy are not even available on the other platforms, so they're the ones losing out.

As for system administration, Linux is way, way ahead. I've worked several years as a Unix sysadmin, but you could never pay me enough to administer an NT box. Shell scripts, command line, useful administration tools, easy config files, Unix/Linux has it all. Sure Active Directory is nice, but again, it's nowhere near close in flexibility.

Finally, as a user, Linux works wonderfully. I've hit upon the annoying Flash bug and a compatibility issue with a sound card, but it's just the same with Windows not wanting to reboot, forcefully rebooting itself, and failing unpredictably. We can all agree we have these tiny issues, but the continuous progress the platform makes means we have fewer and fewer of these with time. I sure can't say the same for Windows.

---

### Post by shadoweva00 on 2008-10-08
> **Daishiman said:**
> Well, I've taken the time to read your posts, and while I think your intentions are good, you've missed the point so thoroughly that it's been right under your nose and you didn't even realize it....

As i said I'm giving up on the thread, so I'm not replying to specific content anymore. That said, your post... it could not be a more perfect example of my point of the community being a problem in the first blog post. You make claims without explanations and clearly adhere to the "our way is right, our way is the only way" line of thinking. I'm only responding because it is just too perfect to illustrate my point.  Also, soo much of it is bent truth and some things that are completely wrong, if anything your post is a troll clearly meant to try to destruct a constructive conversation.

---

### Post by chungy on 2008-10-08
> **Daishiman said:**
> Theo DeRaadt (not the nicest guy around) petitioned several wireless device makers to release driver specs and got most of them.

de Raadt might not be the nicest guy around, but he sure knows how to get the job done.  He doesn't take NDAs or blobs as an answer, he doesn't say "well we have ndiswrapper (OpenBSD has no such thing), so you can take your sweet time in releasing free drivers or documentation."  He's friendly to those he agrees with, but a little stringent with those he disagrees with.  yeah, I agree that ndiswrapper isn't a good solution, though I have to unfortunately use it on my laptop and it makes me very sad.  The fact that it exists just tells manufacturers that they can continue making Windows blobs without a care in the world.

I read your entire post and agree with it whole-heartedly, this is just the one thing that I wanted to comment on :)

> **shadoweva00 said:**
> As i said I'm giving up on the thread, so I'm not replying to specific content anymore. That said, your post... it could not be a more perfect example of my point of the community being a problem in the first blog post. You make claims without explanations and clearly adhere to the "our way is right, our way is the only way" line of thinking. I'm only responding because it is just too perfect to illustrate my point.  Also, soo much of it is bent truth and some things that are completely wrong, if anything your post is a troll clearly meant to try to destruct a constructive conversation.

He's pointing out that you're just complaining about the advantages of Linux and free software, rather than making a useful contribution.  There's no issues with the state of dependencies (go try Slackware 3.0 sometime and tell me that Ubuntu is bad!  Yes, in those early days it was quite a wild thing, but I'm glad we're beyond them), and the kernel certainly doesn't even need libraries built into it (it doesn't even contain any of the basic userland programs like the shell or cp!).  "Desktop unity/standards"?  We've got far stronger consitency/standards than Microsoft's operating systems can demonstrate (I can even make a case using purely software from Microsoft, nothing 3rd party: [http://arstechnica.com/articles/culture/microsoft-learn-from-apple-II.media/vista.png](http://arstechnica.com/articles/culture/microsoft-learn-from-apple-II.media/vista.png)).

Okay, there's the thing of multiple package formats.  For the most part, the major ones are just deb and rpm (other package formats are generally restricted to just the distribution they originated on).  I believe the Linux Standard Base dictates RPM as the standard package format for all LSB-compliant distributions, although since Debian and Ubuntu are LSB-compliant, I'm not exactly sure how this works out (well, there is an rpm package in Debian/Ubuntu (somewhat ironically distributed as a deb), so you can install software from RPMs).  Besides this one point, it's still a non-issue for almost all users; they just stick to the official repositories and probably never need to install RPMs.

---

### Post by Sorivenul on 2008-10-08
> **cardinals_fan said:**
> I know, but Arch, Slackware, Gentoo, etc. serve a niche group.  I happen to be part of that niche, but a niche it remains.  My point was that the OP's complaint about distros not including a desktop is confusing.
My point was simply to add to your original idea.  I'm part of that niche as well.  Obviously the ;) wasn't enough of a hint that my comment was slightly sarcastic.

---

### Post by david_lynch on 2008-10-08
> **qazwsx said:**
> T
Standard package format is nonsense. For example you just  can not use Debian Woody repositories in your fresh Ubuntu install. ;) Linux isn't binary  compatibile across distributions. And it is free to modify so that will remain.
Actually most 3rd party software is compatible across distros -

Example: I frequently use debian packages of 3rd party software e.g. webmin on ubuntu.  
Example: Go to firefox.com and look at the downloads, there is *one* linux package, for all distros.
Example: I downloaded q3demo for linux in 1999, when I was on redhat 5.2. It kept working on fedora and suse, and it works today on hardy heron.:KS

---

### Post by mentallaxative on 2008-10-08
If you want to see change, be prepared to work for it *yourself*. 

Seriously, don't bother replying to any of these messages or posting on that blog. Go write a new kernel and new desktop environment and find a new community and companies willing to use and support it. And even if you do fail, it would have been so much more productive than what you are trying to do here.

---

### Post by DrMega on 2008-10-08
> **shadoweva00 said:**
> I doubt one will ever prevail, since they're open source they can all just re use whatever code makes the other distros popular while keeping all the stuff they disagree on.

The fact that there can always be many distros is good, and I don't think you'll ever get down to one last man standing scenario because there will always be people who don't like the "standard distro" and so build their own. The fact that people can do this is a good thing.

I do agree with what others have said about certain packaging methodologies and formats will eventually arise as a standard. We are already seeing that in the .deb package. I've seen loads of third party downloads where you can choose between the source to compile yourself, or a .deb package for Debian derivatives, and this seems to be becoming increasingly common.

I've said it before and I'll saying again, the only thing I can see that might be a hindrance to progress is the lack of consistent API, meaning that pure compiled binaries can't be expected to work across all distros.

As for binding a desktop straight into a kernel, that would be a seriously bad idea for a number of reasons, just some of which are:
[LIST]
[*]Server installations often have no need of a fancy desktop but do need to keep as much CPU and memory resources available as possible
[*]If the GUI should crash for whatever reason, it usually doesn't render the whole system unstable until the next reboot (you just restart the GUI)
[*]A layered architecture promotes diversity without compromising compatibility
[*]A wider range of hardware is supported because low spec machines can have a no-frills desktop while cutting edge machines can have all the bells and whistles
[/LIST]

On my main machine, I have the standard Gnome setup, but I also have the Xfce desktop installed. For normal usage I just use Gnome, because I like it better than Xfce, but when I play some games I prefer to switch to an Xfce session because I find that the games run better (presumably because more resources are available to the game than would be the case if I was in Gnome).

One point you've mentioned is bloat. I think you have missed the point that unlike Windows, the bloat is not forced upon us. As I just mentioned I have Gnome and Xfce desktops installed on my machine. It is not a cutting edge machine, but it is happy enough with my setup. Having Xfce and Gnome on one machine doesn't use loads of memory and CPU time, because only one is running at any time. If you're worried about hard disk usage, well disks are dirt cheap now and the capacity of most hard disks sold in the last 5 years (even cheap ones) is more than enough to comfortably accomodate a solid Linux setup with a choice of desktops and a good range of apps.

My machine that I'm on now has the following spec. I challenge anyone to get Windows Vista to run smoothly on it in a usable way:

AMD Duron 1.8GHz
512MB RAM
nVidia N6200 128MB AGP graphics card
40GB hard disk (primary)
20GB hard disk (secondary)

---

### Post by aysiu on 2008-10-08
> **DrMega said:**
> 
I've said it before and I'll saying again, the only thing I can see that might be a hindrance to progress is the lack of consistent API, meaning that pure compiled binaries can't be expected to work across all distros. I don't know what an API is. Can you explain a bit what you mean by this? I may be getting my terminology screwed up here, but I've seen precompiled binaries that work across all distros (Google Earth, Firefox from Mozilla's website, FirstClass, Songbird, etc.). Is that something different?

---

### Post by DrMega on 2008-10-08
> **aysiu said:**
> I don't know what an API is. Can you explain a bit what you mean by this? I may be getting my terminology screwed up here, but I've seen precompiled binaries that work across all distros (Google Earth, Firefox from Mozilla's website, FirstClass, Songbird, etc.). Is that something different?

API == Application Programmers Interface. Basically a set of functions, objects, methods etc in a library that always have the same interface, are linked at runtime, and provide a a means by which a developer can utilise system functionality without concern for the hidden complexity of that functionality.

I'm pretty sure Linux doesn't have a consistent API (some distros might have one specific to a family of distros - I really don't know), because there are lengthy threads on this forum where people have pointed out all the good reasons why there isn't one and should be one.

---

### Post by phoenix_snake on 2008-10-08
a lack of a consistent API is I think the main reason no company bothers to create commercial software for linux right?

---

### Post by aysiu on 2008-10-08
> **phoenix_snake said:**
> a lack of a consistent API is I think the main reason no company bothers to create commercial software for linux right?
Surely you're exaggerating. *No* company bothers to create commercial software for Linux?

Actually, quite a few companies create commercial software for Linux. Not all commercial software has Linux ports, but you can't say there are none.

---

### Post by aysiu on 2008-10-08
> **DrMega said:**
> API == Application Programmers Interface. Basically a set of functions, objects, methods etc in a library that always have the same interface, are linked at runtime, and provide a a means by which a developer can utilise system functionality without concern for the hidden complexity of that functionality.

I'm pretty sure Linux doesn't have a consistent API (some distros might have one specific to a family of distros - I really don't know), because there are lengthy threads on this forum where people have pointed out all the good reasons why there isn't one and should be one.
I think I get it, but I'm not sure. Thanks for explaining.

---

### Post by Canis familiaris on 2008-10-08
The Linux Kernel has a consistent API, period.
However about the shared libraries this is not the case, precisely the reason about the so called 'inconsistent "API" '

---

### Post by DrMega on 2008-10-08
> **phoenix_snake said:**
> a lack of a consistent API is I think the main reason no company bothers to create commercial software for linux right?

Some companies do create commercial software for Linux, and of those that don't I reckon the API issue is just one reason but not necessarily the main reason. I reckon the perception that Linux only has a comparatively small userbase is maybe the main reason, but if we did have a consistent, well documented API then that would be one less obstacle.

The thing is, at the rate things are moving, I reckon Linux (or at least the more dominant distros) *will* have a consistent API at some point in the foreseeable future. There are already many shared libraries that are becoming increasingly "standard", so I reckon its just a matter of time.

The thing is it is a kind of catch 22 in a way. The more people switch to Linux, the more people will develop for it and the faster it will progress, and as that happens more commercial companies will notice. As they do, and as more people switch, development will move ever faster and so ever more people will switch, and so on.

---

### Post by Canis familiaris on 2008-10-08
> **aysiu said:**
> I think I get it, but I'm not sure. Thanks for explaining.

[http://en.wikipedia.org/wiki/API](http://en.wikipedia.org/wiki/API)

---

### Post by aysiu on 2008-10-08
> **Anurag_panda said:**
> [http://en.wikipedia.org/wiki/API](http://en.wikipedia.org/wiki/API)
Thanks, but reading and understanding are not the same thing. That just looks like gibberish to me. I am not a programmer.

---

### Post by Canis familiaris on 2008-10-08
> **aysiu said:**
> Thanks, but reading and understanding are not the same thing. That just looks like gibberish to me. I am not a programmer.
Well, all software has to request other software to do some things for it.
In order to accomplish this, the asking program uses a set of standardized requests, called as application programming interfaces (API), that have been defined for the program being called upon. Almost every application depends on the APIs of the underlying operating system to perform such basic functions as accessing the file system. In essence, a program's API defines the proper way for a developer to request services from that program. 
For example when a program asks to print. It will give call to the print instruction according to the API. It shouldn't matter to the developer whether the person uses an HP printer or an Epson. The developer uses the API of the operating system to perform printing and then the OS takes control and completes the printing.
A proper real life example is OpenGL API. The game programmer will write code in OpenGL API and the OpenGL API will perform low level operations in any card and would abstract real instruction sent to the card. Seriously the developer cannot write different code for an Intel or nVidia or ATI. :)

---

### Post by phoenix_snake on 2008-10-08
u see a lack of many consistent things is the reasons most companies won't support linux, u see linux's API layer changes to rapidly creating more bugs and stuff in applications for example flash, most linux users blame Adobe but the truth is its linux's fault.

u see when adobe releases a specific version of flash for linux it checks it on some standard configurations of that time in linux and since there r billions of distros and stuff they can't possibly check all for just 1% of the market so they might test it on a few most powerful ones, I have heard they test flash for linux on Novell's SLED and Redhat linux.

for example maybe when they release flash its tested on the alsa sound server or something but now pulse audio comes out and breaks some stuff and the fact that many distros have their own patches on their kernels, different sound systems, libraries and unstable AP1 layer makes it extremely difficult for any company to support linux and the time and effort it would take to develop and maintain apps for linux is in their opinion not worth it for 1% of the market.

Linux lacks stable API and ABI, things change all the time and break apps and drivers, this is also one of the reasons many companies don't make linux drivers.

---

### Post by S0VERE1GN on 2008-10-08
> **RiceMonster said:**
> 
Actually, none of this has much to do with the kernel either. **Go use Windows.**

ooh , burn!

---

### Post by DrMega on 2008-10-08
> **Anurag_panda said:**
> The Linux Kernel has a consistent API, period.
However about the shared libraries this is not the case, precisely the reason about the so called 'inconsistent "API" '

Hmmm, I'm not so sure about this. Is it not true that I could take the source of the kernel, strip bits out that *I* consider unnecessary, modify bits I don't think are as efficient as they could be, generally mess with it, and then using my heavily modified kernel in a custom distro? That's kind of an extreme, hypothetical example of course.

A more realistic example is where different versions of the kernel are used in different distros. I'm told that newer kernel releases are not always 100% backward compatible with older ones (I don't know how true it is, its just something i read on UF). If this is true, then you can't say that the kernel has a consistent API. 

> **Anurag_panda said:**
> Well, all software has to request other software to do some things for it.
In order to accomplish this, the asking program uses a set of standardized requests, called as application programming interfaces (API), that have been defined for the program being called upon. Almost every application depends on the APIs of the underlying operating system to perform such basic functions as accessing the file system. In essence, a program's API defines the proper way for a developer to request services from that program. 
For example when a program asks to print. It will give call to the print instruction according to the API. It shouldn't matter to the developer whether the person uses an HP printer or an Epson. The developer uses the API of the operating system to perform printing and then the OS takes control and completes the printing.
A proper real life example is OpenGL API. The game programmer will write code in OpenGL API and the OpenGL API will perform low level operations in any card and would abstract real instruction sent to the card. Seriously the developer cannot write different code for an Intel or nVidia or ATI. :)

That's a very good explanation. Sometimes it is difficult to express technical issues in a non-technical way.

---

### Post by david_lynch on 2008-10-08
> **phoenix_snake said:**
> a lack of a consistent API is I think the main reason no company bothers to create commercial software for linux right?LOL!
never heard of oracle, IBM, Novell?

---

### Post by phoenix_snake on 2008-10-08
> **david_lynch said:**
> LOL!
never heard of oracle, IBM, Novell?
please tell me what useful app do these companies make for DESKTOP users? most linux's apps for desktop users r all open source

---

### Post by DrMega on 2008-10-08
> **phoenix_snake said:**
> please tell me what useful app do these companies make for DESKTOP users? most linux's apps for desktop users r all open source

Have a quick google, there are quite a few. Just not as many as there are for Windows, but certainly there are more than you might think.

---

### Post by david_lynch on 2008-10-08
> **phoenix_snake said:**
> 
Linux lacks stable API and ABI, things change all the time and break apps and drivers, this is also one of the reasons many companies don't make linux drivers.
The linux kernel API is not intended to be stable, since it is for kernel developers only. Linus doesn't really want binary drivers from 3rd parties because such drivers will always be falling behind. Greg K-H has been very straightforward about this, letting hardware vendors know that the linux kernel developers will be glad to write and maintain the drivers, for free, as long as they have access to the documentation needed to do so. Intel and other clueful hardware vendors have been getting on board with this, and linux hardware support has been getting steadily better.

If you're talking about GUI apps or something, don't confuse that with the linux kernel since the one has absolutely nothing to do with the other. 

There is a stable gnome ABI/API for instance, and this has nothing to do with the kernel- that's why gnome runs just the same on freebsd as it does on linux.

---

### Post by phoenix_snake on 2008-10-08
> **david_lynch said:**
> The linux kernel API is not intended to be stable, since it is for kernel developers only. Linus doesn't really want binary drivers from 3rd parties because such drivers will always be falling behind. Greg K-H has been very straightforward about this, letting hardware vendors know that the linux kernel developers will be glad to write and maintain the drivers, for free, as long as they have access to the documentation needed to do so. Intel and other clueful hardware vendors have been getting on board with this, and linux hardware support has been getting steadily better.

If you're talking about GUI apps or something, don't confuse that with the linux kernel since the one has absolutely nothing to do with the other. 

There is a stable gnome ABI/API for instance, and this has nothing to do with the kernel- that's why gnome runs just the same on freebsd as it does on linux.
ok u see many companies don't want to share their hardware secrets with the world, for example graphic cards.

Intel is open source right? they make basic and cheap graphic cards, they r not competing for making very powerful graphic cards, its just for regular use.

Another thing is that when u buy a product from a company, if the driver for their hardware sucks the customer may blame the company for crappy drivers whereas it might be linux devs fault and companies want to main responsibility for themselves so other people like linux devs don't harm their image. does that make sense? they don't trust linux devs to do a good job with their drivers and when a customer calls and complains they would like to know what exactly is going on.

there is something called business, and making everything open source is bad for business, simple as that and if u think about it would u trust someone else to make drivers for something u have created???

---

### Post by DrMega on 2008-10-08
> **david_lynch said:**
> The linux kernel API is not intended to be stable, since it is for kernel developers only.

Who else would an API be for if not developers? That's the whole point of an API so that developers can develop stuff that integrates well with the rest of the system.

---

### Post by phoenix_snake on 2008-10-08
there is another awesome thing I have noticed about some people here, I read in a few posts that some people only want to use open source software and hate anything that is commercial or proprietary.

what the? what kind of a message does that give to developers? so what some people here r saying is that anyone who wants money for their hard work and won't share the code is evil?

linux devs and even a few users NOT ALL obviously but some of them really need a lesson in economics if u ask me

---

### Post by aysiu on 2008-10-08
> **phoenix_snake said:**
> there is another awesome thing I have noticed about some people here, I read in a few posts that some people only want to use open source software and hate anything that is commercial or proprietary.

what the? what kind of a message does that give to developers? so what some people here r saying is that anyone who wants money for their hard work and won't share the code is evil?

linux devs and even a few users NOT ALL obviously but some of them really need a lesson in economics if u ask me
Tell that to the millionaires at Red Hat, MySQL, Sun, Mozilla, and Google.

Open source is not the antithesis of making money.

---

### Post by david_lynch on 2008-10-08
> **phoenix_snake said:**
> there is another awesome thing I have noticed about some people here, I read in a few posts that some people only want to use open source software and hate anything that is commercial or proprietary.

what the? what kind of a message does that give to developers? so what some people here r saying is that anyone who wants money for their hard work and won't share the code is evil?

linux devs and even a few users NOT ALL obviously but some of them really need a lesson in economics if u ask me
You're confused, go back and read what I said about the API. The kernel API is for *kernel developers*. Applications developers don't use the kernel API, they use e.g. the gnome API or the QT API. Can you see the difference?

When 3rd party devs tie things to the kernel, we end up with ugly kludges like apps which run only on redhat 7.3, which hasn't been supported in years.

---

### Post by phoenix_snake on 2008-10-08
> **aysiu said:**
> Tell that to the millionaires at Red Hat, MySQL, Sun, Mozilla, and Google.

Open source is not the antithesis of making money.
these r just a few examples, in fact red hat doesn't aim towards desktop users am I right, they aim for servers and linux is great for servers no doubt, its cheaper than paying for windows, its stable since linux supports server hardware very well and stuff.

all these companies u mention have some kind of business model, and they understand business.

most linux devs don't for example the kernel devs which r asking hardware companies to give them their products documentation, do they want their employees secrets too?

these companies u mention all have a workable business model but most open source projects don't, u see these companies have something others don't and that is **paid developers**. What other motivation is there for someone to improve their products if they aren't getting paid for it?

Redhat is actually smart, they don't aim for desktop users cause they know the weaknesses of linux on the desktop, no company is ever going to complain that we only want open source stuff, or asking for money for software is evil but desktop users do.

---

### Post by david_lynch on 2008-10-08
> **phoenix_snake said:**
> ok u see many companies don't want to share their hardware secrets with the world, for example graphic cards.

Intel is open source right? they make basic and cheap graphic cards, they r not competing for making very powerful graphic cards, its just for regular use.

Another thing is that when u buy a product from a company, if the driver for their hardware sucks the customer may blame the company for crappy drivers whereas it might be linux devs fault and companies want to main responsibility for themselves so other people like linux devs don't harm their image. does that make sense? they don't trust linux devs to do a good job with their drivers and when a customer calls and complains they would like to know what exactly is going on.

there is something called business, and making everything open source is bad for business, simple as that and if u think about it would u trust someone else to make drivers for something u have created???
What you said about driver quality and complaints are *precisely* the reasons that the kernel developers should be the ones writing the drivers. Writing drivers is quick and easy for linux kernel devs, but confusing and frustrating for outsiders.

What you said about trade secrets is open to debate. smarter people than you or I disagree with you about that.

As for intel, they are the world's largest chipmaker. They make not only CPUs, but ethernet and wifi network cards, sound cards and more. By your logic, Intel should be going out of business, because all their drivers are open source. What happened?

ATI is going open source on their graphics drivers as well. 

One other point where you are confused is thinking that somehow all linux apps are supposed to be "open source", but nobody has ever said that. Closed source apps run just fine on linux - oracle is closed source and works very closely with the linux devs to make sure their product works well on linux.

---

### Post by phoenix_snake on 2008-10-08
> **david_lynch said:**
> You're confused, go back and read what I said about the API. The kernel API is for *kernel developers*. Applications developers don't use the kernel API, they use e.g. the gnome API or the QT API. Can you see the difference?

When 3rd party devs tie things to the kernel, we end up with ugly kludges like apps which run only on redhat 7.3, which hasn't been supported in years.
I wasn't talking about the kernel API's in that post sorry, I completely switched over to apps.

the kernel api is for driver developers to right?

---

### Post by phoenix_snake on 2008-10-08
> **david_lynch said:**
> What you said about driver quality and complaints are *precisely* the reasons that the kernel developers should be the ones writing the drivers. Writing drivers is quick and easy for linux kernel devs, but confusing and frustrating for outsiders.

What you said about trade secrets is open to debate. smarter people than you or I disagree with you about that.

As for intel, they are the world's largest chipmaker. They make not only CPUs, but ethernet and wifi network cards, sound cards and more. By your logic, Intel should be going out of business, because all their drivers are open source. What happened?

ATI is going open source on their graphics drivers as well. 

One other point where you are confused is thinking that somehow all linux apps are supposed to be "open source", but nobody has ever said that. Closed source apps run just fine on linux - oracle is closed source and works very closely with the linux devs to make sure their product works well on linux.
intel makes commodity hardware, they don't make graphic cards that compete with nvidia do they? it makes sense for them to go open source cause they make standard hardware for regular use and they sell that hardware for money.

no u see what if kernel devs don't write good drivers? a company such as nvidia won't want the blame when their customers complain that their vga card drivers for linux suck when nvidia didn't even make them.

wait a sec though, doesn't nvidia the best support for linux? ATI is open source right? why do their cards on linux suck so bad? shouldn't the kernel developers be up to something?

---

### Post by Vince4Amy on 2008-10-08
I think most of that blog is a joke, you have dependencies on any Operating System you have, you just don't notice on Windows for example.

If there are no dependencies on other OS's why do I have to install .net framework 3.5 to run Visual Studio.

Why do I have to install Windows Media Player to play certain games etc.

There are dependencies on any Operating System and it can't be avoided.

---

### Post by phoenix_snake on 2008-10-08
I should add here that intel is already having a huge market share among chipset and mother board manufacturers and stuff right? so what happens here is that since they already have a large portion of the market and they make basic hardware so it actually saves them on development costs for not having to write drivers for their hardware.  they have nothing to lose cause they already have a majority market.

they take a small risk by trusting that linux devs will right good linux drivers for their hardware, well not everyone is that trusting, I definitely wouldn't trust anyone to do my job for me.

if u don't understand this post please tell me I will explain in better words :)

---

### Post by sydbat on 2008-10-08
> **phoenix_snake said:**
> Redhat is actually smart, they don't aim for desktop users cause they know the weaknesses of linux on the desktop, no company is ever going to complain that we only want open source stuff, or asking for money for software is evil but desktop users do.Red Hat makes a [desktop version]("https://www.redhat.com/rhel/desktop/"). And they make/financially support Fedora, their free ($) desktop system.

I think this whole thread started out as flamebait/FUD, but no one took the bait, really. No matter how the OP tried to make it otherwise, the vast majority of answers from whatever perspective was presented in mature language and with respect. This makes me feel good about this community.

---

### Post by handy on 2008-10-08
> **sydbat said:**
> Red Hat makes a [desktop version]("https://www.redhat.com/rhel/desktop/"). And they make/financially support Fedora, their free ($) desktop system.

I think this whole thread started out as flamebait/FUD, but no one took the bait, really. No matter how the OP tried to make it otherwise, the vast majority of answers from whatever perspective was presented in mature language and with respect. This makes me feel good about this community.

***_[http://ubuntuforums.org/showthread.php?p=5922490#post5922490](http://ubuntuforums.org/showthread.php?p=5922490#post5922490)_***

---

### Post by phoenix_snake on 2008-10-08
> **sydbat said:**
> Red Hat makes a [desktop version]("https://www.redhat.com/rhel/desktop/"). And they make/financially support Fedora, their free ($) desktop system.

I think this whole thread started out as flamebait/FUD, but no one took the bait, really. No matter how the OP tried to make it otherwise, the vast majority of answers from whatever perspective was presented in mature language and with respect. This makes me feel good about this community.
do u have a link to the market share for their enterprise desktop? lets see how many people actually use it, I read an article that ubuntu is the most used linux desktop in the world, is that right?

that means lets say out of 1% of people on earth 0.5% use ubuntu and u can give another 0.4% to the other remaining **free** distros leaving lets 0.1% people that actually pay.

to be honest a friend of mine who introduced me to linux told me that fedora was a testing ground or something for their commercial products, they just sell support for it for extra cash for that extremely small minority that might actually pay for support.

notice how it also says enterprise desktop?

doesn't that mean its still aimed at enterprise customers? isn't it still aimed for commercial deployment, r there any regular home users using this at home? if they r they r very few like I said earlier I remember reading ubuntu is the most used linux distro in the world meaning hardly anyone pays right?

---

### Post by david_lynch on 2008-10-08
> **phoenix_snake said:**
> 
they take a small risk by trusting that linux devs will right good linux drivers for their hardware, well not everyone is that trusting, I definitely wouldn't trust anyone to do my job for me.
And that is *exactly* why linux kernel programmers should the ones be writing linux device drivers, if you are interested in quality. Nobody else is as well qualified to do the job.

The linux drivers shipped by most companies are really bad, and they would be much better off just letting the experts take over the job. I give props to nvidia, they do a pretty good job of keeping their drivers up to date, but nvidia is the exception.

---

### Post by DrMega on 2008-10-08
> **david_lynch said:**
> You're confused, go back and read what I said about the API. The kernel API is for *kernel developers*. Applications developers don't use the kernel API, they use e.g. the gnome API or the QT API. Can you see the difference?

What about hardware drivers? They need to talk to the kernel.

> **david_lynch said:**
> When 3rd party devs tie things to the kernel, we end up with ugly kludges like apps which run only on redhat 7.3, which hasn't been supported in years.

Why would 3rd party developers need to tie anything into the kernel? The whole point of an API is that *nothing* has to be tied in, stuff just talks to each other. If I install the latest nVidia drivers in Windows, I'm not in anyway modifying the Windows kernel (I can't even if I wanted to), but the drivers and the kernel just talk to each other via the API.

---

### Post by phoenix_snake on 2008-10-08
> **david_lynch said:**
> And that is *exactly* why linux kernel programmers should the ones be writing linux device drivers, if you want quality. Nobody is as well qualified to do the job.

The linux drivers shipped by most companies are really bad, and they would be much better off just letting the experts take over the job. I give props to nvidia, they do a pretty good job of keeping their drivers up to date, but nvidia is the exception.
u see I understand ur point that no one knows the linux kernel better then its creators right? thats true but companies that r competing can't hand over their secrets cause competitors will take advantage of that and companies like to have full control of their products right from its manufacturing till the point the consumer uses it.

I hope u understand my point here as well..................

---

### Post by Mr. Picklesworth on 2008-10-08
> **DrMega said:**
> What about hardware drivers? They need to talk to the kernel.



Why would 3rd party developers need to tie anything into the kernel? The whole point of an API is that *nothing* has to be tied in, stuff just talks to each other. If I install the latest nVidia drivers in Windows, I'm not in anyway modifying the Windows kernel (I can't even if I wanted to), but the drivers and the kernel just talk to each other via the API.

That's exactly the point. What this good person is pointing out is that most developers (particularly commercial ones) work in userland. The surrounding platform is meant to be open source, but high level user-space stuff can do as it pleases. There are piles of stable APIs out there for user-space software. Those libraries abstract away any concern one developer may have about unstable kernel ABIs since the distro packaging that kernel also properly configures the library appropriately. (Though it should be kept in mind that such tweaking is only even hinted at for deep down stuff like libc), For GUI widgets, GTK is not entirely stable but has a well organized pattern for deprecating things. Most commonly used abstraction libraries *are* stable. Alternatively, a GUI abstraction library like wxwidgets is a popular choice.

---

### Post by cardinals_fan on 2008-10-08
> **chungy said:**
> de Raadt might not be the nicest guy around, but he sure knows how to get the job done.  He doesn't take NDAs or blobs as an answer, he doesn't say "well we have ndiswrapper (OpenBSD has no such thing), so you can take your sweet time in releasing free drivers or documentation."  He's friendly to those he agrees with, but a little stringent with those he disagrees with.  yeah, I agree that ndiswrapper isn't a good solution, though I have to unfortunately use it on my laptop and it makes me very sad.  The fact that it exists just tells manufacturers that they can continue making Windows blobs without a care in the world.

True.  I think Theo de Raadt is a bit obnoxious, but there's no denying that he knows his stuff.
> **phoenix_snake said:**
> 
for example maybe when they release flash its tested on the alsa sound server or something but now pulse audio comes out and breaks some stuff and the fact that many distros have their own patches on their kernels, different sound systems, libraries and unstable AP1 layer makes it extremely difficult for any company to support linux and the time and effort it would take to develop and maintain apps for linux is in their opinion not worth it for 1% of the market.

This isn't a flaw with Linux overall.  Only distros with PulseAudio experienced these particular issues precisely because Adobe did not support PulseAudio.  In my opinion, including PulseAudio by default was a stupid decision on the part of those distros that did so.  However, it reflects poorly on them, and not all Linux distros.
> **phoenix_snake said:**
> 
Redhat is actually smart, they don't aim for desktop users cause they know the weaknesses of linux on the desktop, no company is ever going to complain that we only want open source stuff, or asking for money for software is evil but desktop users do.
Red Hat doesn't aim for home users because they don't think that market is profitable.  I agree with them on this, but it has nothing to do with Linux in general.  They simply can't see a reliable way to make money marketing a Linux distro to home users.

---

### Post by chungy on 2008-10-08
> **aysiu said:**
> Tell that to the millionaires at Red Hat, MySQL, Sun, Mozilla, and Google.

Open source is not the antithesis of making money.

WTF is Google doing on that list?  Besides Chrome (which doesn't even compile on Linux, CrossOver's thing of compiling a Windows binary and tying it into Wine doesn't count), what has Google contributed to open source?

If anything, they're the antithesis of an open source focused company.

---

### Post by aysiu on 2008-10-08
> **chungy said:**
> WTF is Google doing on that list?  Besides Chrome (which doesn't even compile on Linux, CrossOver's thing of compiling a Windows binary and tying it into Wine doesn't count), what has Google contributed to open source?

If anything, they're the antithesis of an open source focused company.
A little extreme a statement there, eh?
[http://code.google.com/hosting/projects.html?filter=1&start=0](http://code.google.com/hosting/projects.html?filter=1&start=0)
[http://google-opensource.blogspot.com/](http://google-opensource.blogspot.com/)
[http://code.google.com/soc/2008/](http://code.google.com/soc/2008/)
[http://www.informationweek.com/news/software/open_source/showArticle.jhtml?articleID=178600189](http://www.informationweek.com/news/software/open_source/showArticle.jhtml?articleID=178600189)
[http://www.google.com/linuxrepositories/index.html](http://www.google.com/linuxrepositories/index.html)

---

### Post by Mr. Picklesworth on 2008-10-08
Phoenix, you are all over the place. Frankly, you need to focus on something with this or you will find yourself on a spaghetti-like labyrinth steadily drawing further and further away from reality. I think it could be too late already, but that decision is up to you. You were pretty confident about your first topic, so maybe dig a bit deeper into that one to try and find answers instead of just a generally unimportant black and white picture.
The Linux ecosystem involves a *different* kind of economics, which scares the hell out of people used to or reliant on traditional economic systems where gains happen instantly and consistently in the form of "money".

Novell also has a desktop operating system, which makes profit commercially and has a big community. If you poke around Ubuntu, you will find that Novell has a pretty big presence in desktop Linux land and they don't just do it "for fun". I should also take this moment (while the trail of thought in this post is totally off course) to point out that products can have different licenses for individuals, nonprofits, contributors and profiting corporations to encourage the gradual growth of a more relaxed trade-based economy.


There is profit involved in simply getting people interested in your software. Look at Microsoft, who would *not* be where they are today had their software not been pirated. People would not have built up a need for Microsoft software if they had become used to paying astronomical amounts of money for it; they would be using cheaper alternatives or at least sensitive to the fact that it is morally wrong to require someone pay money to Microsoft to work with them.
Similar deal with Adobe (now that they have established themselves as industry standard with people pirating Adobe Photoshop practically a part of our culture...), who are just recently working to push their products up to web services.

Out here it's quite a bit less nasty seeming, but there is a similar thought going on: The product being free means it gains interest. If more developers are interested in Linux, more users will use Linux. If more users use Linux, there are more opportunities for cash flow via end user services on userspace products, donations (which have been known to work) and paid developers. Yes, developers get paid by for-profit corporations to build software that interests them.

It is healthy for development that the surrounding computer platform be open and free. Take a look at the existence of open standards to verify that one. Take a look at the success of the web, which would not be where it is today if people needed a particular $300 device to read pages served over the Internet. If you need a more tactile example, look at Flash which is now ubiquitous because the Flash player is free. PDF is even more popular (relatively speaking) because the format is an open standard.

To nurture Linux desktop platforms *at the moment*, it is important to have tons of good high level software for the user that is free. In the future, once the platform is sufficiently nurtured, we will no longer have that necessity to grow interest since it can grow organically after a point. The interwebs are at the same stage right now: Look at Google's awesome services, Yahoo and the likes. Incidentally, I don't see many "Google will fail because they have a lot of services that are totally disconnected from each other and they charge nothing for them" threads.
The important thing here is not that there is a free 3D modelling tool, or a free photo manager. It is that the platform for accessing those tools hides nothing and is available to everyone. Developers don't need to worry about their target platform being exclusive, and users don't need to worry about buying new platform chunks (or operating systems) to get their purchases working.


PS: I have not mentioned how it is entirely possible to [sell free software]("http://www.gnu.org/philosophy/selling.html") for profit, rendering this detour irrelevant regardless.

---

### Post by Ripfox on 2008-10-08
> This blog is currently under review due to possible Blogger Terms of Service violations.

If you're a regular reader of this blog and are confident that the content is appropriate, feel free to click "Proceed" to proceed to the blog. We apologize for the inconvenience.

If you're an author of this blog, please follow the instructions on your dashboard for removing this warning page.

;)

---

### Post by david_lynch on 2008-10-09
> **DrMega said:**
> What about hardware drivers? They need to talk to the kernel.

You've made my point for me. The best qualified people on the planet to write linux kernel drivers are the linux kernel developers. Since the kernel devs are ready, able and willing to write and maintain the hardware drivers for free, why not just give them the required info, step aside and let them do their job?

As for your other question, it sounds like you're not sure whether you want to talk about drivers (kernel space) or apps (user space) which are two different realms. There are stable user space APIS, and that's how apps such as firefox for linux are written, and work across all distros.

---

### Post by handy on 2008-10-09
***@Mr. Picklesworth:***

Thanks, great post.

---

### Post by phoenix_snake on 2008-10-09
> **Mr. Picklesworth said:**
> Phoenix, you are all over the place. Frankly, you need to focus on something with this or you will find yourself on a spaghetti-like labyrinth steadily drawing further and further away from reality. I think it could be too late already, but that decision is up to you. You were pretty confident about your first topic, so maybe dig a bit deeper into that one to try and find answers instead of just a generally unimportant black and white picture.
The Linux ecosystem involves a *different* kind of economics, which scares the hell out of people used to or reliant on traditional economic systems where gains happen instantly and consistently in the form of "money".

Novell also has a desktop operating system, which makes profit commercially and has a big community. If you poke around Ubuntu, you will find that Novell has a pretty big presence in desktop Linux land and they don't just do it "for fun". I should also take this moment (while the trail of thought in this post is totally off course) to point out that products can have different licenses for individuals, nonprofits, contributors and profiting corporations to encourage the gradual growth of a more relaxed trade-based economy.


There is profit involved in simply getting people interested in your software. Look at Microsoft, who would *not* be where they are today had their software not been pirated. People would not have built up a need for Microsoft software if they had become used to paying astronomical amounts of money for it; they would be using cheaper alternatives or at least sensitive to the fact that it is morally wrong to require someone pay money to Microsoft to work with them.
Similar deal with Adobe (now that they have established themselves as industry standard with people pirating Adobe Photoshop practically a part of our culture...), who are just recently working to push their products up to web services.

Out here it's quite a bit less nasty seeming, but there is a similar thought going on: The product being free means it gains interest. If more developers are interested in Linux, more users will use Linux. If more users use Linux, there are more opportunities for cash flow via end user services on userspace products, donations (which have been known to work) and paid developers. Yes, developers get paid by for-profit corporations to build software that interests them.

It is healthy for development that the surrounding computer platform be open and free. Take a look at the existence of open standards to verify that one. Take a look at the success of the web, which would not be where it is today if people needed a particular $300 device to read pages served over the Internet. If you need a more tactile example, look at Flash which is now ubiquitous because the Flash player is free. PDF is even more popular (relatively speaking) because the format is an open standard.

To nurture Linux desktop platforms *at the moment*, it is important to have tons of good high level software for the user that is free. In the future, once the platform is sufficiently nurtured, we will no longer have that necessity to grow interest since it can grow organically after a point. The interwebs are at the same stage right now: Look at Google's awesome services, Yahoo and the likes. Incidentally, I don't see many "Google will fail because they have a lot of services that are totally disconnected from each other and they charge nothing for them" threads.
The important thing here is not that there is a free 3D modelling tool, or a free photo manager. It is that the platform for accessing those tools hides nothing and is available to everyone. Developers don't need to worry about their target platform being exclusive, and users don't need to worry about buying new platform chunks (or operating systems) to get their purchases working.


PS: I have not mentioned how it is entirely possible to [sell free software]("http://www.gnu.org/philosophy/selling.html") for profit, rendering this detour irrelevant regardless.

first of what r u talking about? we r talking about linux on the desktop aren't we? they don't even think that selling to home users is profitable right, they sell their Enterprise products to companies, and I noticed that some of those didn't even have the latest version of specific software on them for example kernel version.

I found something here, this is a novell certified linux laptop

[http://developer.novell.com/yes/91523.htm](http://developer.novell.com/yes/91523.htm)

read this

**1) Intel 865GM graphics needs to install seperately, please download the driver from [http://forgeftp.novell.com/hp/HP-Compaq-6510b](http://forgeftp.novell.com/hp/HP-Compaq-6510b), and follow instructions 2) Suspend to disk and Suspend to RAM: Hotkey (fn+f3) does not work, however, powersave -U and powersave -u function at the command line and hibernate, sleep works when invoked from the power management icon on the gnome panel. Occasionally, the system may need a reboot when waking up 3) Same behavior as #2 is observed when Desktop Effects are enabled.**

this thing got certified? thats really going to show a good image for Novell....lol, so we r certified to not have things working properly out of the box, suspend may not work once in a while causing us to loose data and desktop effects breaks functionality too? 

I doubt anyone who bought that crap would ever bother with linux again.

this thread is about linux on the desktop, so we shouldn't be talking about redhat since they don't aim there, isn't linux already doing well with servers and stuff?

yes I know free software must not have free price, but would u pay for free software? I wouldn't, and nor r most people going to pay for something that is supposed to be free, like u mentioned SLED, well a home user would rather just download a copy of Ubuntu.

Piracy helps to give exposure but another thing that helps is the quality of the software it self, there r good open source programs but these programs have work able business models meaning they pay their devs to write code and they aim at desktop users, but most of the open source projects don't have any direction.

there could be like 3000 different programs in the repos that do the same thing and they all suck, most successful free software such as mozilla or openoffice, ones that have a workable business model, they have windows ports for their apps as well so using linux isn't required.

a product being free doesn't gain interest if it isn't good and there is obviously a flaw in linux that its been free for so long and still has only got 1% market share. it would gain interest in the beginning may be but if it doesn't work well people will leave it.

donations I doubt could make as much money as actually selling the product if its worth placing a price on and people who get paid by corporations to build software that interests them, well they r paying it to them for private use right? normal desktop users don't have tailor made software, I doubt most people can afford to have software specifically written for them.

I have used many open source apps and many of them don't come up to the standards of commercial apps, sorry but GIMP is not as great and easy to use as Photoshop. u see the difference here is that open source devs don't usually listen to their users or want feed back.

lets take an example, KDE devs have said something like they don't need users? what the? that shows that they don't really care about user feed back and by feed back I mean regular people who can't code.

everyone says the best advantage of open source stuff is u can improve it yourself well u see technically u can't cause most people aren't programmers, I know people who think the internet is the blue "IE" icon on their desktop, thats how much they understand about computers.

there r other problems too, since they develop for free, they don't think up many original ideas and probably try and keep up with commercial apps, and they have this weird thinking I have noticed here to that it "its free so u have no right to complain".

I can't believe people actually take that kind of crap from ur devs, people whose income depends on selling software realize if they don't listen to their regular users who BUY their stuff then they may go out of business, where as the open source world isn't like this, its more like "hey u don't pay me, I couldn't care less about what u want"

an example of this can be ur desktop theme people here have been crying about:

user 1: I thought we were promised a new theme?
user 2: yeah what happened? we r all sick of this theme.
user 3: hey shut up u 2, its free so don't complain and besides u can always change it.
user 4: yup it doesn't matter most people change their themes anyway.
user 3: go back to windows, we don't need u
mod 1: keep it civil people

this is just an example but there r posts where this happens and shows an idea of your users/devs mentality.

every program has some kind of a customer experience program where they go and collect feed back from their users.

open source is a great idea that we can share our works and stuff, but in reality it won't work that well cause of the people here that think stuff like I mentioned before and those who think closed source is evil.

---

### Post by Mr. Picklesworth on 2008-10-09
> **phoenix_snake said:**
> Piracy helps to give exposure but another thing that helps is the quality of the software it self,So you understand! In the proprietary software world, they still expect to sell software and make money while over here there is some acceptance that such a model is pointless. Charging $100 for a duplicate of software that costs a few cents to manufacture (since software can be duplicated endlessly) is just broken. It's the service that costs money, so any sane company (new-fangled business model or not) should work to reverse loss specifically on that.

> **phoenix_snake said:**
> Piracy there r good open source programs but these programs have work able business models meaning they pay their devs to write code and they aim at desktop users, but most of the open source projects don't have any direction.Take a look at the following:

[http://kernel.org/](http://kernel.org/)
[http://www.gnome.org/](http://www.gnome.org/)
[http://kde.org/](http://kde.org/)
[https://www.linuxfoundation.org/](https://www.linuxfoundation.org/)

There is direction. There is a plan, there is an underlying rhythm to a lot of development and both KDE and GNOME have design guidelines they follow. (On another thought entirely, has KDE.org changed? It looks nice).

> **phoenix_snake said:**
> there could be like 3000 different programs in the repos that do the same thing and they all suck, most successful free software such as mozilla or openoffice, ones that have a workable business model, they have windows ports for their apps as well so using linux isn't required.Do you know where Mozilla gets a lot of their money? That little Google search box. Ultimately, advertising. Advertising is a pretty straight-forward business model.


> **phoenix_snake said:**
> a product being free doesn't gain interest if it isn't good and there is obviously a flaw in linux that its been free for so long and still has only got 1% market share....Linux grows at a climbing rate as huge corporations like Microsoft lose their grip on new markets with their only contendor in that space being an ancient operating system. Yep, real big problem there.
(Change does not happen overnight).

> **phoenix_snake said:**
> normal desktop users don't have tailor made software, I doubt most people can afford to have software specifically written for them.That is true, but normal desktop users do benefit from software built for particular local services they use.

> **phoenix_snake said:**
> there r other problems too, since they develop for free, they don't think up many original ideas and probably try and keep up with commercial apps, and they have this weird thinking I have noticed here to that it "its free so u have no right to complain".It's less that, more that people shouldn't be completely unpleasant with their complaints. Bug reports are complaints, but they're *constructive* complaints that solve problems.

> **phoenix_snake said:**
> I can't believe people actually take that kind of crap from ur devs, people whose income depends on selling software realize if they don't listen to their regular users who BUY their stuff then they may go out of business, where as the open source world isn't like this, its more like "hey u don't pay me, I couldn't care less about what u want"So what about the developer working for an organization that wanted a feature... and then implemented the feature himself? It happens.
Or what about the person who realizes that software development is not some dark art and in fact can be learned by everyone (really!), so set out to fix the problems he saw *himself*. It really isn't an exclusive locked-and-keyed community.

To implement a feature needs a cost-benefit analysis. Does the feature cause technical bloat? Does it confuse new users? Does it complicate the code base for future contributors? Does it work as advertised? Is there an actual problem being solved, or is it just to scratch one vocal user's itch?

Part of the problem is transparency. People are unaware of how much work is actually involved in software development, expecting changes to happen overnight or specific things to always be 100% simple. (Ignorant of how said changes could make the system in question absolutely insane to work with). Thus, when they can actually see the development and see that it is not on their feature but on something they do not understand, they panic.

> **phoenix_snake said:**
> an example of this can be ur desktop theme people here have been crying about:

user 1: I thought we were promised a new theme?
user 2: yeah what happened? we r all sick of this theme.
user 3: hey shut up u 2, its free so don't complain and besides u can always change it.
user 4: yup it doesn't matter most people change their themes anyway.
user 3: go back to windows, we don't need u
mod 1: keep it civil people

this is just an example but there r posts where this happens and shows an idea of your users/devs mentality.It should be pointed out that the beta release is not the final release, and Canonical's own art team currently works in a very closed-doors way.

> **phoenix_snake said:**
> every program has some kind of a customer experience program where they go and collect feed back from their users.[http://www.launchpad.net/](http://www.launchpad.net/)
Present the benefits of an idea well enough, and someone who knows how to implement it could pick up the job and submit a patch. It's all about being constructive.

> **phoenix_snake said:**
> open source is a great idea that we can share our works and stuff, but in reality it won't work that well cause of the people here that think stuff like I mentioned before and those who think closed source is evil.You say this as if [free software]("http://en.wikipedia.org/wiki/Free_software_movement") is something new.

Don't worry about it.

---

### Post by DrMega on 2008-10-09
> **Mr. Picklesworth said:**
> That's exactly the point. What this good person is pointing out is that most developers (particularly commercial ones) work in userland. The surrounding platform is meant to be open source, but high level user-space stuff can do as it pleases. There are piles of stable APIs out there for user-space software. Those libraries abstract away any concern one developer may have about unstable kernel ABIs since the distro packaging that kernel also properly configures the library appropriately. (Though it should be kept in mind that such tweaking is only even hinted at for deep down stuff like libc), For GUI widgets, GTK is not entirely stable but has a well organized pattern for deprecating things. Most commonly used abstraction libraries *are* stable. Alternatively, a GUI abstraction library like wxwidgets is a popular choice.

Great for top level apps, but this doesn't solve the problem of drivers, which are by their very nature very low level and nothing to do with the GUI.

> **david_lynch said:**
> You've made my point for me.

I don't think I have. I think a consistent API to the kernel would be beneficial. You seem to think it isn't.

> **david_lynch said:**
> The best qualified people on the planet to write linux kernel drivers are the linux kernel developers. Since the kernel devs are ready, able and willing to write and maintain the hardware drivers for free, why not just give them the required info, step aside and let them do their job?

Why? I don't get it. People talk about open source being about choice, yet those same people would like to deny commercial organisations of the choice to develop hardware drivers for their kit to work on Linux systems. If I said to you that you can't use Ubuntu, but if you give me the information I need to develop you a system that I think is suitable for you, would that be OK?

---

### Post by phoenix_snake on 2008-10-09
> **Mr. Picklesworth said:**
> 
Take a look at the following:

[http://kernel.org/](http://kernel.org/)
[http://www.gnome.org/](http://www.gnome.org/)
[http://kde.org/](http://kde.org/)
[https://www.linuxfoundation.org/](https://www.linuxfoundation.org/)

There is direction. There is a plan, there is an underlying rhythm to a lot of development and both KDE and GNOME have design guidelines they follow. (On another thought entirely, has KDE.org changed? It looks nice).

Do you know where Mozilla gets a lot of their money? That little Google search box. Ultimately, advertising. Advertising is a pretty straight-forward business model.


u see the thing is these r just few of the open source projects that u mention and there r billions of them, for example one person decides to write a program gets bored and someone else takes over, these r how the majority of the open source projects apart from mozilla, apache, mysql and stuff work.

> **Mr. Picklesworth said:**
> 
...Linux grows at a climbing rate as huge corporations like Microsoft lose their grip on new markets with their only contendor in that space being an ancient operating system. Yep, real big problem there.
(Change does not happen overnight).


do u mean netbooks? I read in the community cafe that linux ones r being returned more than windows ones, also u see that ancient Xp still works pretty well. what about the SUSE certification link I found, Novell certified a laptop to be linux ready when it barely works, and I hear that Novell is a very powerful company in the linux world, if they r dumb enough to do something like this then what about others?

> 
It's less that, more that people shouldn't be completely unpleasant with their complaints. Bug reports are complaints, but they're *constructive* complaints that solve problems.

So what about the developer working for an organization that wanted a feature... and then implemented the feature himself? It happens.
Or what about the person who realizes that software development is not some dark art and in fact can be learned by everyone (really!), so set out to fix the problems he saw *himself*. It really isn't an exclusive locked-and-keyed community.

To implement a feature needs a cost-benefit analysis. Does the feature cause technical bloat? Does it confuse new users? Does it complicate the code base for future contributors? Does it work as advertised? Is there an actual problem being solved, or is it just to scratch one vocal user's itch?


first of the idea that a regular person should make a bug report is insane, as linux grows more people who don't crap will use it, that is the same kind of people who can't change the position of the windows taskbar from top to bottom. such people will go crazy with the idea of making a bug report.

don't u see the flaw here? how do u expect a regular person to debug programs and post outputs of certain commands or keeping checking their inbox for more news on the bug? 

also what if the reporter can't provide enough info or doesn't know how, then it won't get fixed? I read some reports on launchpad and the devs have closed some bugs saying that the next distro doesn't have this problem, well what about the current release?

check out this one below:

[http://bugs.launchpad.net/ubuntu/+source/dolphin/+bug/136695](http://bugs.launchpad.net/ubuntu/+source/dolphin/+bug/136695)

Its a complain that a file manager in kubuntu can't cut and paste files and it wasn't fixed and they still included that file manager in Hardy knowing it didn't work....sweet. Read the last comment where that person says he won't be using it again and I agree with him, this was such a simple fix, all they had to do was make konqueror the default file manager.

what users want is when a program crashes it itself sends a bug report and devs fix it without the user ever having to worry, and since many people here think hey we r doing the work for free for u so don't complain, chances r problems won't get resolved.

u should also understand that a user does not need to do constructive criticism at all, he or she has the right to shout, scream or do whatever they want. why? cause u r providing them with a product, u should expect complains no matter how bad they sound, its a simple part of business, if u can't hear criticisms no matter how bad they r then don't provide a product.

remember u need the user, the user doesn't need u, unless u count the kde devs who say we don't need users, thats just shows how much they care about feed back. this is a nice example of open source devs saying "hey listen, u users don't pay our salaries, or some of us our volunteer workers so we don't care what u want"

if a dev works for an organization and implements a feature for them then thats great but we r talking about linux on the desktop. another thing I disagree with is the thinking of linux users that whenever someone complains some of them say "hey the code is there, change it yourself". u see not everyone is a programmer or even smart enough to be one. maybe this is because the person doesn't pay for it so the devs don't really care?

> 
Part of the problem is transparency. People are unaware of how much work is actually involved in software development, expecting changes to happen overnight or specific things to always be 100% simple. (Ignorant of how said changes could make the system in question absolutely insane to work with). Thus, when they can actually see the development and see that it is not on their feature but on something they do not understand, they panic.


agreed

> 
It should be pointed out that the beta release is not the final release, and Canonical's own art team currently works in a very closed-doors way.


that was just an example, I don't hate the theme, I haven't used ubuntu long enough as u all to be sick of it ;)

> 
[http://www.launchpad.net/](http://www.launchpad.net/)
Present the benefits of an idea well enough, and someone who knows how to implement it could pick up the job and submit a patch. It's all about being constructive.


this is a good idea but I seriously doubt it will work cause of the way open source projects work for example when ubuntu users want a new feature in gnome for example, ubuntu devs have to talk to gnome devs to implement that feature. 

all open source projects r scattered each going their own direction, if the gnome devs agree to that feature fine, if not then the ubuntu devs can't do anything for their users.

that is why Apple's business strategy is pretty good, they create their OS and choose hardware for u so in case there r requests they don't have to rely on others.

---

### Post by david_lynch on 2008-10-09
> **DrMega said:**
> Great for top level apps, but this doesn't solve the problem of drivers, which are by their very nature very low level and nothing to do with the GUI.
My point exactly.

> **DrMega said:**
> I think a consistent API to the kernel would be beneficial. You seem to think it isn't. What you or I think doesn't matter. What matters is what the people who write the drivers think. And they are pretty clear on the subject.

> **DrMega said:**
> People talk about open source being about choice, yet those same people would like to deny commercial organisations of the choice to develop hardware drivers for their kit to work on Linux systems. If I said to you that you can't use Ubuntu, but if you give me the information I need to develop you a system that I think is suitable for you, would that be OK?Can you show me where any commercial organization has ever been denied the choice to develop linux drivers? For me to say that the kernel developers are best qualified to write kernel code is not the same thing as denying anybody else the chance to try. 

Nvidia writes linux drivers, ATI has been writing linux drivers, but is now seeing the wisdom of letting the kernel experts write the kernel code. Intel wrote linux drivers but has also benefited from leveraging the expertise of the linux kernel experts. 

Hey, anybody that wants to to study computer science and become a linux kernel coder is free to help out, nobody's denying them the chance, commercial or otherwise.
:guitar:

---

### Post by cardinals_fan on 2008-10-09
> **phoenix_snake said:**
> first of what r u talking about? we r talking about linux on the desktop aren't we? they don't even think that selling to home users is profitable right, they sell their Enterprise products to companies, and I noticed that some of those didn't even have the latest version of specific software on them for example kernel version.

You don't include the latest software in an enterprise operating system.  Red Hat and Novell expect extreme stability, which can only come from software that has been out for a while.  Also, they don't consider home Linux unprofitable because of any flaws in the system.  When you make all your money of support contracts (as Red Hat does), home users are very poor customers.  They use whatever is preinstalled, and that's it.

By the way, typing 'r' and 'u' instead of 'are' and 'you' doesn't support your arguments.  If you can't take the time to write it out, why should I take the time to read it?  No offense meant, that's just my opinion.

---

### Post by -grubby on 2008-10-09
> **cardinals_fan said:**
> 
by the way, typing 'r' and 'u' instead of 'are' and 'you' doesn't support your arguments.  If you can't take the time to write it out, why should i take the time to read it?  No offense meant, that's just my opinion.


+1

---

### Post by phoenix_snake on 2008-10-09
> **cardinals_fan said:**
> You don't include the latest software in an enterprise operating system.  Red Hat and Novell expect extreme stability, which can only come from software that has been out for a while.  Also, they don't consider home Linux unprofitable because of any flaws in the system.  When you make all your money of support contracts (as Red Hat does), home users are very poor customers.  They use whatever is preinstalled, and that's it.

By the way, typing 'r' and 'u' instead of 'are' and 'you' doesn't support your arguments.  If you can't take the time to write it out, why should I take the time to read it?  No offense meant, that's just my opinion.
may be because I am typing in a hurry, if I can't type it out then DON'T read it, no ones forcing u too

---

### Post by cardinals_fan on 2008-10-09
> **phoenix_snake said:**
> may be because I am typing in a hurry, if I can't type it out then DON'T read it, no ones forcing u too
Don't be in such a hurry.  Relax and spend some time writing a post before slamming the submit button.

Just my 2¢

---

### Post by phoenix_snake on 2008-10-09
> **cardinals_fan said:**
> Don't be in such a hurry.  Relax and spend some time writing a post before slamming the submit button.

Just my 2¢
u see, yes I used "u" instead of "you", most people like to get their responses quickly and don't like to wait to read the reply :)

---

### Post by cardinals_fan on 2008-10-09
> **phoenix_snake said:**
> u see, yes I used "u" instead of "you", most people like to get their responses quickly and don't like to wait to read the reply :)
I'm in no rush.  I prefer a well-written and grammatically correct post that is easy for me to read to one that is filled with netspeak and abbreviations.

@topic: In a nutshell, could you sum up your issues with the Linux kernel and how you think some new system would solve them?  Take your time with the reply; I'll check back after I finish some calculus homework :)

---

### Post by Ripfox on 2008-10-10
> this thing got certified? thats really going to show a good image for Novell....lol, so we r certified to not have things working properly out of the box, suspend may not work once in a while causing us to loose data and desktop effects breaks functionality too?

Erm, have you ever used Vista? Desktop effects break functionality all the time. There is no perfect OS. Just a better alternative that doesn't get viruses ;)

---

### Post by p_quarles on 2008-10-10
> **phoenix_snake said:**
> u see, yes I used "u" instead of "you", most people like to get their responses quickly and don't like to wait to read the reply :)
The Forum Rules state that you should avoid abbreviations of this nature. I think everyone here is glad to wait a few extra seconds while you proofread your posts. Thanks.

---

### Post by david_lynch on 2008-10-10
All those who say the linux needs a "stable kernel API" should read what this leading linux kernel developer has to say on that subject:

[http://www.kroah.com/log/linux/stable_api_nonsense.html]("http://www.kroah.com/log/linux/stable_api_nonsense.html")

And here is a blog entry about the free linux driver service, which has resulted in improved device support over the past few months:

[http://www.kroah.com/log/linux/free_drivers.html]("http://www.kroah.com/log/linux/free_drivers.html")

You may want to look at those links before posting more of your thoughts.

---

### Post by chungy on 2008-10-10
> **phoenix_snake said:**
> u see, yes I used "u" instead of "you", most people like to get their responses quickly and don't like to wait to read the reply :)
Do you hunt and peck?  Using those "abbreviations" causes any normal typist to take *longer* to think about using them instead of two extra key-strokes.

---

### Post by phoenix_snake on 2008-10-10
> **chungy said:**
> 
Do you hunt and peck?  Using those "abbreviations" causes any normal typist to take *longer* to think about using them instead of two extra key-strokes.


are you crazy? you are the first person I have heard say something like this, everyone I know uses short forms for informal stuff and no one ever thinks, in fact we think about typing it properly ;)

> 
Erm, have you ever used Vista? Desktop effects break functionality all the time. There is no perfect OS. Just a better alternative that doesn't get viruses


hahaha so funny, lets insult windows instead when Novell's dumb engineer made the stupid mistake of certifying that machine. how is Dell in certifying linux machines?

I have used loads of Vista machines and all my friends use it and we have never had Aero break any functionality at all, you must be a rare case cause most of the time windows has better drivers, but in linux there are many people facing problems.

the reason windows has better drivers is again the topic of the argument here somewhat. 

listen up Vista has UAC right, and isn't that what protects linux from viruses right? I am only talking about viruses and since Vista has that, as long as its enabled any virus attack is the users fault.

Now please don't come with a crappy reply like "go back to windows or something"

maybe I should wait for a reply like this "how much is Microsoft paying you?" I don't work for Microsoft or Apple so no point even saying that.

> 
The Forum Rules state that you should avoid abbreviations of this nature. I think everyone here is glad to wait a few extra seconds while you proofread your posts. Thanks.


ok thank you, I won't use abbreviations, but don't you get the feeling these people just picked that point out cause they can't really argue back? :)

> 
All those who say the linux needs a "stable kernel API" should read what this leading linux kernel developer has to say on that subject:


the kernel developers want driver devs to release their documentation which is never going to happen since companies have to compete with each other.

and since they don't want a stable API, linux drivers will never be great and it makes it pointless to blame hardware companies cause believe it or not companies and people actually **want** to support your platform. Your developers aren't making it easy for them.

---

### Post by DrMega on 2008-10-10
> **phoenix_snake said:**
> the kernel developers want driver devs to release their documentation which is never going to happen since companies have to compete with each other.

and since they don't want a stable API, linux drivers will never be great and it makes it pointless to blame hardware companies cause believe it or not companies and people actually **want** to support your platform. Your developers aren't making it easy for them.

We could have a stable API to the kernel without every modifying the kernel in theory. As I've mentioned before it could just be an extra layer on top of the kernel, that distro creators could implement if necessary.

For example, if the Ubuntu devs decided that Ubuntu would have a stable API, they wouldn't need to modify the Linux kernel, they'd just need to create a package of libraries with a consistent interface, that doesn nothing more that make kernel calls to whatever version of the kernel was there.

For example, lets say we want a consistent interface to something as simple as writing a 32 bit word to a specific memory address (don't get too hung up on my oversimplified and unrealistic example, it is just to illustrate my point).

Lets say two releases of the kernel have two different ways to achieve this. For simplicity, we won't use real examples:

Kernel A has a funtion WriteWordToAdress(int address, int dataword)

Kernel B has a function WriteDataWordToAddress(int dataword, int address)

Then a higher level layer might have WriteWordToAddress(int address, int dataword). If the kernel is version A, it simply refers the call on to the kernel as is. If the kernel is version B, then the function just calls version B's function and passes the params over.

In reality I doubt very much that it would change so much between kernel versions, so it wouldn't be a complete rewrite every time, but it would leave the kernel devs to do their own thing while at the same time maintaining a consistent API in a seperate layer.

The example/illustration I used is over simplified and over exagerated but I hope it makes my point. This API could even be maintained by the kernel devs if they so wished.

It is not unusual in professional development (in fact it is the norm) to break down functionality into layers. A common example in database application development is writing classes to to translate data access/updates from a higher level generic call to a server specific SQL call, the idea being that if you change the database server, you only have to rewrite a tiny proportion of the system. A Linux kernel API layer would follow the same principle.

---

### Post by mike1772 on 2008-10-14
> **shadoweva00 said:**
> First, I know it will never "fail" because it's open source. It would be nearly impossible to kill an open source product, just take it as irony and move on.

Secondly I tried to answer the how the kernel is related to dependencies question, but I can't seem to write something that I feel does a good enough job of explaining it. Here it is anyway: [http://whydesktoplinuxwillfail.blogspot.com/2008/10/unix-compatable-kernels-and.html]("http://whydesktoplinuxwillfail.blogspot.com/2008/10/unix-compatable-kernels-and.html")

I'm not sure I yet understand how the kernel is related to dependencies.  The kernel just operates your hardware.  The dependencies have many causes.  Software developers who 'choose' to use a particular library rather than write something from scratch (a good choice by the way).  Shared libraries are similar to .dll's on windows.  Every application does not needs it's own copy of a dll - instead they use the shared copy of it.   This reduces disk and memory usage.  But it's not a limitation of the Linux Kernel any more than it's a limitation of the Windows Kernel.  You could just as easily statically link libraries and the dependency issue goes away.  I'm not sure why you'd want to though.  The real issue with dependencies is not the Kernel at all but the whole open source model (which again - is not a bad thing).  Microsoft is driven by money.  To get more of our money - they have to release finished products at regular intervals in order to entice us to upgrade.  Further - they must attempt to maintain backwards compatibility if they wish us to upgrade.  Linux - not being financially driven - can release at different intervals - and can scrap a poorly designed API if something better comes along.  In the long run - this approach would be better as you'd end up with a more stream lined OS.  But this means that libraries and API's on Linux fluctuate more than their windows equivalents.

Also - Linux is a Kernel.  It needs the other parts to be a functional operating system.  Because of this, personally I would consider the different distributions to be different OS's.  So, out of curiousity as I've not tried it, how difficult is it to run some of the recent games that require libraries MS only ships with Vista to run under a different Windows distribution?  Say Windows XP?  Or Windows 2000?  Probably easier than Linux (due mostly to my last paragraph) but I'll bet there are some that just won't run.

---

### Post by klange on 2008-10-14
OP still doesn't seem to understand much about Linux, FOSS, or POSIX.
Even the "problems" he mentions are not with Linux - they're exactly the same in the heavily kernel-hardened Solaris. I have *never*, in my entire time on Linux, had a dependency issue, save libc6 after bombing an upgrade during Alpha season.

---

### Post by Ripfox on 2008-10-18
If you have never seen Aero break functionality you have probably not used "tons" of Vista boxes, because it definitely screws up with various programs. The only reason I mentioned it is b/c you state Compiz as a reason why Linux is inferior. Fail.

---

### Post by Zyphrexi on 2008-10-18
this discussion seems totally pointless.

linux failing the desktop? what? so like, it loses a popularity contest? who cares?

as long as there are people willing to code it, it'll be here. Just because x amount of people don't use it means absolutely nothing. As long as I use linux, it lives. booya.

---

### Post by sicofante on 2008-10-19
There are people using MS-DOS, COBOL or the Citroen 2CV. If you think that makes those alive, you're a happy fellow.

Linux is a failure on the desktop so far. I think it will succeed and that will happen because someone decided to put money on a desktop oriented distro. Or may I say "because someone decided", since what's stopping Linux from becoming a serious contender in the desktop was the lack of a company making decisions for their users. Canonical is making that decisions and ordinary users won't need to become geeks in order to use Linux.

In spite of the naiveness of so many open source advocates, failure and success in the computer industry do have a meaning and it's measured in popularity and usage terms. The mere existence of something doesn't equal to its success.

---

### Post by phoenix_snake on 2008-10-19
Linux needs applications, when I say this I mean really amazing apps. Both Windows and OS X not only rely on 3rd party apps, they make their own as well.

For example Apple has iLife, and iWork, both are great, iCal, Address book, Mail, Safari, iTunes, Quicktime.

This makes them usable, then move on to other stuff.

Final Cut Pro for video editing, is the best on the Mac and is no doubt one of the best programs for video editing according to most people. Which program has linux got as good as this? There is Aperture, Photoshop, Logic Studio, Logic Pro, and Logic Express etc which are all very popular.

Now lets move on to Windows, they have Internet Explorer, I know many people here don't like it but its still the most popular and on Vista with Internet Explorer Protected Mode On, its one of the safest browsers for Vista.

Windows Live Messenger, Windows Media Player, Silverlight, Visual Studio, .Net, etc make windows usable.

Lets not forget Microsoft Office, the most used Office suite in the World.

Now linux has many of its own apps, but most of them aren't that great and **all** of the good ones are ported to other platforms, for example VLC, Firefox, openoffice, etc. You all know what I mean.

You need great for **your own** platform and not bother about anyone else.

Now why there is not much support by 3rd party devs for linux, market share is a reason but here are a few more:

Stable, and standardized API and ABI.

For example Linux has what a few million different sound systems, you have to choose between esd, pulseaudio, alsa, oss, arts, phonon, gstreamer, xine, did I miss a lot more? Yes I did. Can't memorize all of them.

Windows has got DirectX, Apple's got Core Audio, see how easy that is just target these if you make an app for them.

In Graphics Apple has Core Image, and Windows DirectX and WPA or something. 

Linux has nothing like this I think.

Both Windows and OS X have **one** set of toolkits, frameworks, and widgets. OS X has Cocoa, and Windows has .net.

Linux, which one? QT, GTK+, GTK2, TCL/TK, or wxWidgets? I might have missed another few hundred of them sorry.

Now most of these problems a friend told me about this stuff, anyway.

Now another thing is stability, and we are not talking about applications crashing.

The APIs and ABIs themselves don't change so much and core subsystems aren't changed at random. Windows is still capable of running 16-bit and 32-bit legacy applications.

Cocoa, CoreImage and CoreAudio frameworks are stable. They don't change on a day to day basis, they're backwards compatible, and don't break all kinds of core functionality between point releases, let alone major releases.

Now linux is a nightmare for developers. Even in the kernel development occurs in the stable branch breaking stuff a lot.

If you want others to develop for your platform, devs really need to fix this stuff, but that will mean letting go of a lot of choice and I really doubt this will happen.

Another problem with the linux community is "freedom", remember Nokia and how it tried to teach linux devs business?

[http://www.businessweek.com/globalbiz/content/jun2008/gb20080612_288518.htm?chan=top+news_top+news+index_global+business](http://www.businessweek.com/globalbiz/content/jun2008/gb20080612_288518.htm?chan=top+news_top+news+index_global+business)

> Jaaksi, Nokia's vice president of software and head of the Finnish handset manufacturer's open-source operations, said: "We want to educate open-source developers. There are certain business rules [developers] need to obey, such as DRM, IPR [intellectual property rights], SIM locks and subsidised business models."

Jaaksi admitted that concepts like these "go against the open-source philosophy", but said they were necessary components of the current mobile industry.

Also lack of co ordination and direction:

> In his speech, Jaaksi detailed some of the lessons Nokia had learned in its work with the Maemo developer community, primarily the need to avoid 'forking' code. He said: "Don't make your own version. The original mistake we made was to take the code to our labs, change it and then release it at the last minute. **The community had already gone in a different direction than [us], and no-one was pushing it other than [us]. Everybody wants to make their own version and keep it too close to their chest but that leads to fragmentation.**"

---

### Post by p_quarles on 2008-10-19
@phoenix_snake: A shorter way of saying that would be to just say that Linux sucks because it's free and open source. Now, you're free to believe that if you like, but you are complaining about it's defining feature. It's kind of like going into an ice cream shop and complaining that there's no meat loaf.

---

### Post by phoenix_snake on 2008-10-19
> **p_quarles said:**
> @phoenix_snake: A shorter way of saying that would be to just say that Linux sucks because it's free and open source. Now, you're free to believe that if you like, but you are complaining about it's defining feature. It's kind of like going into an ice cream shop and complaining that there's no meat loaf.
no thats not what I am saying, I am saying that if you set standards you can move ahead really fast for example, all those sound servers, why do you need them? why not have one?

---

### Post by cardinals_fan on 2008-10-19
> **sicofante said:**
> 
In spite of the naiveness of so many open source advocates, failure and success in the computer industry do have a meaning and it's measured in popularity and usage terms. The mere existence of something doesn't equal to its success.
Linux (Arch and Slackware) does what I want, how I want it.  Therefore, I consider it successful.
> **phoenix_snake said:**
> 
You need great for **your own** platform and not bother about anyone else.
Why?  Why shouldn't people be free to write for whatever platform they want?
> **phoenix_snake said:**
> 
For example Linux has what a few million different sound systems, you have to choose between esd, pulseaudio, alsa, oss, arts, phonon, gstreamer, xine, did I miss a lot more? Yes I did. Can't memorize all of them.

[This article]("http://www.linux.com/articles/113775") might interest you.

---

### Post by Zyphrexi on 2008-10-19
> @phoenix_snake: It's kind of like going into an ice cream shop and complaining that there's no meat loaf.

That has always bothered me. Also my local bicycle repair shop doesn't carry aardvarks. This issue needs to be remedied IMMEDIATELY.

---

### Post by phoenix_snake on 2008-10-19
you all agree with me about my previous post right? ain't I right that these problems do exist with linux and as soon they are solved I bet you will have great drivers and apps from 3rd parties.

people are free to make apps for any platform they want, when did I say they will only choose what I want them to choose?

just don't let all of your good stuff to the other side, be smart, look at Apple, they have kept some of their cool apps with them for example iLife, they only ported Safari and iTunes over for market share and the ipod and stuff.

---

### Post by Canis familiaris on 2008-10-19
> **phoenix_snake said:**
> just don't let all of your good stuff to the other side, be smart, look at Apple, they have kept some of their cool apps with them for example iLife, they only ported Safari and iTunes over for market share and the ipod and stuff.

As I said to someone in another thread: The Aim of FOSS is the joy of sharing and giving services to people as much as it can and NOT to get maximum users.

---

### Post by cardinals_fan on 2008-10-19
> **phoenix_snake said:**
> you all agree with me about my previous post right? ain't I right that these problems do exist with linux and as soon they are solved I bet you will have great drivers and apps from 3rd parties.

people are free to make apps for any platform they want, when did I say they will only choose what I want them to choose?

just don't let all of your good stuff to the other side, be smart, look at Apple, they have kept some of their cool apps with them for example iLife, they only ported Safari and iTunes over for market share and the ipod and stuff.
No, I don't agree.  If everything works perfectly for me now, how can there be "problems" with my system?

Also, you just repeated that people should only develop apps for Linux.  Read your post and think about it.

---

### Post by Mr. Picklesworth on 2008-10-19
phoenix_snake, you may also like this article on Linux sound APIs:
[http://0pointer.de/blog/projects/guide-to-sound-apis.html](http://0pointer.de/blog/projects/guide-to-sound-apis.html)

I definitely agree that there are problems! (Sorry I didn't make that clear :P)
This all has to happen organically, though. The organic solution here is for a significant number of developers to put weight behind a certain collection of software. The standardizing of a library is not some feature that the developers of that library can just throw in; it happens because the outside world agrees on it. This is no different from a collection of operating systems (or standards) being built at once, except on this end we are not just stealing each other's ideas and we are not intentionally forming fences between each other. Instead free software developers choose to share components and ideas where it is possible.

Keep in mind that "Linux" is *not* just Linux. I like to think that we have two major free software platforms: GNOME and KDE. There are some other exciting young contendors like Enlightenment, and XFCE is a pretty close sibling of GNOME (being that it uses similar design philosophies and many of the same technologies).

The different platforms are most compatible, thanks to packaging systems (automatic dependency resolution that only downloads the necessary components instead of the whole KDE desktop) and the fact that free software shares a lot of components. For example, FreeDesktop's specification that defines .desktop files in /usr/share/applications is consistent across desktop environments. So is the sound theme spec. Telepathy has FreeDesktop's blessing and indeed has a KDE end coming happily. Everything here uses the same kernel so is compatible at least from a low level (eg: the terminal).
The "fix" of those not existing is impossible. The only thing that could happen if Linux as a whole became totally GNOME-centric or totally KDE-centric is that the other wad of projects would be detached into a completely different community.

Having said that, when a *sensible* developer targets Linux, he targets a specific platform instead of targeting everything. I don't know KDE very well, but for my projects for example I am using (specifically!) components like GTK, GStreamer, Cairo, Pango and Clutter. This way the developer does not go crazy and his users get a top notch program.
It is the golden rule: Start simple.

UI toolkits like XUL and whatever OpenOffice is using, which are equally ugly wherever you put them, arise when developers do not follow that rule. The result is unpolished releases with *tons* of coverage but where depth is very difficult to achieve. A neat method that works really well for projects is to have detached front ends and back ends. For example, Pidgin is designed like that. This way one developer can build a superbly polished release for GNOME, then another developer can use the back-end specifically to build a superbly polished release for KDE or Enlightenment, without a moment of cruft.
(On that topic, I understand Enlightenment has some neat UI abstraction going on).

For real time graphics work, OpenGL works well for enterprising developers who need to do really neat low level graphics stuff. Otherwise you can try a good graphics engine like Ogre, which does beautifully at abstracting it all. SDL is great, too, if a less pointy system is needed.
With graphics work, all the libraries are *very* cross platform, which makes sense to this end since the DEs don't attempt anything fancy with such things. They all agree on the same fundamental standards for graphics so that stuff generally does 'just work' (until we get to the video drivers).

---

### Post by phoenix_snake on 2008-10-19
I can't believe none of you want to accept there is a problem with your platform, linux on the server is great, but on the desktop there are issues.

Stick to your 0.9% market share, enjoy watching flash crash and blaming Adobe for something that isn't their fault.

Keep on telling new users lies that 3rd party devs only support those with huge market shares, though thats true to some extent, Windows and OS X have given devs a proper development platform.

Even OS X started out with no market share and look at the 3rd party support they have.

Since I am tired of this discussion, I won't be replying here again.

I am just going to wait for Intrepid right now, so far it supports everything on one of my desktops except power management, which I hope is fixed in the final.

Bye, see every one in the other sections of the forum.

---

### Post by cardinals_fan on 2008-10-19
> **phoenix_snake said:**
> I can't believe none of you want to accept there is a problem with your platform, linux on the server is great, but on the desktop there are issues.

Stick to your 0.9% market share, enjoy watching flash crash and blaming Adobe for something that isn't their fault.

There are problems for you, but not for me.  I have never experienced a Flash crash on Opera (or Firefox with Flash 10), and I don't blame Adobe for anything.

Don't assume that everyone has the same problems as you.

I'm looking forward to seeing you in other sections of the forum.

---

### Post by p_quarles on 2008-10-19
> **phoenix_snake said:**
> I am just going to wait for Intrepid right now, so far it supports everything on one of my desktops except power management, which I hope is fixed in the final.
Yes, and obviously Intrepid has accomplished this by moving to a stable ABI and forking Pulseaudio into a closed source project. You heard it here first.

---

### Post by Mr. Picklesworth on 2008-10-19
Another worthy audio library for games that everyone neglects to mention: OpenAL.

My thought on game development is that being specific to a platform is really great where it can be afforded. That allows for neat things like Telepathy's Tubes feature which can really enhance the experience for an end user. However, it is nice that the libraries which games tend to use are abstracted to the point that they can be cross-platform since platform-specific polish is less of an issue for a full screen game. More a "nice touch" than anything else. (Most games aren't expected to integrate with much, but to be single cohesive experiences).

With that in mind, I don't think "GameKit" would work very well for any platform.

---

### Post by caeroe on 2008-10-19
Why so complex on the reasons?

It fails because there's limited software and gaming support.  

I have to jump through hoops to find a properly working printer and have it stay working. 

It took years for me to be able to play music in Rhythmbox and watch a Youtube video.  If I tried to do both simultaneously, the video wouldn't load due to audio conflicts.  It's not like I use obscure hardware, it's just a SB Live type card.

Wireless networking is always, always a frustration.  Every time I run the Update Manager I wonder if it'll once again break my settings, forcing me to drag my notebook back and troubleshoot for hours to get the wireless running.  

Speaking of, why can't Ubuntu's Network tool remember my settings, EVER?  I have to use Wicd now, which works, but I had to spend hours trying to find a management program.

/sigh

---

### Post by Delever on 2008-10-20
@phoenix_snake, I get what you are saying, but some of your examples have mistakes. (one of them: on graphics front, linux has OpenGL. look it up if you don't know what it is. Another one: "for interface, windows has .net", well, not necessarily, etc.). You can't sum up whole world :)

As for the topic, how do you define "fail"? If "fail" means OP will not use it tomorrow, then it's his problem. If "fail" means linux-based systems won't be on most desktops, then I don't care about this definition.

---

### Post by Polygon on 2008-10-20
> **caeroe said:**
> Why so complex on the reasons?

It fails because there's limited software and gaming support.  

I have to jump through hoops to find a properly working printer and have it stay working. 

It took years for me to be able to play music in Rhythmbox and watch a Youtube video.  If I tried to do both simultaneously, the video wouldn't load due to audio conflicts.  It's not like I use obscure hardware, it's just a SB Live type card.

Wireless networking is always, always a frustration.  Every time I run the Update Manager I wonder if it'll once again break my settings, forcing me to drag my notebook back and troubleshoot for hours to get the wireless running.  

Speaking of, why can't Ubuntu's Network tool remember my settings, EVER?  I have to use Wicd now, which works, but I had to spend hours trying to find a management program.

/sigh

sounds exactly like what i had to deal with on my friends vista computer yesterday. Now i fixed it all, but it keeps bluescreening for no apparant reason.

---

### Post by caeroe on 2008-10-24
> **Polygon said:**
> sounds exactly like what i had to deal with on my friends vista computer yesterday. Now i fixed it all, but it keeps bluescreening for no apparant reason.

I never, never had a crash in WinXP.  Move him back to that.

Oh and I was able to get my wireless by reverting back to the 2.6.24-19 kernel.  But guess what happened next?  Another wonderful update from Ubuntu broke my soundcard.  Now I get Gstreamer audio errors on any playback.

Ubuntu Linux:  One step forward, two steps back.

I might try this (non)operating system again in a few months.  I wonder if my USB mouse will be next to break, the rate I'm going with 8.04.  This seems to be my trend.  Try out the next big release, only to discover nothing has really changed.  Poor hardware support, bugs galore, and no software/games.

---

### Post by sicofante on 2008-10-24
> **phoenix_snake said:**
> I can't believe none of you want to accept there is a problem with your platform, linux on the server is great, but on the desktop there are issues.
The first and biggest problem we have is that we don't actually have a platform...

I actually agree pretty much with you. I understand your frustration and I'm sorry I haven't been around earlier to support you but I've had a lot of work lately.

Linux for the desktop has indeed a lot of issues for 3rd party developers that mean there won't be many commercial apps for home/soho end users anytime soon (only the enterprise, education and some niche markets can attract commercial developers right now).

It's been said before, but I'll try again: there won't be any standards set by a conscious decision made by developers. If we ever see standardization on the Linux desktop it will come in the form of a de facto standard. So far, Ubuntu is the closest thing to that, but it's still far from absolutely dominating the Linux desktop.

You're right most forums are crowded by "it works for me" people, "go back to Windows" zealots, "Linux is about choice" dumbheads and so many other stereotypical Linux users. (You must admit, though, Ubuntu forums have a great share of common sense that other Linux forums lack.) Linux attracts mostly geeks today while 99% of desktop users out there (Windows, Mac or Linux) are regular fellows that don't go posting their opinions about the operating system their computers use. They just use their computers. They talk about football, movies or fashion, they don't talk about computers.

Saying Linux "will" fail on the desktop is playing psychic. It's an evolving system and anyone who's tried Ubuntu for the last two years must admit it's going fast. Every new Ubuntu release is a blow of fresh air in the right direction.

---

### Post by Polygon on 2008-10-24
> **caeroe said:**
> I never, never had a crash in WinXP.  Move him back to that.

Oh and I was able to get my wireless by reverting back to the 2.6.24-19 kernel.  But guess what happened next?  Another wonderful update from Ubuntu broke my soundcard.  Now I get Gstreamer audio errors on any playback.
.

then all the bluescreens and crashes and issues i get with windows xp are just a figment of my imagination =)

---

### Post by BGrigg on 2008-10-24
Possibly. The only times I've experienced BSOD with XP have been hardware failures. I've had many program crashes, but not XP.

I once had an XP system that, other then when there was NO power, ran continuously with reboot for over a year and a half.

The crashes might not be because you're imagining them. You may have configuration problems that are at fault, and not the fault of the OS. I have experienced WAY more crashes with Ubuntu than XP. I continue to use both (just not on the same machine!).

And everyone has been because I've mucked something up.](*,)

---

### Post by Polygon on 2008-10-25
there are no configuration problems. Ive installed my drivers and i still get issues.

Windows ide controller (for a pci card, i forget the proper name) is buggy, so i get errors about timeouts when reading and writing, and the only way to solve this is to completely reinstall windows and provide the 'proper' driver on boot. yeah, not gonna happen

windows update provided updates to my wireless card. too bad it made my computer bluescreen on boot and i had to boot into safe mode to get it to stop crashing the entire system


random things won't work after continued use. like for some reason i cannot click on my computer or else it will freeze the entire system. And as you can imagine this basically crippled the use of my computer.

just remember, 'works for me' goes both ways. You have problems with ubuntu, I have problems with windows. And this is with official drivers provided by the manufacturers, while ubuntu is using non-offical stuff

---

### Post by Saint Angeles on 2008-10-25
my linux desktop hasn't failed once in the year ive had it.

and is it really important what the OP thinks about anything? i mean... we should be interested in facts, not opinions.

not trying to be rude... but if you look at how much linux has improved in the last couple years and the exponential growth in users, you'll realize that linux will steadily grow more popular. it doesn't matter what anybody "thinks" about it.

and if you think linux will fail, why don't you just stop whining and start helping by creating better programs? i know why, because you prefer starting flamewars to being helpful. go ahead and use windows and stop crying out for attention in these forums. ubuntuforums is mostly about being helpful and giving advice.

man... a new kernel? really? thats why you think linux isn't good? this has to be a joke. they estimate that the kernel alone would've cost about 1.4 BILLION dollars in R&D had it not been free.

so feel free to spend more on a new kernel if you want... I'll stick with linux. so will [many other people.]("http://www.usatoday.com/money/industries/technology/2002-08-04-linux_x.htm")

---

### Post by schauerlich on 2008-10-25
Oh god... that blog is... painful to read. He's got absolutely no clue how OS's work. He thinks it's just a kernel and "the desktop" and that dependencies are just something developers throw in there to be mean and to spite Microsoft. WTF?

---

### Post by Saint Angeles on 2008-10-25
> **EDavidBurg said:**
> Oh god... that blog is... painful to read. He's got absolutely no clue how OS's work. He thinks it's just a kernel and "the desktop" and that dependencies are just something developers throw in there to be mean and to spite Microsoft. WTF?
HAHA... i didn't even bother going there.

i assumed there were a bunch of youtube videos playing at the same time and the background was an animated gif file.

EDIT: OK... WOW

I'm trying to read his blog with my fiance (an avid user of linux also) and neither of us can understand ANYTHING he's trying to write here. He keeps mentioning the "kernel", "dependencies", and "desktop" but he has no idea what they actually are. Here's a prime example of utter nonsense: > The first thing that needs to be considered is installing software on Mac and Windows doesn't usually involve dependencies. It is very simple, their kernel ships with their desktop. I have no idea what his definition of "desktop" is. is he referring to the GUI?
here's a funny paragraph above that last quote: > The most common request I'm getting is a better explanation of how dependencies are related to the kernel. I'm going to try to explain it as thoroughly as possible, but it probably wont be enough so leave detailed feedback in the comment section (and start using the comment section). The two biggest reasons for this are: Open source usually takes the lazy road, and the kernel will never ship with a desktop.The kernel will never ship with a desktop? no matter how many times i try to read this, it makes no sense. I think his site needs cliff notes. or possibly a translator and grammar check.
Here's some more solid gold:> The much bigger issue here is that the typical user thinks dependencies are obsolete technology. To be brought up to par with competition, they must go. However, eliminating them would essentially take an act of God. It could be done by having everyone agree what software will constitute a desktop and that they will never use dependencies unless absolutely necessary to get rid of them and the need for a package manager. This is just too painful to read.

---

### Post by akiratheoni on 2008-10-25
Linux hardly ever gives me any problems, yet I don't scream that it's "ready for the desktop". I know that every computer is different and while Linux support is readily increasing I don't tell someone "hey, install this and it'll work fine". I give them the LiveCD and then test it on their computer before I actually hand it over to them to fend for themselves.

I don't like to declare that Linux is "ready for the desktop" because it's ready on some, but fails on some others. The only reason why this is a problem is because the zealots keep insisting that it works perfectly, no questions asked. I like Linux as much as they do but... c'mon.

---

### Post by Delever on 2008-10-26
Can anyone give me a link where I can download dependencies?

---

### Post by Saint Angeles on 2008-10-28
hah

i don't see how "dependencies" are a problem because when you go to install something via apt-get or synaptic,  the dependencies are automatically installed as well.

---

### Post by ruiseixas on 2008-12-29
> **shadoweva00 said:**
> I've studied all the things that annoy me about Linux, and come to the conclusion that if open source will succeed on the desktop it will need a new kernel to be written. To be professional and thorough in describing why I think that, I have started a blog: [http://whydesktoplinuxwillfail.blogspot.com/]("http://whydesktoplinuxwillfail.blogspot.com/")

So far I've described the community, and package managers. The next post will probably be about driver licensing or the kernel, and then some posts responding to your angry comments.

Hi,

I don't think that there is a kernel problem, but a cooperative problem. For example, some software developed, ends compatibility with new kernel versions, for instance, compiling with make, generates erros due to the simple fact that the kernel change version. It's hard to have programs behaving like in windows, maintaining is compatibility with Win98 programs.

Another real problem comes from the unsupported hardware, not because it's unsupported, but because some of them it's considerated as supported where in fact it isn't. I'm thinking in the Atheros wireless cards, where you still need the HAL binary file (not open source).

Because normally new technology it's associated with new hardware, it's very common to find unsupported Linux drivers for them, and I don't see much care in publishing what is supported and what is not...

For instance, I don't see a straight association between some specific laptops and his compatibility with Linux from the perspective of a Linux distribution, like ubuntu, fedora, or other; It's always from the perspective of some one that claims to be very easy to install Linux on some specific machine, not being necessarily true to other person.

I have a Sattelite A200, that is considerated good for Linux by some users, but I'm still having problems with the wireless card as I describe here: [http://ubuntuforums.org/showthread.php?t=1011304]("http://ubuntuforums.org/showthread.php?t=1011304")

Again, I don't see any problem with Linux it self, in my opinion it's an OS with all it takes to be a very good one.

Regards :)

---

### Post by ronbravo on 2008-12-29
> Linux hardly ever gives me any problems, yet I don't scream that it's "ready for the desktop". I know that every computer is different and while Linux support is readily increasing I don't tell someone "hey, install this and it'll work fine". I give them the LiveCD and then test it on their computer before I actually hand it over to them to fend for themselves.

I don't like to declare that Linux is "ready for the desktop" because it's ready on some, but fails on some others. The only reason why this is a problem is because the zealots keep insisting that it works perfectly, no questions asked. I like Linux as much as they do but... c'mon.

Well said. Being new to Ubuntu and GNU Linux, I've only had it for about a year, in my opinion it is an excellent piece of technology but it is not for everyone. Just like some people like to ride a bike others may prefer to take a bus. Different strokes for different folks.

The original post that GNU Linux will fail on the desktop seems odd at best. 

GNU Linux and it's system is obviously working for several individuals and organizations around the world or else it would have failed a long time ago. I can understand some of the concerns addressed like development API issues and easy right out of the box type of access, but that's what I thought distros like Ubuntu were trying to solve? Isn't it supposed to provide a more consistent and wildly used version of GNU Linux to make life easier for developers and consumers? If the original poster feels that GNU Linux has all these issues that make it doomed for failure, then that is OK. Windows and Apple are still making their OS available for use so it's not too late to switch back and use those for the time being until GNU Linux and it's communities resolves these subjective issues. Posting about how GNU Linux will fail as a desktop seems like a waste of time. Why not use that energy instead to read up and get more familiar with GNU Linux? However, I will say I learned a few interesting things in this post about GNU Linux and it's shared libraries which is pretty cool. 

As for me I'm loving Ubuntu and I try to convert people any chance I get, provided I can give them the support they need. GNU Linux is an excellent piece of technology to bad not everyone sees it that way. Hopefully they will have better experiences in the future with it. C ya.

---

### Post by dj-toonz on 2009-02-12
How i see it TBH, why people say Linux will fail, is because apt / yum or whatever needs a internet connection to download & install the dependencies what the software needs. take for example a friend of mine bought a linux mag to read and tried to install some software on his machine what was in .deb files but the installer said it needed blah blah blah but he has not got a net connection. rang me up, i tock my 3.5g usb modem round. wouldn't work as he is using ubuntu 8.04. take for another example. if shops did start selling cd / dvd's with linux software on them aswell as windows software (how would newbiews to linux figure out how to install them. It's not a case of inserting the disk and a box pops up on screen. press here to install the game or application and hold there hand to install there hardware of what ever. IMHO that's why a lot of people say linux is rubbish. I did have that problem with linux when i first started using it but after nearly 10 years now. I dont have that problem. Yes linux is getting there but intill the devolopers / software / hardware companys made it easier for new users of linux to install there hardware or software then i dont know

---

### Post by Bonsanto on 2009-02-13
1.- My system crashes.
2.- I got many "initramfs" bugs in the start of ubuntu.
3.- I got many many times "fsk" bugs.
4.- I can't open many firefox becouse It makes my system crash.
5.- If I listen music and play freecell, It makes my system crash.
6.- I get many problems when I try to install something. Becouse If it crashes It makes Ubuntu delete a "lib" things, So I have to reinsall all the OS again (I have done 9 times).
7.- I have been looking for the "crash solution" for 1 week and nothing was found.
8.- In WIndows XP, my system dosen't crash, I can leave my pc turned on for weeks and no crash. But in Ubuntu 2 programs = crash.
9.- People said "try with no acpi" I don't know where to type that comand, is too much genereic isn't especific.

---

### Post by Kopachris on 2009-02-13
Linux doesn't need to "win" as you see it.  We only need to be left to our own devices (pun intended).  The goal of the Linux power users (not the general users) is not to beat Microsoft (which would be nice), but it's to build the best OS that we can, how *we* think it should be built.  To quote NatBro, "[...] it's not too hard for a developer in the OSS space to scratch their itch [...]"  To most FOSS developers, including the vast majority of Linux-specific developers, that's what it's all about.  Scratching their itch.  That one little thing about that program is bugging me, so I get the source code, fix it, and maybe even reupload it.  For those who make Linux distros (an extremely popular hobby), it's about fixing something they don't like about the distro they're using.  I, for instance, don't like having to download a ton of extra software after I install.  So, I'm working on making a distro that includes tons of stuff.  At installation, the user will be presented with a list of checkboxes so they can choose *not* to install some of it.  That's how I think an OS should work, that's scratching my own itch.  That's what FOSS development, and Linux in particular, is all about.  That's how Linux was started, even.  Linus felt the urge to make a kernel, to see if he could do it, and he did.  And he posted the results on the internet.  And now here we are, over 15 years later.[FONT=Helvetica][SIZE=3][COLOR=#000080][/COLOR][/SIZE][/FONT]

---

### Post by Sorivenul on 2009-02-13
> **Bonsanto said:**
> 
7.- I have been looking for the "crash solution" for 1 week and nothing was found.
Have you tried posting your own thread on the specific issues you are having? If you aren't coming up with results on your own, the forum folks usually have quite a knack at finding the solution themselves or on another site you may have missed.

---

### Post by Bonsanto on 2009-02-13
I did, NO answers or suggestions.

---

### Post by pgatrick on 2009-02-16
> **shadoweva00 said:**
> It's the downsides of package dependencies, they are directly tied to using Unix kernels. If you want universal single file installs that work on every OS distro under the name, they have to go. The only way they will is if the Unix kernel is abandoned for desktops since the same old software will just be ported to it and give the same experience with the same problems.

So you're saying linux will only work if you make something new which isn't linux? Oooooookay.....:popcorn:

---

### Post by Koori23 on 2009-02-17
You're right. Linux is failing bad. It's falling flat on it's face. We better pull the plug on the whole operation. Goodbye Google, Wikipedia, most of NASA, IBM, Lowes, .. The list goes on. All of those guys are suckers for buying into this whole thing.

---

### Post by Kopachris on 2009-02-17
> **Koori23 said:**
> You're right. Linux is failing bad. It's falling flat on it's face. We better pull the plug on the whole operation. Goodbye Google, Wikipedia, most of NASA, IBM, Lowes.. The list goes on. All of those guys are suckers for buying into this whole thing.
+1.  If Linux goes, so does half the web.  Goodbye Web 2.0... :p

---

### Post by Koori23 on 2009-02-17
Those aren't just servers either. Many of those organizations use Linux on both sides, end user and server roles.

---

### Post by |{urse on 2009-02-17
Seems a bit like the OP has no idea what a kernel is.

---

### Post by bobbob1016 on 2009-03-21
> **shadoweva00 said:**
> ....have a wacom tablet? The typical user must never have to edit these files by hand, like they wouldn't have to edit them on the competition. The fact that they exist means they will have to be hand edited if some unusual new piece of hardware is installed.

Device driver issues like this aren't as much Linux's fault as they are the fault of lack of hardware vendor's support for Linux.  Ever have to buy a copy of XP tablet for your tablet, not simply having to add a few lines to 1 file?

Have you tried BSD, or ReactOS?

---

### Post by Bios Element on 2009-03-21
> **|{urse said:**
> Seems a bit like the OP has no idea what a kernel is.

Or like the OP is just a troll. Which he is.

---

### Post by MasterNetra on 2009-03-21
> **Koori23 said:**
> You're right. Linux is failing bad. It's falling flat on it's face. We better pull the plug on the whole operation. Goodbye Google, Wikipedia, most of NASA, IBM, Lowes, .. The list goes on. All of those guys are suckers for buying into this whole thing.

Don't forget about window's live.com :p

---

### Post by Eddie Wilson on 2009-03-24
This is really a dead thread. The last post made in his blog on this subject was in Oct. of 2008. His blog does not follow any logical reasoning thus has not attracted any attention. Its better not to beat a dead horse. All that does is stir up a stink so its time to move on.

---

### Post by basenvironment on 2009-05-05
someone put this thread out of its misery....

The OP is still a member here?
[http://ubuntuforums.org/showthread.php?t=1110486](http://ubuntuforums.org/showthread.php?t=1110486)

---

### Post by blazoner on 2009-05-16
> **|{urse said:**
> Seems a bit like the OP has no idea what a kernel is.
Isn't that who you go to to get some fried chicken???? =P~

Seriously, if the hardware developers need an API, why don't they just create one to protect their tech, and publish it to the community at large? That way the kernel can be designed and re-designed around the hardware without violating NDA's and such. Although it wouldn't be optimal, it would likely be leaps and bounds ahead of the current situation. Code could probably even be recycled between disparate OS's, like using some of the same driver code for Linux as is used for Windows.

---

### Post by praveesh on 2009-05-28
Why not adopting a new technique?. It is creating an archive like .iso or .nth(nokia theme) or jad which contains the package to be installed and all the dependancies . If a dependancy is already installed , no need of installing it , otherwise it should be installed automatically. There should be a software to manage it .  It will certainly increase the size of package but will help the end user very much . It is similar to a gaming software coming with directx in its cd . If directx is not installed , game installer will automatically  install it . There is room for another technique . It is including all the popular binaries of various distros in a single archive  .appropriate binaries will be installed in different distros . By this,same binary can be  used in different distros . Iam not a dev so if Iam wrong , please forgive me.

---

### Post by Intrepid Ibex on 2009-08-01
Doesn't seem like this fella studied anything, even though that's what he claims.

Well, there will always be windows users complaining about something about linux when they blindly love M$ and who's "linux tests" have ended before they have even started.

---

### Post by Viva on 2009-08-01
*linsux alert*

---

### Post by pepperphd on 2009-08-01
My experience with Vista: Crashed EVERY DAY.  My experience with Linux(any distro): How do I crash this thing?

---

### Post by Dullstar on 2009-08-01
If the GUI was integrated into kernel, GUI crashes, kernel may go down.  Also, it removes the choice.

Don't make us all sad pandas!  Some people like GNOME!  Some like KDE!  Some like XFCE!  Some like Fluxbox!  Some like OpenBox!  Some like LXDE!  Some like "OTHER".

Look, OP, go and make your own Linux kernel if that's how you feel.

---

### Post by MikeTheC on 2009-08-02
And now for something completely equally pointless...

[quote=Monty Python's Contractual Obligation Album]I Like traffic lights.
I Like traffic lights.
I Like traffic lights,
No matter where they've been.
I Like traffic lights.
I Like traffic lights.
I Like traffic lights.
I Like traffic lights.
I Like traffic lights,
But only when they're green.

He likes traffic lights.
He likes traffic lights.
He likes traffic lights,
No matter where they've been.

He likes traffic lights.
He likes traffic lights.
He likes traffic lights,
But only when they're green.

I Like traffic lights.
I Like traffic lights.
I Like traffic lights.
That is what I said.

I Like traffic lights
I Like traffic lights
I Like traffic lights,
But not when they are red.

He likes traffic lights.
He likes traffic lights.
That is what he said.

He likes traffic lights.
He likes traffic lights.
He likes traffic lights.
He likes traffic lights.
He likes traffic lights,
But not when they are red.

I Like traffic lights.
I Like traffic lights.
I Like traffic lights,
Although my name's not Bamber.

I Like traffic lights.
I Like traffic lights.
I Like traffic lights.
I-- Oh, God![/quote]

---

### Post by Giant Speck on 2009-08-02
[img]http://palinoscopy.files.wordpress.com/2009/06/sarah_palin_pancakes.jpg[/img]

---

### Post by MikeTheC on 2009-08-02
Additionally, [here's a web site which doesn't work any more.](http://www.flingthecow.com/)

Or, if that proves to be insufficient, [here's actual instructions on how to screw in a lightbulb.](http://www.wikihow.com/Screw-in-a-Lightbulb)

Also, consider [this kindly book on 99 uses for a dead cockroach.](http://openlibrary.org/b/OL2876315M/99-uses-for-a-dead-cockroach)

---

