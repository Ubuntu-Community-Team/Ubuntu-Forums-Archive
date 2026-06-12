---
title: "Arch vs. Debian minimal"
date: 2008-10-20
forum: Other OS Talk
---

### Post by bwhite82 on 2008-10-20
I am in the process of installing Arch now (Virtualbox) and I can't help but notice the similarities between an Arch install and a Debian minimal install.

What makes them different? The only thing I can see is that Debian uses dpkg/apt and Arch pacman. While I've found pacman to be very intuitive and easy to use, I can't overlook the fact that Debian has their very huge repos and Arch does not.

Both installs allow you to build a system from the ground up, both require you to configure everything yourself. Am I missing something?

---

### Post by snowpine on 2008-10-20
Arch has a rolling release schedule that gives you the latest and greatest versions of everything. Debian provides new releases very slowly with an emphasis on stability (unless you're using Debian Sid). 

That is one main difference. I'm sure there are others...

---

### Post by bwhite82 on 2008-10-20
> **snowpine said:**
> Arch has a rolling release schedule that gives you the latest and greatest versions of everything. Debian provides new releases very slowly with an emphasis on stability (unless you're using Debian Sid). 

That is one main difference. I'm sure there are others...

You can get the same by using Debian testing (its not the same as Sid), and Debian's testing is actually very stable.

BTW, wanted to point out that I have nothing against Arch, I only seriously want to know the difference. Still installing now.

---

### Post by snowpine on 2008-10-20
> **Soldierboy said:**
> You can get the same by using Debian testing (its not the same as Sid), and Debian's testing is actually very stable.

BTW, wanted to point out that I have nothing against Arch, I only seriously want to know the difference. Still installing now.

I am quite certain that Arch uses newer packages than Debian Testing (Lenny). Never tried Sid so I'm not sure about that.

---

### Post by bwhite82 on 2008-10-20
> **snowpine said:**
> I am quite certain that Arch uses newer packages than Debian Testing (Lenny). Never tried Sid so I'm not sure about that.

Hmm...well I had to go and double check what you said at packages.debian.org and my findings are not consistent with yours.

I compared several packages that I can see installing right now in Virtualbox for arch (misc. gnome packages) with Debian testing. They were either the same version or Debian Testing contained newer ones.

---

### Post by snowpine on 2008-10-20
Debian Lenny's packages were "frozen" back in July. This means that Lenny and Arch will drift farther and farther apart over time, since Arch does rolling updates.

Check out distrowatch.com for a list of which versions are in each. For example, Lenny uses Openoffice 2.4.1 and Nautilus 2.20 ([http://distrowatch.com/table.php?distribution=debian](http://distrowatch.com/table.php?distribution=debian)) while the current Arch uses OO 3.0 and Nautilus 2.22 ([http://distrowatch.com/table.php?distribution=arch](http://distrowatch.com/table.php?distribution=arch)).

---

### Post by snowpine on 2008-10-20
Oh, I just re-read your post. You are still installing Arch from the CD, yes? If so, your packages will all get upgraded to the latest versions when you update. :)

---

### Post by bwhite82 on 2008-10-20
It seems that you are right. I did find however newer packages in Debian Testing. But as you say, Testing was frozen so it will drift apart. Ok, any other differences?

---

### Post by bwhite82 on 2008-10-20
> **snowpine said:**
> Oh, I just re-read your post. You are still installing Arch from the CD, yes? If so, your packages will all get upgraded to the latest versions when you update. :)

No, FTP installation.

---

### Post by bwhite82 on 2008-10-20
Well it seems that the Arch wiki had the answer:
[http://wiki.archlinux.org/index.php/Arch_vs_Others#Arch_vs_Debian_GNU.2FLinux](http://wiki.archlinux.org/index.php/Arch_vs_Others#Arch_vs_Debian_GNU.2FLinux)

> Debian is a much larger project and community and features stable, testing, and unstable branches, offering over 18,000 binary packages. Arch does not 'split' their packages into -dev and -common as Debian does, therefore, Arch repositories will seem much smaller. Debian has a more vehement stance on free software. Arch is more lenient when it comes to 'non-free' packages as defined by GNU. Debian's design approach focuses more on stability and stringent testing. Arch is focused more on the philosophy of simplicity, minimalism, and offering bleeding edge software. Arch packages are more current than Debian Stable and Testing, typically being about equal with Debian unstable. Both Debian and Arch offer well-regarded package management systems. Arch is a rolling release, whereas Debian Stable is released with "frozen" packages. Debian is available for many architectures, including alpha, arm, hppa, i386, ia64, m68k, mips, mipsel, powerpc, s390, and sparc, whereas Arch is i686 and x86_64 only. Arch provides more expedient support for building custom, installable packages from outside sources, with a ports-like package build system. Debian does not offer a ports system, relying instead on its huge binary repositories. **The Arch installation system only offers a minimal base, transparently exposed during system configuration, whereas Debian's methods offer a more automatically configured approach** as well as several alternative methods of installation. 

Though I disagree with the bolded item for a Debian Minimal install.

---

### Post by bwhite82 on 2008-10-20
Ok, will offer some initial impressions because everything is so fresh in my mind.

-I used the ArchWiki Beginner's Guide to install with the FTP Install ISO. This guide was an excellent resource, relatively up-to-date and worked flawlessly and most importantly covered every single thing that was presented during the install.

+1 Arch

-A few times now I've searched google for various things relating to Arch, every time google's top results were either the Arch Wiki or Arch Forums. All times I have searched, have brought back something that directly related to what I was looking for.

+1 Arch

-I encountered absolutely zero issues from installation to boot-up into the new Gnome desktop. I do believe that this is a first for me for a minimal-type install.

I've answered my own question with the whole vs. Debian Minimal because I do believe that I couldn't boot into Gnome when I first did their Debian's Minimal install, I think this was largely due to not being able to find good or up-to-date documentation.

+1 Arch

After all of these installs of various distros in Virtualbox, I think I have finally found a viable alternative to Ubuntu. I love the transparency of Arch, the excellent documentation and have heard good things about the community as well. I shall have to do a Hard drive install tomorrow and migrate from Ubuntu. Thanks for the insight snowpine.

---

### Post by jseiser on 2008-10-20
arch handles its configuration files differently.  Better in my opinion.  It is more like BSD systems i think.  like you edit a rc.conf for static ips, dns info, daemons to start/blacklist.  Arch also allows for a good source install of packages that are not in teh 'core' repo.  They are called pkgbuilds and they are great.  you can modify a line in there to disable /enable certain features without having to do all the ./configuire make make install, and with ABS it will update them etc for you just like it was a regular package.

so the config scripts and ABS make arch different.

---

### Post by Rumor on 2008-10-20
> **Soldierboy said:**
> 
After all of these installs of various distros in Virtualbox, I think I have finally found a viable alternative to Ubuntu. I love the transparency of Arch, the excellent documentation and have heard good things about the community as well. I shall have to do a Hard drive install tomorrow and migrate from Ubuntu. Thanks for the insight snowpine.

Welcome to Arch! Don't forget to stop by the forums and say [hi]("http://bbs.archlinux.org/viewtopic.php?id=32421")!

I think you will find the Arch community is a very friendly place. Many current Arch users (including myself) migrated to Arch from Ubuntu.

---

### Post by chucky chuckaluck on 2008-10-20
+1 on the quality of arch's documentation. it is vividly clear and gets right to it. it's probably one of the few distros where "RTFM" is an actually helpful suggestion.

---

### Post by FLCLFan on 2008-10-20
> **snowpine said:**
> 
Check out distrowatch.com for a list of which versions are in each. For example, Lenny uses Openoffice 2.4.1 and Nautilus 2.20 ([http://distrowatch.com/table.php?distribution=debian](http://distrowatch.com/table.php?distribution=debian)) while the current Arch uses OO 3.0 and Nautilus 2.22 ([http://distrowatch.com/table.php?distribution=arch](http://distrowatch.com/table.php?distribution=arch)).

Actually arch has Nautilus 2.24 in testing and will be put in extra very soon.

So lets just say Nautilus 2.24 and make make arch look even better, ok? ;)

---

### Post by snowpine on 2008-10-20
Slightly off-topic, but does anyone have an opinion which would be better (Debian or Arch) for an Atom-based Asus eee PC 900?

---

### Post by sethvath on 2008-10-20
Are people picking a minimal system for one of the Asus EEEpc or generally want a min system to avoid bloat? If its the latter I would rather go with gentoo and compile everything the way I want it. 

Gentoo on a 1.6Ghz 901 would work but I've heard complains about how long it takes to "emerge".

---

### Post by kpkeerthi on 2008-10-21
Arch should not be compared to Debian Sid. In Debian Sid, packages are built as they are released upstream and added to the repositories and tested there. While in the case of Arch, packages are built, tested in a separate 'testing' repository and only when they are considered stable they are moved to the main repositories. Arch rolls but contains only tested & stable packages. Debian Sid rolls but contains untested unstable packages. 

1. Arch + Main repositories = Stable 
2. Arch + Testing repository = Unstable, like Debian Sid.

Most users will choose option 1, the default setup, with the stable repos. If you are a tester or more adventurous and want Debian Sid like bleeding-edge packages use option 2 with the testing repository. 

* I use the word 'unstable' loosely here. It means untested and has nothing to do with the package's or system's stability (though in reality unstable packages may compromize system stability :) )

---

### Post by basenvironment on 2008-10-21
> **kpkeerthi said:**
>  Debian Sid rolls but contains untested unstable packages. 

> **kpkeerthi said:**
> 
* I use the word 'unstable' loosely here. It means untested and ...
Then aren't you using two words with the same meaning in the above quote?

How long is a package in arch 'testing' tested and by how many users before it moves to arch 'main'?

Packages in debian testing have been tested so I would think 
Arch + Main repositories = Debian Testing
Arch + Testing repository = Debian Sid

Debian has expermental repo for anything that is...well...experimental and likely to cause problems so things are not just dumped into unstable without thought either.

---

### Post by Rumor on 2008-10-21
> **snowpine said:**
> Slightly off-topic, but does anyone have an opinion which would be better (Debian or Arch) for an Atom-based Asus eee PC 900?

I've not tried Debian on my eee (901). I am running Arch on it with no problems.

There are some good resources at your disposal for installing and tweaking your Arch install. 
A (currently) [46 page thread]("http://bbs.archlinux.org/viewtopic.php?id=39375") in the Arch forums for installing on the eee, and a [good article in the wiki]("http://wiki.archlinux.org/index.php/Installing_Arch_Linux_on_the_Asus_EEE_PC") which consolidates much of the info from that same thread.

---

### Post by basenvironment on 2008-10-21
> **snowpine said:**
> Slightly off-topic, but does anyone have an opinion which would be better (Debian or Arch) for an Atom-based Asus eee PC 900?
Debian has a eeepc team...

[http://wiki.debian.org/DebianEeePC?highlight=(eee](http://wiki.debian.org/DebianEeePC?highlight=(eee))

[http://wiki.debian.org/Teams/DebianEeePC?highlight=(eee](http://wiki.debian.org/Teams/DebianEeePC?highlight=(eee))

---

### Post by snowpine on 2008-10-21
Wow, thanks for the links guys! I got the new eee with the 160gb drive for purposes of multi-booting, so maybe I will try both Arch *and* Debian.

---

### Post by wolfen69 on 2008-10-21
> **Rumor said:**
> I've not tried Debian on my eee (901). 

i'm running [DebianEeePC]("http://wiki.debian.org/DebianEeePC") on my eee, did a minimal install, (had to because of my 2gig drive) put xfce on it and i absolutely love it.

one of these days i might try arch on a spare drive though.

---

### Post by mentallaxative on 2008-10-22
> **Soldierboy said:**
> I am in the process of installing Arch now (Virtualbox) and I can't help but notice the similarities between an Arch install and a Debian minimal install.

What makes them different? The only thing I can see is that Debian uses dpkg/apt and Arch pacman. While I've found pacman to be very intuitive and easy to use, I can't overlook the fact that Debian has their very huge repos and Arch does not.

Both installs allow you to build a system from the ground up, both require you to configure everything yourself. Am I missing something?

While I admit that the Debian repositories are large, I am not sure if the Arch repos are so small as to be a disadvantage. A direct comparison of number of packages is not clear-cut; Debian splits some its packages while Arch tends to leave them whole.

I find the combination of the official and community repos and AUR to be quite sufficient for my needs.

---

### Post by SomeGuyDude on 2008-10-22
> **mentallaxative said:**
> While I admit that the Debian repositories are large, I am not sure if the Arch repos are so small as to be a disadvantage. A direct comparison of number of packages is not clear-cut; Debian splits some its packages while Arch tends to leave them whole.

I find the combination of the official and community repos and AUR to be quite sufficient for my needs.

If you count AUR I haven't found a single thing that I couldn't install straight from the repos. Thus far I have yet to do any actual compiling and installing.

---

### Post by b9anders on 2008-10-23
> **basenvironment said:**
> Then aren't you using two words with the same meaning in the above quote?

How long is a package in arch 'testing' tested and by how many users before it moves to arch 'main'?

Packages in debian testing have been tested so I would think 
Arch + Main repositories = Debian Testing
Arch + Testing repository = Debian Sid

Debian testing is not quite as bleeding edge however.

The main differences in arch's favour is solid and more accessible documentation (debian has a huge documentation but I always found it hard to find what I needed there), simple configuration as 95% of any configuration you want to do is gathered in a handful of well documented and annotated files and ABS/AUR, which is the most elegant system for building from source I've seen on linux.

In Debian's favour are the huge repositories and better out-of-the-box configuration.

---

### Post by b9anders on 2008-10-23
> **SomeGuyDude said:**
> If you count AUR I haven't found a single thing that I couldn't install straight from the repos. Thus far I have yet to do any actual compiling and installing.

AUR is not a repository. Anything you install from there is done by compiling from source.

---

### Post by b9anders on 2008-10-23
> **mentallaxative said:**
> While I admit that the Debian repositories are large, I am not sure if the Arch repos are so small as to be a disadvantage. A direct comparison of number of packages is not clear-cut; Debian splits some its packages while Arch tends to leave them whole.

I find the combination of the official and community repos and AUR to be quite sufficient for my needs.

Although repos+aur more than fulfil my needs (another plus for aur is the access to even more bleeding edge packages as there are a lot of development builds available if you want to be on the absolute bleeding edge. Easier to manage than plugging into experimental in debian, imo), there's no getting around that Debian just has a larger selection available.

---

