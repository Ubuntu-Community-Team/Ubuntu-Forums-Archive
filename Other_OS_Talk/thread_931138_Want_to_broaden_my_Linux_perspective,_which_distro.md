---
title: "Want to broaden my Linux perspective, which distro do you reccomend?"
date: 2008-09-26
forum: Other OS Talk
---

### Post by Eion on 2008-09-26
I've been very happy with Ubuntu for a while now, and have no intentions of stopping use right now, I just think it would be good to explore other areas of Linux.  I'm leaning toward trying out Debain, just because it's very similar (as far as I know) to Ubuntu.  My question to you is, do you think this is a good choice, and if so, are there any guides for partitioning your hard drive so I can install and play around w/ my new setup but keep my Ubuntu setup?  And if not, what distro would you recommend?

Thanks already :)

---

### Post by cardinals_fan on 2008-09-26
Slackware will teach you a ton about Linux.  It's a great learning experience, and you might just keep on using it (I have).

---

### Post by Eion on 2008-09-26
I also forgot to mention, I'd like to give KDE a try as well, I've been using Gnome so far, is Slackware easy to setup?  I've only had experience w/ the Ubuntu auto install.

---

### Post by smartboyathome on 2008-09-26
If you are looking to broaden your Linux perspective in gradual steps, then I would say try Arch. You have to build it yourself after the core command line system is built, which teaches you partially how Linux works.

Then, I would go Linux From Scratch, which makes you build your own linux system completely from scratch. It teaches you the inner workings of Linux which you can't get from any other distro.

---

### Post by cardinals_fan on 2008-09-26
> **Eion said:**
> I also forgot to mention, I'd like to give KDE a try as well, I've been using Gnome so far, is Slackware easy to setup?  I've only had experience w/ the Ubuntu auto install.
Slackware is a manual distro.  If you're new, you might want to do Zenwalk or Vector first.  They are both based off Slack, but automate things to help you out.  Of course, that means you won't learn as much, but I wouldn't install Slack without some CLI experience.

Arch is also worth a look.  It makes you set up the system manually, but provides automated packaging tools to help make setup quick and easy.

---

### Post by Eion on 2008-09-26
Yea, I dont think I'm ready to go the "compile my own" route yet.  I'm checking out Slack right now, and prolly will do Zenwalk or Vector if I go that route, as I prolly need all the help I can get. btw what is CLI?

EDIT: Zenwalk looks really neat :D

---

### Post by cardinals_fan on 2008-09-27
> **Eion said:**
> Yea, I dont think I'm ready to go the "compile my own" route yet.  I'm checking out Slack right now, and prolly will do Zenwalk or Vector if I go that route, as I prolly need all the help I can get. btw what is CLI?

EDIT: Zenwalk looks really neat :D
CLI == Command Line Interface.

Slackware does **not** require compiling (it uses binary packages).  However, it does require manual configuration and some knowledge (or plenty of willingness to learn).

---

### Post by Eion on 2008-09-27
Well, My experience w/ command line is pretty much limited to installing apps, or closely following tutorials.

So, what does "manual configuration" mean? :D  I'm plenty willing to learn, but I don't want it to be totally an episode in futility.

---

### Post by cardinals_fan on 2008-09-27
> **Eion said:**
> 
So, what does "manual configuration" mean? :D  I'm plenty willing to learn, but I don't want it to be totally an episode in futility.
Editing config files, solving your own problems, setting up hardware manually (no Restricted Drivers Manager), etc.  In other words, learning about the guts of your system.

I don't mean to scare you away from Slack - it's my favorite distro.  However, you should be prepared before jumping in.  A good way to start is by using a Slackware-based system like Vector, Zenwalk, or SLAX (a live CD).

Arch also makes you do things manually, but it provides a certain degree of automation that can take away some of the sting.

---

### Post by david_lynch on 2008-09-27
kde on suse is a nice alternative perspective - as for editing config files, you can do that now on ubuntu server.

---

### Post by geogur on 2008-09-27
have you thought of fedora they are worth looking at i run ubuntu/zandros/fedora right now ubuntu pc / zandros laptop / fedora laptop . like them all they are linux distros that work well .

---

### Post by Eion on 2008-09-27
The one thing that jumps out at me there "setting up hardware manually" . . .  I think I might give Zenwalk a shot though.
I

---

### Post by cardinals_fan on 2008-09-27
> **geogur said:**
> have you thought of fedora they are worth looking at i run ubuntu/zandros/fedora right now ubuntu pc / zandros laptop / fedora laptop . like them all they are linux distros that work well .
I always wanted to like Fedora, but ended up with too many hardware issues.
> **Eion said:**
> The one thing that jumps out at me there "setting up hardware manually" . . .  I think I might give Zenwalk a shot though.
I
Zenwalk is pretty easy and would give you a good taste of something different.  The Zenwalk Forums are also very helpful.

---

### Post by Eion on 2008-09-27
Fedora is somewhat like Redhat right?  And SuSe is part of Novell, or something like that?

I'm downloading the ISO for Zenwalk right now though, give that a shot.  Any tips on setting up partitions?  I'm guessing it doesn't have the auto partition manager like Ubuntu does.

---

### Post by cardinals_fan on 2008-09-27
> **Eion said:**
> Fedora is somewhat like Redhat right?  And SuSe is part of Novell, or something like that?

