---
title: "HELP! Slight mistake with a bash script. Need help deleting TONS of files"
date: 2011-05-04
forum: Programming Talk
---

### Post by oopsie on 2011-05-04
So yeah, a slight oversight in creating a little script has created a folder with I estimate now has half a million files.

I'd like to be able to leave my good files and delete my mistake, but it's so huge I can't do this

**rm blah*png**

deleting my mistakes, leaving my old work behind. It appears I have too many files for things like * to work any more.

Hell, even typing **ls** took 150MB before I killed it for taking too long and doing nothing.

So any advice for an idiot bash scripting newbie? :D

---

### Post by DaithiF on 2011-05-04
try:
```
find . -maxdepth1 -type f -name 'blah*.png' -exec rm -f '{}' \;
```

in this case 'blah*.png' will not get expanded by the shell, but instead find will apply that test to each file it finds in that directory.  it will take a long time, but shouldn't choke on the number of files.

---

### Post by Arndt on 2011-05-04
> **DaithiF said:**
> try:
```
find . -maxdepth1 -type f -name 'blah*.png' -exec rm -f '{}' \;
```

in this case 'blah*.png' will not get expanded by the shell, but instead find will apply that test to each file it finds in that directory.  it will take a long time, but shouldn't choke on the number of files.

You can use 'xargs', to avoid letting 'find' create a new subprocess for each file. It's easier to type too:

```
find . -maxdepth1 -type f -name 'blah*.png' | xargs rm

```

---

### Post by DaithiF on 2011-05-04
> **Arndt said:**
> You can use 'xargs', to avoid letting 'find' create a new subprocess for each file. It's easier to type too:

```
find . -maxdepth1 -type f -name 'blah*.png' | xargs rm

```

though this would break for files with spaces so a safer version would be to use the -print0 / xargs -0 combination to use nulls as the delimiter
```
 find . -maxdepth1 -type f -name 'blah*.png' -print0 | xargs -0 rm
```

---

### Post by oopsie on 2011-05-04
Thank you all!

:)

---

### Post by hakermania on 2011-05-04
Please mark the thread as solved ;)

---

