---
title: "CRUX Talk"
date: 2009-01-19
forum: Other OS Talk
---

### Post by cardinals_fan on 2009-01-19
I think we need a generic thread for thoughts, questions, and updates about CRUX.  For those who aren't familiar with it, CRUX is a lightweight distro designed for experienced users who want more control over their system.  It uses a source-based ports system for software installation, with a ports manager called prt-get to automate upgrading and installation.

Discuss!

---

### Post by fwojciec on 2009-01-19
Awesome distro, very conservative in its minimalism, and also a great learning experience.  There are downsides to this minimalism, though -- I don't like the fact that when you remove a package you have to manually remove the dependencies that were installed along with it (prt-get only resolves dependencies when installing packages, or has this changed in the latest release?)  Another issue is that CRUX is not necessarily easily expendable beyond what's available in various ports collections; back when I used CRUX I had to maintain about 50 custom packages, as well as separate installations of things like texlive in /opt, all of which became quite time consuming in the long run.  Still, it's a great distro and I do recommend it to those who like things minimal, simple, and fast.

---

### Post by K.Mandla on 2009-01-19
Big fan here. Using it on four or five machines, everything from a 100Mhz Pentium to a 1Ghz Pentium III. I also put it on an OLPC XO-1 a while back, although I haven't used it on that in a while. ... I should try that again. ...

Anybody who enjoys Arch will be able to move to Crux without too much hassle. :)

---

### Post by K.Mandla on 2009-01-19
> **fwojciec said:**
> I don't like the fact that when you remove a package you have to manually remove the dependencies that were installed along with it (prt-get only resolves dependencies when installing packages, or has this changed in the latest release?)
That's probably my only grievance too. I would prefer prt-get could do something like pacman's -Rcsn, and tear out anything unneeded as well. As far as I can tell, prt-get hasn't changed that behavior yet. I don't know if it will or not, either.
> **fwojciec said:**
> Another issue is that CRUX is not necessarily easily expendable beyond what's available in various ports collections; back when I used CRUX I had to maintain about 50 custom packages, as well as separate installations of things like texlive in /opt, all of which became quite time consuming in the long run.
Also true. I have a hefty collection of personal favorites that I keep on a spare drive, so I can build the stuff I use in the future. Most of them are converted from Arch or AUR PKGBUILDs with [Colin Zheng's conversion script]("http://jcolinzheng.org/"), so it's no great loss if they're lost or deleted.

---

### Post by cardinals_fan on 2009-01-19
> **K.Mandla said:**
> 
Anybody who enjoys Arch will be able to move to Crux without too much hassle. :)
+1, but for psychological rather than technical reasons.  Installing Arch is really quite simple.  Pacman, the installer, and the Beginner's Guide make installing Arch a very simple process that requires a paltry amount of technical skill.  CRUX, on the other hand, definitely expects a bit more out of the user and requires more manual configuration.

However, while it may be possible to install Arch with little knowledge, it is not possible without a willingness to read and learn just a little bit.  That interest in going beyond the defaults, even if it's only the tiny amount required by Arch, sets up users for success with more manual distros such as CRUX.  Hence the "enjoys" part of your post :)

---

### Post by yabbadabbadont on 2009-01-19
How does it differ from Gentoo?

---

### Post by K.Mandla on 2009-01-19
> **cardinals_fan said:**
> +1, but for psychological rather than technical reasons.  Installing Arch is really quite simple.  Pacman, the installer, and the Beginner's Guide make installing Arch a very simple process that requires a paltry amount of technical skill.  CRUX, on the other hand, definitely expects a bit more out of the user and requires more manual configuration.

However, while it may be possible to install Arch with little knowledge, it is not possible without a willingness to read and learn just a little bit.  That interest in going beyond the defaults, even if it's only the tiny amount required by Arch, sets up users for success with more manual distros such as CRUX.  Hence the "enjoys" part of your post :)
Actually, you're right. I should stipulate that a little experience with things like ABS and custom kernels is a good idea. I stand corrected. ... :oops:
> **yabbadabbadont said:**
> How does it differ from Gentoo?
I haven't used Gentoo enough to really answer that; last time I spun it up was a year or two ago, but it's [on my list]("http://kmandla.wordpress.com/2009/01/07/goals-and-resolutions-2/"). I'll defer to others on that one. ...

---

### Post by cardinals_fan on 2009-01-19
> **yabbadabbadont said:**
> How does it differ from Gentoo?
Gentoo always seemed like an unfinished hack to me.  CRUX is barebones, but it just feels... *right* that it should be that way.  After producing a usable Gentoo system, I always felt like I had completed some ritualistic rite of passage.  With CRUX, the effort to get it installed just felt like part of the job, a logical task.  I find Gentoo "harder" than CRUX.  Perhaps this is because CRUX's version of minimalism focuses on simplicity while Gentoo's focuses on customization options.  

