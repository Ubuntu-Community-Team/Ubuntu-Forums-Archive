---
title: "New computer / second drive problem"
date: 2008-08-05
forum: New to Ubuntu
---

### Post by groeswenphil on 2008-08-05
Hi,

Had to get a new computer after last one died.
The hard drive was recoverable so I had it installed to use as a second drive...thus keeping all of my old files.
Now.......I'd like to get rid of my old Ubuntu installation.....but how?
When I go to the files, the computer won't let me delete them.

I've a feeling that this computer is finding the old installation and when I start up with a duel boot, I'm given an awful lot of options. 
Any suggestions?

Phil

---

### Post by Matthew Green on 2008-08-05
I'd like to help you.

When you say "the computer won't let me delete them" - can you say exactly the process you go through and exactly the error message, please?

I am making a guess that maybe you are trying to delete them in the nautilus window, and you may have a new installation with a different username - Ubuntu thinks the old files are owned by a different user and won't let you delete them.  If this is the case, try hitting alt+f2 and entering (you'll be prompted for your password):

```
gksudo nautilus
```

and trying to delete them again.

If this doesn't work, can you post the output from the following command:

```
cat /etc/fstab
```

---

### Post by groeswenphil on 2008-08-05
That worked.
Thanks.

---

### Post by groeswenphil on 2008-08-05
That worked.
Thanks.

---

