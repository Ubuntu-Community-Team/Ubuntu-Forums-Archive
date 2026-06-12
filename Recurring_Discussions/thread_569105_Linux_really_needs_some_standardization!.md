---
title: "Linux really needs some standardization!"
date: 2007-10-06
forum: Recurring Discussions
---

### Post by Snif on 2007-10-06
I think Linux developers should somehow come to conclusion about lots of things in making OS and applications. You can't always start new small communities for making your little ideas come true, it's just too complicated for relatively small group of developers to make something really good. Developing serious things takes a lot of time, and in needs a STABLE TEAM and MANAGEMENT and some kind of control. And it's also a RESPONSIBILITY to users, i mean releasing new versions, support, etc. That's also what soft developers are payed for. Some applications are not free, and they can't really be free if users need progress and support. They need to keep the team together, for example :) It's quite another matter that apps could cost not so much and soft developers shouldn't release new versions with a bunch of useless "make-marketing-director-happy" features. 

I use both Win and Linux, and i can say Linux much improved in a last few years. I remember installing Linux, say, four years ago, it was like "wow! Looks cool,.. aaand there's a lot of little games and some infinite packages on 9 CD's.. Sooo what can I do with it after playing games and looking how cool it looks? Err, where's my Photoshop, my Office, my mp3-players, video codecs and players, pretty instant messengers, image viewers, cool utilities etc. etc. etc. that i use every day?? And why the hell should i install apps in such a disguistind way?? And why doesn't an application ask me where i want to install it and doesn't even tell me where it installs by itself? " 

And then i installed Ubuntu a few weeks ago, and it's much better now. Now i have my video codecs and players (not really brilliant but finally useful :)) and all needed hardware drivers and multilanguage support, and almost everything seems to "just work". There's a lot of really useful software, almost enough, but - almost. I think the only and the biggest problem still present is a kind of a mess with all those numerous distros, graphic desktop evironments, little similar programs etc. AND it still looks too customized and, well, cartoonish. Yes, i do like all those bright colours and shiny enormous icons and buttons - at first sight, but when it comes to work, you mention that it's all too messy, too colorful, and contains too much "visual trash". What for do i need a big "help" button in every window which i use everyday? I might need help first time i use it, but the next time it's just a waste of space! Why is OK button on the right of Cancel? Do i read from right to left? why there isn't often an "Apply" or "OK" or "Do that!" or something button, and only "Close?" is present? Finally, why not make buttons the same way in different apps? Developing interfaces IS NOT AN ARTWORK! I repeat, it not! It's developing of a MANAGEMENT TOOL first of all! So - it should be standarts and supervision by interface professionals, not that "i'll make this icon colorful and funky 'cause i like cartoons and big 'cause i'd like everyone to mention it!". Visit gnome-look.org - it's mostly like giving some red paint to children and leving them alone for a while! :) I've found less then ten really useable themes, among thousands!

So the conclusion is - Linux is getting much better but it slill needs much more standartization and cooperation, and setting developers on the right track - by professionals in specific spheres. Where come standards, come serious applications too, look at what's going on on web :)

And, finally, THANK YOU Canonical for Ubuntu, this forum and really good support for users. It's not like that trashy information sources on Linux i get used to see :)

---

### Post by Lord Illidan on 2007-10-06
Welcome to the forums!

About your issues with stand**art**isation, I do agree with you, but mainly where it comes to GTK/QT issues. For example, break out a GTK based player like Rhythmbox..Then break out a QT based player like Amarok. Since they use different widgets, they look completely different.

However, that might be solved soon, hopefully. Now, regarding your problem with gnome-look, well that's not really our problem per se. Anyone can make a theme and post it on Gnome Look, so you're inevitably going to have to seperate the wheat from the chaff!

---

### Post by 23meg on 2007-10-06
Moved to Community Cafe, since this does not pertain to Gutsy development.

---

