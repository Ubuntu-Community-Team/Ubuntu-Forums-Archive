---
title: "How is Slackware?"
date: 2010-02-24
forum: Recurring Discussions
---

### Post by gymophett on 2010-02-24
I've been looking at it lately, and I seem very interested.
Some people look down on it, and I haven't really seen the reasons why.

Is it worth trying? I probably will anyway, but is it any really tough configuring or anything?
I don't mind some configuring, but not a butt load.
So how good would you say Slackware is?
Pros and Cons?

---

### Post by kidux on 2010-02-24
Slackware was one of the best distros I've ever used. People look down on it because it's not bleeding edge, meaning the software is usually a version or 2 behind, at least when I used it, around 10.0. Also, there is a lot of compiling your own packages because it doesn't ship with a package manager like Ubuntu, though there is a manager you can get for it. A lot of packages can be got pre-built, but I don't remember the website rightnow. Overall, it's one of if not THE stablest distro out there.

---

### Post by aviedw on 2010-02-24
Lets just say slack isn't for slackers lol pun intended. Its like one of grand daddy distros around. I have not used it but from what i hear it requires above average knowledge of Linux in general and command line usage. I heard it doesnt start of with a GUI at all lol, and i heard that it doesn't use prepackaged programs like .deb or .rpm for example. Everything is from source and has to be compiled. Its considered a very stable system once its up and running. Im still trying to work my way up to lol, im such a chicken :)

---

### Post by Bachstelze on 2010-02-24
Slackware is the most KISS-compliant distro there is. Definitely a great learning experience, much more than Debian or Gentoo. Go for it.

@aviedw: What you've heard is wrong, stop spreading that BS.

---

### Post by gymophett on 2010-02-24
> **aviedw said:**
> Lets just say slack isn't for slackers lol pun intended. Its like one of grand daddy distros around. I have not used it but from what i hear it requires above average knowledge of Linux in general and command line usage. I heard it doesnt start of with a GUI at all lol, and i heard that it doesn't use prepackaged programs like .deb or .rpm for example. Everything is from source and has to be compiled. Its considered a very stable system once its up and running. Im still trying to work my way up to lol, im such a chicken :)

So it's pretty much like an Ubuntu or Debian minimal, or Arch?

I've used Arch a little while, and it doesn't have prepackaged programs, you have to either install from the package manager or from a dowloaded .tar.gz or whatever.
I love installing from .tar.gz, and it isn't hard at all.
Its mostly just navigating to the folder:
./configure
make
make install

And that's all. :)
I like using the terminal in general though.
Although I don't like having to install hal and everything and changing what starts up, it gets annoying (like in Arch)..

I am ALL for stable though. I used to be for bleeding edge, but a stable  fast system seems to win me overall.

---

### Post by gymophett on 2010-02-24
> **Bachstelze said:**
> Slackware is the most KISS-compliant distro there is. Definitely a great learning experience, much more than Debian or Gentoo. Go for it.

@aviedw: What you've heard is wrong, stop spreading that BS.

A greater learning experience than Gentoo? I may be misinformed about Gentoo. Never really searched into it.
I thought you could get an up and running system and GUI from the DVD.
Because it already has KDE and XFCE in it already.
I want Gnome though. :/
Guess I'll have to use this [http://gnomeslackbuild.org/](http://gnomeslackbuild.org/)

---

### Post by kidux on 2010-02-24
NVM, double posted...

---

### Post by aviedw on 2010-02-24
I cant really say because i haven't used either. But do you know if there is a huge benefit to compiling programs as apposed to getting them prepackaged?

But i do know that when they talk about the grand daddies of linux they usually include slackware, Debian and sometimes Red Hat usually ultra stable but not bleeding edge.

---

### Post by gymophett on 2010-02-24
> **aviedw said:**
> I cant really say because i haven't used either. But do you know if there is a huge benefit to compiling programs as apposed to getting them prepackaged?

