---
title: "What does 'Stable' really mean?"
date: 2012-03-01
forum: New to Ubuntu
---

### Post by ConchX on 2012-03-01
Hey guys, so I've been wondering for a while now, when I see a distribution that is 'stable', What exactly does it mean? Does it mean the system never crashes? Bug fixes are released faster due to more support? Or that the greatest applications are pre-installed as working versions, without beta releases, which might be buggy?

Or is it all of them? I've experimented with the last one and found out it's not always true :( , as some of the software in my debian stable don't even run properly.

Just curious is all :)
Thanks!

---

### Post by mikewhatever on 2012-03-01
I'd say it's none of the above, since 'never crashes' or 'greatest applications' are not really applicable to software. Stable is relative to beta or alpha, it also means that major changes are no longer introduced, only minor bug fixes and security updates.

---

### Post by Double.J on 2012-03-01
Hi ConchX,

"stable" really is a relative term, as different distro's will have different criteria for what they define as standard. As a general rule the older and more traditional minded distro's have stricter rules regarding stability, such as debian. However remember that it is a relative term - my personal interpretation is that none of the opensource projects are as stable as OS such as Windows and OS X, for daily computing. Again however OS X is only stable when run on Apple hardware; if you try and run it on unsupported hardware, you loose that stability assurance.

Think of "stable" as "tested"; generally speaking, stable variants of distros have their own repositories of packages that are often older versions than in the "current" or "testing" branch. 

Unfortunately, this doesn't mean that you get a rock solid system, for Linux itself it considered a "work in progress"; there all kinds of features that you can turn on and off when compiling a kernel that are new or known to have bugs. "stable" versions of distros often avoid using packages that need these features and generally avoid packages that have known bugs when an alternative is available. This means that "stable" branches progress far more slowly than the current or testing branch.

A lot of problems occur by adding packages not included in the stable repositories, though not the sole cause of problems (as I said a work in progress), it is common for people to add packages they don't need - for example a newer version of firefox.

Linux isn't perfect; it's a part of the choice we make as users. However it grows at an alarming rate - just comparing how 10.04 runs on my hardware now to when it was released is a showcase of this.

In terms of implementation, there is little reason you wouldn't be able to use something such as debian for business - many do. But, just as windows users, using the older packages is a must. 

For simpler OS's such as servers, open source OS, such as freeBSD and Linux are often favorable as they offer stability at a low cost.

Hope it helps!

---

### Post by Zill on 2012-03-01
ConchX:  As far as Debian is concerned, see [The Debian GNU/Linux FAQ - Chapter 3 - Choosing a Debian distribution]("http://www.debian.org/doc/manuals/debian-faq/ch-choosing.en.html").
> Unstable has the most recent (latest) versions. But the packages in unstable are not well tested and might have bugs.

On the other hand, stable contains old versions of packages. But this package is well tested and is less likely to have any bugs.

The packages in testing fall between these two extremes.

---

### Post by snowpine on 2012-03-01
"Stable" in Linux means; no major changes, only bug fixes and security patches.

All Ubuntu releases are considered "stable" for example.

---

### Post by dFlyer on 2012-03-01
> **snowpine said:**
> "Stable" in Linux means; no major changes, only bug fixes and security patches.

All Ubuntu releases are considered "stable" for example.

+1, best on I've read so far concerning stable and opensource.

---

### Post by Double.J on 2012-03-01
> **snowpine said:**
> 
All Ubuntu releases are considered "stable" for example.

I think this depends on your needs - for most home users I'd agree there's not a lot of difference in stability at the end of a version's cycle, but for business use, I'd always recommend the long term support, and I certainly wouldn't consider any ubuntu release stable at the time of release.

It is worth baring in mind that Ubuntu typically introduces the major changes such as Unity in the standard releases so that they have been subject to more real world testing by the time the LTS comes around. 

I like to have two ubuntu's - the current or testing (I got a bit impatient and am using 12.04 since A1) and the LTS for work related things, but then I probably won't switch my 10.04 to 12.04 until the release of 12.10;)

---

### Post by snowpine on 2012-03-01
Ubuntu and Ubuntu LTS are both "stable," the difference being the support period (18 vs. 60 months).

---

### Post by Zill on 2012-03-01
> **snowpine said:**
> Ubuntu and Ubuntu LTS are both "stable," the difference being the support period (18 vs. 60 months).
Except, as pointed out in other posts above, "stable" is a relative term.

Ubuntu Releases (non-LTS) are based on the Debian Unstable branch.

Ubuntu LTS (Long Term Support) releases are initially based on the Debian Testing branch.

[http://www.wikivs.com/wiki/Debian_vs_Ubuntu]("http://www.wikivs.com/wiki/Debian_vs_Ubuntu")

---

### Post by snowpine on 2012-03-01
> **Zill said:**
> Except, as pointed out in other posts above, "stable" is a relative term.

I believe it has a specific meaning (in the context of Linux development), as I defined in my post above.

> **Zill said:**
> Ubuntu Releases (non-LTS) are based on the Debian Unstable branch.

Ubuntu LTS (Long Term Support) releases are initially based on the Debian Testing branch.

So is Debian Stable. :)

---

### Post by Double.J on 2012-03-01
> **snowpine said:**
> I believe it has a specific meaning (in the context of Linux development), as I defined in my post above.


I completely agree with you Snowpine, and I think your definition is pretty much spot on.

I was (probably incorrectly) taking a few liberties and talking about what I'd consider the end user's expectations of "stability", but you're quite correct, it's best to be accurate about these things to reduce confusion.

After all, it's completely possible to have a debian unstable system that never crashes, and an LTS stable release that has persistent problems in one area or another, and this can cause confusion!

---

### Post by snowpine on 2012-03-01
I agree that the word "stable" also has a layperson's definition of "reliable, dependable, bug-free, won't break."

But then it gets confusing because it's easy to imagine a poorly-implemented "Stable" distro that is full of bugs and crashes all the time and therefore "unstable"; or to imagine a well-engineered "Unstable" distro that is dependable and problem-free (ask an Arch fanboy) and therefore "stable."

Fortunately there are several distros (Ubuntu LTS, Debian, Red Hat, CentOS, etc.) that are both "Stable" and "stable." :)

---

