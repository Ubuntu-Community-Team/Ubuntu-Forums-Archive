---
title: "anyone want to tell me about their LFS experience?"
date: 2009-01-01
forum: Other OS Talk
---

### Post by il-luzhin on 2009-01-01
I have some surgery coming up that will put me off work for some time so I need a project to consume my hours and hours of sitting around healing.  I've always wanted to build an LFS OS so I thought this might e my moment.

Is the experience a horror show or enjoyably interesting?

---

### Post by gnomeuser on 2009-01-01
I ran LFS as my sole OS for over a year. If you think this will teach you about how Linux works you are likely mistaken. It's following a guide to build the base system and then ontop you get to do a whole lot of ./configure && make && make install.

If the aim is to learn more about what goes into building an OS, you may want to look at Gentoo. That would let you focus on learning, tinkering and still let you have package management to do your compile and installation jobs. I have run both and Gentoo is by far the more rewarding experience in the area of learning.

I would say LFS is not worth it unless you have a very specific use case in mind or you really want to become comfortable with compiling code by hand.

Gentoo has another advantage, of the distributions out there I doubt there is a more dedicated community for writing how-tos, gentoo-wiki (at least used to be) an excellent resource for the eager student. Many fine articles explaining how to customize and tweak every aspect of your system.

---

### Post by Kvark on 2009-01-01
You don't learn much from installing LFS because you're just following instructions and sometimes applying premade patches. Following instructions doesn't prepare you for installing a different setup (with newer versions of the packages, different packages and different options) than the book's on your own and solving problems that aren't in the book on your own. So installing LFS doesn't mean you know how to install Linux from scratch (which is a useless skill btw), it means you can follow instructions.

The best way to learn from the LFS book is to go through chapter "6. Installing Basic System Software" and read the last part about each package, the part called "Contents of PackageName". Try to use each program/command in the lists there. If you have no use for a command then make up an example just to test what the command does. You'll forget most of it but when you later encounter a task it might pop up that you once tried a command that does what you need. Make a personal cheat sheet as you go along.

If you want a minimal Linux system you're better of installing a lightweight distribution and stripping it down.

If you want a customized desktop system you're better off cherry picking things to customize from the top down than building everything from the bottom up. Install a distribution that is known to be good for customization, get everything working in a default setup, then search for things to tweak.

If you want your own distribution you're better off forking Debian than LFS.

---

### Post by smartboyathome on 2009-01-01
> **Kvark said:**
> If you want your own distribution you're better off forking Debian than LFS.

[off topic]
I disagree with this completely. There are too many distros which are based off of other distros with only minor tweaks. One of the stars of LFS (imo) is that it can be customized down to the very lowest level, something which not many distros can do without much tweaking (even Gentoo). It also gives you as pure an install which you can get, as you don't *have* to try to strip everything down.
[/off topic]

I find that LFS is good for those who want to have complete control of absolutely everything, as you can even control where packages install to (on most other distros, you have to recompile the kernel, move pre-existing packages to where you want, etc, which isn't very good).

---

### Post by Grant A. on 2009-01-01
Their IRC channel is full of pricks, I would not recommend it.

---

### Post by Sorivenul on 2009-01-01
> **smartboyathome said:**
> I find that LFS is good for those who want to have complete control of absolutely everything, as you can even control where packages install to (on most other distros, you have to recompile the kernel, move pre-existing packages to where you want, etc, which isn't very good).
+1 to this.

I personally enjoy LFS, and when I first followed the manual, it *did* teach me a lot about how to manage my own system and what each packages does and does not do. Outside of what was said by smartboyathome, LFS really *is* just a manual. If you really want to try something different, do an LFS install, or a few, and get comfortable with the process. Then try to build your own system that diverges from the default packages/patches. I've been trying my hand at building a uClibc/BusyBox system lately, which isn't covered by the main LFS book or very well by the Hint for a BusyBox system.

gnomeuser offers an interesting point about Gentoo and their documentation as well. If you decide LFS is not for you, try Gentoo, or another distribution altogether.

Good luck!

---

### Post by mohitchawla on 2009-01-02
If you view LFS as a learning tool for building linux systems, it is a good start. Not much to do on your own, but its good for familiarizing yourself with the various necessary tools and utilities, the concepts behind things like packages, boot up scripts, chroot environment and a lot about the various packages you work with.

The real fun starts when you are done with building the LFS system and now you take whatever direction you want. Customize to the core and see the results. Good feeling, without a doubt !

---

### Post by il-luzhin on 2009-01-03
Thanks everyone,

I've looked into Gentoo before and it has always seemed as much like a 'follow the dots' install as LFS but with a few more options laid out for you.  I always thought that as much as LFS may be an instruction manual, the more you choose to get into the more branches their are to follow.  I never thought about the support element though.  Maybe I'll reconsider Gentoo.

A debian install just seems like an upstream ubuntu build.  I was hoping for something a little different just to see what else is out there.  

I was hoping to learn a little something but foremost I guess what I'm looking for is just a major time sink!

---

### Post by Sorivenul on 2009-01-03
> **il-luzhin said:**
> I was hoping for something a little different just to see what else is out there.  

I was hoping to learn a little something but foremost I guess what I'm looking for is just a major time sink!
You could try any BSD you can find and set it up. 

The research to make sure your hardware works, combined with actual setup time is a pretty good way to pass some time. I personally prefer FreeBSD, and the accompanying documentation is excellent, though you may choose otherwise if you wish. 

While I can set up FreeBSD to my liking in about 20 minutes, it may take you considerably longer. Just an additional thought...

---

### Post by mikjp on 2009-01-04
> **Sorivenul said:**
> While I can set up FreeBSD to my liking in about 20 minutes, it may take you considerably longer. Just an additional thought...

NetBSD and OpenBSD might provide more of a challenge :-)

---

### Post by Sorivenul on 2009-01-04
> **mikjp said:**
> NetBSD and OpenBSD might provide more of a challenge :-)
They may or they may not. Like I said, the OP can choose whatever they want. NetBSD, IMO, is the easiest of the BSDs, especially to set up. Likewise, OpenBSD is on the more difficult end IMO, mainly because many new users will be unfamiliar with the concepts as they are presented in the installer.