But i do know that when they talk about the grand daddies of linux they usually include slackware, Debian and sometimes Red Hat usually ultra stable but not bleeding edge.

This should answer your question;)
[http://ubuntuforums.org/showthread.php?t=1088590](http://ubuntuforums.org/showthread.php?t=1088590)

But if you ever wanna try out a harder distro, I'll help you out. Even though, I probably wouldn't be much help. :P

---

### Post by kidux on 2010-02-24
> **aviedw said:**
> I cant really say because i haven't used either. But do you know if there is a huge benefit to compiling programs as apposed to getting them prepackaged?

But i do know that when they talk about the grand daddies of linux they usually include slackware, Debian and sometimes Red Hat usually ultra stable but not bleeding edge.

It requires more steps, but usually a compiled package is a bit better because it is designed specifically for the hardware in your machine. The hard part, at least when I used it, was tracking down dependencies because they aren't automatically downloaded and installed like distro with package managers.

---

### Post by Bachstelze on 2010-02-24
> **aviedw said:**
> I cant really say because i haven't used either. But do you know if there is a huge benefit to compiling programs as apposed to getting them prepackaged?

You're a funny guy, you know that? "I can't really say but I say it anyway." What is that "huge benefit" you speak of?

---

### Post by aviedw on 2010-02-24
Thanks a lot that link was very useful. Next time i should make use of the search button :) Now im trying to consider if i want a distro that requires compiling.

---

### Post by gymophett on 2010-02-24
> **kidux said:**
> It requires more steps, but usually a compiled package is a bit better because it is designed specifically for the hardware in your machine. The hard part, at least when I used it, was tracking down dependencies because they aren't automatically downloaded and installed like distro with package managers.

Agh! I hate that too.

Blank blank requires blank blank. Aborted.

But in Slackware, since it doesn't have it's own package manager, where will I get the packages?

> Now im trying to consider if i want a distro that requires compiling.

You can always start compiling your packages in your Ubuntu install just to get the feel of it.

---

### Post by guren on 2010-02-24
If you want to have a greater understanding on the bits and pieces of Linux. I'd say try it. You may also want to try Gentoo.

Installing it means configuring then compiling it from scratch. You'll get your hands dirty on kernel modules (figuring out what you need and when you want to load it). At some point, you may want to install your desktop environment (I was like "woahh fast" when I saw my freshly compiled gnome desktop). Then if you find yourself missing some modules/drivers/etc, you can always find your way back to the kernel and reconfigure it.

Basically, it's a really great experience.
Good luck and have fun! :popcorn:

---

### Post by aviedw on 2010-02-24
> **Bachstelze said:**
> You're a funny guy, you know that? "I can't really say but I say it anyway." What it that "huge benefit" you speak of?

I've heard the compiled programs run better for your individual system. Before i read that link i had a very vague understanding of compiling, and still dont know if its worth the time and effort. 

The reason i say this is because i have not done any compiling except for a screen saver (Electric Sheep) and my system runs fine and pretty fast for my needs. So i dont know what type of speed boost i would be looking at in conjunction with time and effort.

---

### Post by Bachstelze on 2010-02-24
> **gymophett said:**
> 
But in Slackware, since it doesn't have it's own package manager, where will I get the packages?

