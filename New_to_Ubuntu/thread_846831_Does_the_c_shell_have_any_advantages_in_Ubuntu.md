---
title: "Does the c shell have any advantages in Ubuntu?"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by raymondvillain on 2008-07-01
New to Ubuntu, have Hardy on a desktop.

The default (I think that is the right word) shell in my installation (8.04) seems to be bash.

Does anybody use the c shell in Ubuntu?  If not, why?

Thanks

---

### Post by ibuclaw on 2008-07-01
csh in my personal view is rather outdated. (from way back to UNIX days).
tcsh may be a better option to ponder, but besides; bash incorporates quite a few features from them anyway.

Plus, if you were to run into some odd trouble, since everyone uses bash, they will give you a solution in bash.
And you can't be too sure whether or not a bash command given to you will work in the same way (or work at all).

[EDIT]
This is true also for the sh shell as well (one culprit are that variable names with hifens in won't work with sh, but are recognised just-fine-in-bash).

Regards
Iain

---

### Post by ChameleonDave on 2008-07-01
BASH is the latest shell.  It is based on CSH and others.  If you are programming and happen to run across documentation that suggests the use of some specific feature of CSH, then use it.  Otherwise, just use BASH like everyone else.

And, as always, the Internet is your friend:

[http://en.wikipedia.org/wiki/Bash](http://en.wikipedia.org/wiki/Bash)
[http://en.wikipedia.org/wiki/C_shell](http://en.wikipedia.org/wiki/C_shell)

---

### Post by bab1 on 2008-07-02
sh = Bourne Shell (the original unix shell)
bash = Bourne Again Shell (updated sh)

csh = C shell ( more of a programmers shell (C language like)
tcsh = Updated C shell

Use bash as most do.  Use tcsh if you have complex shell scripts to run.

-BAB1

---

### Post by InfinityCircuit on 2008-07-02
No. Bash can do everything and more.  Zsh is even more complex than Bash and introduces spell-checking and advanced tab completion.

For reference, in Ubuntu:

/bin/sh is linked to /bin/dash, which is a POSIX-compliant shell.

/bin/bash is default user shell.

/bin/ash is the shell in the initramfs.

---

### Post by kuja on 2008-07-02
I'm surprised dash hasn't been mentioned yet. It's the debian almquist shell, benefits are that it's very fast and posix compliant per defaults. It wouldn't be very nice to use as a login shell, however. It has been the default non-login shell for Ubuntu since 6.10.

---

