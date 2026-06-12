---
title: "how about a BSD-based Ubuntu?"
date: 2006-06-07
forum: Other OS Talk
---

### Post by Abraxias on 2006-06-07
would you be interested in a [BSD]("http://www.bsdwiki.com")-based Ubuntu :?:

if so, which should be used: [FreeBSD]("http://www.freebsd.org/"), [OpenBSD]("http://www.openbsd.org/"), [NetBSD]("http://www.netbsd.org/"),  [DragonFly BSD]("http://www.dragonflybsd.org") :?:

[Mac OS X]("http://www.apple.com/macosx") is partially based on [FreeBSD 5.0]("http://www.freebsd.org/releases/5.0R/readme.html")
[Mac OS X > Darwin > FreeBSD + Mach 3.0]("http://developer.apple.com/opensource/index.html")
[OpenDarwin]("http://www.opendarwin.org/")
[Mach 3.0]("http://www.cs.cmu.edu/afs/cs/project/mach/public/www/sources/sources_top.html")

if it's a [FreeBSD]("http://www.freebsd.org/")-based Ubuntu, can/will it be compatible to [Mac OS X]("http://www.apple.com/macosx") :?:

---

### Post by prizrak on 2006-06-07
What would that possibly accomplish? Ubuntu can be compatible with OS X as OS X can run Linux applications and they both can be networked w/o a problem. If by compatible you mean that OS X programs will run on Ubuntu, well they don't on BSD's so why would they on BSD based Ubuntu?

---

### Post by Kvark on 2006-06-07
It would be pointless to make a new flavor of Ubuntu unless the new flavor provides a significantly different experience for the average user during normal everyday useage.

Would the average user notice any significant difference? Wouldn't it look just like Linux-based Ubuntu?

---

### Post by Abraxias on 2006-06-07
BSD kernels can run on other hardware not currently suppored by Linux kernel.  a BSD-based Ubuntu increases the number of platforms for Ubuntu.

> **prizrak]What would that possibly accomplish? Ubuntu can be compatible with OS X as OS X can run Linux applications and they both can be networked w/o a problem. If by compatible you mean that OS X programs will run on Ubuntu, well they don't on BSD's so why would they on BSD based Ubuntu?[/QUOTE]
hi prizrak,

I'm assuming your questions are all OS X related.

I don't know, if OS X programs (e.g. 3rd party software) would be able to run on FreeBSD said:**
> Fink[/url]'s goal&#8230;  something not exactly similar to [Wine](http://www.winehq.org) but similar to its intentions&#8230;  no need for a 'compatibility layer', if 3rd party OS X software are (from start) designed to be interoperable.

[color=darkbrown](excuse me for the off-topic, how did you manage to use an ***_animated_*** avatar?)[/color]

[QUOTE=Kvark]It would be pointless to make a new flavor of Ubuntu unless the new flavor provides a significantly different experience for the average user during normal everyday useage.

Would the average user notice any significant difference? Wouldn't it look just like Linux-based Ubuntu?
[color="DarkGreen"][size="2"]**what are/were the reasons for creating other Ubuntu flavors (e.g. Kubuntu & Xubuntu)?**[/size][/color]

I can't answer this, but it seems like you might know:  Do average users notice any signficant difference between the other current flavors of Ubuntu?

I don't know what the end results of a BSD-based Ubuntu might look like.  I assume that it could be just as different as the other current flavors of Ubuntu, if it uses a Desktop environment that's currently available ***only*** to BSD.

