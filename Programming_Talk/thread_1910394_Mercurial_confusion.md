---
title: "Mercurial confusion"
date: 2012-01-17
forum: Programming Talk
---

### Post by denarced on 2012-01-17
Hello,

I have a repository on my machine and it has about 70 commits and a couple of branches. Now there's another "central" repo which is empty. Is it possible for me to push my commits to the central instead of the central cloning my repo?

---

### Post by Zugzwang on 2012-01-17
Hmmm, why don't you just try it out.
```

hg push http://the-location-of-the-other.com/repository

```

---

### Post by denarced on 2012-01-18
> **Zugzwang said:**
> Hmmm, why don't you just try it out.
```

hg push http://the-location-of-the-other.com/repository

```

I did and I got:
pushing to ssh://user@192.168.11.4//var/lib/mercurial/myapp
searching for changes
remote: abort: could not lock repository /var/lib/mercurial/myapp: Permission denied
abort: unexpected response: empty string

This error could have something to do with rights; my user group does not have write privileges to the .hg-directory.
I'll let you all know if that indeed is the reason.

---

### Post by Zugzwang on 2012-01-18
> **denarced said:**
> This error could have something to do with rights; my user group does not have write privileges to the .hg-directory.
I'll let you all know if that indeed is the reason.

Well, if you cannot write to the repository, then you also cannot push, unless a user having write access to the repository starts a HTTP server to let you push via it.

---

### Post by denarced on 2012-01-18
Yep!
The missing write privileges was the problem.

---

