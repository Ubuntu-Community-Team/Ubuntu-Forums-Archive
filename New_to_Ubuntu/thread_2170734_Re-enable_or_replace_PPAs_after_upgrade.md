---
title: "Re-enable or replace PPAs after upgrade?"
date: 2013-08-27
forum: New to Ubuntu
---

### Post by Wheel on 2013-08-27
Hi all,

I've recently upgraded twice in succession.

First, from 12.04 to 12.10.
Then from 12.10 to 13.04.

The handful of 3rd party PPAs which I have (a couple of app-indicators, WINE, and one or two others), were disabled (as usual) during the first upgrade.
I did not bother re-enabling them prior to the 2nd upgrade.
Now, Software sources shows these as "Quantal" PPAs.

Since I'm now using Raring, does this matter?

Should I simply re-enable them OR remove them and re-download the "Raring" version of the PPAs?

---

### Post by 1/0 on 2013-08-27
It can cause problems, e.g. with dependencies. I would, if possible, update the ppa:s in /etc/apt/sources.list and the files in /etc/apt/sources.list.d/.

---

### Post by tgalati4 on 2013-08-27
Many PPA's have different web addresses (directories) for each Ubuntu or Linux version that the package is built for.  There is no framework to automatically update PPA's so you have to do it yourself.  A quick search on the web will usually find the correct (matching) PPA for the current distro that you are running.  And yes, having mixed distro PPA's can cause breakage.  Turn off or fix them quickly.

---

### Post by Wheel on 2013-08-27
Thanks to both of you.  I suspected this might cause some conflicts, but I wasn't positive.

I've gone ahead and cleaned up both sources.list and sources.list.d, removing all references to Precise and Quantal.  I've also replaced most of those with the appropriate Raring versions.

But while looking through /etc/apt, I see a file which was written during the upgrade:  souces.list.distUpgrade.  This file contains several Quantal references on lines which are not commented out.

Is this file useful for anything? Is it safe to delete this file, or should I save it and simply comment out those lines?

[HR][/HR]> There is no framework to automatically update PPA's so you have to do it yourself.



After I went through all of this, I found what looks like a useful tool (for future reference): _YPPA Manager_, which looks like it *might* be able to automate the process of updating a bunch of PPAs.
Ah, well.  Maybe next time.

---

### Post by Wheel on 2013-08-29
No suggestions as to the usefulness of the souces.list.distUpgrade file?

Any comments would be welcome.

---

### Post by Wheel on 2013-08-31
Hi again,

All I've been able to discover is that the /etc/apt/sources.list.distUpgrade file _used to_ show up as an invalid filename when updating sources.

I found no info as to whether or not this has any use.  So, I'm still uncertain.

Is it OK to delete this file?

---

