---
title: "Close to UNIX"
date: 2008-12-09
forum: Other OS Talk
---

### Post by jus71n742 on 2008-12-09
So if I wanted to get as close as possible to a UNIX enviroment (like original UNIX ...no GUI etc etc) would Free BSD or Open BSD be a good idea since A) they are free  B) thats all I can find when searching the topic.

Any ideas?

---

### Post by jocko on 2008-12-09
Why not just a minimal ubuntu install?
Get the alternate cd and use it to install a command line system...

---

### Post by cariboo on 2008-12-09
Linux is Unix-like so I would suggest giving the Ubuntu server version a try. If you don't set up any servers during installation, you will have a command line system, and you can add things from there.

Jim

---

### Post by jocko on 2008-12-09
> **cariboo907 said:**
> Linux is Unix-like so I would suggest giving the Ubuntu server version a try. If you don't set up any servers during installation, you will have a command line system, and you can add things from there.

Jim

Unless he really want to use it as a server, what's the point of installing a server system (which, as far as I know, comes with server applications preinstalled and a kernel which is optimized for servers)?
A minimal install is probably better if all he wants is a command-line only system...

---

### Post by HotShotDJ on 2008-12-09
I can't really comment on the BSD's, since I don't have any experience with them.  I DO know that the are direct decedents of UNIX, which Linux is not.  If Unix-like is what you are looking for, you would probably want to give [Slackware Linux]("http://slackware.com/") a try.  It has been called the most Unix-like Linux distribution available.  Just don't install any GUI's.

---

### Post by kellemes on 2008-12-09
> **hotshotdj said:**
> if unix-like is what you are looking for, you would probably want to give [slackware linux]("http://slackware.com/") a try.  It has been called the most unix-like linux distribution available.  Just don't install any gui's.

+1

---

### Post by bapoumba on 2008-12-09
Moved to Other OS Talk.

---

### Post by linux_tech on 2008-12-09
Beyond Unix, BSD System V, Slackware is the most like Unix to me.
Arch is also unixlike.  More scripting, shell interaction, editors, 
cmdline. Also more manual configuration of hardware.

---

### Post by radu_chindris on 2008-12-09
Depends on what you want to use it for.
If you want to deploy a server OS, choose any linux distro (ubuntu server, centos, fedora, open suse, you name it) and tweak it to your needs OR go with any BSD flavor or OpenSolaris. If you want to develop userland programs, it doesn't really matter what you choose since all of them are POSIX compliant, AFAIK. If you want to get into kernel mode and build modules or play with the kernel code, I go with *BSD or OpenSolaris since you'll find good quality documentation.

---

### Post by ibutho on 2008-12-09
> **jus71n742 said:**
> So if I wanted to get as close as possible to a UNIX enviroment (like original UNIX ...no GUI etc etc) would Free BSD or Open BSD be a good idea since A) they are free  B) thats all I can find when searching the topic.

Any ideas?

Try Solaris because it has a lot of original UNIX Sys V code. Another alternative is the BSDs. Linux is a good alternative to both and depending on the distro, you can install it without the GUI and other stuff you do not need.

---

### Post by DeadSuperHero on 2008-12-09
I have to say, Solaris is an awesome UNIX. Takes some experience, but now that OpenSolaris has various bits of the GNU userland, the learning curve is much easier.

Provided, of course, that you can get your hardware to work with it. It took awhile for me to figure out how to get the network card working, but by gum, I got it!

---

### Post by MisfitI38 on 2008-12-09
The closest you can get to UNIX is to use genuine UNIX.
Solaris is genuine UNIX, and offers openSOLARIS, which is free of charge.
HP-UX and AIX are UNIX as well, but may not be as convenient to obtain for you, being proprietary.

If you want a GNU/Linux distribution that is a bit more like original UNIX, then try CRUX, Slackware, or Arch.

All of the BSD's are UNIX clones as well, each offering their own version of what they consider ideal.

---

### Post by Sorivenul on 2008-12-09
OpenSolaris or any of the BSD systems (I prefer FreeBSD) would work fine.
Or, if you want, you could try [v7/x86]("http://www.nordier.com/v7x86/").

---

