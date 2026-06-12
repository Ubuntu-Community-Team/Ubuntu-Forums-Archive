---
title: "cat equilvalent in python?"
date: 2012-02-08
forum: Programming Talk
---

### Post by conradin on 2012-02-08
hi all,
I am trying to get the functionality of something like cat on the command line, into a python script. Something like when I run the script and a bunch of file names, the files are all concatenated to one long file.
In bash I would write:
```
cat a.txt b.txt c.txt d.txt ...> long.txt
``` 

I want to run the script and ./script a.txt b.txt c.txt d.txt ... 
where a,b,c,d etc.txt are user specified texts,
and have it output long.txt but Im stuck on how i might get that to work.
any ideas?

---

### Post by MadCow108 on 2012-02-08
there is not really a "cat equivalent" in python, cat is a program, python is programming language.
you can write code that does a similar thing to cat
e.g.:
```

import sys
with open(sys.argv[1], "a") as out:
  for fn in sys.argv[2:]:
    with open(fn) as f:
      out.write(f.read()) # unlimited read to ram, you might want to loop over chunks for large files here

```

you can also call cat directly with the subprocess module (or more convinient the external psd modules [https://github.com/amoffat/pbs](https://github.com/amoffat/pbs))

if you want to use python as a shell replacement, use better python shell's like ipython or bpython where it looks somthing like this:
```
>>> !cat a.txt b.txt > out.txt
```

---

