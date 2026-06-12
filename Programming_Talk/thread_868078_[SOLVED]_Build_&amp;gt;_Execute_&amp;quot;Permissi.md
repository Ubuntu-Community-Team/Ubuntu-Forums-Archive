---
title: "[SOLVED] Build &amp;gt; Execute: &amp;quot;Permission Denied&amp;quot;"
date: 2008-07-23
forum: Programming Talk
---

### Post by Zeotronic on 2008-07-23
The other day I downloaded some rather simple code from the Boost website, from their tutorial for filesystem. (specifically simple_ls.cpp) Now when I try to execute this code (after I compile it of course) I get the following error:
> ./geany_run_script.sh: 3: ./simple_ls: Permission denied
(I use Geany for my IDE by-the-way, it's probably relevant that you know) This (besides file_size.cpp, also Boost code) is the only thing that does this to me... my projects don't do it to me, other people's code I've compiled never did it to me (that is provided I actually compiled someone else's code successfully once). **So, does anyone have any clue what I'm doing wrong?**

---

### Post by Tuna-Fish on 2008-07-23
It would appear that you lack execute permissions for the file simple_ls.

Fix by:
chmod a+x simple_ls

usually, the compiler is supposed to set the permissions, for some reason, it didn't.

---

### Post by Zeotronic on 2008-07-23
> bash: ./simple_ls: cannot execute binary file
Crap. Thats what I get now... any ideas?

And from Geany's 'execute' I get:
> ./simple_ls: 1: Syntax error: word unexpected (expecting ")")

---

### Post by Zeotronic on 2008-07-25
It seems I needed to include -lboost_filesystem.

---

