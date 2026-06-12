---
title: "How do I apply a svn-diff file?"
date: 2010-02-12
forum: Programming Talk
---

### Post by kevdog on 2010-02-12
I was wondering if someone could tell me how to apply a svn-diff file.  I thought the output of svn diff made a file similar to a patch file which you would then apply with the patch utility.  This doesn't seem to be working for me.  I can post the svn-diff file if anyone is interested.  Can someone maybe point me in the right direction -- I keep getting HUNK errors when trying to apply the patch.

---

### Post by nrs on 2010-02-12
I don't know about the default svn diff, but you can tell svn which diff to use. 
svn diff --diff-cmd /usr/bin/diff -x "-whateverdiffargs" so you can just the standard diff for patches.

---

### Post by MadCow108 on 2010-02-12
I usually have to add the -p0 option to patch for it to work.
But I have no idea about the exact setup of the svn I'm currently using ;)

---

### Post by kevdog on 2010-02-12
Im really trying to create a patch file that I can use.  Someone has an svn diff file, and I have a git repository so I don't think the two are interchangeable.

---