### Post by ssam on 2007-10-06
> **Snif said:**
> why there isn't often an "Apply" or "OK" or "Do that!" or something button, and only "Close?" is present?

[http://developer.gnome.org/projects/gup/hig/2.0/windows-utility.html#windows-instant-apply](http://developer.gnome.org/projects/gup/hig/2.0/windows-utility.html#windows-instant-apply)

unfortunatly only gnome software follows the [gnome HIG]("http://developer.gnome.org/projects/gup/hig/").

if you use a more pure gnome desktop (use epiphany and abiword instead of firefox and openoffice), then you will find it more consistent

i think KDE are working on a similar set of guidelines for KDE 4.

for cross desktop stuff lots of work is being done by [http://www.freedesktop.org/wiki/](http://www.freedesktop.org/wiki/)

---

### Post by 23meg on 2007-10-06
[QUOTE=Snif]What for do i need a big "help" button in every window which i use everyday? I might need help first time i use it, but the next time it's just a waste of space! Why is OK button on the right of Cancel? Do i read from right to left? why there isn't often an "Apply" or "OK" or "Do that!" or something button, and only "Close?" is present? Finally, why not make buttons the same way in different apps?[/QUOTE]

In GNOME, there's a "standard" that provides developers with guidelines regarding those things called the [GNOME Human Interface Guidelines]("http://developer.gnome.org/projects/gup/hig/"); it should answer your questions. Most major applications follow it closely, and definitely all that are included by default in the desktop environment do; where they don't, it's most probably a valid bug.

If you mix and match apps from different desktop environments, and/or use software that for some reason doesn't follow the HIG (or similar guidelines), it's inevitable that you'll get some non-standard behaviour and design.

---

### Post by Dimitriid on 2007-10-06
Standardization is the end of progress just like Satisfaction is the end of desire.


*oooohmmmm*

---

### Post by phen on 2007-10-06
the small groups making software are the soul of oss! its the way it works! its not about management, its about finding exactly the solution you want. either in programming your own or in browsing repos. everyone can use the code of these small projects for a bigger, more managed project if he likes....

for example cd-burning: k3b uses a lot of small command line tools and combines them to a very nice looking frontend. thats the idea

---

### Post by Sp4cedOut on 2007-10-06
> **phen said:**
> the small groups making software are the soul of oss!

OSS doesn't have a soul.  Explain how standardization will hurt OSS progress.

---

### Post by perce on 2007-10-06
> **Snif said:**
> 
 Err, where's my Photoshop, my Office, my mp3-players, video codecs and players, pretty instant messengers, image viewers, cool utilities etc. etc. etc. that i use every day?? 


I did watch movies on Linux five years ago: I was preparing for TOEFL and I was watching a lot of movies in original language on my laptop.

> 
And why the hell should i install apps in such a disguistind way?? 


I was installing applications the same way I'm doing now: apt-get

> 
And why doesn't an application ask me where i want to install it and doesn't even tell me where it installs by itself? " 


Because applications are put in standard directories the use doesn't need to know unless he wants to learn how the OS works.

> 
 why there isn't often an "Apply" or "OK" or "Do that!" or something button, and only "Close?" is present? 


Because Gnome usually applies changes immediately

---

### Post by koenn on 2007-10-06
> the small groups making software are the soul of oss! ... is a short and somewhat colorful way of saying that oss is a distributed software development merhod. It mainly consists of self-organising groups of programmers all over the world. 
What makes this possible is
1- the internet, for global communication
2- open source code, so people can see it, download it, work with it, and publish it without constraints
3- standards such as rfc's, ISO standards, ... and guidlines such as the Gome usibility guidelines, and common 'programming on Unix" practise.

It's different in concept from the "development needs a STABLE TEAM and MANAGEMENT" approach  the OP promotes, but somehow still produces quality software. How that works is very well explained in "The Cathedral and the Bazaar" - [http://www.catb.org/~esr/writings/cathedral-bazaar/cathedral-bazaar/index.html](http://www.catb.org/~esr/writings/cathedral-bazaar/cathedral-bazaar/index.html)

---

### Post by BuffaloX on 2007-10-06
Seems like what you really want, is more and better software for Linux.

considering that Linux only has 1-5% market share, many of which don't want to pay for software. The availability of quality software for Linux is actually quite good.

I agree that more and better software for Linux would be cool, but it's not lack of cooperation or standards that is to blame, because they exist already.
The problem is lack of developers, and sometimes patents and secrecy from proprietary vendors.

The amount of developers for Windows is probably more than thousand fold that of Linux.
Fortunately there's a shift of developers towards Linux, so the situation is steadily improving.

---

### Post by koenn on 2007-10-06
re: > OSS doesn't have a soul. Explain how standardization will hurt OSS progress.
------------------
> the small groups making software are the soul of oss! ... is a short and somewhat colorful way of saying that oss is a distributed software development merhod. It mainly consists of self-organising groups of programmers all over the world. 
What makes this possible is
1- the internet, for global communication
2- open source code, so people can see it, download it, work with it, and publish it without constraints
3- standards such as rfc's, ISO standards, ... and guidlines such as the Gome usibility guidelines, and common 'programming on Unix" practise.

It's different in concept from the "development needs a STABLE TEAM and MANAGEMENT" approach  the OP promotes, but somehow still produces quality software. How that works is very well explained in "The Cathedral and the Bazaar" - [http://www.catb.org/~esr/writings/cathedral-bazaar/cathedral-bazaar/index.html](http://www.catb.org/~esr/writings/cathedral-bazaar/cathedral-bazaar/index.html)

---

### Post by Anessen on 2007-10-06
What we need is more control over a stable "desktop" version of Ubuntu. Really strict standards control, go for stability and control. Us geeks can have fun with the unstable version, letting new developments trickle down to the stable version - after extensive testing. Of course, this doesn't help the fact that hardware developers can't be arsed to support us, but it will attract people to write software for a stable, unified distro.

Really, we need to unify the different bits and pieces under a cover-all standard for desktop distros, leaving other distros for development and fun. People can write software that follows these standards that makes it less prone to compatibility issues.

---

### Post by smartboyathome on 2007-10-06
> **Anessen said:**
> What we need is more control over a stable "desktop" version of Ubuntu. Really strict standards control, go for stability and control. Us geeks can have fun with the unstable version, letting new developments trickle down to the stable version - after extensive testing. Of course, this doesn't help the fact that hardware developers can't be arsed to support us, but it will attract people to write software for a stable, unified distro.

Really, we need to unify the different bits and pieces under a cover-all standard for desktop distros, leaving other distros for development and fun. People can write software that follows these standards that makes it less prone to compatibility issues.

Isn't that what Debian does?

---

### Post by toupeiro on 2007-10-06
Standardization is a double-edged blade.  While it contributes to the ease of development and problem solving, it can hinder innovation if overdone.

Linux, is much more a follower of standards than Microsoft is.  As I've said many times before on this forum, Linux derrives fundamentally from operating standards that were developed and abided by since the late 60's to early 70's.  All subset applications, while they may be unique in their method of development, conform to a set of standards set by the operating system.  The OS development drives the software, which doesn't exist in the microsoft world.  With Microsoft windows, we've seen the integration of Internet Explorer into the core GUI, and now with vista the same thing applies to their media player.  The applications then start affecting the stability of the core OS because there is no seperation of OS layer and Application layer.  This is a very bad thing, as it not only promotes unfair business practices it jeopardized the security of the core OS with application exploits that are now native OS exploits.  Microsoft has always, and will always change their core standards every so many years to the benefit of their programmers, but not necessarily to the benefit of people who program for a Microsoft OS.  It is truly, their way or no way.  This makes their standards impractical, and they become restrictive to production and innovation because you lose the option of having an alternative, and many times a smarter, more efficient way of performing a task or writing an application.

So, while Microsoft has "standards" it is only within their sphere of influence that they can call them such.

---

### Post by Snif on 2007-10-06
> What we need is more control over a stable "desktop" version of Ubuntu. Really strict standards control, go for stability and control. Us geeks can have fun with the unstable version, letting new developments trickle down to the stable version - after extensive testing. Of course, this doesn't help the fact that hardware developers can't be arsed to support us, but it will attract people to write software for a stable, unified distro.

Really, we need to unify the different bits and pieces under a cover-all standard for desktop distros, leaving other distros for development and fun. People can write software that follows these standards that makes it less prone to compatibility issues.

I totally agree - there should be at least one stable and predictable distro with well-known plans for the future. 

> [QUOTE]And why the hell should i install apps in such a disguistind way?? 
I was installing applications the same way I'm doing now: apt-get[/QUOTE]
It wasn't a debian-based distro which i installed, and, by the way, some distros need something more complicated than apt-get nowadays.

> [QUOTE]And why doesn't an application ask me where i want to install it and doesn't even tell me where it installs by itself? " 
Because applications are put in standard directories the use doesn't need to know unless he wants to learn how the OS works.[/QUOTE]
Well maybe it's just a windows-based habit (because you may have more than one logical partition and sometimes there's not enough place on one so you put an app to another :)) But sometimes it's useful to fix something in app's files so i'd rather have info about where they're stored. Besides, when you don't have a package manager like synaptics, it's quite hard to delete an app which name you don't remember :) Not an "F8-No problem" i got used to ;) 

