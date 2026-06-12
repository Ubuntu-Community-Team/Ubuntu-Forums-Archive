---
title: "Source Code"
date: 2005-02-09
forum: Programming Talk
---

### Post by orion_114 on 2005-02-09
Hey Guys,

Where can I find some Ubuntu Source code ?
I am trying to make the move from windows programming to Linux programing
and I am interested to see how the source looks for the apps on Ubuntu.
Is there an Ubuntu Source repository anywhere?

Thanks.

---

### Post by orion_114 on 2005-02-09
Oh yea ....

Is Python the way to go or should I stick to my the languages I already know ?
I currently use C, C++, C#, Java &  PHP

---

### Post by wtd on 2005-02-09
[QUOTE=orion_114]Oh yea ....

Is Python the way to go or should I stick to my the languages I already know ?
I currently use C, C++, C#, Java &  PHP[/QUOTE]

Having more languages in your toolbox never hurts.

---

### Post by DJ_Max on 2005-02-09
[QUOTE=wtd]Having more languages in your toolbox never hurts.[/QUOTE]
I agree, all of those languages are good for something.

Ubuntu uses the Debian Linux source code. But, you have to know that linux is a [kernel](http://www.kernel.org/), and a distribution is the [software](http://www.gnu.org/) bundled with it.

---

### Post by Quest-Master on 2005-02-09
Python is undoubtedly the best language to use for Ubuntu application development though right now.

---

### Post by az on 2005-02-09
"Is there an Ubuntu Source repository anywhere?"

Yes.  archive.ubuntu.com

That is the repository.  The binaries as well as the source are all there, as per the GPL.


Fire up Ubuntu and run the command

sudo apt-get build-dep $package
where package=whatever package you want.

then do 
sudo apt-get source $package
to get the source for that package.

example:
sudo apt-get build-deb abiword
sudo apt-get source abiword.

---

### Post by orion_114 on 2005-02-10
Thanks guys !
Hopefully one of these days I can contribute back to Ubuntu ! :)

---

### Post by Pausanias on 2006-02-04
Thank you thank you azz!

---

### Post by cbntrt on 2008-03-12
> **az said:**
> "Is there an Ubuntu Source repository anywhere?"

Yes.  archive.ubuntu.com

That is the repository.  The binaries as well as the source are all there, as per the GPL.


Fire up Ubuntu and run the command

sudo apt-get build-dep $package
where package=whatever package you want.

then do 
sudo apt-get source $package
to get the source for that package.

example:
sudo apt-get build-deb abiword
sudo apt-get source abiword.



How can i get all the packages of ubuntu?
Because i have download the source iso of fedora,but i can not find any iso source of ubuntu.
If i do as you told,that is too hard.

---

### Post by mssever on 2008-03-12
> **cbntrt said:**
> How can i get all the packages of ubuntu?
Because i have download the source iso of fedora,but i can not find any iso source of ubuntu.
If i do as you told,that is too hard.
Ubuntu has no source ISO, AFAIK. Really, the Ubuntu ISOs are mainly to get you up and running. Once you've installed, the ISO isn't worth a whole lot. The Ubuntu way is to follow the instructions posted by az that you quoted. You can get the source for any Ubuntu package that way.

I don't think that there's a way to get the source for everything all at once unless you write yourself a little script to do it, but I can't imagine why someone would want the source for everything all at once, anyway.

---

### Post by pmasiar on 2008-03-12
> **mssever said:**
> I don't think that there's a way to get the source for everything all at once unless you write yourself a little script to do it, but I can't imagine why someone would want the source for everything all at once, anyway.

yes, there is. See answer #6, by az. :-)

I see: that is download by package. Still. :-)

---

### Post by cbntrt on 2008-03-21
> **mssever said:**
> Ubuntu has no source ISO, AFAIK. Really, the Ubuntu ISOs are mainly to get you up and running. Once you've installed, the ISO isn't worth a whole lot. The Ubuntu way is to follow the instructions posted by az that you quoted. You can get the source for any Ubuntu package that way.

