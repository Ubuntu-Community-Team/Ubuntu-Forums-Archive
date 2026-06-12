---
title: "Can I use git for version tracking a website?"
date: 2010-09-05
forum: Programming Talk
---

### Post by jon.reeve on 2010-09-05
I'm building a website for some people, and I'm looking for an easy way to manage the testing site, versions, changes, etc. I see a lot of programmers using git. Is it easy to set up? Is it worth it to set it up since I'm the only one working on this project? Will git still be useful for a website? Any advice would be much appreciated.

---

### Post by Mordred on 2010-09-05
Hi,

version control is a very useful tool even if you are the only developer.

Git is a rather good choice. You may also want to try mercurial.
Both are in the repositories and plenty of tutorials are available
on the internet.

---

### Post by GenBattle on 2010-09-05
I would definitely give Bazaar (Canonical sponsored) a look. It's much simpler than mercurial or git; you can version a directory locally without having to set up a separate server at all. It basically allows you to use it either like SVN or like git/mercurial, depending how you need to use it.

---

### Post by phrostbyte on 2010-09-05
I use git for version control on my documents. So I would say yes. :)

---

### Post by jon.reeve on 2010-09-07
Thanks! I installed Bazaar and the bzr-upload plugin and can now publish, annotate, and version-control my webpages all in one go with 

```
bzr commit
bzr upload
```

So awesome.

---

