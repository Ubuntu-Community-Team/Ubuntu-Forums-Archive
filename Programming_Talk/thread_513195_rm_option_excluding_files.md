---
title: "rm option: excluding files"
date: 2007-07-30
forum: Programming Talk
---

### Post by buschi on 2007-07-30
Hi!

Is there a special reason (or am I simply too dumb to discover it) for **rm** not having an option to exclude some files? It is easy to erase all tex-files in a folder with

```
rm *.tex
```

However, if I want to erase all files *except* the tex-files, I have to use something like

```
rm `ls * | grep -v ".tex"`
```


If someone knowing C who wants to save me from replacing /bin/rm with an evil bash-script introducing a **-x** option feels like this was a good starting point to revolutionize coreutils, I am happy about any snippets... (already took a look at rm.c but can't even figure out where the actual "remove it" steps takes place :/)

Any advice why this is a really bad idea is also appreciated,
Sebastian.

---

### Post by tomcheng76 on 2007-07-30
```

find ! -regex '.*\.\(tex\)' -exec echo {} \;

```
if what echo out is correct, change echo to rm

---

### Post by tomcheng76 on 2007-07-30
i think the reason why rm dont include excluding file option
is dangerous, delete except .tex may accidently cause deleting file u dont want
also shell script is acturally program of many programs
as in the above example of yours and mine, we can already do the recursive delete except tex

---

### Post by cwaldbieser on 2007-07-30
> **buschi said:**
> Hi!

Is there a special reason (or am I simply too dumb to discover it) for **rm** not having an option to exclude some files? It is easy to erase all tex-files in a folder with

```
rm *.tex
```

However, if I want to erase all files *except* the tex-files, I have to use something like

```
rm `ls * | grep -v ".tex"`
```


If someone knowing C who wants to save me from replacing /bin/rm with an evil bash-script introducing a **-x** option feels like this was a good starting point to revolutionize coreutils, I am happy about any snippets... (already took a look at rm.c but can't even figure out where the actual "remove it" steps takes place :/)

Any advice why this is a really bad idea is also appreciated,
Sebastian.


The "rm" command really just takes a list of file names as its input.  The '*.tex' pattern you give it is expanded by the shell, so rm really sees something like 'rm a.tex b.tex c.tex x.tex y.tex'.
There is a bash variable called GLOBIGNORE that will stor the shell from expanding certain patterns.
```

$ GLOBIGNORE='*.tex'
$ echo *

```
This should list all the files in the directory except those that match the *.tex pattern.

---

