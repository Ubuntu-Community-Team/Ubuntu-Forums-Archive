---
title: "Was my patch submitted or only generated?"
date: 2009-03-15
forum: Packaging and Compiling Programs
---

### Post by thtrgremlin on 2009-03-15
After finding a simple bug within my programming skill level, I began investigating patch submission. Sadly I trashed a few pages with comments on launchpad submitting in the wrong format, but today I think I got the hang of it having found every bug report oe launchpad addressing a string typo. Anyway, while I submitted my patches as .debdiff, a number of packages mention the use of bzr for their source / package management, so following [http://doc.bazaar-vcs.org/latest/en/mini-tutorial/index.html](http://doc.bazaar-vcs.org/latest/en/mini-tutorial/index.html) after bzr whoami foobar <blah>, I did ```
bzr branch foo
bzr upgrade
#fix problem
dch -i #and inserted relevant info
bzr commit -m "LPbug######fix"
bzr send -o "LPbug######fix.patch"
```
From there the guide says:
> You can now email the merge directive to the bzr-gtk project who, if they choose, can use it merge your work back into the parent branch.
Does this mean that bzr send only generates the patch and does not actually 'send' anything? I emailed the patch to the maintainer listed in debian/control, but not really certain whether or not it was necessary.

---

### Post by thtrgremlin on 2009-03-15
ok, been following my own advice and read the man page more thoroughly, but still not clear. I am not certain if 'xdg-email' is setup properly. bzr whoami is setup, but is that all I need? The maintainers email address is right there in debian/control, so it has everything necessary to send it... just don't know if it did.

Maybe next time I should be running tcpdump at the same time and figure it out.  :) joking (sort of)

---

### Post by thtrgremlin on 2009-03-15
grr... so I came by [https://help.launchpad.net/BranchMergeProposals](https://help.launchpad.net/BranchMergeProposals), but when I go to the relevant page, there is no 'action' menu as it describes. I am on the right page, right? ```
grep XS-Vcs-Bzr ./deb/control
```

---

### Post by thtrgremlin on 2009-03-16
Ok, got everything figured out. Thanks anyway.

---