Ubuntu uses "[*the breadth of **Debian***](http://www.ubuntu.com/ubuntu/relationship)" and [Debian does have a variety of ports](http://www.debian.org/ports/index);  notably, [Non-Linux ports](http://www.debian.org/ports/index.en-gb.html#nonlinux):  [Debian FreeBSD](http://www.debian.org/ports/kfreebsd-gnu) & [Debian NetBSD](http://www.debian.org/ports/netbsd)

the same reasons for "[Why Debian GNU/NetBSD?](http://www.debian.org/ports/netbsd/why)" can be used for '*why a BSD-based Ubuntu?*'

---

### Post by prizrak on 2006-06-07
> hi prizrak,

I'm assuming your questions are all OS X related.

I don't know, if OS X programs (e.g. 3rd party software) would be able to run on FreeBSD; but if you say it can't, then I'll accept that answer. I am not familiar with how interoperable or proprietary (3rd party) software is when it's designed for OS X. it would be nice, if 3rd party OS X software are designed to be interoperable&#8230; sort of the opposite of Fink's goal&#8230; something not exactly similar to Wine but similar to its intentions&#8230; no need for a 'compatibility layer', if 3rd party OS X software are (from start) designed to be interoperable.

That's the issue, OS X software cannot be run on Linux (or even BSD) without a compatibility layer, which has not been created yet to my knowledge. It would be nice if they did many people with iPods would breathe much easier :) 
> what are/were the reasons for creating other Ubuntu flavors (e.g. Kubuntu & Xubuntu)?

Kubuntu uses KDE, which is different from Gnome and is prefered by some users. Xubuntu is XFCE based, which is better for slower hardware. Ubuntu could support more platforms than it does now w/o going to BSD but chooses not to as it is mainly a desktop distro.
> (excuse me for the off-topic, how did you manage to use an animated avatar?)
Didn't do anything special just set an animated .gif as the avatar.

---

### Post by Abraxias on 2006-06-07
[color="darkred"]**off-topic**[/color]
> **prizrak]Didn't do anything special just set an animated .gif as the avatar.[/quote]
[color="darkbrown"]they must've restricted it sometime after you've uploaded yours&#8230 said:**
> 
[quote]You may not upload animated images.
:(

---

### Post by Abraxias on 2006-07-26
back on June 3rd, I asked Canonical, if they had any plans to release a BSD-based Ubuntu;  I just got a reply that I believe is worth sharing:

> On Sat, 2006-06-03 at 15:15 -0700, ;-) wrote:
> just curious, if there are plans to release a BSD-based Ubuntu?
> 
> if so, which will be used:
> FreeBSD
> [http://www.freebsd.org](http://www.freebsd.org)
> OpenBSD
> [http://www.openbsd.org](http://www.openbsd.org)
> NetBSD
> [http://www.netbsd.org](http://www.netbsd.org)
 
We apologise for the late reply as your mail slipped through!
 
At this point, there are no plans to release a BSD-Based Ubuntu.  We do,
however, welcome folks using Ubuntu as a derivative platform.  For an
example of this, consider taking a look at Nexentia
[https://launchpad.net/distros/nexenta](https://launchpad.net/distros/nexenta) or [http://gnusolaris.org/](http://gnusolaris.org/)
 
If you're interested in starting something like this, I suggest you put
a proposal together and talk to a member of the Techincal Board
[https://launchpad.net/people/techboard](https://launchpad.net/people/techboard)
 
Kind regards
Marilize

I didn't know of [NexentaOS]("http://www.gnusolaris.org") ([overview]("https://launchpad.net/distros/nexenta")) nor the [Ubuntu Technical Board]("https://launchpad.net/people/techboard"), till now.

I'm just an OS end-user, maybe others with the know-how might be interested.

---

### Post by FISHERMAN on 2006-07-26
I would love to see a Major and good-working HURD-based distro(but I expect that won't happen in the near future).

---

### Post by az on 2006-07-26
It is already possible to run Debian on two BSDs.  Running a non-linux Ubuntu is already a reality with Nexenta.  

Why is this in the backyard?

Here:
[http://www.debian.org/ports/](http://www.debian.org/ports/)

Non-Linux ports
Debian GNU/Hurd (“hurd-i386”)

The GNU Hurd is a totally new operating system being put together by the GNU group. In fact, the GNU Hurd is the final component which makes it possible to built an entirely GNU OS -- and Debian GNU/Hurd is going to be one such (possibly even the first) GNU OS. The current project is founded on the i386 architecture, but expect the others to follow soon.


Debian GNU/NetBSD (“netbsd-i386” and “netbsd-alpha”)


This is a port of the Debian operating system, complete with apt, dpkg, and GNU userland, to the NetBSD kernel. It is currently in a very preliminary stage, but since NetBSD is a production-level kernel, the usability of Debian GNU/NetBSD should increase rapidly. Currently Debian GNU/NetBSD for Intel x86 is the most advanced flavor, but work has also begun on supporting Alpha-based computers.


Debian GNU/kFreeBSD (“kfreebsd-gnu”)

This is a port of the Debian GNU system to the kernel of FreeBSD. It is still an immature port (although some developers are known to be using it as a production environment for day-to-day work). We expect to meet the technical requirements to release this with sarge+1.

---

### Post by prizrak on 2006-07-26
HURD will never be released. GNU has been working on it since before Linux was around....

---

### Post by matthew on 2006-07-26
> **Abraxias said:**
> back on June 3rd, I asked Canonical, if they had any plans to release a BSD-based Ubuntu;  I just got a reply that I believe is worth sharing:

I didn't know of [NexentaOS]("http://www.gnusolaris.org") ([overview]("https://launchpad.net/distros/nexenta")) nor the [Ubuntu Technical Board]("https://launchpad.net/people/techboard"), till now.
I think Nexenta looks great. It's still pretty new in the development cycle, though. I don't see why someone with the technical knowledge and desire to do so couldn't make a BSD based Ubuntu similar to Nexenta's Solaris based one.

---

### Post by mips on 2006-07-26
I know people don't like Theo Raadt but OpenBSD would be the one to go for. It' just needs a little optimization ;)

---

### Post by RAV TUX on 2006-07-26
Debian already has a BSD based distro out:

Ging
[http://glibc-bsd.alioth.debian.org/ging/](http://glibc-bsd.alioth.debian.org/ging/)

> **1. What is Ging?**

         Ging is a Live system that you can burn on a CD. It is based on     [Debian GNU/kFreeBSD]("http://www.debian.org/ports/kfreebsd-gnu")     (which, as its time, is based on [Debian]("http://www.debian.org/"),     [GNU]("http://www.gnu.org/") and the kernel of     [FreeBSD]("http://www.freebsd.org/")).

  
         Ging consists entirely of free software (as per Debian Free Software     Guidelines) and has a commitment to remain this way.

**2. Where are the screenshots?**

         [Here]("http://glibc-bsd.alioth.debian.org/ging/screenshots") are mines. The people at Softpedia also     [     made some]("http://linux.softpedia.com/progScreenshots/Ging-Screenshot-4354.html") that look realy nice.   
    **3. What does "Ging" stand for?**

         It stands for "Ging Is Not Ging". It is one of the first recursive acronyms     with an implicit contradiction.   
    **4. Where can I obtain Ging?**

         You can download the iso image (and gpg-signed sha1sum) from:   [LIST]
[*][http://gnu.ethz.ch/ging/](http://gnu.ethz.ch/ging/)
[*][http://ftp.gnuab.org/pub/ging/](http://ftp.gnuab.org/pub/ging/)[/LIST]or order cheap CDs online. The following stores are selling them for a fair     near-to-cost price (dont't forget to verify they are selling the latest     version):   [LIST]
[*][PyraSoftware]("http://www.pyrasoftware.com/")
[*][maxtux.co.uk]("http://maxtux.co.uk/")
[*][cheapiso.com]("http://cheapiso.com/index.php?manufacturers_id=71")[/LIST]**5. Can I catch you at IRC?**

         Yes, we hang in #gnu-kbsd at [freenode]("http://www.freenode.net/").   
    **6. How to build an image?**

         Use the scripts from glibc-bsd svn repository (check svn.debian.org), in     trunk/web/ging/.   

 
Gentoo also has one.

so why not a Ubuntu/PC-BSD Distro?


This isn't an option in the poll but I think a Ubuntu/PC-BSD Hybrid would be great.

---

### Post by RAV TUX on 2006-07-26
I am moving the thread to the:

**"Other Linux Talk** Discuss other linux distro's and OS's here."

while not Linux it is a "other...OS"

---

### Post by wdo_will on 2006-07-28
I think *buntu would be a great idea with  *BSD (probably FreeBSD) core.  As long as the devs ported apt over ;).

---

### Post by Lord Illidan on 2006-07-28
Why? What would be the advantages of bsd over a linux kernel? More supported platforms? Come on, then we'd have to delay each release to port to more platforms and test them all, as Debian has to do.

apt-get? BSD already has its own ports system.

hardware support? Linux support is better than BSD so far.

compatibility with mac needs a compatibility layer anyway, so neither BSD nor Linux will have an advantage.

---

### Post by az on 2006-07-29
> **Lord Illidan said:**
> Why? What would be the advantages of bsd over a linux kernel? 

Because it's nice to know you can.  Because choice is good.  Because if someone really didn't like the way the kernel development was going, they could use a different Unix kernel - It certainly is possible to make Ubuntu an OS that is kernel-agnostic.

It's a little like the question we often hear: "why run linux if windows does what you want?"  Mind you there is a big difference: software freedom.  I personaly find the BSD licence less of a guarantee that the software will remain free than the GPL, so I would't say it's the *same* argument, just similar.

---

### Post by Lord Illidan on 2006-07-29
> **azz said:**
> Because it's nice to know you can.  Because choice is good.  Because if someone really didn't like the way the kernel development was going, they could use a different Unix kernel - It certainly is possible to make Ubuntu an OS that is kernel-agnostic.

It's a little like the question we often hear: "why run linux if windows does what you want?"  Mind you there is a big difference: software freedom.  I personaly find the BSD licence less of a guarantee that the software will remain free than the GPL, so I would't say it's the *same* argument, just similar.

Aye, choice is good. But is it wise to sacrifice developers to port Ubuntu over to BSD, when we need more work in the linux direction? When Ubuntu becomes more well known, and we'll have more devs working on it..then a BSD port will be feasible, and welcome enough.

---

### Post by az on 2006-07-30
> **Lord Illidan said:**
> Aye, choice is good. But is it wise to sacrifice developers to port Ubuntu over to BSD, when we need more work in the linux direction? When Ubuntu becomes more well known, and we'll have more devs working on it..then a BSD port will be feasible, and welcome enough.

That's the thing about open source.  People come out of the woodwork.  It's not like the fact that some people would be interested in a BSD project that fewer people will be interested in a linux one.  There is not a finite number of developers that are shared.

Everybody scratches their own itches.  It's a fundemental difference in the development process of open source.  The market truly decides, because the people who make up the market often are also writing code.

---

### Post by Abraxias on 2006-11-26
can someone please move this thread to the [BSD Discussions]("http://www.ubuntuforums.org/forumdisplay.php?f=171") :?:

---

### Post by kahlil88 on 2008-07-22
How about a Hurd-based Ubuntu! I sure hope they finish it before I die. I hear microkernels are where it's at. If any Linux kernel developers read this post, PLEASE HELP FINISH THE HURD!!!

---

### Post by SunnyRabbiera on 2008-07-22
Why isnt desktop BSD listed?
Out of all of them Desktop BSD is the most logical for Ubuntu to go to if the linux kernel ever fell by the wayside.
But this wont happen, Ubuntu is linux not BSD.

---

### Post by mips on 2008-07-22
Because it is basically FreeBSD repackaged. Only the core BSDs are listed.

---

### Post by SunnyRabbiera on 2008-07-22
> **mips said:**
> Because it is basically FreeBSD repackaged. Only the core BSDs are listed.

Yes but it does have more desktop readiness then free bsd.
Even small changes can be very big

---

### Post by cardinals_fan on 2008-07-22
Necromancing!

Anyway, DragonFlyBSD **will be** great.  It's just not quite there yet.  NetBSD is awesome too.

---

### Post by K.Mandla on 2008-07-22
Boy, talk about dredging up the dead. Why not just dig up post No. 1 and tack on a "bump!"

Thread closed.

---

### Post by K.Mandla on 2008-07-22
Boy, talk about dredging up the dead. Why not just dig up post No. 1 and tack on a "bump!"

Thread closed.

---

