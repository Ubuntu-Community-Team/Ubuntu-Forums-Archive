---
title: "Linux Most Recent Stable Kernel Snapshot"
date: 2012-04-09
forum: Programming Talk
---

### Post by gardnan on 2012-04-09
I was wondering if there was a git repository that contained the most recent stable kernel release on kernel.org. What I want is a git tree that is just the code in the most recent stable release, but has all of the git log history in it. I have tried looking through the linux-stable.git branch, but I can't seem to find a tag for the most recent kernel version.

---

### Post by dylan07 on 2012-04-09
Maybe look on launchpad.net ?

---

### Post by r-senior on 2012-04-09
The stable tree is: [http://git.kernel.org/?p=linux/kernel/git/stable/linux-stable.git;a=summary](http://git.kernel.org/?p=linux/kernel/git/stable/linux-stable.git;a=summary)

Which you can clone locally (and get commit history) using the git url that it quotes on that page:

```
$ git clone git://git.kernel.org/pub/scm/linux/kernel/git/stable/linux-stable.git linux-stable
```

That clones into a 'linux-stable' sub-directory of your current working directory. It takes a while, but then you can keep it up to date with:

```
$ cd linux-stable
$ git pull
```

The tree is at 3.4-rc2, but if you want the latest stable release, look in the list of tags on the kernel .org page I linked at the top. The latest stable is tagged v3.3.1, so:

```
$ git checkout v3.3.1
```

---

### Post by gardnan on 2012-04-10
Thanks r-senior, that worked!

I had tried looking for the 3.3.1 tag before in the log, but I couldn't seem to find a log entry announcing it, so I thought it didn't exist.

---