If both minimal distros provide blueprints for a house, this is how they differ: CRUX is a foundation with  a set of spartan supplies.  You build what you can from these supplies, producing a minimal yet complete house of your own design.  If you build the house wrong, you're screwed.  Gentoo is a large staff of workers with a vast variety of supplies available to them.  They follow your instructions *to the letter*, and build you a custom house.  If you give them bad instructions, you're screwed.  That analogy was either completely awesome of totally pathetic.  You decide which.

/opinion

Gentoo is rolling-release while CRUX has stable releases (although you can get newer versions from Ports).  Gentoo supports more architectures.  The CRUX installation is binary, though all packages are source-based.  This means that CRUX installs much faster, but offers fewer choices at install time.  A stage 3 Gentoo install includes less by default, but has more available.

/fact

---

### Post by smartboyathome on 2009-01-19
Is the CRUX site down for anyone else? I'm getting timeouts. :(

---

### Post by cardinals_fan on 2009-01-19
> **smartboyathome said:**
> Is the CRUX site down for anyone else? I'm getting timeouts. :(
Yes, unfortunately.  The x86_64 and PPC sites are still up, but the official page appears to be down.  I'll ask around on #crux...

---

### Post by MisfitI38 on 2009-01-19
I like CRUX. In fact, I was the one who recommended you try it. ;)
It is a bit too 'crude' for me to use as my everyday system. As was mentioned, it requires too much patience and user intervention when dealing with packages. Messy removal of installed ports and waiting for compilation of everything is just not my idea of the ideal system.
The number of ports is also an issue for me; even if they doubled the ports collection in size, it would still be lacking quite a bit. 
As I have mentioned many times, I believe that package management should be an absolute 'no-brainer'- the main reason I avoid CRUX and Slack.
I certainly like the concept- a streamlined set of core packages, and serious community contributions, (prt-get was a community innovation). 
But, Arch simply does it so much better for me; much larger repositories, much larger community, pacman and binaries in addition to a ports-like system and the AUR.
If I was 20 years younger and still enamored by the thrill of being an 'outsider', or 'one of the few' who use an unpopular yet incredibly cool thing, I might like it even more.
For me, CRUX does a lot of things the right way. 
Arch just does them all better, and adds more extensibility along with it, effortlessly.

---

### Post by cardinals_fan on 2009-01-19
> **MisfitI38 said:**
> I like CRUX. In fact, I was the one who recommended you try it. ;)

I remember.  It turned out to be good advice, though I prefer Slackware and NetBSD :)

---

### Post by cardinals_fan on 2009-01-21
Announcement: The CRUX site is back up!  Yay!

Thoughts (aka meaningless drivel): 

I really like the CRUX documentation.  The Handbook is complete yet concise.  It explains everything necessary to use the system, but nothing unneeded or out of place.  It offers step-by-step commands but avoids redundancy.  Overall, CRUX has some of the best docs of any distro I've seen.

I also like the #crux IRC channel.  Most Linux IRC channels I've seen fall into one of two categories: "my internet dosnt wrk, plz hlp" and "rtfm n00b".  Most people on #crux are scrupulously competent and expect effort in return, but nonetheless welcome questions from the less experienced.  It seems to have a good mix of users who a) have questions, b) want to answer questions, or c) just want to chat.  #crux isn't always full (it wasn't exactly a hotbed of activity last night ;)), but it's a nice place to stop by.

/random thoughts of the day

---

### Post by smartboyathome on 2009-01-22
> **cardinals_fan said:**
> Announcement: The CRUX site is back up!  Yay!

Thoughts (aka meaningless drivel): 

I really like the CRUX documentation.  The Handbook is complete yet concise.  It explains everything necessary to use the system, but nothing unneeded or out of place.  It offers step-by-step commands but avoids redundancy.  Overall, CRUX has some of the best docs of any distro I've seen.

I also like the #crux IRC channel.  Most Linux IRC channels I've seen fall into one of two categories: "my internet dosnt wrk, plz hlp" and "rtfm n00b".  Most people on #crux are scrupulously competent and expect effort in return, but nonetheless welcome questions from the less experienced.  It seems to have a good mix of users who a) have questions, b) want to answer questions, or c) just want to chat.  #crux isn't always full (it wasn't exactly a hotbed of activity last night ;)), but it's a nice place to stop by.

/random thoughts of the day

Yay! I may soon be able to play with it more! (when the site crashed, I was trying to install Crux's kernel :()

---

### Post by cardinals_fan on 2009-01-22
> **smartboyathome said:**
> Yay! I may soon be able to play with it more! (when the site crashed, I was trying to install Crux's kernel :()
Ouch ;)

---

### Post by smartboyathome on 2009-01-22
> **cardinals_fan said:**
> Ouch ;)

