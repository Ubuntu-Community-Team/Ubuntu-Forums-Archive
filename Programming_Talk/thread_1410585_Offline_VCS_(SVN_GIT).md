---
title: "Offline VCS (SVN GIT)"
date: 2010-02-18
forum: Programming Talk
---

### Post by weezerBo on 2010-02-18
from what i've read, offline development is one of the major +s git has over svn, but i'm not sure i understand why this can't be accomplished with svn. if the repository is non-local i get it, but why couldn't you just import the checked out code into a local repository. work from there, and when the time comes to commit to the non-local repository, just patch or copy the file and commit? 

why is this an inferior solution? 

i also suspect for a local one man project there are really no advantages or disadvantages to either. it's only when other people begin to work with your code that it begins to matter. am i wrong?

---

### Post by falconindy on 2010-02-19
Commits are like checkpoints. If you can only commit when you have access to the remote repo, then your freedom to make random commits for debugging, testing or whatever else, is lost. I often create new branches, commit a bunch of times (maybe revert once) and merge back into master all without touching the remote repo.

SVN needs to disappear. Git is gold.

---

### Post by weezerBo on 2010-02-19
> **falconindy said:**
> Commits are like checkpoints. If you can only commit when you have access to the remote repo, then your freedom to make random commits for debugging, testing or whatever else, is lost. I often create new branches, commit a bunch of times (maybe revert once) and merge back into master all without touching the remote repo.

SVN needs to disappear. Git is gold.
i understand that, but i don't feel you answered my questions. 

why couldn't you check out the code from the remote repo, and then import it to a local repo? you're free to commit anything you want, and when you wanted to merge to the remote repo all you'd have to do is patch or copy the file. am i completely wrong?

and if you're not using remote repositories, and are working on a local one person project, does it really matter which system you use? i can see git being advantageous for group projects, i'm just wondering if it has any advantages for local-solo projects or if they're generally equal for that.

-vcs noob.

---

### Post by Zugzwang on 2010-02-19
One of the points of VCS is to have individual steps you did reversible. Distributed VCS like Mercurial have an advantage here: Before you merge, you can commit your changes. This way, in case you find out that you did something wrong during your merging, you do not lose your changes that you did before  merging but can rather restart the whole thing at the point of merging.

Also, sometimes you want to set a checkpoint at a place in which your code doesn't compile or isn't meant to be used by others (e.g., before refactoring), such that you can roll-back to this point if needed. With a distributed VCS, this is no problem. With a non-distributed VCS, everyone else would see the changes as well, before they are supposed to.

---

### Post by weezerBo on 2010-02-19
lol. think people may be only reading the title of the thread.

---

### Post by falconindy on 2010-02-19
I think you're misunderstanding. There's no such thing as a 'local repo' in SVN. A commit pushes your changes to the remote repo. If you wanted to create a remote repo locally on the same machine as the checkout, you could do that. But then you'd have to deal with sync'ing the local-remote with the remote-remote (if that makes sense). Git simplifies this by separating commits from the remote update.

---

### Post by weezerBo on 2010-02-19
> **falconindy said:**
> I think you're misunderstanding. There's no such thing as a 'local repo' in SVN. A commit pushes your changes to the remote repo. If you wanted to create a remote repo locally on the same machine as the checkout, you could do that. But then you'd have to deal with sync'ing the local-remote with the remote-remote (if that makes sense). Git simplifies this by separating commits from the remote update.
by local repo I simply mean a repository hosted on your machine. as in
[PHP]
svn co svn://remote
svnadmin create local
svn import remote file:///path/to/local
**work / commit in local** 
diff local/file remote/file | patch 
cd remote &&  svn commit
[/PHP]so the answer is there is nothing theoretically stopping you from doing this, it's just more trouble than it's worth?

---

### Post by falconindy on 2010-02-19
> **weezerBo said:**
> by local repo I simply mean a repository hosted on your machine. as in
[PHP]
svn co svn://remote
svnadmin create local
svn import remote file:///path/to/local
**work / commit in local** 
diff local/file remote/file | patch 
cd remote &&  svn commit
[/PHP]so the answer is there is nothing theoretically stopping you from doing this, it's just more trouble than it's worth?
SVN still calls that a remote repo, but I see what you mean. You could do it, sure. I don't see why though. A place like GitHub will give you more than ample space for single person projects which adds in the benefit of a free offsite backup.

Short version: No sir, I don't like SVN.

---

### Post by weezerBo on 2010-02-19
> **falconindy said:**
> SVN still calls that a remote repo, but I see what you mean. You could do it, sure. I don't see why though. A place like GitHub will give you more than ample space for single person projects which adds in the benefit of a free offsite backup.

Short version: No sir, I don't like SVN.
Do you think it makes much of a difference when you're a single developer, on a single machine? Most of gits or mecurials features deal with sharing code, but if you're not, is there something else that still makes them special?

---

### Post by falconindy on 2010-02-19
I'm a single developer on a single machine and I prefer Git over SVN because:

- Flexibility of offline commits
- Metadata is stored in **one** directory rather than every directory
- Faster than SVN in almost every regard -- SVN can be faster when making extremely large commits
- Better debugging tools, should you run into an issue either in your code or with the tree
- GitHub (really, it kicks butt)

---

### Post by weezerBo on 2010-02-19
> **falconindy said:**
> I'm a single developer on a single machine and I prefer Git over SVN because:

- Flexibility of offline commits
- Metadata is stored in **one** directory rather than every directory
- Faster than SVN in almost every regard -- SVN can be faster when making extremely large commits
- Better debugging tools, should you run into an issue either in your code or with the tree
- GitHub (really, it kicks butt)
alright, thanks

---

