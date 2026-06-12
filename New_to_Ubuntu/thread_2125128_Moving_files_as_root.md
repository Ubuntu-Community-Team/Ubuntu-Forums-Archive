---
title: "Moving files as root"
date: 2013-03-13
forum: New to Ubuntu
---

### Post by Absolute Terror on 2013-03-13
When I move files with sudo dolphin it seems to make all the files that I copy owned by root.

I never have this problem when I use a GTK based distro, but with KDE its a big issue.

What is the proper way to move / copy things in Dolphin as root.

---

### Post by schragge on 2013-03-13
This won't answer your question, but: instead of *sudo dolphin*, please do *kdesudo dolphin*. Here is why:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

As to your question, there are many ways to accomplish this from command line ([cp -a]("http://manpages.ubuntu.com/manpages/precise/en/man1/cp.1.html"), [rsync -a]("http://manpages.ubuntu.com/manpages/precise/en/man1/rsync.1.html"), [cpio]("http://manpages.ubuntu.com/manpages/precise/en/man1/cpio.1.html"), [tar]("http://manpages.ubuntu.com/manpages/precise/en/man1/tar.1.html")), e.g. see [post=12510349]this post[/post] by oldfred. It's about moving */home*, but also applies to moving any directories around. I cannot comment about Dolphin however as I don't use it.

---

