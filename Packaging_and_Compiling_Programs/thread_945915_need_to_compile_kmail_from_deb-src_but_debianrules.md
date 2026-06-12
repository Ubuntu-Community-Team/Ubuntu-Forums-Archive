---
title: "need to compile kmail from deb-src but debian/rules file has changed"
date: 2008-10-12
forum: Packaging and Compiling Programs
---

### Post by Pollywoggy on 2008-10-12
I am having a problem with kmail-kde4 and I fetched the deb-src for kde4pim-4.1.2 in order to recompile kmail-kde4 with debugging enabled.  I went to kde4pim-4.1.2/debian/rules only to discover that the format of the 'rules' file is now different and there must be some other file where I would enable debugging.

A reference for the new way to build debs from deb-src would suffice.  I don't know when this changed byt it must have been very recently.

thanks

---

### Post by InfinityCircuit on 2008-10-14
What do you mean "debian/rules" has changed format?  There are four possible ways (off the top of my head) to build a debian package in debian/rules:

1) dh_* calls
2) build the package manually in a temp directory and call dh_builddeb (deprecated)
3) cdbs
4) dh 7 calls

Perhaps if you post the contents of debian/rules and clarify what you expected to find that would help.

---

### Post by Pollywoggy on 2008-10-14
> **InfinityCircuit said:**
> What do you mean "debian/rules" has changed format?  There are four possible ways (off the top of my head) to build a debian package in debian/rules:

1) dh_* calls
2) build the package manually in a temp directory and call dh_builddeb (deprecated)
3) cdbs
4) dh 7 calls

Perhaps if you post the contents of debian/rules and clarify what you expected to find that would help.

The following two lines are all that is in the rules file:

#!/usr/bin/make -f

include debian/cdbs/kde.mk

# eof #

Every other rules file I have seen has much more, including the configure options.
I need to enable debugging before building the deb package for kmail-kde4 but I can't find the file where I would set this option.

---