I'm downloading the ISO for Zenwalk right now though, give that a shot.  Any tips on setting up partitions?  I'm guessing it doesn't have the auto partition manager like Ubuntu does.
The main Zenwalk installer uses cfdisk, a sensible command line partitioner.  However, if you download the live CD, you can install with a GUI installer/partitioner.

---

### Post by Artemis3 on 2008-09-27
IMO [gentoo](http://www.gentoo.org/) is a good learning experience, also [Freebsd](http://www.freebsd.org/) to go beyond linux.

---

### Post by Eion on 2008-09-27
So, would that be the "Live Edition" as opposed to the "Standard" editon?

---

### Post by cardinals_fan on 2008-09-27
> **Eion said:**
> So, would that be the "Live Edition" as opposed to the "Standard" editon?
Yes.

---

### Post by Eion on 2008-09-27
Much thanks :D

---

### Post by mips on 2008-09-27
> **Eion said:**
> I also forgot to mention, I'd like to give KDE a try as well,

In that case I would recommend Arch + KDEmod.

---

### Post by K.Mandla on 2008-09-27
Moved to Other OS Talk.

For what it's worth, even just one attempt at installing something source-based can be immensely educational. For the shortcut through that forest, you might want to try something that starts only with a console, and builds up. Arch is a good idea there.

---

### Post by basenvironment on 2008-09-27
I would suggest debian. It can be anything you make it. You are free to do things manually but there is usually tools to help do thing in case you get stuck. The cool thing is you can run debian and still have so many choices.
stable
stable with newer kernel
testing
testing mixed with unstable
unstable
unstable mixed with experimental
and any of those can be a minimal install, middle of the road install, slam dunk bloated install
and any of them can be gnome, kde, xfce, or any combination of those and many other DE/WMs
and I can easily compile from source if I wish
or even grab cool stuff from other debian-compatible distros

hard to beat IMO!

---

### Post by Sorivenul on 2008-09-27
I would agree with the suggestions of Slackware or Arch for learning without jumping off the deep end.  They require manual configuration, which is a great next step in the Linux journey.  

I would stay away from Gentoo for a while until they get their issues sorted out, as it appears they may be going to a true rolling-release system, causing delays in development.  

For a nice KDE experience I agree with Arch + KDEmod, but must also mention Pardus, which includes 3.5.10 by default and KDE4 is available in the repositories.  Pardus also has an alternative package management system for you to learn, and depending on your preferences requires some manual setup still.  You won't learn as much from Pardus as Slackware or Arch, probably, however.

Good luck!

---

### Post by Eion on 2008-09-27
Well, I havent installed Zenwalk yet, got too late last night.  But I think I might have a look at Arch too, but don't you have to semi-complie that one?  And if so, is that reasonable if you have limited CLI experience?

EDIT: So, Arch looks like total awesome :D  I'm reading the ArchWiki Beginners Guide and I think I could make it through that install with a printed copy by my side.  I'm going to see what I need to do to partition my drive so I can keep ubuntu and then get started on Arch.  Thanks to everybody :D, and btw I'll still prolly end up exploring Slack and others after this, so thanks for all the input.

---

### Post by smartboyathome on 2008-09-27
> **Eion said:**
> Well, I havent installed Zenwalk yet, got too late last night.  But I think I might have a look at Arch too, but don't you have to semi-complie that one?  And if so, is that reasonable if you have limited CLI experience?

EDIT: So, Arch looks like total awesome :D  I'm reading the ArchWiki Beginners Guide and I think I could make it through that install with a printed copy by my side.  I'm going to see what I need to do to partition my drive so I can keep ubuntu and then get started on Arch.  Thanks to everybody :D, and btw I'll still prolly end up exploring Slack and others after this, so thanks for all the input.

The beginners guide is available on the disk just to let you know. It states where the file is at start, and then you can just open it in nano.

---

### Post by Eion on 2008-09-27
Thats helpfull, I tried to print it out on my parents mac laptop, it decided to not print any of the code boxes, and only the text, found that out after 58 pages of printing that took like 3 hours >:(  So I just have said laptop hooked up next to my desktop and I'm going to read it off there.

EDIT:  Is it normal for Gparted to take so long to resize a partition?

---

### Post by mips on 2008-09-28
How's it going so far?

---

### Post by Eion on 2008-09-28
Its going alright, I had some issues with partitions, connecting to the internet, and getting mirros and repos set up, but all were pretty easily solved, however it was like 2am at that point so I went to sleep :D But Right now I'm hung on a problem with Pacman, but I just posted a question on the forums, and hopefully I'll find out what I'm doing wrong soon.  Doing all this stuff from Command Line is pretty neat I guess, I at least think i'm learning some, even if for some reason I can't get it installed.

EDIT:  I fixed my problem, with my own workaround too!

---

### Post by Eion on 2008-09-29
Well, its all said and done, I'm now typing this on my fresh Arch install with my shiny KDEmod!  :D  Thanks for all the support and help! :popcorn: and :KSs to all!

---

### Post by kaldor on 2008-09-29
If you want to dig deep into Linux, try out Gentoo.

If you just want to learn more, try out some other distros such as Fedora (similar to Ubuntu, but at the same time very different) openSuSE, and Arch.

---

### Post by TheSlipstream on 2008-09-30
> **kaldor said:**
> If you want to dig deep into Linux, try out Gentoo.


Common misconception, Gentoo won't teach you much about the true Linux. If real, actual, in your face Linux is what you want, go for Linux From Scratch, which I have never, and maybe will never attempt myself.

---

