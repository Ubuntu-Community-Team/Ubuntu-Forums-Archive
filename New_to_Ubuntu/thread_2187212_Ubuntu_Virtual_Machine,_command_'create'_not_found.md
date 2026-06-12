---
title: "Ubuntu Virtual Machine, command 'create' not found"
date: 2013-11-11
forum: New to Ubuntu
---

### Post by mdkalish4git on 2013-11-11
So I am running Ubuntu 12.04.3 as VM on Windows 7 and trying to configure my first Git project. While this works on the same installation of Ubuntu on my other laptop, the command ```
create file1.txt
``` results in cheesy ```
No command 'create' found, did you mean: 
Command 'mcreate' from package 'lustre-utils' (universe)
create: command not found
```
How come that the basic 'create' doesn't work? Could it lack some configuration?

---

### Post by TheFu on 2013-11-11
To create an empty file on UNIX/Linux there are many different ways. A few:

```
touch  file1.txt
echo "" > file1.txt
```

"create" is not a standard Linux or git command.  After creating the file somehow, add the file to your git repository.
```
git add file1.txt
```
and commit all the current changes.
```
git commit
```

Of course none of the git commands will work until a **git init** happens in the top level of the project.

Don't know what "cheesy" is - google didn't enlighten me either.

There are a few nice [git tutorials]("http://git-scm.com/docs/gittutorial") and a free [Pro-Git]("http://git-scm.com/book") ebook if you need more complex information.  When I needed to setup a shared git repo for my company, read about 3 pages in that book and 10 minutes later, it was done and ready for use by our dev team(s).  I'm fairly good at Linux/UNIX, so little file and directory permission issues didn't slow me down.

Hopefully, the info above is helpful. If not, please explain a little more.

---

### Post by mdkalish4git on 2013-11-11
[QUOTE="TheFu"]"create" is not a standard Linux or git command.[/QUOTE]
Thanks, that is fair enough to me. Though why they use this command in the git basics video tutorials?
Check [cheesy]("http://dictionary.reference.com/browse/cheesy?s=t").

---

