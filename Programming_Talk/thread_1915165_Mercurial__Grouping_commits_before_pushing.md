---
title: "Mercurial : Grouping commits before pushing"
date: 2012-01-25
forum: Programming Talk
---

### Post by GuilhermeBrant on 2012-01-25
Hello fellows,

I was wondering if there were any way to group some 'commits' in Mercurial before pushing. I found something about Mercurial Queues, but didn't quite get how to do that with it.

The motivation for doing this, if you're wondering, is : Suppose you're on a big project, with lots of other people doing stuff in many files. There is a central repository for the project, and each one has it's own local repository, so one can pull and push between these. Now suppose you're working on one class of that project, and want to keep track of minor things (i.e commiting) like for example : "Added method() to the class" ; " Implemented method2()"; "Implemented method3()" . So, you can revert, see what's been done and have a log of it. When you're done, you should push these changes to the central rep. But these commits are too specific  for everybody else, which would flood the 'log' with irrelevant information. I guess that would be more interesting if before 'pushing', I could group these commits together into a single changeset ("Implemented Class myClass") which would make more sense to the whole project.

Anyone?
Thanks in advance.

---

### Post by nvteighen on 2012-01-26
> **GuilhermeBrant said:**
> Hello fellows,

I was wondering if there were any way to group some 'commits' in Mercurial before pushing. I found something about Mercurial Queues, but didn't quite get how to do that with it.

The motivation for doing this, if you're wondering, is : Suppose you're on a big project, with lots of other people doing stuff in many files. There is a central repository for the project, and each one has it's own local repository, so one can pull and push between these. Now suppose you're working on one class of that project, and want to keep track of minor things (i.e commiting) like for example : "Added method() to the class" ; " Implemented method2()"; "Implemented method3()" . So, you can revert, see what's been done and have a log of it. When you're done, you should push these changes to the central rep. But these commits are too specific  for everybody else, which would flood the 'log' with irrelevant information. I guess that would be more interesting if before 'pushing', I could group these commits together into a single changeset ("Implemented Class myClass") which would make more sense to the whole project.

Anyone?
Thanks in advance.

Uh, I don't see any problem with having lots of local commits. The whole idea of DVCS is that people can do stuff however they like without disrupting the "trunk". Some will do smaller commits, some will do bigger ones... The important thing is that whoever coordinates the merging into the main branch knows what he's doing.

(And actually, I think there will be a lot people that will appreciate small commits... it helps for bug tracking, for example...)

---

