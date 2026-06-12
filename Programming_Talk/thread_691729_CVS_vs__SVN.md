---
title: "CVS vs  SVN"
date: 2008-02-08
forum: Programming Talk
---

### Post by bschleusner on 2008-02-08
Simple question:

What versioning system should I use for my programs. CVS or SVN.  I have read about both but don't know what to use. Could anyone enlighten me on this?:)

---

### Post by pmasiar on 2008-02-08
SVN is CVS done right. CVS team decided that CVS is no more worth adding features, and redesigned it. Result is SVN. See also wikipedia

For new project, I can hardy see any good reason to go with CVS.

---

### Post by johnnyb1726 on 2008-02-08
I use SVN for all my projects and it works great.

---

### Post by Sam on 2008-02-08
SVN is a must-have.

---

### Post by bschleusner on 2008-02-09
What about GIT? I just watched a video on it, is it actually that good?

---

### Post by shaggy999 on 2008-02-09
git is for huge projects that span the globe and are developed by lots of people around the world. It's a *distributed* cvs. If you're a lone coder or a company w/ only one office (not, say, like MS which has offices all around the globe where people might be working on a project) then there is absolutely no need for git.

Just use SVN, from the standpoint of not only is it all you need but if you ever work on a project w/ a team of people they are far more likely to be using svn than git.

---

### Post by pmasiar on 2008-02-09
... and SVN as single central repository is easier to understand: merging branches distributed system like git is HARD.

---

### Post by scruff on 2008-02-09
We recently switched from CVS to SVN at work and I am impressed. As stated earlier, CVS is old and there are no new features in development. My favorite SVN features that CVS somehow did not support are:

1. Support for versioned renames and moves
2. SVN has native support for directories

If you are choosing a version control system for the first time, just go with the new :)

---

### Post by fyplinux on 2008-02-09
If you are working on small projects personally, try RCS:[http://en.wikipedia.org/wiki/Revision_Control_System](http://en.wikipedia.org/wiki/Revision_Control_System)

it is quite simple and easy to use with your single pc.

---

### Post by pmasiar on 2008-02-09
RCS is even older and more obsolete than CVS, no? Is it easier to set up than SVN?

---

### Post by shaggy999 on 2008-02-09
I can't imagine anything being more simple to install than SVN, at least for a basic install on a single machine for local access.

---

### Post by bschleusner on 2008-02-09
Is SVN capable of being used for small projects? How do I create branches in it? Is merging a branch easier with it than CVS?

Thanks to all who have responded so far. :)

---

### Post by scruff on 2008-02-09
[http://svnbook.red-bean.com/nightly/en/svn.branchmerge.html](http://svnbook.red-bean.com/nightly/en/svn.branchmerge.html)

---

### Post by ema on 2008-06-23
Go for **CVS**!
The only good bit of *SVN* is the ability to manage multiple files at once.

If you have to commit mainly text documents/code, then I would use CVS.
Easier to setup, easier to run, less disk space.
Just think to this:
You can't TAG in SVN, it creates another branch and if you stich to it then switch back it forces you to keep it locally even if you're working on HEAD revision. Why?!?!?!?
The missing TAG feature is the most annoying!!!
SVN has a lot of useless features and worst of all is a waste of space.
Again, if you have to work with sources/text files go for CVS.
Just ask yourself why even if CVS is so old is still *largely* used.
Look [here]("http://www.pushok.com/soft_svn_vscvs.php") to find a quick comparison. The smaller the project, the better CVS is.

Cheers,
Ema.

---

