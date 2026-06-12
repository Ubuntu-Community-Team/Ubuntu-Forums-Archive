---
title: "bash script 2.0"
date: 2010-06-17
forum: Programming Talk
---

### Post by Zorgoth on 2010-06-17
With some help, I successfully wrote a bash script to find all the *.m files in a directory and put quotes around their names (including multiword names)([http://ubuntuforums.org/showthread.php?t=1511952](http://ubuntuforums.org/showthread.php?t=1511952)).

However, if I then type 

```

grep my_search_term `my_shell_script`

```

grep claims that none of the files exist.  If I type the file names in individually there is no such problem.  Since there are over 300 arguments perhaps that is just too many; I don't know.  Any idea how I could effectively search these files from the command line?

---

### Post by DaithiF on 2010-06-17
Hi,
try this:
```
grep --include='*.m' -r mysearchterm .

```

---

### Post by schauerlich on 2010-06-18
```
find . -type f -name "*\.m" -exec grep -l "pattern" {} \;
```

That will print the name of all of the files that end in ".m" and whose contents match "pattern" anywhere in the current directory (or subdirectories).

---

### Post by Zorgoth on 2010-06-18
Thanks!  I have everything working now.  -exec is definitely useful

---

