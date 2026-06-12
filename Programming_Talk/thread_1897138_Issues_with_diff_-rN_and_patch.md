---
title: "Issues with diff -rN and patch"
date: 2011-12-18
forum: Programming Talk
---

### Post by Miltnoid on 2011-12-18
Hey guys, I'm trying to run a patch on a directory, but I'm having some difficulties.

  I'm trying to apply the patch [http://hpaste.org/55423](http://hpaste.org/55423)
[URL="http://hpaste.org/55423"]
[/URL]
  I'm running patch < hs-ffmpeg-patch (and tried patch -p1 <  hs-ffmpeg-patc), in a directory with hs-ffmpeg-patch and old-hs-ffmpeg,  but nothing is helping.  Does anybody know how to get patches to work?


Furthermore, I'm trying to test this out now with a less complicated example, so I made a diff 


diff -rN newdifffolder/ olddifffolder/ > difffolder.diff within diffpatchtest


Now, I'm trying to run
patch -p1 < difffolder.diff
and patch < difffolder.diff from within diffpatchtest


and I get the same error with


patch: **** Only garbage was found in the patch input.


Any help would be appreciated!
-Miltnoid

---

### Post by nvteighen on 2011-12-19
It's much simpler than what you're doing. Look at this: [http://www.linuxtutorialblog.com/post/introduction-using-diff-and-patch-tutorial](http://www.linuxtutorialblog.com/post/introduction-using-diff-and-patch-tutorial)

---

