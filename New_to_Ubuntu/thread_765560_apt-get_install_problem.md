---
title: "apt-get install problem"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by MegaJim on 2008-04-24
I can't install a large amount of software, when I try to install it using the command line I am told:

"Package freeciv-client-gtk is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package freeciv-client-gtk has no installation candidate"

When I try to install software using add/remove programs it tells me that there my architecture (i386) is not supported, even though it has been before.

To fix it I've tried running apt-get check which executes cleanly, and I've tried installing the meta package ubuntu-desktop to check I have all the pre-requisites.

Any help greatly appreciated.

---

### Post by swoll1980 on 2008-04-24
try apt-get update. It could be a server problem to. There are a couple million people trying to get stuff of those servers right now

---

### Post by MegaJim on 2008-04-24
Thanks, but thats not the problem, I've been experiencing this issue for a couple of days.

---

### Post by GuitarRocker2562 on 2008-04-24
Are you on gutsy or hardy? I am gonna guess hardy, try using synaptic.

---

### Post by MegaJim on 2008-04-24
I'm using 7.10, the same problem happens with synaptic, add/remove programs gui and apt-get command line.  Is there some way to rebuild the apt-get database?

---

