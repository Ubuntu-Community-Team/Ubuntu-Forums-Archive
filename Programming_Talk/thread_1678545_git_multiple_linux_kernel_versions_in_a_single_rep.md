---
title: "git: multiple linux kernel versions in a single repository"
date: 2011-01-30
forum: Programming Talk
---

### Post by BattlePanic on 2011-01-30
I'm new to the linux kernel and somewhat new to git as well.  I've cloned the kernel.org mainline kernel from the following location:

git://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux-2.6.git

Because I am currently running 2.6.35 and I want to be able to track bugfixes to this particular kernel release.  As such, I have also cloned the stable 2.6.35 repository at:

git://git.kernel.org/pub/scm/linux/kernel/git/longterm/linux-2.6.35.y.git

This works, but tracking two different versions of the kernel source in two separate repositories seems like a waste of disk space.  Can I simply track these as separate branches within a single local repository?  Is this advisable?  Is there a reason why kernel.org distributes previous versions and separate repositories?

---

### Post by BattlePanic on 2011-01-30
After some reading and experimentation it turns out that I can indeed track both repositories within the a single local repository.

From my cloned repository of the mainline kernel, I issued the following command to tell git to also track the 2.6.35-longterm tree:

```
git remote add v2.6.35.y git://git.kernel.org/pub/scm/linux/kernel/git/longterm/linux-2.6.35.y.git
```

I then fetched any new git objects and refs from the newly tracked remote repository:

```
git fetch v2.6.35.y
```

To then create a local branch based off the master branch of the this remote repository I entered the following:

```
git branch --track my_2.6.35.y v2.6.35/master
```

I now how have a local branch named 'my_2.6.35.y' which is synced with the 2.6.35 longterm tree.

---

