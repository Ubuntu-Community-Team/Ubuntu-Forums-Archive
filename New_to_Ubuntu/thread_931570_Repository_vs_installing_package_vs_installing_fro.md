---
title: "Repository vs installing package vs installing from source"
date: 2008-09-27
forum: New to Ubuntu
---

### Post by ldfj3jf on 2008-09-27
I've read and read and read but I still don't get it - so any info would be much appreciated!!! :)

Apart from the fact apt-get is cron'ed and will warn you of an update (when installing a package won't), is there any difference at all? 

For example, if I try to download the Klavaro Deb package from Freshmeat, install it, or even build it from source, in what way would the repository version be 'better' - if the version number is the same wouldn't it be just the same codebase anyway?

I find the help provided very confusing - on one hand, the help pages state that 'oooh be careful, downloading software from other source than the official repos is bad and scarrrrry' but at the same time if you read the comments in the sources.list file it states "software in universe won't receive and review or UPDATES from the security team". 

Well sorry to be a n00b but what's the point of the repos if they aren't being security-checked or updated anyway? Why would I not want to download straight from the 3rd party site instead?

Very confused here !!

PS: which 'support' is canonical talking about - you have to pay for support from what I've read on their site - does 'not supported' mean they refuse to provide commercial support on things like the flash player? Arrrg.

---

### Post by SunnyRabbiera on 2008-09-27
> **ldfj3jf said:**
> I've read and read and read but I still don't get it - so any info would be much appreciated!!! :)

Apart from the fact apt-get is cron'ed and will warn you of an update (when installing a package won't), is there any difference at all? 

For example, if I try to download the Klavaro Deb package from Freshmeat, install it, or even build it from source, in what way would the repository version be 'better' - if the version number is the same wouldn't it be just the same codebase anyway?

I find the help provided very confusing - on one hand, the help pages state that 'oooh be careful, downloading software from other source than the official repos is bad and scarrrrry' but at the same time if you read the comments in the sources.list file it states "software in universe won't receive and review or UPDATES from the security team". 

Well sorry to be a n00b but what's the point of the repos if they aren't being security-checked or updated anyway? Why would I not want to download straight from the 3rd party site instead?

Very confused here !!

PS: which 'support' is canonical talking about - you have to pay for support from what I've read on their site - does 'not supported' mean they refuse to provide commercial support on things like the flash player? Arrrg.

well the resson why we say keep to the repos is that outside packages can break the system.
By using the repositories and not risking possibly unstable packages the system works in my mind

---

### Post by jimmy the saint on 2008-09-27
apt is like the add/remove programs in windows, except that it does a hell of a lot more than just tell you (most of) what is installed on your system.  It is a package managager.  A package is simply precompiled software wrapped up in a form that tells the OS what other things need to be installed along with that piece of software, and where to put everything.  It is like an instruction manual for the system.

When you compile and install software from source, you have to do all of that.  If you really want to see everything that the package and manager are doing when you install something, check out a tutorial on installing from source!

The packages in the OFFICIAL repositories are confirmed to work and are supported by Cononical.  No, Canonical will not support flash.  Why would they?  They did not give it to you.  If you called MS because you had issues with PhotoShop, they would not give you support for the same reason.

---

### Post by ldfj3jf on 2008-09-27
Thank you for your replies!!

May I ask - who is keeping the repos up to date then? (please don't say an army of friendly elves)

And when they see something needs updating - do they 'test' the package or not? (because the sources.list make it sound like they're not).

---

### Post by jimmy the saint on 2008-09-27
The repositories are maintained by the maintainers.  Im not making that up, that's what they are called.  First they create package, then they install it on a bunch of systems to test it out.  If there are issues, they repackage the app, fix the issues and finally, when it has been fully tested,they add it to the repos.  That is why it is safer to use the repos than to blinly download a .deb package from someones website.

---

### Post by oldsoundguy on 2008-09-27
> **jimmy the saint said:**
> The repositories are maintained by the maintainers.  Im not making that up, that's what they are called.  First they create package, then they install it on a bunch of systems to test it out.  If there are issues, they repackage the app, fix the issues and finally, when it has been fully tested,they add it to the repos.  That is why it is safer to use the repos than to blinly download a .deb package from someones website.

+1
If you year about a hot new program from some guy you met at an internet cafe or coffee shop and it he gives you this link to a site you never heard of, installing same on your system is just the same as surfing with a Windows machine with NO AV or spyware protection!
There are very few non repository sites that are really trustworthy.  Source Forge is a good one, and getting a program to upgrade something you have already and getting it it FROM THE SOURCE (such as Adobe) will, at least, be a lot more safe than just "going for it".
However, some like to experiment .. if so BACK UP first.  Then feel free.  It is your computer and your time.

---