Remember, "challenge" is a subjective matter. What is easy for one may be challenging for another, and vice versa. That is why you will see many "suggestions" or "opinions" in the Other OS Talk subforum, but rarely any "instructions", unless specifically asked for.

Cheers!

---

### Post by kk0sse54 on 2009-01-04
> **Sorivenul said:**
> NetBSD, IMO, is the easiest of the BSDs, especially to set up. 

NetBSD is extremely straight forward if you follow the NetBSD guide however I wouldn't say it's the easiest of the BSDS to set up since I thought FreeBSD was a easier but it's all subjunctive based on personal opinion helped by the fact that most BSDs have excellent documentation. 

> 
Remember, "challenge" is a subjective matter. What is easy for one may be challenging for another, and vice versa. That is why you will see many "suggestions" or "opinions" in the Other OS Talk subforum, but rarely any "instructions", unless specifically asked for.
+1

---

### Post by albinootje on 2009-01-04
> **Sorivenul said:**
> They may or they may not. Like I said, the OP can choose whatever they want. NetBSD, IMO, is the easiest of the BSDs, especially to set up. Likewise, OpenBSD is on the more difficult end IMO, mainly because many new users will be unfamiliar with the concepts as they are presented in the installer.


Having used FreeBSD, NetBSD and OpenBSD in the past I completely disagree with NetBSD being the easiest to set up. 
Of those three I find NetBSD the hardest for the new BSD user.
For the NetBSD installation you need to know your way around on the console, and you need the install guide printed out or a second computer with internet next to the machine you're installing on.

FreeBSD is by far the easiest of those three if you look at the installation, and I'm certainly not the only person on the internet claiming this.
The partitioning is the easiest (The one in OpenBSD was really hard for me at first!), and there's no extra knowledge needed apart from using the installation menu.

---

### Post by Sorivenul on 2009-01-04
> **albinootje said:**
> Having used FreeBSD, NetBSD and OpenBSD in the past I completely disagree with NetBSD being the easiest to set up.
Like I said, this is completely subjective, and a matter of opinion.
 
> **albinootje said:**
> Of those three I find NetBSD the hardest for the new BSD user. For the NetBSD installation you need to know your way around on the console, and you need the install guide printed out or a second computer with internet next to the machine you're installing on.
The same could be said for any system, BSD or not. I had many "afterinstall" instructions printed for my first FreeBSD setup. I personally have never touched a console in my NetBSD install processes, except for after installation.

> **albinootje said:**
> FreeBSD is by far the easiest of those three if you look at the installation, and I'm certainly not the only person on the internet claiming this.
You certainly aren't the only person claiming this, but again this is a matter of opinion.
 
> **albinootje said:**
> The partitioning is the easiest (The one in OpenBSD was really hard for me at first!), and there's no extra knowledge needed apart from using the installation menu.
cfdisk in FreeBSD is easy, but can also be frightening if you have never used it. NetBSD's partition system, IMO, is a bit more straightforward. I would definitely agree that the OpenBSD install, especially the partitioning, was the most foreign, but there are many excellent related guides available.

Anyway, *BSD, partitioning, and such are not the original subject. Let it suffice for the OP that our little *BSD tangent is a small representation of the varied opinions and experiences with "do-it-yourself" systems, which is a bit more on-topic.

Cheers!

---

