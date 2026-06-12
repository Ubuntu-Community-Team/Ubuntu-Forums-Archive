---
title: "Text processing (challenge!)"
date: 2009-01-23
forum: Programming Talk
---

### Post by s04bf1c2 on 2009-01-23
Hi,

I'm been toying around with a script to automate backup of my text files (require a revision history so using Mercurial as its my favoured VCS). During backup I process diffs to extract the filenames of edited files. However encountered one or two problems when processing the data as a variable...

Below is a sample of data I face and what I wish to extract (highlighted).

> diff -r efb93662e8a7 -r 53784895c0f7 diff.txt --- [COLOR="Red"]diff.txt[/COLOR] Fri Jan 23 14:48:30 2009 +0000 +++ b/diff.txt Fri Jan 23 14:49:58 2009 +0000 @@ -1,9 +0,0 @@ -diff -r 9741ec300459 myfile.c ---- [COLOR="Red"]myfile.c[/COLOR] Thu Aug 21 18:22:17 2008 +0000 -+++ b/myfile.c Thu Aug 21 18:22:17 2008 +0000 -@@ -1,4 +1,4 @@ - int myfunc() - { -- return 1; -+ return 10; - }

I can do this through the creation/parsing and removal of a "helper" file, but feel there is probably a better (cleaner) way... Sadly when using a variable, the file structure is lost and therefore upsets my current solution.

```
edited_files=`cat diff.txt | grep -w "a/*" | sed -e 's/a\///g' | awk '{print $2}'`
```

Any help is appreciated,

s04bf1c2

---

