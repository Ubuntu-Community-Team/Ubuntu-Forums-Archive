---
title: "Breakout Linux - Developers, designers wanted to develop blueprint for new distro"
date: 2008-10-04
forum: Other OS Talk
---

### Post by jrothwell97 on 2008-10-04
Hello all,

I'm looking to gather together some developers and UI designers to help formulate a plan for a new Linux distribution, which I'm tentatively naming Breakout Linux. I've had the idea for this distribution swimming about in my head for the last few months or so: the idea is to build the distribution from scratch, and te build it from the ground up with inexperienced users in mind. This means abandoning the FHS file hierarchy (at least from the user's perspective), more helpful error messages, and probably a new desktop environment too. The idea is to make it the FLOSS operating system for the rest of us: the entire system should be GUI driven, simple, intuitive, and also quite pretty (to provide another 'pull' factor for Windows users).

Just to be clear, I'm not recommending planning to start actual code development immediately. The project will be quite a while in gestation, as I want to make *absolutely sure* that this distribution, when it appears, will work flawlessly and beautifully for almost anyone. (It's also to allow time to arrange hosting, planning and initial experimentation.)

If you're interested or would like to help, please reply to this thread, send me an e-mail (my address is available scattered around my web sites), or join me in the IRC channel #breakout at Freenode. (I'll sort out a temporary website for the project, probably at breakout.jonathan-rothwell.co.uk, when I can.)

Many thanks,

Jonathan Rothwell

---

### Post by SomeGuyDude on 2008-10-05
What's your philosophy for it? Are you planning on a user-friendly distro like Mandriva, or a build-it-yourself deal like Arch? Who's your target user, the newbie or the veteran? Will it take advantage of newer machines or run on ancient hardware?

I'm no dev, but I think outlining your ambitions is a good idea to get people on board.

---

### Post by jrothwell97 on 2008-10-05
> **SomeGuyDude said:**
> What's your philosophy for it? Are you planning on a user-friendly distro like Mandriva, or a build-it-yourself deal like Arch? Who's your target user, the newbie or the veteran? Will it take advantage of newer machines or run on ancient hardware?

I'm no dev, but I think outlining your ambitions is a good idea to get people on board.

The target user is the complete newbie. The idea is to give her a reason to switch to Linux (fast, pretty, stable and free) whilst simultaneously dispelling the myth that Linux is for men with lab coats and genetically-modified mice living in their pocket.

In a nutshell, the user should never, EVER have to touch the command line. Neither should they have to encounter FHS, or be told by support forums, etc to STFW. Things should be obvious and intuitive so that new users can sniff their way around their computer.

Distilled to technical points, what I'd like to achieve is:
[list][*]A new desktop environment, which is familiar to Windows/OS X users, pretty and functional
[*]A file hierarchy different to FHS, with a distinction between end-user apps such as Firefox and system utilities such as bash, ls, et cetera. This will, as a result, probably also mean drag-and-drop application installation, Mac OS X-style
[*]An automatic update framework in the style of Sparkle OS X)
[*]Helper applications to find restricted drivers, display EULAs, and then download them
[*]System packages such as the kernel, bash, etc managed by a version of, say, apt or yum, modified to use BitTorrent for downloading packages
[*]Error messages that mean something to the novice user. e.g. instead of "operation failed, are you root?" it may say "this operation has failed as you do not have the access rights to do so: (click here) to authenticate as the superuser." The idea being to make things less cryptic for first-time users.
[*]With regard to target machines, in my opinion the distro should run *just fine* on older (early 2000s) machines, but also be able to take advantage of the machines of tomorrow (multi-threading, compositing using OpenGL, etc.)
[*]Ultimately, it must also have the 'wow' factor. People should look at it and think "my god, this lets me do things better than I ever thought was possible."[/list]

I hope that's answered a few of your questions - any more, please feel free to ask.

---

