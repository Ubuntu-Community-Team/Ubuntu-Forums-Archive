---
title: "Private Git"
date: 2009-12-09
forum: Programming Talk
---

### Post by huangyingw on 2009-12-09
Hello all,
     I have a question about private GIT.
     For personal convinience, I have cloned a private git and do my actual coding work there.
     As I intend to commit every 2 or 3 lines of code, so, my private git repository would grow quickly with the increasing of commits.
     While, if others pull or fetch from my private one, they would receive a lot of meaningless commits. This is rather annoying and disturbing to others.
     How could I balance between self-convinience and team work?
     Currently, my solo solution is to maintain 2 GIT repository, one for others to pull, and one for self-convinience, and regularly and rawly copy mature code to the public repository. While, indeed, I don't think it a good idea.

---

### Post by nvteighen on 2009-12-09
> **huangyingw said:**
> Hello all,
     I have a question about private GIT.
     For personal convinience, I have cloned a private git and do my actual coding work there.
     As I intend to commit every 2 or 3 lines of code, so, my private git repository would grow quickly with the increasing of commits.
     While, if others pull or fetch from my private one, they would receive a lot of meaningless commits. This is rather annoying and disturbing to others.
     How could I balance between self-convinience and team work?
     Currently, my solo solution is to maintain 2 GIT repository, one for others to pull, and one for self-convinience, and regularly and rawly copy mature code to the public repository. While, indeed, I don't think it a good idea.

Er...
1) I don't see why someone will consider your commits meaningless. Just use your common sense... 
2) Your "intuition" is a really widely used solution when using Distributed CVS (e.g. git, bazaar, mercurial)... A "trunk" or "master" branch where relatively more stable code is published and a personal development place where you can feel free to literally destroy your code without ruining the project :D

---

### Post by huangyingw on 2009-12-09
> **nvteighen said:**
> Er...
1) I don't see why someone will consider your commits meaningless. Just use your common sense... 
2) Your "intuition" is a really widely used solution when using Distributed CVS (e.g. git, bazaar, mercurial)... A "trunk" or "master" branch where relatively more stable code is published and a personal development place where you can feel free to literally destroy your code without ruining the project :D
About 1)In my practice,if really commit with a frequency of per 2/3 lines a commit, I would just lazily commit with the same message "no compilation error". And I only make tags at my mature stage. So, if other pull from my private GIT, they will receive a lots of commit with same message "no compilation error" That's why I said they are meaningless. A high frequency of commits have a great merit: it would be easy and more exact to find the root cause of bug when bisecting.
2)Is there a better solution? For my intuition, I have to physically maintain 2 directories/folders. One is for public, one for self. And regularly copy codes. Is there a replacement choice of "direct copy code"? Does GIT support "check out",  or better "Mirror", code from my private to my public?

---

### Post by falconindy on 2009-12-09
> A high frequency of commits have a great merit: it would be easy and more exact to find the root cause of bug when bisecting.
Exactly. If you take a few seconds to make your commit messages meaningful, you solve your own problem.

If you're bent on doing it "cleanly", you could create a new branch, make your changes and then create a patch between the master and the new branch. Apply the patch to the master and commit it as a single change.

---

### Post by nvteighen on 2009-12-09
You can 'merge' your branches, which is like patching and applying in just one stroke. The differences will be calculated and no "direct copying" will be needed.

---

### Post by slakkie on 2009-12-09
> **falconindy said:**
> exactly. If you take a few seconds to make your commit messages meaningful, you solve your own problem.

If you're bent on doing it "cleanly", you could create a new branch, make your changes and then create a patch between the master and the new branch. Apply the patch to the master and commit it as a single change.

+1

---

### Post by huangyingw on 2010-01-13
> **falconindy said:**
> 
If you're bent on doing it "cleanly", you could create a new branch, make your changes and then create a patch between the master and the new branch. Apply the patch to the master and commit it as a single change.
Hey, are you sure? I have tried, no matter I choose apply patch or merge between two branch, git would inevitablely bring the unwanted changeset into my targeted, and want-to-be clean branch...

---

