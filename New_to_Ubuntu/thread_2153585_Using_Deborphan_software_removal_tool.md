---
title: "Using Deborphan software removal tool?"
date: 2013-06-11
forum: New to Ubuntu
---

### Post by TNFrank on 2013-06-11
Ok, so I got that if it's orphaned you can remove it without issue but under "Non-Orphaned Packages" there's a lot of stuff, some of which says "extra", so can I uninstall/delete extra stuff without issue. Also, what about "optional" stuff? Thanks.

---

### Post by ArminasAnarchy on 2013-06-11
What are you actually trying to remove specifically? apt-get autoremove is the command to remove un-needed packages, otherwise I'd recommend using Synaptic to see what a package does/what it links to etc.

---

### Post by TNFrank on 2013-06-11
Didn't have any certain files in mind, just being somewhat OCD I wanted to keep my system as clean as possible without extra "stuff" on it.  So I can use "apt-get autoremove" and it'll clean things up. Sounds good. Might have to also install Synaptic too. Thanks.

---

### Post by Cheesehead on 2013-06-11
> **TNFrank said:**
> Ok, so I got that if it's orphaned you can remove it without issue but under "Non-Orphaned Packages" there's a lot of stuff, some of which says "extra", so can I uninstall/delete extra stuff without issue. Also, what about "optional" stuff? Thanks.


Deborphan can be a handy tool. However, if you are already using the command line for package management (apt-cache and apt-get), then deborphan may be superfluous. It won't hurt, but it does duplicate functionality already provided by apt-get.

For example,
```
sudo apt-get remove foo        # removes only package foo
sudo apt-get autoremove foo    # removes package foo and subsequently removes all orphans
sudo apt-get autoremove        # removes all orphans
```

The definitions of Extra, Optional, and other priorities is set by Debian. See [http://www.debian.org/doc/manuals/debian-faq/ch-pkg_basics.en.html#s-priority](http://www.debian.org/doc/manuals/debian-faq/ch-pkg_basics.en.html#s-priority) . The short answer is that you generally should not remove them...the applications that depend them will lose some functionality. The package manager settings define whether packages with one of these priorities should be ignored - new users should not fiddle with that setting until they know how to use dpkg to fix the resulting problems.

---

