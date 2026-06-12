---
title: "git and svn on same server?"
date: 2009-09-11
forum: Programming Talk
---

### Post by aaronLund on 2009-09-11
Howdy.

Just wondering what the ramifications of git and subversion being on the same server with svn being there first (i.e. many svn commits being made before my first git init).

Will commits made in svn trigger git to record those changes as well?

Say if a svn commit was made even though no changes to any file was actually commited?  Will that svn commit make any changes to the file system that git will recognize as being different from its last commit?  

(kind of thinking out loud here so forgive me if this seems relatively obvious........)

I'm not exactly sure how svn tracks its changes.....

Anyone had any experience with this?

Thanks.

---

### Post by v8YKxgHe on 2009-09-11
GIT and Subversion are completely different programs, which keep their repositories in different locations. There is no unified place and format where a repository is stored, where you just pick your favour RCS to interface with them.

So no, commiting to a GIT repository will not effect a Subversion repository and vice versa, since they are 100% separate. There are tools and methods around that let you sync them up, though.

---

### Post by aaronLund on 2009-09-11
Many thanks, Alex.

Salut!

---

### Post by falconindy on 2009-09-11
If you have the option, dump SVN! You can easily convert SVN repos to Git repos by installing and utilizing the package 'svn-git' (available thru apt-get).

Mmm, nevermind.. you're running the repos themselves on the same server, not the clients.

---

