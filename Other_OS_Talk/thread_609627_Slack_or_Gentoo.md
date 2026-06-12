---
title: "Slack or Gentoo"
date: 2007-11-11
forum: Other OS Talk
---

### Post by KentS on 2007-11-11
I have been using Ubuntu for about a year, and I don't feel I have learned much about Linux. So I want to install a distro that really teaches me about Linux, and I understand Slackware and Gentoo does this. (I don't mind a vertical learning curve, even though I'm a beginner.) But I don't manage to decide which one to pick. I would appreciate some input.

I use a HP Pavilion dv2000 with Broadcom BCM4310, but I guess ndiswrapper will handle this? I also have a widescreen with NVIDIA GeForce Go 6150 graphics card. Can I use one of the binary drivers provided by nvidia?
My last concern is that I want to keep XP and Dapper Drake. Can I do this by not installing lilo, but reinstall grub after the OS is installed?
Are there other hardware related things I should consider?

As I said, I want this OS to really learn linux, its inner workings, compiling kernels and so on (in the long run, of course). So I will probably mess up a lot. But in the end I'm hoping for a really stable  and useful system, that will show me what linux is capable of. Usefulness is the reason I'm not considering LFS for this machine, although I want to try it on another machine.

---

### Post by SunnyRabbiera on 2007-11-11
tough call, but personally I would do slack as I have considered it in the past.
Gentoo, I really dont know what to say, on one hand it seems to be good at what it does but on the other ugh it takes forever with compiling crap.
but if you want a more hands on experience with compiling gentoo is for you, I would personally go slack as at least I can get binaries on it.

---

### Post by mips on 2007-11-11
> **KentS said:**
> I have been using Ubuntu for about a year, and I don't feel I have learned much about Linux. So I want to install a distro that really teaches me about Linux, and I understand Slackware and Gentoo does this. (I don't mind a vertical learning curve, even though I'm a beginner.) But I don't manage to decide which one to pick. I would appreciate some input.

I use a HP Pavilion dv2000 with Broadcom BCM4310, but I guess ndiswrapper will handle this? I also have a widescreen with NVIDIA GeForce Go 6150 graphics card. Can I use one of the binary drivers provided by nvidia?
My last concern is that I want to keep XP and Dapper Drake. Can I do this by not installing lilo, but reinstall grub after the OS is installed?
Are there other hardware related things I should consider?

As I said, I want this OS to really learn linux, its inner workings, compiling kernels and so on (in the long run, of course). So I will probably mess up a lot. But in the end I'm hoping for a really stable  and useful system, that will show me what linux is capable of. Usefulness is the reason I'm not considering LFS for this machine, although I want to try it on another machine.

Personally I would go for Gentoo, I like portage and I don't know how well Slackware handles depencies if at all.

If you are doing this as a learning experience could I suggest you do it in VirtualBox. This way you have a stable working system while you play around in the virtual environment without worrying about your system and rebooting the whole time. So you can mess things up as much as you want.

I dunno about slack but the wireless & video stuff will work in Gentoo

Gentoo has very good docs and support resources. If you do decide to go the Gentoo route do NOT use the LiveCD as it sux. Get the minimal install cd and do the Stage3 tarball install.

Sorry but I have no experience with Slack so cannot comment on it.

