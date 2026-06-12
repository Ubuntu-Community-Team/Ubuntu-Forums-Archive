---
title: "Distro for corporate environments?"
date: 2009-02-02
forum: Other OS Talk
---

### Post by nautilusny on 2009-02-02
Hi n00b here.

I have used Solaris, etc. in the past as a sysadmin/programmer in some large corporations in the 90s but have been away from *nixes in the past few years. With the recent downturn, I may have to look for another job soon. I already have a proper 4-year degree in Computers so I could pick up things pretty quickly.

So I thought I would brush up on my skills - programming/sysadmin, etc - and I may have to install development environments as well as server software as necessary. What is the popular distribution (or Unix flavor) in the commercial market? What   programming skills are more marketable these days? What other websites are useful for someone who is trying to return to the 'fold'?

---

### Post by cardinals_fan on 2009-02-02
Red Hat Enterprise Linux (RHEL) is a huge player.  CentOS is a free clone.  SUSE Linux Enterprise Desktop (SLED) is pretty big too.

---

### Post by Crafty Kisses on 2009-02-02
I think SuSE Enterprise is really good, not sure about Red Hat, but I've heard great things about SuSE Enterprise.

---

### Post by Grant A. on 2009-02-02
> **cardinals_fan said:**
> Red Hat Enterprise Linux (RHEL) is a huge player.  CentOS is a free clone.  SUSE Linux Enterprise Desktop (SLED) is pretty big too.

I second RHEL and SLED, although you may want to get familiar with the SuSE Linux Enterprise Server (SLES).

---

### Post by RS3York on 2009-02-02
There are 2 major players in the corporate environment: Red Hat & Novell.

Of those two, Red Hat Enterprise Linux (RHEL) is basically a server-only distro (even though they sponsor the desktop-friendly Fedora Project and provide some GUI-based packages).  Conversely, Novell ships distros targeting both server and desktop - SUSE Linux Enterprise Server (SLES) & SUSE Linux Enterprise Desktop (SLED) respectively.  Both of Novell's corporate distros are just different, fortified & super-QA'ed, subsets of the openSUSE distro.

As noted cardinals_fan noted, CentOS is a free clone of RHEL.  Canonical's Ubuntu is an up-and-comer in the corporate space - and the advantage (or disadvantage) of Ubuntu is that the version for "enthusiasts" is the same as the "corporate" version.  Some companies also use Debian as a server platform.

The value of being certified on a particular platform is variable on where you live. In the US, Red Hat is the dominant corporate Linux.  Europe is a more level playing field, although Germany still has some extra love for their homegrown (Suse).  Not sure about elsewhere in the world. You should also know that:
1. The Novell/Microsoft agreement seems to have spurred along additional momentum for Novell's offerings so far.
2. As of this post...Red Hat still hasn't laid anyone off.  It could be that they're simply delaying an announcement, but by all indications they appear to be in a position of strength despite the economic slowdown.

As far as programming skills go, the "best" language to know still depends on what you're trying to get done.  As far as scripting goes, Python & Ruby are the popular kids in school right now.  Toolkits...the next version of Qt (4.5) will also have the LGPL as an available license - that should make Qt truly trendy as a cross-platform solution.  Otherwise, C# is gaining traction although some in the F/OSS space seem to oppose it on the basis that it's from Bill's house.

---

### Post by nautilusny on 2009-02-03
Thanks for your responses.

I am in US so it looks like it is going to be a battle between CentOS and OpenSuse assuming that, from a learning/tinkering point of view, they are similar to their 'paid' versions.

Re. programming languages, I was thinking about Java but maybe I should take a closer look at C#.

---

### Post by &#32 Greg on 2009-02-03
CentOS is more server-ish than OpenSuse.

In reality though, most of Linux holds for most distros. Just like if you learn C#, learning Java is easy and vice versa.

---

### Post by maybeway36 on 2009-02-03
CentOS is virtually the same as RHEL. openSUSE is to SuSE Enterprise Linux as Fedora is to Red Hat.

---

### Post by cardinals_fan on 2009-02-03
> **RS3York said:**
> 
As noted cardinals_fan noted, CentOS is a free clone of RHEL.  Canonical's Ubuntu is an up-and-comer in the corporate space - and the advantage (or disadvantage) of Ubuntu is that the version for "enthusiasts" is the same as the "corporate" version.  Some companies also use Debian as a server platform.

I didn't know I was noted :)
> **nautilusny said:**
> 
I am in US so it looks like it is going to be a battle between CentOS and OpenSuse assuming that, from a learning/tinkering point of view, they are similar to their 'paid' versions.

Not a good analogy.  openSUSE is to SLED what Fedora is to RHEL; a testbed for new features officially backed by the company.  Very similar, but not the same.  CentOS is an almost-identical clone of RHEL from a community of volunteers, and is not officially related to Red Hat.

---

### Post by mechanic on 2009-02-03
What happened to Solaris and HP-UX?

mechanic

---

### Post by binbash on 2009-02-04
If you are thinking to work on server environments then you have to play with CEntos and redhat.Dont waste time with suse since i never saw and heard a Suse server for YEARS

---

### Post by fistfullofroses on 2009-02-04
CentOS, Ubuntu/Debian for your distribution

As far as development environments go, a lot of places use in house development software. The most popular open source environments are Netbeans, Eclipse, Kdevelop, and Geany.

Languages that are most popular are Java, Ruby, PHP, Perl, C, and believe it or not Fortran.

Getting back into the fold really isn't hard. Read Slashdot, and attend conferences. You'll be back in no time.

---

### Post by fistfullofroses on 2009-02-04
PS: Slashdot is slashdot.org

No matter the language concentrate on OO (object oriented programming techniques {for C this means looking into objective C and C++)

And, I forgot to mention that Bash is almost a necessity despite it not being oft mentioned (I made the mistake of not learning Bash during college, and I got to the market place only to find out that despite no one mentioning Bash, it was used everywhere! All three of my jobs as a programmer so far have used Bash extensively).

---

### Post by nautilusny on 2009-02-04
Thanks for the clarification on CentOS/OpenSUSE and the programming questions.

I think I'd go with CentOS. My laptop will have a 64 bit Celeron M processor. Are there any caveats in choosing the 64 bit versus the 32 bit OS?

---

### Post by fistfullofroses on 2009-02-06
> **nautilusny said:**
> Thanks for the clarification on CentOS/OpenSUSE and the programming questions.

I think I'd go with CentOS. My laptop will have a 64 bit Celeron M processor. Are there any caveats in choosing the 64 bit versus the 32 bit OS?

There were a while back, not as much anymore. If you are using interpreted languages for development, you shouldn't have any problems at all, but 64bit binaries will not run on 32bit machines. 32bit binaries will often run on 64bit though.

---