### Post by cmay on 2008-10-05
[http://www.dreamlinux.com.br/](http://www.dreamlinux.com.br/)

this is a linux distro that looks like a mac. its newbie freindly as well. it looks nice too :)
i would translate and run beta test at anytime if you get a linux distro up and running.
but this goal of having more newbie freindly linux distributions is already done many times.
there is linux mint that does make it easy with codecs as they  are already installed and  the asus eee pc with xandrox is also so easy and intuitive that it is as a matter of my point of wiew only a question about new design as how the overall look and feeling of the new distro that makes a different distro .as i feel  the most user freindly operative system i have tried up to now is ubuntu i would say these goals about making a newbie freindly linux should be about having  more education instead of trying to make linux into something windows users can relate to. i support newbie freindly distros very much but i do not support the idea of having users never touch the commandline or having them run as  root per default for the sake of  newbies feeling like they are on a free version of windows. they are not. i have not seen any linux distro yet that uses drive letters c:\ as a means to please the newcomers and other than that i think there is already so much done in that area that if you want a new linux with these goals then its maybe a new customized ubuntu as the best choice.  i see the future will be more linux on small laptops preinstalled from factory and i think these will be handled the way your project aims. you cant compete with that. the introduction to bsd for me was desktop bsd. then freebsd. i have a open bsd boxset i am goin to install tonight. i admit with out the desktop bsd which  is just as easy to install as ubuntu i would never have learned about bsd simply becouse its harder to install than linux. so the idea of having a linux starter edition is good. as i said if you get it up and running i promise to test it and maybe translate a few things. there are many translations done in danish from other distros you can use but if you feel the messages that are giving to the user in most distros are not understandable enough i would suggest that you get more done in the area of documentation. and a few rewrites of already existing translations. i think some of the danish translations is too weird so i use the default us language settings. 

i sincerely hope this could be of any use to you as its just a matter of my opinion. and good luck to you. if any thing i have written needs explaining or rephrasing please let me know. i am not using my native language. 
regards cmay.

---

### Post by smoker on 2008-10-05
> **jrothwell97 said:**
> The target user is the complete newbie. The idea is to give her a reason to switch to Linux (fast, pretty, stable and free) whilst simultaneously dispelling the myth that Linux is for men with lab coats and genetically-modified mice living in their pocket.

In a nutshell, the user should never, EVER have to touch the command line. Neither should they have to encounter FHS, or be told by support forums, etc to STFW. Things should be obvious and intuitive so that new users can sniff their way around their computer.

good luck with this project, i look forward to seeing it progress :)

---

### Post by Sorivenul on 2008-10-06
I'm definitely interested in a well planned, thought out distribution along these lines.  I have plenty of ideas and some programming experience I'm willing to contribute.  

The question of the distribution's philosophy is a major one, and I'm glad it has already been raised - this to me is both the base and final goal of any good system.  

As for abandoning the FHS standard, I'm not sure this a good idea.  From a new user standpoint I understand it can be offputting.  However, if the plan is to allow the user to "never" use the command line, it shouldn't matter - I don't know a user that graphically navigates to /bin to launch a program if it's available in their menu.  Also on this note, after some time with this hierarchy any other seems unintuitive, so it may be worthwhile to consider this issue from the perspective of current Linux users looking for a switch as well.  I know that Gobo Linux uses an alternative hierarchy, and it may be worthwhile for you to investigate on this front.

As far as error messages go, what do you mean?  Are you talking messages from the system itself, or from specific applications?  The first, IMO, would be "easier" in that it would be less time consuming than manually changing the error output of 100's of 1000's of programs.

A new DE is ambitious project in and of itself.  An attractive KDE theme may be a simple solution, especially in early stages of development.  It's shiny, it's intuitive, it has loads of "native" applications that fill most of the average user's needs.  

I'll write more later, but it is time for rest for now.

---

### Post by jrothwell97 on 2008-10-06
[quote="Sorivenul"]As for abandoning the FHS standard, I'm not sure this a good idea. From a new user standpoint I understand it can be offputting. However, if the plan is to allow the user to "never" use the command line, it shouldn't matter - I don't know a user that graphically navigates to /bin to launch a program if it's available in their menu. Also on this note, after some time with this hierarchy any other seems unintuitive, so it may be worthwhile to consider this issue from the perspective of current Linux users looking for a switch as well. I know that Gobo Linux uses an alternative hierarchy, and it may be worthwhile for you to investigate on this front.[/quote]

Thanks for your comment. Abandoning the FHS standard will, I know, upset many power users who've taken the time to learn the esoteric inner workings of the system. It seems to me there are two possible courses of action.

