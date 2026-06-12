---
title: "recommendation for version control system"
date: 2008-12-12
forum: Programming Talk
---

### Post by Dar1us on 2008-12-12
Hi,

I am working with web projects, sometimes projects have 5 or 6 thousands files. Long time i used svn, but with large project it is very slow. Now i migrate to git, but git is so complicated, and don't have GUI client with full functionality :)

maybe someone can recommend another version control system, or just say how completely remove auto-generated files from git repository (for remote git repository i use gitosis), i put cache folder to gitignore file, but before many auto-generated files was pushed to repository. and often with git-pull i get conflicts..

---

### Post by dentharg on 2008-12-12
Did you try to remove auto-generated files (without being ignored) and commit/push? This should update remote repo that these files are no longer under revision control. Then you can put them to .gitignore.

---

### Post by cb951303 on 2008-12-12
svn should be fine with 5-6 thousands of files. there may be other performance issues.

---

### Post by scourge on 2008-12-12
> **Dar1us said:**
> maybe someone can recommend another version control system, or just say how completely remove auto-generated files from git repository (for remote git repository i use gitosis), i put cache folder to gitignore file, but before many auto-generated files was pushed to repository. and often with git-pull i get conflicts..

If your online repository already has files which shouldn't be there, you obviously should create a commit which removes said files. It's also a very good idea to use the "git status" command before commits to see which files were changed, and "git log -p" before push. And use the .gitignore file.

I just don't see how switching to another VCS could solve your problems.

---

### Post by Dar1us on 2008-12-12
yes, git is fast and have nice features, but need some time to learn how use it :)

i think my fail was because i deleted files only on one local repository, and than another guy from another repository push auto-generated files again.

what about gui git clients? i use qgit, but it can only explore local repository, maybe exists some tools with revert and merge functionality?

---

### Post by scourge on 2008-12-12
> **Dar1us said:**
> yes, git is fast and have nice features, but need some time to learn how use it :)

That's very recommended. Git has a gazillion commands, but you don't need to learn all of them, just the basics.

> i think my fail was because i deleted files only on one local repository, and than another guy from another repository push auto-generated files again.

That gives you some extra work, but hopefully not much. Getting rid of the auto-generated crap should be one commit (because one commit should do one thing). So if you still have the branch where the files are deleted, you can do a "git rebase master", then make the commit and push the changes to origin.
[/QUOTE]

---

### Post by mssever on 2008-12-12
My favorite VCS is Bazaar. It's a bit simpler to learn than git, but it works in much the same way. What I don't know is how well it handles really big projects.

However, as scourge said, the important thing is to learn your tools. I was helping with a project once where people would manually move files rather than using the bzr tools for that. That of course destroyed the history and made for meaningless diffs. Unfortunately, the person who maintained the official branch from which we all pulled didn't enforce correct behavior. The lesson here is that everyone needs to know their tools, and if someone misuses their tools, their code shouldn't be merged until they've fixed it.

---

### Post by scourge on 2008-12-12
> I was helping with a project once where people would manually move files rather than using the bzr tools for that. That of course destroyed the history and made for meaningless diffs.

With Git this wouldn't be a problem, unless the files were moved completely outside of the repository. Git would just recognize that a file had been deleted and a new one created with 100% similarity, and draw the conclusion that the file was moved.

---

### Post by tinny on 2008-12-12
> **cb951303 said:**
> svn should be fine with 5-6 thousands of files. there may be other performance issues.

+1

Ive had projects around that size before and SVN was fine.

---

### Post by ggaaron on 2008-12-13
You want this if you want to clean a branch and it's history from some files:
[http://www.kernel.org/pub/software/scm/git/docs/git-filter-branch.html](http://www.kernel.org/pub/software/scm/git/docs/git-filter-branch.html)

---

### Post by bobrocks on 2008-12-13
> **tinny said:**
> +1

Ive had projects around that size before and SVN was fine.

+1, some of our repos for project have way way more than 5k files and other than the initial checkout there is no noticeable speed difference between our tiny repos.  The main checkout takes a while simply due to the number of small files being created.


That said we are small scale testing git just now, the simple client side branching and tagging alone is worth it in my mind.  Liking it a lot so far.

---

