---
title: "Self-Hosted Repository UI"
date: 2011-09-29
forum: Programming Talk
---

### Post by josheee12 on 2011-09-29
Hi guys.  I currently have SVN deployed on my server.  We all know that SVN is absolutely horrible, but I won't get into that.  Alongside SVN, I run a web-based **admin** frontend called USVN that allows me the ability to manage my users, projects, groups, and the like.  It also has code browsing, but I wanted to emphasize the fact that it's primarily admin.  Is there any similar web UI for Git, Mercurial, or Bazaar?

---

### Post by karlson on 2011-09-29
> **josheee12 said:**
> Hi guys.  I currently have SVN deployed on my server.  We all know that SVN is absolutely horrible
I guess you haven't seen horrible...

> but I won't get into that.  It also has code browsing, but I wanted to emphasize the fact that it's primarily admin.  Is there any similar web UI for Git, Mercurial, or Bazaar?

Have you tried GitWeb, there is [http://doc.bazaar.canonical.com/latest/en/admin-guide/code-browsing.html](http://doc.bazaar.canonical.com/latest/en/admin-guide/code-browsing.html)

---

### Post by josheee12 on 2011-09-30
GitWeb doesn't seem to have an admin interface.  Am I missing something?

---

### Post by karlson on 2011-09-30
> **josheee12 said:**
> GitWeb doesn't seem to have an admin interface.  Am I missing something?

Probably not.

---

### Post by josheee12 on 2011-10-01
So, no USVN-esque UI for me?  Awww.

---

### Post by karlson on 2011-10-01
> **josheee12 said:**
> So, no USVN-esque UI for me?  Awww.

I personally frown upon using GUI as configuration tool until you can figure out how to do this via config files and on the command line.

---

### Post by nvteighen on 2011-10-02
> **karlson said:**
> I guess you haven't seen horrible...


CVS is the definition for horrible ;)

---

### Post by karlson on 2011-10-02
> **nvteighen said:**
> CVS is the definition for horrible ;)

I was thinking more of RCS and SCCS but CVS is right up there.

---