[ftp://ftp.lip6.fr/pub/linux/distributions/slackware/slackware-13.0/slackware/](ftp://ftp.lip6.fr/pub/linux/distributions/slackware/slackware-13.0/slackware/)

There is normally a package browsing page, but it is broken right now, so you have to browse through them directly on the mirrors.

---

### Post by Bachstelze on 2010-02-24
> **aviedw said:**
> I've heard the compiled programs run better for your individual system.

"I've heard", "I've heard", "I've heard"...

---

### Post by Zoot7 on 2010-02-24
Slackware is extremely stable and bug free, more so than most other distros. The problem is that because of it's conservative approach to design, there's little enough in the repos so I rather compile most stuff from source myself on it. It takes a long time to set up but it's very nippy and stable once done so.

> **aviedw said:**
> i heard that it doesn't use prepackaged programs like .deb or .rpm for example. Everything is from source and has to be compiled.
Slackware does indeed have a package manager, the difference is that it doesn't manage *dependencies* for you, which is both good and bad at the same time.

---

### Post by nmccrina on 2010-02-24
You can always try it in a VM or by dual-booting or something, to see how easy it would be to get to a semi-usable Gnome environment.

I've installed it before, but I came back to Ubuntu. It was the same deal as Arch: it started out uber minimal, but by the time I got all the stuff I needed installed and configured (a week later), it was basically a default Ubuntu or Fedora install that I could have done in 20 minutes. I think the main application for the Slackwares and Arches of the world (more so for slackware, though) is on a server where package management isn't a priority, or on a second computer to fiddle around with in spare time.

---

### Post by Zoot7 on 2010-02-24
> **nmccrina said:**
> You can always try it in a VM or by dual-booting or something, to see how easy it would be to get to a semi-usable Gnome environment.
Slackware doesn't use Gnome, rather Xfce and KDE. 

However you could look **[HERE]("http://gnomeslackbuild.org/")** if you want to check out Gnome on Slackware.

---

### Post by gymophett on 2010-02-24
> **nmccrina said:**
> You can always try it in a VM or by dual-booting or something, to see how easy it would be to get to a semi-usable Gnome environment.

I've installed it before, but I came back to Ubuntu. It was the same deal as Arch: it started out uber minimal, but by the time I got all the stuff I needed installed and configured (a week later), it was basically a default Ubuntu or Fedora install that I could have done in 20 minutes. I think the main application for the Slackwares and Arches of the world (more so for slackware, though) is on a server where package management isn't a priority, or on a second computer to fiddle around with in spare time.

Would I be better just doing Debian stable minimal install then?

I mean, I guess I could just try them all.
I've got a Paldo, Mandriva, Slackware, Mepis, and PCLinuxOS cd I still haven't tried. xD

---

### Post by nmccrina on 2010-02-24
> **Zoot7 said:**
> Slackware doesn't use Gnome, rather Xfce and KDE. 

However you could look **[HERE]("http://gnomeslackbuild.org/")** if you want to check out Gnome on Slackware.

Well, the OP expressed an interest in GNOME which was why I mentioned it, but yeah I didn't know that there wasn't an official package for it anyway. :o I just used the default KDE when I tried it.

---

### Post by Bachstelze on 2010-02-24
> **gymophett said:**
> Would I be better just doing Debian stable minimal install then?


It really depends what you want to do. Slackware doesn't hold your hand *at all* so it will make for a better learning experience, but will require more work on your part. Debian on the other hand had debconf and all kinds of stuff that make your life easier, at the expense of simplicity.

Ask yourself what you want to do, and use what works best for that. ;) Slackware, once properly set up, is really rock-stable (much more so than even Debian stable), and therefore makes a good system for everyday use (you don't have to worry about an update breaking everything, for example).

EDIT: and yes, no Gnome. Anyone who has ever tried to compile Gnome from source knows that it is hell. Slackmare aims to be KISS-compliant. Gnome is not.

---

### Post by nmccrina on 2010-02-24
> **gymophett said:**
> Would I be better just doing Debian stable minimal install then?

I mean, I guess I could just try them all.
I've got a Paldo, Mandriva, Slackware, Mepis, and PCLinuxOS cd I still haven't tried. xD

Well, is this something you want to explore and experiment with and potentially break, or use in the long-term? If the latter I *personally* would go with the Debian (among those options), but if you are just out to have fun and learn (and you don't mind occasionally not being able to write a paper or do a project for school or work because your xorg is broke or the wireless doesn't work), go ahead and install everything in turn and see what you like!

Sorry for my clumsy sentences, it's 4:00 AM here. I've been doing homework all night. :(

---

### Post by Bachstelze on 2010-02-24
> **nmccrina said:**
> Well, is this something you want to explore and experiment with and potentially break, or use in the long-term? If the latter I *personally* would go with the Debian (among those options), but if you are just out to have fun and learn (and you don't mind not being able to write a paper or do a project for school or work because your xorg is broke or the wireless doesn't work), go ahead and install everything in turn and see what you like!

Eh? The odds of getting a broken Xorg or wireless because of an update are no greater in Slackware than in Debian.

---

### Post by nmccrina on 2010-02-24
> **Bachstelze said:**
> Eh? The odds of getting a broken Xorg or wireless because of an update are no greater in Slackware than in Debian.

Well, just from personal experience. There's been situations where I needed to go online and download an assignment in .pdf format, but oh great the only OS currently on my computer is the CLI Arch install that I've been trying to get the wpa_supplicant working with. It happens. :)

---

### Post by Bachstelze on 2010-02-24
> **nmccrina said:**
> Well, just from personal experience. There's been situations where I needed to go online and download an assignment in .pdf format, but oh great the only OS currently on my computer is the CLI Arch install that I've been trying to get the wpa_supplicant working with. It happens. :)

