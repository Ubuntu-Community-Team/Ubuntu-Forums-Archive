---
title: "Understanding bzr diff"
date: 2008-04-19
forum: Programming Talk
---

### Post by Jadd on 2008-04-19
I'm learning bazaar, and it feels great. I really am liking the way it works. Anyway, when I run bzr diff or click diff in olive/bzr-gtk, I get a list of what's changed since the last commit. + stands for added, and - stands for removed. So far, so good.
But what do these things mean:
@@ -18,7 +18,7 @@
@@ -207,7 +231,7 @@
It seems like shortening what hasn't changed, but I don't get what the numbers mean. Thanks!

---

### Post by smartbei on 2008-04-19
I am not sure exactly what each is referring to, but the first number in each pair is the line number, and the second may be something like the change number (in a particular file) or file number (if you ran diff on a number of files).

---

