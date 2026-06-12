---
title: "run bash script on all files in directory"
date: 2008-09-16
forum: New to Ubuntu
---

### Post by xravexheavenx on 2008-09-16
How would I write a bash script to do a command to all files in a directory?

---

### Post by iaculallad on 2008-09-16
> **xravexheavenx said:**
> How would I write a bash script to do a command to all files in a directory?

Should be something like:

```
find **[COLOR="Red"]/[/COLOR]** typef -name "*.doc" -print0 | xargs -O -I % ls %
```

You could replace / with a .

/ = starting from root directory
. = starting from current directory

---

### Post by xravexheavenx on 2008-09-16
I'm getting invalid argument after xargs

"-0"

---

### Post by Pro-reason on 2008-09-16
> **xravexheavenx said:**
> How would I write a bash script to do a command to all files in a directory?

The best way to do it is not to make it automatically act on all files in the current directory, but to make it accept multiple input files.  That way, the user can make it act all all files in the current directory by using &#8220;*&#8221;.

But here is an example of a script that acts on the current directory: [reorder.sh]("http://ubuntuforums.org/showthread.php?p=5729403").

---