> If you mix and match apps from different desktop environments, and/or use software that for some reason doesn't follow the HIG (or similar guidelines), it's inevitable that you'll get some non-standard behaviour and design.
That's what i was talking about - you can mix apps from different desktop environments! Why not finally choose one environment and develop it, especially when there's lack of developers. 
As for stand**art**s ;) i think they should be more noticeable and evident, i refer to web again - you can see W3C, CSS, useability etc. everywhere, so people notice it and get the idea.

> the small groups making software are the soul of oss! its the way it works! its not about management, its about finding exactly the solution you want. either in programming your own or in browsing repos. everyone can use the code of these small projects for a bigger, more managed project if he likes....
If you want a big and managed project then you need money, because it will last for years and you'll need to keep your developers. Photoshop was improved for 18 years, and they still have developers that started it in their team. And it's just a single application!
You can't just write a small project that will do the same. And don't tell me about Gimp ;)

> So, while Microsoft has "standards" it is only within their sphere of influence that they can call them such.
Yes, MS doesn't follow the standarts, but at least they have one current version of OS and Apple too ) 

So i think there should be a major linux distro too. :)

---

### Post by rsambuca on 2007-10-06
Snif,  it is obvious that you have strong feelings on these matters, but virtually all of your complaints on the current state of linux OS's are merely complaints as to the appearance of things.  This is nothing more than a rehash of countless other threads of people complaining that linux doesn't look the way they want it out of the box.  Frankly, any linux system is highly configurable, and way more so than Windows ever has been.

