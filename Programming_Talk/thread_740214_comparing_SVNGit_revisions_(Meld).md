---
title: "comparing SVN/Git revisions (Meld)"
date: 2008-03-30
forum: Programming Talk
---

### Post by Ace_NoOne on 2008-03-30
When working with Subversion or Git, I often need to compare my working copy with the last commit.
For visualizing changes I'm using Meld, which seems to be the recommended GTK diff/merge tool.

However, I can't seem to pipe diffs into Meld (using *svn-diff | meld -*, which works with Kompare, for example), and just loading a diff dump merely displays the raw contents (i.e. no context).

Do I need to check out the previous revision and then tell Meld to compare that with my working copy? Seems awfully complicated...

Any tips would be appreciated!

---

### Post by SimonS on 2008-06-26
I just had the same question (well at least in regards to svn) and stumbled upon this post. There are two answers (both executed in relevant WC directory):

1) svn diff --diff-cmd meld

or, far cooler on Meld's part:

2) meld .

---

### Post by Ace_NoOne on 2008-06-26
> **SimonS said:**
> 
1) svn diff --diff-cmd meld

or, far cooler on Meld's part:

2) meld .
I've found out about this in the meantime (sorry for not reporting back).

However, this only works for SVN, not Git (especially the second option). Fortunately though, Git has very nice command-line diff output.

---

### Post by sarath_it on 2009-02-21
> **Ace_NoOne said:**
> I've found out about this in the meantime (sorry for not reporting back).

However, this only works for SVN, not Git (especially the second option). Fortunately though, Git has very nice command-line diff output.

The new version of meld give even better support with git built in. But you have to build from source (not too difficult).

[http://blog.sarathonline.com/2009/02/use-meld-as-git-diff-gui-viewer.html](http://blog.sarathonline.com/2009/02/use-meld-as-git-diff-gui-viewer.html)

---

### Post by Ace_NoOne on 2009-02-21
Thanks.
However, I have since become accustomed to the command line, and realized it's usually far superior to GUIs (for me, anyway).

FWIW, I frequently use the following commands (via custom aliases):
```
git diff -M --color-words
git diff -M -w
git diff -M -w --color-words
```

---