I don't think that there's a way to get the source for everything all at once unless you write yourself a little script to do it, but I can't imagine why someone would want the source for everything all at once, anyway.


I said i have download the source iso of fedora 6.0 , see this address: [http://download.fedora.redhat.com/pub/fedora/linux/core/6/source/iso/]("http://download.fedora.redhat.com/pub/fedora/linux/core/6/source/iso/")

I doubt the spirit of UBUNTU------"be kind to people".
I think ubuntu is  not good as fedora in some place.
the source iso of fedora 6.0 has 1147 packages,2.5G.you can also downlaod a single package but not the whole iso  from this address: 
[http://download.fedora.redhat.com/pub/fedora/linux/core/6/source/SRPMS/]("http://download.fedora.redhat.com/pub/fedora/linux/core/6/source/SRPMS/")

I want to get all the packages of ubuntu ,because i want to rebuild a ubuntu and modify it to fit me.
all the packages are in the directory of /pool .find a package from /pool is hard,there are so many packages!
i don't agree with  the reason that putting them in /pool  will be easier to manage  and reduce more network discharge than putting them in /dist which was the original place.

---

### Post by mssever on 2008-03-23
> **cbntrt said:**
> I want to get all the packages of ubuntu ,because i want to rebuild a ubuntu and modify it to fit me.
Now you tell us what you *really* want. You only need the source for the packages that you want to modify. There's no sense in getting the source for packages that can stay the same. You might be interested in checking out [Reconstructor]("http://reconstructor.aperantis.com/").

By the way, the fact that Fedora and Ubuntu have different packaging systems, and thus different ways of customizing the OS, doesn't necessarily mean that one is inferior to the other.

---

### Post by Can+~ on 2008-03-23
> **Quest-Master said:**
> Python is undoubtedly the best language to use for Ubuntu application development though right now.

In fact, it's the best language for any open source project right now. There's a link on the FAQ about that.

About the original subject: Modify in what sense? There's a lot of things out there on ubuntu that can be configured, but it never hurts to look at the source anyway.

---

### Post by bruce89 on 2008-03-23
> **Can+~ said:**
> In fact, it's the best language for any open source project right now. There's a link on the FAQ about that.

Why are thready hijacked like this by Python fans? There is no need to spread your language preferences like this.

If you really want all the source code, see [http://cdimage.ubuntu.com/daily/current/source/](http://cdimage.ubuntu.com/daily/current/source/)

---

### Post by cbntrt on 2008-04-23
> **bruce89 said:**
> If you really want all the source code, see [http://cdimage.ubuntu.com/daily/current/source/](http://cdimage.ubuntu.com/daily/current/source/)

Thank you! I find it!

---

### Post by TwistedLincoln on 2008-04-24
> **mssever said:**
> 
I don't think that there's a way to get the source for everything all at once unless you write yourself a little script to do it, but I can't imagine why someone would want the source for everything all at once, anyway.

There's a pretty huge reason to want the source code for everything -- if you plan on redistributing Ubuntu.  The GPL requires you to provide access to the full corresponding source code when you distribute binaries -- how can you possibly comply with that when you don't have the source yourself.  I'd hate to give out an Ubuntu CD, get asked for the source, and then have to manually fetch the code for each of the thousands of packages inside of Ubuntu...

That link to the full source is really hard to find.  I didn't know about it until I dug up a similar thread to this on these forums.

Canonical should really make this easier to find on their main download page, as Fedora and other distros do.  There are many people who are eager to promote and distribute Ubuntu, but they need to be complying with the GPL as well.  Having a source ISO that's easy to find would go a long way toward making that happen.

---

### Post by mssever on 2008-04-24
> **TwistedLincoln said:**
> There's a pretty huge reason to want the source code for everything -- if you plan on redistributing Ubuntu.  The GPL requires you to provide access to the full corresponding source code when you distribute binaries -- how can you possibly comply with that when you don't have the source yourself.  I'd hate to give out an Ubuntu CD, get asked for the source, and then have to manually fetch the code for each of the thousands of packages inside of Ubuntu...
That's what deb-src lines are for in sources.list. As long as each repository contains proper source packages, you're covered, as far as the GPL goes.

Besides, I think that this is an artificial problem. Why do you need the source for all of Ubuntu's thousands of packages all at once? Isn't it better to fetch them as needed? Someone pointed out that the source for all Ubuntu packages is available in a single location. But there's no need for it to be prominent, because few people will have a need for something like that.

---

### Post by TwistedLincoln on 2008-04-24
> **mssever said:**
> That's what deb-src lines are for in sources.list. As long as each repository contains proper source packages, you're covered, as far as the GPL goes.

Besides, I think that this is an artificial problem. Why do you need the source for all of Ubuntu's thousands of packages all at once? Isn't it better to fetch them as needed? Someone pointed out that the source for all Ubuntu packages is available in a single location. But there's no need for it to be prominent, because few people will have a need for something like that.

Anyone who ever distributes Ubuntu would need all of those thousands of packages at once.  Think about this:

I distribute a copy of Ubuntu to a customer, along with a written offer to provide the source code, as required by the GPL.  This offer is good for at least 3 years (again, so says the GPL), so what if two and a half years later, the customer that I gave a copy of Ubuntu to wants the source code for everything?  He's entitled to it according to the GPL, but my guess is that the repositories aren't going to be running after the distro reaches end-of-life.

There are only two ways you can be sure to comply with the GPL:

1) Provide the customer with the full corresponding source code at the time  you distribute the binaries

2) Make sure you have a copy of the full corresponding source code in your possession at the time you distribute the binaries, that way if they ever ask for it you'll have it ready.

That's my point.  There's a reason the GPL doesn't allow us to just point to a repository and say "just get the code from there if you ever need it."   
You can't rely on it being there for 3 years if you don't control it.  More importantly, it's hardly fair to ask someone to figure out which 1200 packages you gave them on the CD, when the repository has 20,000 packages to choose from...

I'm looking at this from a business perspective.  Certainly most people giving Ubuntu CDs to their friends know that their buddies won't ever ask them for the source code.  

But if a company sells 500 systems with Ubuntu pre-installed, they can't exactly just sit back and hope that no one ever asks (or that someone from Ubuntu or the Free Software Foundation won't ask to see if they are complying with the GPL).

Whenever I distribute Free Software to anyone, I always provide them with the full corresponding source code at the same time.  That way I know I'm covered.  I suggest everyone else do the same.

---

### Post by mssever on 2008-04-24
> **TwistedLincoln said:**
> I distribute a copy of Ubuntu to a customer, along with a written offer to provide the source code, as required by the GPL.  This offer is good for at least 3 years (again, so says the GPL), so what if two and a half years later, the customer that I gave a copy of Ubuntu to wants the source code for everything?  He's entitled to it according to the GPL, but my guess is that the repositories aren't going to be running after the distro reaches end-of-life.I guess this depends on whether you believe that Canonical will still be in business three years from now. Because they're under the same GPL obligation, which means that the source will be available.

> More importantly, it's hardly fair to ask someone to figure out which 1200 packages you gave them on the CD, when the repository has 20,000 packages to choose from...Easy. They simply get the source for all packages on their system, right? Someone who decides they want the source of all the packages you gave them is not the usual case, so why go out of your way to make it easy. As long as it's possible, that's what counts.

> But if a company sells 500 systems with Ubuntu pre-installed, they can't exactly just sit back and hope that no one ever asks (or that someone from Ubuntu or the Free Software Foundation won't ask to see if they are complying with the GPL).