Cartoonish in your opinion... too messy and too colourful, again, just personal opinion and preference.  "too much visual trash"... Buttons transposed???
Heard all of this before.  Too many times.

---

### Post by 23meg on 2007-10-06
[QUOTE=Snif]That's what i was talking about - you can mix apps from different desktop environments! Why not finally choose one environment and develop it, especially when there's lack of developers.[/QUOTE]

OK, great idea! I choose GNOME and I'll develop on it, as does Ubuntu. Now, your job is to go to the KDE developers and tell them that what they've been working on for all these years is trash, and persuade them to work on GNOME. Good luck.

[QUOTE=Snif]As for standarts i think they should be more noticeable and evident, i refer to web again - you can see W3C, CSS, useability etc. everywhere, so people notice it and get the idea.[/QUOTE]

The people who develop the software do have the idea. Nobody developing software for GNOME is unaware of the HIG. Nobody developing half decent software on any free desktop environment is unaware of the fd.o standards.

---

### Post by canceLinux on 2007-10-06
stable=is great..

standartization=fails..

because everybody wants different things here.. in linux.. :)

---

### Post by picpak on 2007-10-06
Seeing as how I'm in this thread, I gotta ask:

Why on earth do default GTK programs switch the YES and NO buttons??

Do you know how much unwanted software I've installed on the school computers because I expected the YES button to say NO???

