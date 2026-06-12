---
title: "[SOLVED] Git how to change  to a given state"
date: 2008-10-01
forum: Programming Talk
---

### Post by Belerophon on 2008-10-01
Hi.
I'm a newbie in these things:

I have done some commits in a GIT repo, and I realised that my code is all wrong. So I want to change all the files in it to the way they were before a given commit, to a given revision( commit number 10 for example...). 

How do I do this??

Thanks.

---

### Post by artoj on 2008-10-01
You can use *git reset* to reset the state to previous one. The command throws away your commits that follow that state:

For example, if you have this commit history (-> indicating parent):

```

Commit 1 -> Commit 2 -> Commit 3 -> Commmit 4

```

And HEAD is at Commit 4, you do a:

```

git reset --hard HEAD^

```

You'll end up to Commit 3 and Commit 4 is thrown away.

If you want to end up at Commit 1 from Commit 4 you can use:

```

git reset --hard HEAD^^^

```

or

```

git reset --hard HEAD~3

```

Always keep backups though, if something goes wrong.

Git documentation:

[LIST]
[*][Every Day Git]("http://www.kernel.org/pub/software/scm/git/docs/everyday.html") (gives info about the basic commands, very short and to the point)
[*][Git User Manual ]("http://www.kernel.org/pub/software/scm/git/docs/user-manual.html") (the full manual)
[/LIST]

---

### Post by Belerophon on 2008-10-01
:D Thank you very much!

---

