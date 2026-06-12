---
title: "git-svn pkg installed but no command"
date: 2010-03-28
forum: Programming Talk
---

### Post by Seine on 2010-03-28
Hi. On Lucid, I installed the git-svn package. There is a manpage for it, but the command is not present.

```
jeremy@synessi:~$ uname -a
Linux synessi 2.6.32-17-generic #26-Ubuntu SMP Fri Mar 19 23:58:53 UTC 2010 i686 GNU/Linux
jeremy@synessi:~$ man git-svn   # man page present!
jeremy@synessi:~$ git-svn log
git-svn: command not found
jeremy@synessi:~$ which git-svn
jeremy@synessi:~$ 

```

Any ideas what I've done wrong?

---

### Post by snova on 2010-03-28
I think you're supposed to use:

```
git svn
```

no dash.

---

### Post by Seine on 2010-03-28
Thanks. I think you are right. I was following [this guide]("http://flavio.castelli.name/howto_use_git_with_svn"), which says otherwise. But the manpage says to go sans dash.
Cheers

---

