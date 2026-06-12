---
title: "Git.help"
date: 2010-01-16
forum: Programming Talk
---

### Post by jacensolo on 2010-01-16
I am looking into using a Revision control system for my projects. The main one I have been looking at is Git. I downloaded it and started using it with a basic text file. I have a few questions about how it works.

1) I made a branch and changed a word in the text value. Then I changed into the master branch and did "git merge otherbranch". I was expecting it to ask me or say something about if i wanted the file/word changed, but it just overwrote the original word with the word from otherbranch. So what if I am working on a large project and I don't want some files to be merged, or maybe even parts of files to be merged? O is merging just copying branch1 into branch2?

2) Since git keeps a copy of the whole repository, what if I change something on my desktop and have something else changed on my laptop? How do I sync the changes?

Thanks for any help.

---

### Post by falconindy on 2010-01-16
When you create a branch, it becomes a child of the commit it was created at. You can continue to make changes on the master branch and progress the revision "timeline". If you then go back to the created branch, make some commits and then merge them into master, they will be merged according to what the repo looked like at the commit when the branch was created. The commits made to master during the lifetime of the child branch will then be applied in order over the changes made on the branch. It's possible to alter this behavior by doing a rebase.

[Here's](http://www.eecs.harvard.edu/~cduan/technical/git/git-2.shtml) a fairly decent guide to Git. I found that seeing a repo history visually helped greatly in my understanding.

---

### Post by jacensolo on 2010-01-17
Thanks. I'm still really confused but I think I might be able to understand it in the morning.

---

### Post by SledgeHammer_999 on 2010-01-17
This guy explains MANY concepts concerning git quite well. And in many cases, with funny examples too. [link](http://www-cs-students.stanford.edu/~blynn/gitmagic/)

---

