---
title: "How to contribute Ubuntu packages?"
date: 2005-09-24
forum: Packaging and Compiling Programs
---

### Post by wantilles on 2005-09-24
I like Ubuntu very much for the following reasons:

- Debian-based
- excellent modularized kernel
- everything can be setup by GUI
- extremely easy maintenance with Synaptic

All the above qualities make it ideal for newbies' computers (like those of my sister or parents for example).

However, it has one major drawback - especially the amd64 port:

**Lack of packages.**

And I am not talking about some trivial packages for special uses. I am talking about fundamental packages no system can do without -> KRename and KMPlayer are good examples among others.

My own machine is an dual-core Athlon64-X2 Toledo 4400+ with 2x1MB L2 cache, running Gentoo amd64, which is a source distribution as you may know -> everything is compiled from source.

With Portage niceness set at maximum, I can be working all day, while the CPUs are compiling at the background, and this does not interfere with my work.

It is a huge potential & power that sits there wasted (for example, a full kernel compile done from scratch, takes under 5 minutes to complete), while it could assist the whole community.

So, my questions - some of them might be stupid - are as follows:

1. I have permanently added the Portage option to keep the binary packages after they have been compiled and installed. Now, could these binary packages (tgz or bz2) be converted into Ubuntu packages and how? Would they work in Ubuntu, assuming the same dependencies are present and installed? Also, how could they be submitted to the official repositories?

2. If the answer to the above question is negative, then could I build a chrooted environment of Ubuntu amd64 inside my Gentoo amd64, and do the work there? How should I proceed with this?

Needless to say that it would be preferable for the first option to work, since it is much too easier and less time-consuming -> more packages can be built and distributed in less time.

If you need more details (such as compiler options in /etc/make.conf) I would be happy to supply them.

Thank you in advance for your time.

---

### Post by bsussman on 2005-09-24
If I understand, translating you question into technical terms:  How do I make debian packages?

This might be a starting point: [http://www.debian.org/doc/manuals/maint-guide/index.en.html]("http://www.debian.org/doc/manuals/maint-guide/index.en.html")

Then getting the ubuntu distribution folks to include it would be the next step.

---

### Post by Xian on 2005-09-24
This is a great Ubuntu resource for beginning packagers: 

[Developer Resources](https://wiki.ubuntu.com/DeveloperResources)

---