### Post by cardinals_fan on 2008-12-09
OpenSolaris is a direct System V descendant.  NetBSD, FreeBSD, and DragonFlyBSD are all excellent.  Slackware is the most UNIX-like Linux distro.

---

### Post by cmay on 2008-12-09
i use open-solaris. i can reccomend that. the belenix distrubution you can run off an usb stick as  a live cd so if you want to try that out i can reccomend it also . i use that myself.  i called sun Denmark and had shipped a solaris 10 dvd for free so they are very nice and the downloads of the open-solaris distribution are also free and easy. i agree that being  real unix systems any of the bsd already reccemended is good choiche even i do not use them myself yet .the request about being no GUI is a matter of just using no desktop enviroment. but there is a nice alteranative to the real unix systems and some other projects that may interest you like plan 9 from bell labs which should be the new improved unix as they say on their homepage and minix which is a unix like system but still with out a gui.those two are only for research or worht knowing about for more academic purposes.
but i think everyone that is facinated by computers and the histrory would think minix and plan 9 is exiting to learn about. while they are not ment to be on stable production machines or your main desktop systems. good luck to you and happy unix hunting ;)

---

### Post by kk0sse54 on 2008-12-09
> **cmay said:**
> some other projects that may interest you like plan 9 from bell labs 

What really looks interesting is [Glendix]("http://glendix.org/"), 
> In this project, we decouple Linux from GNU utilities, and port Plan 9 user-space applications to run on the Linux kernel. In summary, we are combining the Plan 9 user-space with the Linux kernel-space - resulting in a hybrid operating system.

---

### Post by WaeV on 2008-12-09
Arch is unix-like, fast, and is command-line after install.

---

### Post by jus71n742 on 2008-12-09
So if I want something that is directly from UNIX then BSD or Solaris...if I want UNIX like Linux then SLackware w/o GUI...k got it lol.  Really didn't expect that many replies thanks guys

---

### Post by Sorivenul on 2008-12-09
> **jus71n742 said:**
> Really didn't expect that many replies thanks guys
There is a lot of information about a lot of options, thus, a lot of opinions and ideas as well.

Good luck!

---

### Post by cardinals_fan on 2008-12-09
> **jus71n742 said:**
> So if I want something that is directly from UNIX then BSD or Solaris...if I want UNIX like Linux then SLackware w/o GUI...k got it lol.  Really didn't expect that many replies thanks guys
I personally think that **everyone** *with the proper motivation* should try a BSD.  FreeBSD, NetBSD, and OpenBSD are the biggest and best-known (my favorite being the uber-clean NetBSD), but DragonFlyBSD is definitely worth a look.  The new HAMMER file system is obscenely cool.

---

### Post by fistfullofroses on 2008-12-09
*nix systems are very diverse. UNIX is more of an OS style than it is an actual operating system, because AT&T is no longer maintaining it. Descendant versions of UNIX proper from Bell Labs:

AIX
HP-UX
Solaris
V7
Mac OS X
z/OS
FreeBSD
NetBSD
OpenBSD
OpenDarwin
Nexenta
SchiliX
Belenix
Tru64
IRIX

Unix-Like systems:
GNU/Linux (slackware, crux, and arch in particular)
Fiwix
MINIX3
GNU Hurd

---