Edit:
Just found this:  [http://polishlinux.org/choose/comparison/?distro1=Gentoo&distro2=Slackware](http://polishlinux.org/choose/comparison/?distro1=Gentoo&distro2=Slackware)

Based on the above I would go with Gentoo but thats me.

---

### Post by Bachstelze on 2007-11-11
Slack, without a doubt. Gentoo will surely teach you a lot, but clearly not as much as Slack.

---

### Post by Whiffle on 2007-11-11
Flip a coin.  They're both excellent for what you want.  I used gentoo before I used slack, and i seem to be headed back to slack right now.  Drivers will work the same in either of them, linux drivers are after all linux drivers, but how you install and run them may differ.  Slackware doesn't have an official dependency checking package manager, but I have been using slapt-get lately and while its still not on the same level as apt-get, it does okay.  The only thing that puts me off of gentoo is waiting for stuff to compile, other than that its a very good distro with lots of great documentation and a pretty good forum.  So yeah, take your pick.

---

### Post by shane2peru on 2007-11-11
> **HymnToLife said:**
> Slack, without a doubt. Gentoo will surely teach you a lot, but clearly not as much as Slack.

Can you clarify that?  I have been considering the same thing, and have dove into Gentoo.  Why does Slack teach you more than Gentoo?  

Gentoo isn't bad, especially if you build it from within Ubuntu.  Chroot into it, and work with Ubuntu while you are waiting for your apps to compile. :)

Shane

---

### Post by Bachstelze on 2007-11-11
Slack is all about doing it yourself. When you're done installing, you have your system with packages for the most common applications, but from there on, you're pretty much on your own. You can find precomplied Slackware packages for a few apps but most of the time, they will not include all the needed dependencies, or will just be outdated. So you will most often have to compile your software from source (and I mean, do it *really*, use ./configure, make, make install and track down all the dependencies yourself, not like in Gentoo where it does it all for you) and do all your configuratiion and administration tasks by hand.

Long story short, Slackware provides you with a solid base system, sufficient for most basic tasks, but you're on your own if you want to make it do other things.

---

### Post by shane2peru on 2007-11-11
Yeah, I think I will stick to Gentoo in that case.  I'm getting to lazy to track down dependencies.  Even in Gentoo, I run into problems compiling, and think, I should just stick to Ubuntu. ;)  I just like the extreme end of using Gentoo, and Learning the nuts and bolts of Linux.  Gentoo teaches me enough of that. 

Shane

---

### Post by kellemes on 2007-11-11
> **shane2peru said:**
> Can you clarify that?  I have been considering the same thing, and have dove into Gentoo.  Why does Slack teach you more than Gentoo?  


Gentoo teaches you a lot about Gentoo, a lot of info you gather will be close to useless when running other distro's.
Slack is more of a vanilla kind of GNU/Linux and *may* be the better choice if you want to learn about GNU/Linux in general.
By the way.. dependency resolution can be handled these days.. there are a couple of 3-party packages available for Slackers.

Maybe you should choose the middle road, Zenwalk for example gives you all the power you need to setup your system as you wish without too much hassle and also gives you a lot of transparency on the inner works of GNU/Linux (Slackware in this case).
I'm on Arch, you may try that too, it's like Gentoo only without the compilation errors. :popcorn:

---

### Post by shane2peru on 2007-11-11
> **kellemes said:**
> Gentoo teaches you a lot about Gentoo, a lot of info you gather will be close to useless when running other distro's.
Slack is more of a vanilla kind of GNU/Linux and *may* be the better choice if you want to learn about GNU/Linux in general.
By the way.. dependency resolution can be handled these days.. there are a couple of 3-party packages available for Slackers.

Maybe you should choose the middle road, Zenwalk for example gives you all the power you need to setup your system as you wish without too much hassle and also gives you a lot of transparency on the inner works of GNU/Linux (Slackware in this case).
I'm on Arch, you may try that too, it's like Gentoo only without the compilation errors. :popcorn:

I think that 'useless'  may be a little strong.  I have learned a whole lot of cli and commands in Gentoo, that I use (and sometimes even prefer) in most distros.  I may have to give Slackware a try.  I certainly enjoy the learning.

Shane

---

### Post by Whiffle on 2007-11-11
Speaking of learning things, my linux history is a little interesting.  When I first dabbled with it back in the day I tried Mandrake 8.2.  What a mess.  I couldn't get anything to work, decided to give it a go some other time.  Then one of my friends installed gentoo, and I saw it and was like "cool."  So I installed gentoo, straight from the Stage 1 install.  I think that experience is what got me comfortable with a command line.  I dont think I necessarily knew alot about linux (still dont actually), but I knew where to look for help, and that has what has kept me going on this stuff.  I think after Gentoo I tried ubuntu but it totally disagreed with my hardware, so I left it.  I went to slackware and found home.  My computer never ran smoother than when it was running slack, and I was good enough with google and the cli to figure out whatever i needed to do and make it all work.  I have the feeling that I'll probably go back to slack    on both my machines sooner or later.

---

### Post by KentS on 2007-11-12
Thanks for your replies. Sounds like Slack is what I'm after, but it seems like I really have to install Gentoo some time, too. 

mips: Thank you for mentioning VirtualBox. That sounds like a really good idea.

Now I'm just looking forward to my vacation, so I can get started.

---