The first would be to mimic GoboLinux, and hide FHS from the user (using symlinks to allow him to access the system's innards). However, I can see the problem that there's no distinction between end-user apps and system binaries.

I'm gravitating towards a more OS X style approach - hide FHS, but let root-capable users see it in the terminal, and if the folder's names are explicitly given to the Finder.

With regards to your other concerns, the DE will probably be the last thing to go on. Theming GNOME, KDE or Xfce as a stopgap is what will probably happen, so thanks for your comments.

---

### Post by cammin on 2008-10-07
> **jrothwell97 said:**
> Thanks for your comment. Abandoning the FHS standard will, I know, upset many power users who've taken the time to learn the esoteric inner workings of the system.

So what are your plans for the new file system layout?

---

### Post by jrothwell97 on 2008-10-07
> **cammin said:**
> So what are your plans for the new file system layout?
The idea is to perhaps hide FHS, and create a system that appears to the user as something along the lines of:

/apps
/home
/libraries
/public
/system

Of course, you can help refine the idea, as a [forum is now open]("http://breakout.jonathan-rothwell.co.uk/")! Please feel free to register and start posting in with any ideas you have.

---

### Post by ryclegman on 2008-10-07
Hello,

As a Borderless Linux leader I agree and like your ideas.  The Borderless Linux team is also trying to do some of the things you mentioned. We are trying to make it user friendly, and easy. If you need anything you can PM me and i can help.. We do have a alpha out, but its just a plain old distro based off Debian. We have an Alpha 6 out that its completely themed etc. , but have yet to post it for download. You can see what it looks like at [http://www.borderlesslinux.cchskid.com/Screenshots.html](http://www.borderlesslinux.cchskid.com/Screenshots.html) .... 


Good luck

Ryclegman

---

### Post by mp3_freak_721 on 2008-10-08
I like the idea of this os, but I am not a programmer nor I am good at design. Can I still help out? I already registered at the forums. I would guess that would be the first step in helping out.

---

### Post by Ayuthia on 2008-10-08
> **jrothwell97 said:**
> Thanks for your comment. Abandoning the FHS standard will, I know, upset many power users who've taken the time to learn the esoteric inner workings of the system.
I am not for sure if it would upset the power users or not, but if you do this, you are then planning to rewrite every single linux program that is currently available in some way.  Also, you could also prevent people from easily using the vanilla kernels.

If you change the file structure that is currently being used in Linux, wouldn't almost all the source code makefiles will have to be modified in some way?  When the 'make install' is done, they will go to the directories based on the current file stucture (this includes the kernel).

I am not for sure if I fully understand your reasoning for abandoning the current file structure.  Most basic users will avoid going to a terminal prompt.  I would think that they could care less about the file structure.  They just want a good package manager, working applications, good documentation when they need help, and some easy way to configure applications.  If this is the goal of this OS, then the file structure does not have to change, it is the tools that need to be changed.

One other opinion, using BitTorrent might not be the best way to manage packages.  How would you be able to verify that the source is always going to be valid?  I don't know too much about torrents, but if there are no controls on where the files can be, there will always be people out there that will try to mess up a file just to make the OS look bad.

---

### Post by smartboyathome on 2008-10-09
Just to let you know, you will want to apply the Gobolinux patch first thing and compile it in the folder you will use. Set up your symlinks early so that nothing freaks out when you do symlink it. I tried symlinking Ubuntu and Arch Linux using Gobohide to hide the symlinks, and on both it kernel paniced because the kernel wasn't where it thought it would be.

Also, I would recommend you build this with Linux from Scratch, and then build a package system based off your favorite (I like both Debian and Pacman, though others work as well) if one doesn't suit your needs. I would recommend (if you really want to make the package management organized) to modify the package managers you want to use so that people who compile packages as described in [section 6.3.2.3 of the LFS docs]("http://www.linuxfromscratch.org/lfs/view/development/chapter06/pkgmgt.html") in order to keep each application in its own directory while symlinking it to /usr. Perhaps a combination of 6.3.2.3 and 6.3.2.6 on the aforementioned link.

Don't build your own DE/WM, though. Instead go with a proven one like GNOME, KDE, XFCE, even LXDE, and just modify it so that it works for you. Creating your own will be way too much work and uptake which I am not a fan of.

Those are my tips for now, I may come up with some more later. I hope you take them into consideration.
Smartboy

EDIT: More ideas.

Instead of using the traditional tar.gz for compressing the packages, why not use tar.lzma? It has fast decompression times and high compression rates, with the only downside being it can take a while to compress stuff. It has been used by 7zip for a while (which many people like), but tar is also able to use it since version 1.20.

Instead of the folders you suggested, I suggest that they be something like this:
/Users
/System
   ./Applications
   ./Libraries
   ./Include
   ./Configuration
   ./Boot
      ./Kernel
   ./Media
   ./.OldStructure
With this folder structure, the System directory is hardly noticeable, but is not hidden from the user (which can confuse new users when, for example, they want to install a theme globally so that they can have themes applied to their package manager). The user would most of the time stay in the /Users directory, so hiding the System directory would just be an added disadvantage imo. The System directory would house all the system files, including the Applications (symlinked like in 6.3.2.3 above), Libraries, Configuration (maybe just a symlink from /etc to it), Boot (which would hold Grub and the kernel, as they are both used on boot), and Media (which would hold all the mounted media such as other partitions, CDs, USB flash drives, etc). Other folders included are self explanitory. In addition, a hidden .OldStructure folder would be there to serve as the old /usr folder with all the symlinks to the other folders. It would be messy with all those symlinks, but I think its better to hide this one folder because it is essentially useless.

---

### Post by Changturkey on 2008-10-09
A open-source Mac OS X clone would be cool.

---

### Post by smartboyathome on 2008-10-09
> **Changturkey said:**
> A open-source Mac OS X clone would be cool.

It'd also be very likely to be sued and shut down. ;)

---

### Post by Changturkey on 2008-10-10
> **smartboyathome said:**
> It'd also be very likely to be sued and shut down. ;)

Well not a full on bit-for-bit clone. I was thinking more of a spiritual or conceptual clone.

---

### Post by smartboyathome on 2008-10-10
> **Changturkey said:**
> Well mot a full on, bit for bit clone. I was thinking more of a spiritual or conceptual clone.

Yep, they did create a good concept for a file system, thats for sure. :)

---

### Post by techmarks on 2008-10-11
I'd would be nice, a Mac OS X inspired desktop for Unix.

I'd even be willing to put in work on it, but it would only interest me to do it for a BSD OS, like FreeBSD.

Only because FreeBSD does need a nice lightweight desktop environment. Linux already has so many distro projects going on.

PCBSD is a step in that direction, but unfortunately they chose KDE for their desktop.

The idea of creating a desktop where a user would never need to deal with any command lines, (unless he wants to) A completely graphical system that would still be faithful to the Unix development philosophies is an interesting challenge, and I think it could be done.

---

### Post by smartboyathome on 2008-10-11
> **techmarks said:**
> I'd would be nice, a Mac OS X inspired desktop for Unix.

I'd even be willing to put in work on it, but it would only interest me to do it for a BSD OS, like FreeBSD.

Only because FreeBSD does need a nice lightweight desktop environment. Linux already has so many distro projects going on.

PCBSD is a step in that direction, but unfortunately they chose KDE for their desktop.

The idea of creating a desktop where a user would never need to deal with any command lines, (unless he wants to) A completely graphical system that would still be faithful to the Unix development philosophies is an interesting challenge, and I think it could be done.

Technically, BSD can use all of the DEs that Linux can, a lot of the programs developed for Linux just need very few modifications in order to run on other Unix based OSes.

---

### Post by jrothwell97 on 2008-10-11
Thanks for all the ideas!

A BSD-based fork is something I may consider in the future, but at the moment, let's not run before we can walk.

The system will almost certainly, when built, be based on instructions from *LFS* et al. ScratchLinux (a prebuilt LFS system) might be an option for experimentation in the short term (particularly as I had originally planned to call the new distro Scratch Linux), but the final system, by the time of the first release, should have (from the ground up) a kernel, GNU (or BSD) userland tools, X, a DE in some form or another (but *not* KDE) and a complement of software bundled in a new application framework (like OS X and GNUstep's).

In other news, there's now a [thread open where you can suggest features that certainly *will* go into the first release.](http://breakout.jonathan-rothwell.co.uk/topic.php?id=4) Please do suggest anything you think would be good: all suggestions are welcome.

---

