---
title: "C# and Mono"
date: 2008-02-22
forum: Programming Talk
---

### Post by DrMega on 2008-02-22
I develop in C# .Net 2.0 at work, and would like to do so for some projects at home. As I use Ubuntu at home MonoDevelop seems to be my only choice. I have two questions as follows:

1. How come the version of Mono runtimes and MonoDevelop in the repositories are so out of date? (Note this isn't critiscm, I appreciate there may be a genuine reason).

2. Is there any reason why I shouldn't download the latest versions from their respective websites?

---

### Post by Jussi Kukkonen on 2008-02-22
> **DrMega said:**
> 1. How come the version of Mono runtimes and MonoDevelop in the repositories are so out of date? (Note this isn't critiscm, I appreciate there may be a genuine reason).

Out of date? Mono 1.2.5 was released just two weeks before Ubuntu 7.10 was released. By the mono release Ubuntu was already far in feature freeze, when new versions are no longer pushed in. So Ubuntu 7.10 has Mono 1.2.4.
Same logic probably applies to monodevelop.

> 
2. Is there any reason why I shouldn't download the latest versions from their respective websites?
Just remember to subscribe to a mono security mailing list -- Ubuntu will no longer take care of security updates for you... If you take a closer look, you'll see there has already been a security update on mono.

You can also suggest mono and monodevelop to be backported, if new version are already in Hardy. I think you can do that in launchpad.

---

### Post by DrMega on 2008-02-22
Ok, now a feel a bit silly. Rather foolishly I'd looked at the version number of MonoDevelop (0.14 released in July last year), then looked on the Internet to find the latest version of Mono (1.2.6).

I must drink more coffee before posing my next question.

---

