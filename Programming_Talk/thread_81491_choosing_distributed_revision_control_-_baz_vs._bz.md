---
title: "choosing distributed revision control - baz vs. bzr"
date: 2005-10-24
forum: Programming Talk
---

### Post by SickTwist on 2005-10-24
I've been working on a small project (plan to release it under a Free Software license) in my free time to help me learn [GTK+]("http://www.gtk.org/"), C, Glib and [Gstreamer]("http://gstreamer.freedesktop.org/"). At this point I am not using a revision control system but realize the need for one ever since I broke my program a few days ago and had to struggle to undo the changes that I made which caused the breakage.

I feel that [distributed revision control]("http://en.wikipedia.org/wiki/Distributed_revision_control") is technically superior so I'd prefer to learn a system based on that concept. I've been considering using [Bazaar]("http://bazaar.canonical.com/") or [Bazaar-NG]("http://www.bazaar-ng.org/") but I'm open to other ideas as well. Does anyone have any experience with Bazaar or Bazaar-NG? I realize that the latter is being developed heavily right now. With that in mind, is it too soon to start learning it since the interface may be a moving target at this point? Other the other hand, is it worth learning Bazaar since it seems to be superceded by Bazaar-NG? How accurate and available is documentation for these programs? How do they compare with other distributed revision control systems?

Thanks in advance for any feedback!

---

### Post by LorenzoD on 2005-10-26
Bazaar NG is significantly easier to use than Bazaar. But as you said, it is under heavy development at the moment, so it might give you problems.

I recently backed up my bazaar repository and have begun migrating everything to bzr instead. That is the future. 

You may also want to look at: git, mercurial and darcs. Oh, and perforce too. Haven't really played around with those because, until I found bazaar NG I was satisfied with GNU Arch/tla/bazaar.

---

### Post by jondecker76 on 2007-10-08
Are Bazaar, Bazaar NG and bzr really separate programs? I thought that they were all one and the same??

(from the bazaar website [http://bazaar-vcs.org/HistoryOfBazaar]("http://bazaar-vcs.org/HistoryOfBazaar")

)

> 
Canonical Ltd had a need for a decentralized version control system. At the time, the closest fit to their need was Gnu Arch, however there was some difficulty in adapting it to fit their exact needs.

So Canonical created a Bazaar project. Initially it was thought that the fork of Gnu Arch now known as Baz-1.x would become the official Bazaar project. After some limitations in the Gnu Arch model had been uncovered, a prototype initially called Bazaar-NG was created. Eventually, this prototype became quite robust and easier to use.

Historically the project has had several names, but it is now just simply known as Bazaar. (See also Branding)


---

### Post by Fbot1 on 2007-10-08
Git is pretty good.

---

