---
title: "Where is hoary/postgres on amd64"
date: 2005-02-22
forum: Repositories &amp; Backports
---

### Post by yatesco on 2005-02-22
Hi,

I have updated my sources.list to include main, restricted, universe and multiverse for amd64.

If I try and install postgres, it states:

Package postgresql is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libpg-perl
E: Package postgresql has no installation candidate

Any ideas?

Col

P.S.  Apologies if this is not the right forum.

---

### Post by yatesco on 2005-02-23
Hang on while I wipe the egg of my face ;)

So it helps if you uncomment the "#" at the front of the line in /etc/apt/sources.list.

Hmmm.

Goes off to hide his head in shame after using Linux for more than 7 years....

---

