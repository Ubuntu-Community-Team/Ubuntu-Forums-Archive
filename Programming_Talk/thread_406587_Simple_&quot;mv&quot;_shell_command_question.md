---
title: "Simple &quot;mv&quot; shell command question"
date: 2007-04-11
forum: Programming Talk
---

### Post by nyinge on 2007-04-11
Let's say I'm in a directory with many files and an empty folder (named "haha").  I want to move all the files into that empty folder.  So, I'd issue: ```
 mv * empty_folder 
```  It works but with a warning:  ```
 mv: cannot move `haha' to a subdirectory of itself, `haha/haha' 
```Is there a better solution for such a case?  Thank you.

---

### Post by Ramses de Norre on 2007-04-11
```
find . -maxdepth 1 -type f -exec mv '{}' haha/ \;
```

---

### Post by nmsa on 2007-04-11
ls
1/  2  3
#1 is the folder

$ for i in `find $PWD -type f`
> do
> mv $i 1/
> done
$ ls
1
$ ls 1/
2  3

---

