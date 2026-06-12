---
title: "compiling library for armv7"
date: 2011-04-08
forum: Programming Talk
---

### Post by hanlin on 2011-04-08
I am trying to compile a C++ library for the armv7 architecture to be used for an iPad app. However, I am running into some problems:

1. This library has a bunch of dependencies, which are installed on the computer but compiled for i386, not armv7. Is there a way to compile this library despite the fact that the dependencies are not compiled for armv7? I get errors about wrong architecture when I try.

2. I also tried compiling the dependencies manually for armv7. However, this brings about a new problem: some of the dependencies create executables. Since they were compiled for armv7, the executables will not run. Is there a way around this? Maybe somehow compile for both architectures?

I'm kind of new to all of this cross-platform compiling stuff and don't know what is and what isn't possible to do.

---

