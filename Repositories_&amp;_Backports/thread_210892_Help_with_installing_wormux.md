---
title: "Help with installing wormux"
date: 2006-07-07
forum: Repositories &amp; Backports
---

### Post by hansoffate on 2006-07-07
I can't get wormux installed.

First I added this to sourclist
deb [http://download.gna.org/wormux/debs](http://download.gna.org/wormux/debs) sarge-amd64/  # Debian stable amd64 ("Sarge")

Then i ran apt-get update && apt-get install wormux

It still didn't work.  So I ran it by itself.

```
root@hansoffate-desktop:/home/hansoffate# apt-get install wormux Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wormux: Depends: libglibmm-2.4-1 (>= 2.6.1) but it is not installable
          Depends: libsigc++-2.0-0 (>= 2.0.2) but it is not installable
          Depends: libxml++2.6 but it is not installable
E: Broken packages
root@hansoffate-desktop:/home/hansoffate#

```

How can i get the dependencies? 

Thanks
-Hans

---

### Post by lordlollo on 2006-07-12
> **hansoffate said:**
> First I added this to sourclist
deb [http://download.gna.org/wormux/debs](http://download.gna.org/wormux/debs) sarge-amd64/  # Debian stable amd64 ("Sarge")

Just a question: why did you add a debian repo? Isn't what you're looking for in ubuntu repos? I run a 32-bit system - I don't know if this is the point - but I can find wormux in the 'regular' repos...

Cheers

---