This is a special case. The source is available in one place, as mentioned above. But why clutter the Ubuntu web space with special cases?

---

### Post by pmasiar on 2008-04-25
> **TwistedLincoln said:**
> Anyone who ever distributes Ubuntu would need all of those thousands of packages at once. 

IIRC Canonical  allows ubuntu derivates to only provide diffs (and provides sources for all their code).

---

### Post by TwistedLincoln on 2008-04-25
> **pmasiar said:**
> IIRC Canonical  allows ubuntu derivates to only provide diffs (and provides sources for all their code).

Canonical might allow this, but the GPL does not.  The guy who runs Mepis found this out the hard way after the Free Software Foundation contacted him. 

Not trying to be argumentative here, but this really is important.  The entire point of the GPL and Free Software is lost if people don't fulfill their obligations to distribute the full corresponding source code along with the binaries.  While it might be easy to assume that Canonical will still exist in 3 years (I'm quite sure they will), the same cannot be said for smaller projects.  And when people get into the habit on relying on the upstream vendor to provide the source, rather than provide it themselves like they are supposed to, big problems can occur quickly.

While the person who plans on modifying the entire distribution is surely a special case that doesn't need to be catered to, the person wanting to give out one copy is very typical.  But that person needs access to the full source just as much to stay compliant, and telling them "just go ahead and figure out which of the 20,000 packages you need" doesn't exactly encourage him to promote and distribute that project.

