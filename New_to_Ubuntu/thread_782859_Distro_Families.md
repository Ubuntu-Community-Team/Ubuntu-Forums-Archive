---
title: "Distro Families"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by Palu on 2008-05-05
Someone once mentioned that you can look at the way Linux has evolved in order to give yourself a vague impression of how similar it might be to cross between distributions. They proceeded to tell me useful information which I have since forgotten.

Redhat
[INDENT]SuSe, others[/INDENT]

Debian
[INDENT]Ubuntu, PCLinuxOS, others[/INDENT]
[INDENT][INDENT]Linux Mint[/INDENT][/INDENT]

No idea how Slackware, Gentoo, Damn Small Linux, FreeBSD, Solaris, gOS, or others would fit in a tree like this, or if the tree is correct...

**Note:** This question is mainly important because I'm a novice Ubuntu user installing Fedora on one machine and want to know how much difficulty I should probably expect. :popcorn: Also, is Fedora = Redhat?

---

### Post by hyper_ch on 2008-05-05
FreeBSD is not a Linux ;)

---

### Post by Golem XIV on 2008-05-05
It's quite a task what you're asking, especially since these things are dynamic.  For example, Mandrake (now Mandriva) was based on RedHat but they're now an independent distro. PCLinuxOS is based on Mandriva, not Debian/Ubuntu.

I'd say check out the [DistroWatch site]("http://distrowatch.com/").  There's a lot of information about most Linux, BSD and Solaris distros.

---

### Post by aheckler on 2008-05-05
Here's [a very detailed chart]("http://upload.wikimedia.org/wikipedia/commons/8/8c/Gldt.svg") of the "Linux families"

[COLOR="Red"][WARNING: large .svg file][/COLOR]

---

### Post by hyper_ch on 2008-05-05
wow

---

### Post by Palu on 2008-05-05
That is beautiful...

Also, if it's within scope of this thread, can someone explain what FreeBSD is if not Linux? Is it still a decendent of Unix?

---

### Post by hyper_ch on 2008-05-05
FreeBSD (as any BSD) is a Unix - although on wikipedia they say it's a Unix-like OS

---

### Post by lemming465 on 2008-05-05
short version:  FreeBSD is a true Unix descendent which shares a lot of similarities but very little code with Linux.

slightly longer version:
In the beginning was Bell Labs, where unix was a research project that escaped and became a legal staff support tool, and then a general purpose OS (early 1970's).  But it was the phone company, a regulated monopoly, and they couldn't sell software.

DARPA paid the University of California-Berkeley to add TCP/IP networking to Unix.  Hence the BSD or Berkeley System Distribution era (early 1980's).  Many commercial versions of Unix sprang up.  In 1991 Linux Torvalds starting writing Linux, initially as an exercise in i386 programming.  By that time, DARPA wasn't funding BSD anymore, and the computer systems research group at UC-Berkeley went on to other stuff.  The last version of the 4.4 BSD release was eventually unencumbered from legacy AT&T code, and spawned (via the Jolitz i386 project) all three of FreeBSD, NetBSD, and OpenBSD.

FreeBSD is the most popular descendent of the left coast flavors of Unix, and uses the BSD license, not the GPL.  Linux has more of a right coast flavor.  Last I knew, FreeBSD was the basis for Yahoo's server farm, while Google is based on Linux.

For a lot more detail, see Peter Salus's book "_A Quarter Century of Unix_".

---

### Post by Sef on 2008-05-05
> FreeBSD (as any BSD) is a Unix - although on wikipedia they say it's a Unix-like OS 

Read [Unix-like]("http://en.wikipedia.org/wiki/Unix-like") to explain why.  Basically UNIX (capital letters) is a trademark, and to get a UNIX certification, a lot of money has to be paid to be certified UNIX.

---

### Post by Palu on 2008-05-05
Just read an article on BSD written for people use to Linux (not that I'm all THAT used to Linux yet, but I'm getting pretty comfortable). I'm very happy with the replies to this thread. I was sure some brilliant person had put a chart together like the one linked to. It can be hard to find software or resources to buy sometimes, but chances are anything needed has been done in the Open Source Community, lol...

If anyone has a little commentary on differences between running Fedora as a server vs running Ubuntu, that would be great. I don't mean a "which is better" because I know that's an annoying request, but rather a "where are the different topic areas I'll need to learn?"

---

### Post by T-Virus on 2008-05-05
Nice distro tree there. :)

I actually answered similar question today right [here]("http://ubuntuforums.org/showthread.php?p=4886206#post4886206")

---

### Post by SunnyRabbiera on 2008-05-05
Well even though fedora and Ubuntu are based around the same things (the same basic core, the same basic GUI in the form of gnome)
they are vastly different.
Ubuntu has a rolling release cycle, meaning there is a update to the whole system is updated every 6 months.
Fedora is more of a standard release cycle, with major updates at least once a year.
For servers I think Fedora is a little better then Ubuntu as Fedora's policies enable it to be used for a long time without serious updates.
Ubuntu is good on its own but to be honest BSD and Debian are better then both of them combined in my opinion when concerning servers...
Both are focussed on stability, Debian etch is intended to be rock solid and only major security updates come into it.
BSD is definitely more secure then linux to be sure as its not as high profile and it certainly surpasses linux on the server.
But If you were to run a server, then Debian might be the better choice as Debian is a tad easier to learn.

---

### Post by Monicker on 2008-05-05
> **Palu said:**
> 

If anyone has a little commentary on differences between running Fedora as a server vs running Ubuntu, that would be great. I don't mean a "which is better" because I know that's an annoying request, but rather a "where are the different topic areas I'll need to learn?"


As far as Fedora goes, I would not run a "production" server using it.  Fedora tends to be bleeding edge, and stability is not its main focus.  Look at Centos (free) or RHEL; not the latest and greatest packages but very stable, with long term support.

Obviously the package management is different. Personally I don't like yum all that much.  There are also some minor differences in how services and networking are handled.

If you get familiar with one distro of linux, you should be able to work reasonably well with another one.  Especially on a server where you do most of the management and maintenance from the command line.

---

### Post by Palu on 2008-05-05
A friend is taking a class where she'll use Drupal on Fedora. I have only used Ubuntu Desktop Edition, but I have a spare machine and decent beginner-level knowledge about servers and networks. The question about distros is more for me to begin getting a vague idea how far Fedora would be from Ubuntu. Since I don't have to worry much about the server being production-level in any way, I may go for Ubuntu Server Edition (for some familiarity) or Fedora (to match EXACTLY what she needs to learn) and then install Drupal. In short, my decision will be Ubuntu or Fedora, depending upon how difficult I think it'd be to set up / learn Fedora.

I guess this thread is a little off-topic now, but I am very much enjoying the chatter with so many helpful people. :)