Luckily, I am installing CRUX in a virtual machine for the precise reason of being able to save my state. I might be able to work on it tonight, btw. :KS

---

### Post by K.Mandla on 2009-01-24
I was thinking about the whole package-removal issue and I was wondering if it would take a lot of effort to screen installed packages against the ones that are required, and make a script of some sort that can pluck out ones that are removable as dependencies.

I have all the coding skills of a rock, but with the quickdep and listinst options for prt-get, isn't that most of the information that would be needed?

---

### Post by Frak on 2009-01-24
> **cardinals_fan said:**
> Discuss!

I like it? A lot?

I'm a fan of source based distributions, and I find it easier to use than Gentoo. I run it in a virtual machine though.

---

### Post by SomeGuyDude on 2009-01-24
Since the big thing here seems to be moving form Arch to CRUX, I have basically one question, split into two halves:

1a) How are the repos?

1b) Is there anything comparable to the AUR?

---

### Post by cardinals_fan on 2009-01-24
> **SomeGuyDude said:**
> 
1a) How are the repos?
The official repos are small, but there are many custom repos available.  Check out the [ports page]("http://crux.nu/portdb/").
> **SomeGuyDude said:**
> 
1b) Is there anything comparable to the AUR?
The whole system is comparable to the AUR.  CRUX is a source-based distro, and it strongly resembles the AUR in several ways.

---

### Post by K.Mandla on 2009-01-25
Most of the software I use in Crux actually isn't hosted either in the official repos or through the community. [Colin Zheng]("http://jcolinzheng.org/") has a fantastic PKGBUILD-to-Pkgfile conversion script that simplifies the task of converting an Arch version into a Crux version. 

In general, with that script you can take almost anything you want from Arch and have it compiling in Crux, in a few minutes. The most difficult part after the conversion is finding the package names that correspond for the dependencies.

So in all, anything you want from AUR or the standard Arch menu is also available in Crux. You just have to get your hands dirty. :mrgreen:

P.S.: [http://kmandla.wordpress.com/category/linux/crux-linux/crux-ports/](http://kmandla.wordpress.com/category/linux/crux-linux/crux-ports/)

P.P.S.: Yes, yes, I know. It's CRUX, not Crux. Sorry. :oops:

---

### Post by kk0sse54 on 2009-01-25
Just installed crux over my Gentoo partition and everything was successful except for the fact that it refuses to boot with a nice kernel panic.

---

### Post by fwojciec on 2009-01-25
> **C!oud said:**
> Just installed crux over my Gentoo partition and everything was successful except for the fact that it refuses to boot with a nice kernel panic.

That is really not something you should complain about with regard to CRUX.  It just means that you didn't configure kernel/grub correctly.  CRUX doesn't do *anything* for the user when it comes to the kernel; as a user it is you who is solely responsible for providing CRUX with a working kernel that it can run on top of.

---

### Post by cardinals_fan on 2009-01-25
> **C!oud said:**
> Just installed crux over my Gentoo partition and everything was successful except for the fact that it refuses to boot with a nice kernel panic.
Kernel compilation is always fun :)

---

### Post by kk0sse54 on 2009-01-25
> **fwojciec said:**
> That is really not something you should complain about with regard to CRUX.  It just means that you didn't configure kernel/grub correctly.  CRUX doesn't do *anything* for the user when it comes to the kernel; as a user it is you who is solely responsible for providing CRUX with a working kernel that it can run on top of.

I'm not complaining about crux and this isn't the first time I've compiled a kernel or configured grub :roll:. Merely stating that my first attempt at installing was unsuccessful, instead I'll have to recompile the kernel later.

---

### Post by K.Mandla on 2009-01-26
> **C!oud said:**
> I'm not complaining about crux and this isn't the first time I've compiled a kernel or configured grub :roll:. Merely stating that my first attempt at installing was unsuccessful, instead I'll have to recompile the kernel later.
I've been there. I could swear a few times the computer was laughing at me, when it saw the kernel I built. "You want me to boot *that*?!" :lol:

---

### Post by cardinals_fan on 2009-01-26
> **K.Mandla said:**
> I've been there. I could swear a few times the computer was laughing at me, when it saw the kernel I built. "You want me to boot *that*?!" :lol:
My problems came when I tried to set up GRUB.  I ***hate*** bootloaders...

---

### Post by SomeGuyDude on 2009-01-27
I'm so glad I've never had to do that stuff for myself. Just the idea of it frightens me.

---

### Post by K.Mandla on 2009-01-27
It's really not that bad once you understand what's going on and why they work. Of course, getting to that point is the difficult part. :roll:

By the way, anybody compiled mutt out of opt (or is it contrib? I forgot)? It's ending with errors for me.

Edit: Never mind, I'll just use the one off the CD.

---