---

### Post by mssever on 2008-04-25
> **TwistedLincoln said:**
> the person wanting to give out one copy is very typical.  But that person needs access to the full source just as much to stay compliant, and telling them "just go ahead and figure out which of the 20,000 packages you need" doesn't exactly encourage him to promote and distribute that project.
Sections 6.c-e of GPL v. 3 allow this. Most, it not all, GPL v2 software actually is licensed as version 2 or later, so it's possible to apply the terms of GPLv3.

---

### Post by pie4freedom on 2008-09-27
[EMAIL="josh1470@hotmail.com"]josh1470@hotmail.com[/EMAIL]thats my msn plz add me so u could help i do lern really quick =]plz reapile or add my msn

---

### Post by rvndrk3233 on 2009-02-02
I agree to these GPL posters. What the hell, man...??

downloading sources for a 2.5GB file, not to mention the WASTED bandwidth involved for a 650MB ISO is obsurd.you are luckly I'm grabbing this image  at home, not somewhere that pays for a T1 line by the minute or by bandwidth.

for example I need the sources to files in /bin and /sbin from the base filesystem package and have to get the whole DVD? These sources are not in the kernel.

half this time these sources are rpm'd or deb'd in such a way that the end user cannot install or access the sources anyway.so what good does this do?? 

If I can't access the SOURCE, the GPL License on the OS, at least in my opinion, is INVALID. THIS IS OUR POINT.

You practically close source it at this point and tell us that you *patched* debian to get your OS made.This MAY be true, BUT.....you didn't give us the patches.besides, what good is a patch if you don't know how to apply it or have to apply it 5000 times?

I'm hardly an expert in C, but when I need something I don't need to waste 5 hours looking for a link to the CURRENT,[ya Im using LENNY you idiots...] relase.

BTW, where is lenny at? I see the isos for intrepid and jackalope in the source link.furthermore, where is SID? 

I stop at v6.Beyond that is too far back.

ETCH
INTREPID (IBEX)
LENNY
SID
JACKALOPE.

Yu are missing a good few sources, I might add.And funny, I can't add the source through synaptic.The box won't check.

---

### Post by mssever on 2009-02-03
> **rvndrk3233 said:**
> I agree to these GPL posters. What the hell, man...??

downloading sources for a 2.5GB file, not to mention the WASTED bandwidth involved for a 650MB ISO is obsurd.you are luckly I'm grabbing this image  at home, not somewhere that pays for a T1 line by the minute or by bandwidth.

for example I need the sources to files in /bin and /sbin from the base filesystem package and have to get the whole DVD?It would be a good idea to read the documentation (or even this full thread) before making these kinds of complaints. apt-get source is your friend, and will get you the source for any program in the repositories that you want, provided you've enabled the source code option for the relevant repositories.