### Post by cardinals_fan on 2008-12-10
[http://upload.wikimedia.org/wikipedia/commons/7/77/Unix_history-simple.svg](http://upload.wikimedia.org/wikipedia/commons/7/77/Unix_history-simple.svg)

---

### Post by WaeV on 2008-12-10
> I personally think that everyone with the proper motivation should try a BSD. FreeBSD, NetBSD, and OpenBSD are the biggest and best-known (my favorite being the uber-clean NetBSD), but DragonFlyBSD is definitely worth a look. The new HAMMER file system is obscenely cool.

Why is that?

---

### Post by cardinals_fan on 2008-12-10
> **WaeV said:**
> Why is that?
If you mean the last comment, read the following:

[http://apollo.backplane.com/DFlyMisc/hammer01.pdf](http://apollo.backplane.com/DFlyMisc/hammer01.pdf) (a fantastic and recent overview)
[http://cisx1.uma.maine.edu/~wbackman/bsdtalk/bsdtalk053.ogg](http://cisx1.uma.maine.edu/~wbackman/bsdtalk/bsdtalk053.ogg) (a somewhat old interview with Matthew Dillon)
[http://leaf.dragonflybsd.org/cgi/web-man?command=hammer&section=ANY](http://leaf.dragonflybsd.org/cgi/web-man?command=hammer&section=ANY) (a man page)

If you're interested in DragonFlyBSD, read this as well: [http://www.dragonflybsd.org/docs/goals.shtml](http://www.dragonflybsd.org/docs/goals.shtml)

---

### Post by WaeV on 2008-12-10
I meant the first comment.

---

### Post by smartboyathome on 2008-12-10
You know, I remember reading about a new version of Unix being released for i386, so you can technically use the real deal (no need to use "-like" ones like BSD, Linux, OS X, etc).

---

### Post by WaeV on 2008-12-10
I thought BSD was considered unix and not just unix-like.  ?

---

### Post by smartboyathome on 2008-12-10
> **WaeV said:**
> I thought BSD was considered unix and not just unix-like.  ?

Its considered as following the Unix STANDARD (not Unix itself) since thye paid for the evaluation to be done. Linux is considered Unix LIKE because no one has paid for testing to be done to see if it follows the standards for Unix.

---

### Post by WaeV on 2008-12-10
Oh, I see.  Does Linux meet Unix standards, even though it hasn't been evaluated for the classification?

---

### Post by smartboyathome on 2008-12-10
> **WaeV said:**
> Oh, I see.  Does Linux meet Unix standards, even though it hasn't been evaluated for the classification?

It mostly does, though there are some differences.

---

### Post by basenvironment on 2008-12-10
leaving out a bunch of detail but hitting the high-lights....

USL/BELL/AT&T were the original creators/owners of unix but they shared the code to get others to help develop it. They later tries to claim that the others had no right to it.

A lawsuit ensued and the outcome was that both had rights to at least some of the code and they could take their code and go their separate ways. So then you had BSDs and you had UNIX and they have diverged since then but share a common heritage.

novell bought at&t

The UNIX trademark name was transferred to the OPEN GROUP who has developed the standard a product must meet to use the trademark.

The business of licensing unix source code was put in the hands of SCO.

A company can obtain a license to the source code and/or the trademark name. That is why many companys have their own UNIX operating system. A company can develop their own unix and relicense it to their customers.

):P

---

### Post by cardinals_fan on 2008-12-10
> **WaeV said:**
> I meant the first comment.
Most of the **real** BSDs (not FreeBSD remixes like PC-/DesktopBSD) are extremely clean systems that are very fun to play with.  It's a good way to discover new things and play around with something different.

---

### Post by Sorivenul on 2008-12-10
> **cardinals_fan said:**
> Most of the **real** BSDs (not FreeBSD remixes like PC-/DesktopBSD) are extremely clean systems that are very fun to play with.
I agree, but would add they are equally fun to *work* with. I haven't run into half the problems on my FreeBSD install as I have on any Linux install.  Granted, my problems on Linux are few, but are still more than my BSD issues.

---

### Post by cardinals_fan on 2008-12-10
> **Sorivenul said:**
> I agree, but would add they are equally fun to *work* with. I haven't run into half the problems on my FreeBSD install as I have on any Linux install.  Granted, my problems on Linux are few, but are still more than my BSD issues.
True.  Once set up, most BSD systems will just keep on ticking.

---

### Post by andr100 on 2008-12-11
> **smartboyathome said:**
> It mostly does, though there are some differences.

What diference do you meen?

---

### Post by smartboyathome on 2008-12-11
> **andr100 said:**
> What diference do you meen?

I mean that there are differences in how some stuff is stored, compiled, etc. I don't know the specifics, but I just know that there are some differences from the Unix standard.

---

### Post by cmay on 2008-12-11
i read and think it is still so that there is a specification made after a unix war where different unix systems divided them self into different standards which was not always compatible whit each other and this was actually almost destroying the unix systems after a while so they made a standard which from a programmers view looks pretty much the same if it is bsd or system v unix or linux . i read many of the man pages while studying c and i think there is not that much difference. then again i am not a programmer so i cant say for sure none of this is the truth. its just what i been able to pick up about unix and the standards.

---

### Post by MisfitI38 on 2008-12-13
It is almost too easy to over-simplify UNIX, its heritage, and its history. It really is quite a long, and sometimes convoluted, story..sort of like pealing an onion, only to find another layer beneath- and so on.
Suffice to say, that GNU/Linux is UNIX-like, as are the *BSD's..
In my experience, CRUX, Arch and Slack are more 'UNIXy' than most others, for a few reasons; they all focus on the importance of the simple base, GUI's are always an afterthought, and all adhere pretty closely to the [worse is better]("http://en.wikipedia.org/wiki/Worse_is_better") mentality, inherent to UNIX.

---

### Post by x3roconf on 2008-12-13
openbsd just sucks

---

### Post by Sorivenul on 2008-12-13
> **x3roconf said:**
> openbsd just sucks
What's your justification?

Best be careful saying mean things like that with cardinals_fan and myself around...  ;)

---

### Post by Bachstelze on 2008-12-13
And myself.

---

### Post by kk0sse54 on 2008-12-13
> **x3roconf said:**
> openbsd just sucks

You can't make an absolute statement like that without evidence to backup it up unless you have the agenda of the common troll...

Otherwise I've been actually quite likely OpenBSD lately, just installed yesterday, however I still find netBSD to be my favorite *BSD.

---

### Post by cardinals_fan on 2008-12-13
> **x3roconf said:**
> openbsd just sucks
I'm not a big OpenBSD fan, but you really should justify that kind of statement.  OpenBSD has both positive and negative attributes, and you could make your point a lot better if you actually presented reasons instead of a blank insult.

---

### Post by mips on 2008-12-13
> **c!oud said:**
> you can't make an absolute statement like that without evidence to backup it up unless you have the agenda of the common troll...


+1

---

### Post by handy on 2008-12-13
I really liked PC-BSD, just how close to UNIX it or any of the other BSD's are I don't know, I've never had a need to research it, 'cause I've never had a reason to care about it.

I haven't read this thread, hopefully someone has posted a genuinely informed answer to the question.

---

### Post by handy on 2008-12-13
> **MisfitI38 said:**
> It is almost too easy to over-simplify UNIX, its heritage, and its history. It really is quite a long, and sometimes convoluted, story..sort of like pealing an onion, only to find another layer beneath- and so on.
Suffice to say, that GNU/Linux is UNIX-like, as are the *BSD's..
In my experience, CRUX, Arch and Slack are more 'UNIXy' than most others, for a few reasons; they all focus on the importance of the simple base, GUI's are always an afterthought, and all adhere pretty closely to the [***_worse is better_***]("http://en.wikipedia.org/wiki/Worse_is_better") mentality, inherent to UNIX.

Thanks for the link, I found it to be very interesting.

---

### Post by fistfullofroses on 2008-12-14
A fork is still real UNIX ppl.

---

### Post by fistfullofroses on 2008-12-14
AIX, HP-UX, Solaris, V7, Mac OS X, z/OS, *BSD, Darwin, Nexenta, SchiliX, Belenix, Tru64, IRIX, and so on are all "real" UNIX systems. There is not one "true" UNIX system out there. There are many. If you use any of the original AT&T code, and your system functions in a UNIX-like way, you are using a "real" UNIX system. Anyway, all of those listed are direct AT&T descendants, and as such represent UNIX in the modern computing era. V7 is the one you are talking about though. It's antiquated in comparison to Linux or BSD, and its hardware support is seriously lacking.

---

### Post by chachawpi on 2008-12-15
OpenBSD makes an awesome secure web server.  You don't really have to configure anything, because the devs design the OS with the assumption that you aren't a six-figure security expert.  I couldn't imagine using it as a desktop OS though.

---

### Post by mips on 2008-12-15
> **chachawpi said:**
>  I couldn't imagine using it as a desktop OS though.

It actually makes a nice snappy desktop with openbsd. Had it on my laptop with Intel chipset.

---

### Post by Sorivenul on 2008-12-15
> **mips said:**
> It actually makes a nice snappy desktop with openbsd. Had it on my laptop with Intel chipset.
Me too.

---