It's really frustrating.

---

### Post by perce on 2007-10-07
> **picpak said:**
> 
Why on earth do default GTK programs switch the YES and NO buttons??

Do you know how much unwanted software I've installed on the school computers because I expected the YES button to say NO???



Maybe to make you read before clicking? ;)

---

### Post by toupeiro on 2007-10-07
> **Snif said:**
> 
Yes, MS doesn't follow the standarts, but at least they have one current version of OS and Apple too ) 

So i think there should be a major linux distro too. :)

Good lord, thats the last thing I want..  Hasn't the trend of the Microsoft desktop OS shown you what "A" major distribution is capable of doing .. or not doing?

If you want to talk about statistics, and you absolutely have to make a  "major" classification for linux distributors out there..  Redhat, Novell, and Canonical are the big three I can think of.  I'll take the option of three over the de-facto of one any friggin day!

btw..  Linux's kernel certification to classify it as stable is just as centralized as Microsoft or apple having a "current version of OS".  THe difference is you have three "major" companies striving to bring you the best OS around that kernel that can be brought.  I don't see that happening with NTOSKRNL processes or whatever they may have renamed it to in Vista or server 2008.  I just see regurgitated bloated code, overwhelming shininess, and underwhelming productivity.

The truth is, its not about distributors, major distributions or primarily about making money, its about collaboration.  Sun, Novell, Redhat, Canonical, IBM, and millions of people contribute to linux.  The distributions are made possible because you have such an array of choice.  Businesses will make the best choice for their business, and to transition to another distribution is not a difficult effort (I know because I've done it many times, from IRIX to Solaris to Redhat to Windows, to Ubuntu and back to Redhat again.  The ease of these transitions come from the same long standing standards I mentioned before.).  But linux should never be driven by one major distribution.  That would be a fatal blow to the innovation linux has to offer in this mans humble opinion.

---

### Post by koenn on 2007-10-07
> **Snif said:**
> 
Well maybe it's just a windows-based habit (because you may have more than one logical partition and sometimes there's not enough place on one so you put an app to another.  But sometimes it's useful to fix something in app's files so i'd rather have info about where they're stored.

Yes, it's a Windows habit.
On Linux, your file system covers all disks / partitions. In stead of C:\ D:\ E:\ ... you just have (computer);/ , no matter how many disks or partitions are below it. So you can add disks for additional space, but the paths to your files don't change. /home is still /home, /etc is still /etc, .. Very convenient.

As for 'fixing' apps : there configuration files (on Debian, ubuntu ..) are all under /etc. That's where you do the tweaking if you want do it manually.

---

### Post by picpak on 2007-10-07
> **perce said:**
> Maybe to make you read before clicking? ;)

Maybe to make you end up with hundreds of viruses, steering you clear from Windows and towards Linux?

BWAH HAHA!

---

### Post by 2cute4u on 2007-10-07
> **picpak said:**
> Seeing as how I'm in this thread, I gotta ask:

Why on earth do default GTK programs switch the YES and NO buttons??

Do you know how much unwanted software I've installed on the school computers because I expected the YES button to say NO???

It's really frustrating.

I find the way KDE/MS has it to be frustrating.  Having the Ok button on the right and the Cancel button on the left is what I grew up used to, and seems much more natural to me.  I wish that people would stop looking at the MS way of doing things as the right way.

---

