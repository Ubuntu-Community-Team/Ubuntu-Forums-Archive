---
title: "Downgrading and pinning?"
date: 2006-03-06
forum: Repositories &amp; Backports
---

### Post by blargity on 2006-03-06
I keep all my packages up to date, and I'm generally quite happy with the result. However, I'm doing some Ruby development using YAML, and of course my Ruby is now 1.8.3, which breaks YAML. When this was installed it had 1.8.2 on it. So, how do I downgrade back to the latest 1.8.2 and then pin it there? I tried dinking around with dpkg --force-downgrade, and then some apt-get install ruby1.8=1.8.2_1 but nothing's working for me.

Adept claims to be able to downgrade packages, but it's unintuitive if it's there.

---

### Post by Xian on 2006-03-06
There are multiple ways of doing this.
Here's one method:

To downgrade the package:
$ sudo aptitude install <pkgname>=<version>

To hold that package in state:
$ sudo apt-get install wajig
$ sudo wajig hold <pkgname>

To unhold the package:
$ sudo wajig unhold <pkgname>

To find versions of a package and what is installed:
$ sudo apt-cache showpkg <pkgname>
$ sudo apt-cache policy <pkgname>

---

### Post by blargity on 2006-03-06
kevin@unitedstates:~/dli/frontend$ sudo apt-get install ruby=1.8.2-1
Reading package lists... Done
Building dependency tree... Done
ruby is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

I get the same result when I use aptitude (with more output).  But yet:

kevin@unitedstates:~/dli/frontend$ ruby -v
ruby 1.8.3 (2005-06-23) [i486-linux]

---

### Post by blargity on 2006-03-06
So I guess my question is what am I doing wrong here?  When I check with Adept, I show version 1.8.2-9ubuntu1 (which is really 1.8.3) installed, yet when I try to force it down to 1.8.2-1, it says it's already the newest.  Yeah, got it. :)  So how do I make it not the newest?

---

### Post by blargity on 2006-03-09
*bump*

---

### Post by blargity on 2006-03-13
*bump*

---

### Post by magnetism on 2006-04-19
any news on this?

---