You're right that downloading a 2.5GB image just to get the sources is absurd. So don't do it. There's a much better way, which you would know if you had read this thread before posting in it.> These sources are not in the kernel.Nor should they be. Only kernel stuff belongs in thekernel source tree.

> half this time these sources are rpm'd or deb'd in such a way that the end user cannot install or access the sources anyway.so what good does this do??There's hardly an easier way for an end user to get a usable source package than a .deb. Try apt-get source. It's drop-dead easy. As for RPMs, they aren't intended for use with a Debian-derived system, so it should be no surprise if you have to clear additional hurdles before using them.

> If I can't access the SOURCE, the GPL License on the OS, at least in my opinion, is INVALID. THIS IS OUR POINT.

You practically close source it at this point and tell us that you *patched* debian to get your OS made.This MAY be true, BUT.....you didn't give us the patches.besides, what good is a patch if you don't know how to apply it or have to apply it 5000 times?You can access the source if you follow the published methods. That's in perfect compliance with the GPL.

As for patches, they're included in the source package--usually under debian/patches. It's the distro's responsibility to provide full source code. At that point, they've kept their end of the bargain. It's your responsibility to learn how to use the source--which should start with reading the documentation.

> I'm hardly an expert in C, but when I need something I don't need to waste 5 hours looking for a link to the CURRENT,[ya Im using LENNY you idiots...] relase.

BTW, where is lenny at? I see the isos for intrepid and jackalope in the source link.furthermore, where is SID? The current release is Intrepid, and it's very prominant. If you're using Debian, then you have to look on their site (and complain to them, not us, if their site is hard to use).

> I stop at v6.Beyond that is too far back.

ETCH
INTREPID (IBEX)
LENNY
SID
JACKALOPE.

Yu are missing a good few sources, I might add.And funny, I can't add the source through synaptic.The box won't check.
Um, Intrepid and Jaunty are Ubuntu releases. Etch, Lenny, and Sid are Debian. Ubuntu has no control over the Debian releases and doesn't include Debian repos by default. And vice-versa.

---

### Post by nvteighen on 2009-02-03
> **rvndrk3233 said:**
> 
BTW, where is lenny at? I see the isos for intrepid and jackalope in the source link.furthermore, where is SID?

In Debian, of course. (This post is sent from a Lenny box :))
[http://www.debian.org/CD/torrent-cd/](http://www.debian.org/CD/torrent-cd/) ("testing" is Lenny; "stable" is Etch)

For sid, install any Debian version and then just change the apt sources to "unstable", do "aptitude update" and then "aptitude safe-upgrade".

> I stop at v6.Beyond that is too far back.

ETCH
INTREPID (IBEX)
LENNY
SID
JACKALOPE.

Yu are missing a good few sources, I might add.And funny, I can't add the source through synaptic.The box won't check.

You are missing what OS you're using. Ubuntu != Debian.

---

### Post by shanegowda on 2010-01-05
Hi Guys,

Can any one guide me where can i get source code for ftp(file transfer protocol) utility in ubuntu linux

Thanks in advance :)

---

### Post by Hellkeepa on 2010-01-05
HELLo!

If you've read the thread, you'd seen this post:
[http://ubuntuforums.org/showpost.php?p=67109&postcount=6](http://ubuntuforums.org/showpost.php?p=67109&postcount=6)

Happy syncin'!

---

### Post by ajtiik on 2011-04-25
> **bruce89 said:**
> 

If you really want all the source code, see [http://cdimage.ubuntu.com/daily/current/source/](http://cdimage.ubuntu.com/daily/current/source/)

While that link no longer works today,
if you want the source iso for a release, start here:
[http://cdimage.ubuntu.com/](http://cdimage.ubuntu.com/).

To get to the source CDs for 
Ubuntu 10.04.2 LTS (Lucid Lynx)
you would click on releases, 10.04.2, release, source:

[http://cdimage.ubuntu.com/releases/10.04.2/release/source/](http://cdimage.ubuntu.com/releases/10.04.2/release/source/)

---

