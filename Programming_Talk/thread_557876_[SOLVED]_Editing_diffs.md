---
title: "[SOLVED] Editing diffs?"
date: 2007-09-23
forum: Programming Talk
---

### Post by olejorgen on 2007-09-23
I've made some changes to a program, but I want to make a patch that only contains some of the them. Obiviously I could copy the files and remove the changes I don't want, but I think it's a lot easier to remove the changes from a diff file. Unfortunately this is not as easy as one might think, because to remove lines in a diff, you have to manually adjust *all* line numbers.

I thought that it might exist a tool that took two diffs and produced a new diff?

---

### Post by olejorgen on 2007-09-23
Ok, **patchutils** should do what I want, but it seems its tools operate on a different kind of diff :-/

```

rediff full.patch title.patch
rediff: Original patch seems empty
```
full.patch:
```
3a4,5
> new line 2
6c8,9
< foo bar
---
> foo 100*bar
> new line 3
```
title.patch:
```

3a4,5
> new line 1
> new line 2
6c8,9
< foo bar
---
> foo 100*bar
> new line 3
```

---

### Post by xtacocorex on 2007-09-23
There is a program called diff that allows you to find what has changed between two versions of a file and will allow you to create patches.

Here is a link: [http://www.cs.fiu.edu/support/unix/unix-tutorial/util-diff-comp.html](http://www.cs.fiu.edu/support/unix/unix-tutorial/util-diff-comp.html)

You can also manually edit the patch file once it is created if you know how they work.

---

### Post by olejorgen on 2007-09-23
The format patchutils operates on is unfied diff. To produce unified diffs with cvs: **cvs diff -u ...**

Hope this will help someone in the future, or I've just wasted lots of time posting with myself :p

---

### Post by winch on 2007-09-23
Try generating the diffs in [unified format]("http://en.wikipedia.org/wiki/Diff#Unified_format") by passing diff the -u option.

Unified diffs include unmodified lines around the changed line. This allows patch to find the modified line even if it is in a different place.

You could create a diff.
Remove the unneeded changes.
Use the diff to patch a clean source tree.
Diff the patched source tree against a clean copy to obtain a diff where the line numbers match up.

---

