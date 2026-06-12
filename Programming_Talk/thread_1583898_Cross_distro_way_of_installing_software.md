---
title: "Cross distro way of installing software?"
date: 2010-09-28
forum: Programming Talk
---

### Post by papillion on 2010-09-28
So I'm developing a piece of software that depends on another piece of software to function.  When my program starts, it checks to see if the other software is installed and, if it isn't, installs it for the user.  Obviously, on Ubuntu, I can use apt or I can programmatically download and execute the .debs. But what about something more cross-distro?

I don't want the user to have to install *anything* except my program and it will take care of the rest. Is there a common installer that's available on all distros that I could rely on? If not, how would you handle this?

Thanks!
Anthony

---

### Post by nvteighen on 2010-09-28
The most cross-distro thing you'll get is a tarball with a Makefile (Autotools if the case). You have to understand that talking about cross-distro software is actually talking about cross-platform software: each distro is a different OS. OK, you can say the basis underlying Ubuntu and Red Hat is more or less the same (GNU/Linux), but as soon as you get into subtle stuff like glibc versions, default shell, and, of course, what's shipped as default and what's available in the distro's repos (if it works with a repos system)... you start realizing that the best assumption is to consider each distro as separate OSs where portability isn't granted at all (no, not even between Ubuntu and Debian... for instance, you'd have to decide what Debian you're referring to, "stable", "testing", "unstable" or "experimental?).

That's why a source tarball is possibly the best way to have your code be the most portable it can get. I know it's not the "user-friendliest" way to go, but if the code doesn't rely on very arcane stuff, it'll work because it will be natively compiled by the platform (in the case of an interpreted language, there's less chance to run into problems... just specify what version and what libraries you're using). Of course, write comprehensive documentation on how to run this.

Also, a source tarball has another advantage: you allow people to adapt your code to their distros of choice. That's why upstream releases usually don't package things into distro-specific packaging formats: it's better to leave that task to the Ubuntu, Debian, Fedora, Ret Hat, OpenSUSE, etc. mantainers because they will very likely know how to conform to the distro's requirements much better than the upstream maintainer.

---