Oh, yes. Of course, if you're in the middle of installing an OS, things won't work as expected. ;) What I meant was that if he wants a system with long-term stability, Slackware is at least as good as Debian.

---

### Post by nmccrina on 2010-02-24
> **Bachstelze said:**
> Oh, yes. Of course, if you're in the middle of installing an OS, things won't work as expected. ;) What I meant was that if he wants a system with long-term stability, Slackware is at least as good as Debian.

I can't deny or confirm that, I've never stuck with any distro more than about 2 weeks in a row. :D

---

### Post by gymophett on 2010-02-24
> **nmccrina said:**
> Well, is this something you want to explore and experiment with and potentially break, or use in the long-term? If the latter I *personally* would go with the Debian (among those options), but if you are just out to have fun and learn (and you don't mind occasionally not being able to write a paper or do a project for school or work because your xorg is broke or the wireless doesn't work), go ahead and install everything in turn and see what you like!

Sorry for my clumsy sentences, it's 4:00 AM here. I've been doing homework all night. :(

It's okay. I think I'll go with Debian stable for now, and try out Slackware in VB.

It's 4 AM here too! :P

---

### Post by ~sHyLoCk~ on 2010-02-24
Slackware lacks contributors. If it had same user-base and contributors like Arch does it would be within top 10 atleast in DistroWatch , always and not just during a release a year or so! That said, I'm an Archer and a Slacker. Though I prefer Arch more these days coz of ArchBang. ;-)

---

### Post by blueshiftoverwatch on 2010-02-24
> **gymophett said:**
> I love installing from .tar.gz, and it isn't hard at all.
Its mostly just navigating to the folder:
./configure
make
make install

And that's all. :)
I usually get hung up during the ./configure stage where one of the following happens:
- I'm told to install some obscure dependency or a dependency but aren't given the exact name of what to look for
- I look around to find out that I already have the dependency installed, sometimes even the same or greater version
- I am forced to choose between overriding my existing dependency with one that is third party, getting the app to work, but possibly causing dependency issues in the future because of it. Or giving up on getting the app to work.

Although, I've heard that Slackware is a lot better at detecting if you already have X dependency installed than Ubuntu.
> **aviedw said:**
> I've heard the compiled programs run better for your individual system. Before i read that link i had a very vague understanding of compiling, and still dont know if its worth the time and effort...i dont know what type of speed boost i would be looking at in conjunction with time and effort.
The faster your system is the less worth while it probably is. I remember reading threads where people would say how they spent 3 hours compiling Gnome and people would just respond "well, I hope you enjoy that half a second faster loading time".

---

### Post by Tibuda on 2010-02-24
> **gymophett said:**
> I've used Arch a little while, and it doesn't have prepackaged programs, you have to either install from the package manager or from a dowloaded .tar.gz or whatever.
I love installing from .tar.gz, and it isn't hard at all.
Its mostly just navigating to the folder:
./configure
make
make install

What? Arch does have prepackaged programs, that's what you download with pacman! And when compiling from source in Arch, you better use PKGBUILDs instead of configure/make/makeinstall to let pacman handle it.

---

### Post by sh4d0w808 on 2010-02-24
I will be a completely newbie in Slackware, so I've also started to read slack documentation. It is recommended to install all packages within 13.0, then you will have all the necessary tools and dependent softwares to compile from tgz format.

Later you can delete those you won't need.

---

### Post by koshatnik on 2010-02-24
> **gymophett said:**
> I've been looking at it lately, and I seem very interested.
Some people look down on it, and I haven't really seen the reasons why.

Is it worth trying? I probably will anyway, but is it any really tough configuring or anything?
I don't mind some configuring, but not a butt load.
So how good would you say Slackware is?
Pros and Cons?

Its awesome, but requires effort. Its the fastest and most stable linux distro I have ever used, and I've used alot. Personal opinion, nothing more. I havent conducted scientific tests on that or anything.

I love slackware, and I think Patrick is awesome for the work he does on it.

---

### Post by MisfitI38 on 2010-02-24
> **gymophett said:**
> I've been looking at it lately, and I seem very interested.
Some people look down on it, and I haven't really seen the reasons why.

Is it worth trying? I probably will anyway, but is it any really tough configuring or anything?
I don't mind some configuring, but not a butt load.
So how good would you say Slackware is?
Pros and Cons?

The mighty Slackware!
Slackware is for people who want to interact more directly with their OS. Ubuntu is a bit more designed for people who believe an OS should be a means to an end; to run applications.
There are always exceptions but I believe that most would agree.

In order to get a working and functional Slack desktop, you will have to grab from various sources for things like multimedia. So, by the time you are done setting it up you will know if you like it or not.
Have fun!

---

### Post by gymophett on 2010-02-24
Soo. In about 30 minutes, I'm gonna install it in VirtualBox just to make sure it isn't too hard, and I'll know what to expect. After that, I'm gonna install the real deal. 

Wish me luck. :popcorn:

---

### Post by witeshark17 on 2010-02-24
I'm sure it'll be mostly fun! :popcorn:

---

### Post by gymophett on 2010-02-24
> **witeshark17 said:**
> I'm sure it'll be mostly fun! :popcorn:

I sure hope so. I'm a little nervous. I don't know why. xD

---

### Post by gymophett on 2010-02-25
I just installed Slackware v13.0!!
:D
The install was actually extremely easy. No configuring or anything. Now, I just need to install my graphics card and things will be great!

---

### Post by andrew.46 on 2010-02-26
Hi gymophett,

> **gymophett said:**
> But in Slackware, since it doesn't have it's own package manager, where will I get the packages?

Once you have started using slackware you will be able to see for yourself that there are many myths and legends associated with slackware, this being one of them :). Slackware has a very solid package management system, look for pkgtool, installpkg, removepkg and explodepkg. The great source for third part build scripts for slackware is here:

Slackbuilds.org
[http://www.slackbuilds.org/](http://www.slackbuilds.org/)

Where if you look for mkvtoolnix, libmatroska, libebml and leafnode you will see some of my own work :).

Andrew

---

### Post by beetleman64 on 2010-02-27
If your have the time, patience and substantial skill to configure Slackware properly then you'll love it. However, you do need to be a bit of a Linux/UNIX expert to do that, it's really hard to master.

---

### Post by |{urse on 2010-02-27
Oh thats a fun one to install and config. But you'll learn so much about linux that you might as well have mastered every distro lol.

---