---

### Post by lemming465 on 2008-05-05
Fedora is to Rehat Enterprise roughly what Debian Sid (unstable) is to Debian releases; the place where R&D and merges from upstream projects happens.  Or what the relationship between regular six-month Ubuntu releases and Ubuntu "long term support" releases is.  The complete history is a lot more complicated.

The main differences between Fedora and Ubuntu are in three areas: package management, system administration, and SeLinux integration.  Pretty much all Linux distributions draw from the same set of upstream projects: Linux kernel, Xorg windowing, GCC compilers, Gnome desktop, KDE desktop, FSF utilities, and so on.  The *BSD group uses BSD kernels and BSD rather than FSF utilities; most of the early FSF stuff was GPL rewrites of existing Unix tools still found in BSD.  If you want to run large applications such as Apache or Drupal, most of your effort will be on the application configuration, and what happens as a Fedora or Ubuntu or FreeBSD system boots and goes multiuser will be nearly irrelevant.

Fedora uses RPM packages, yum package command line, and pirut GUI.  SuSE uses RPM packages and "yast".  Network startup in Fedora, SuSE, and Ubuntu is done with three completely different sets of scripts.  Ubuntu created Upstart; I think Fedora is adopting it for their upcoming release 9.

SeLinux was created at the NSA as a way to get multilevel security into off-the-shelf rather than bespoke operating systems.  If you don't need to know what EAL4+ certification is, count yourself fortunate.  If you are selling stuff to 3-letter government agencies or running large installations of internet facing servers, you probably care about SeLinux.  It's not really a desktop technolog - except in Fedora, where Redhat tests new generations of management tools.

---

### Post by wheels. on 2008-05-05
> **SunnyRabbiera said:**
> Well even though fedora and Ubuntu are based around the same things (the same basic core, the same basic GUI in the form of gnome)
they are vastly different.
Ubuntu has a rolling release cycle, meaning there is a update to the whole system is updated every 6 months.
Fedora is more of a standard release cycle, with major updates at least once a year.
*edited out*

ubuntu is not a rolling release. There is updates and you can upgrade to the next version but that does not make it rolling.
A true rolling release distro would be arch, gentoo or sidux.
A rolling release approach refers to a continuously evolving software system.

---

### Post by bgast1 on 2008-05-05
Why does Free BSD show up in some Linux Magazine's DVD's for Linux people to try?

---

### Post by lemming465 on 2008-05-05
Freebsd is high quality free software, and folks in the IT industry are rampant neophiles who often like to try new things.  Also, the BSD line of Unix has a long and respected history dating back to the late 1970's, and some people just want to know what the fuss is about.  My first intel-based PC back in '93 quad-booted windows 3.1, OS/2, FreeBSD, and Linux.  Linux won out as my main desktop because it was evolving faster, which I think was partly due to the GPL license and partly to the "bazaar" style development model.  But in '96 when I needed a stable platform at the office to put an Apache webserver on, I had them use FreeBSD - a decade ago it was a better server OS than Linux.  These days, it's more a matter of taste.

---

