---
title: "Bash one liner to rm files based on content"
date: 2009-11-19
forum: Programming Talk
---

### Post by john_spiral on 2009-11-19
Hi,

I need either a one liner or a bash script to recursively search a folder/sub folders for binary files (windows .lnk files) containing a specific text string. If it finds a match it must delete the file.

After googling for a number of hours I've come accross the below one liner.

Why does it not work? :-(

```
find . -name '*.lnk' -print0 | xargs -0 grep -I "C:" | xargs -0 rm -f
```

---

### Post by Arndt on 2009-11-19
> **john_spiral said:**
> Hi,

I need either a one liner or a bash script to recursively search a folder/sub folders for binary files (windows .lnk files) containing a specific text string. If it finds a match it must delete the file.

After googling for a number of hours I've come accross the below one liner.

Why does it not work? :-(

```
find . -name '*.lnk' -print0 | xargs -0 grep -I "C:" | xargs -0 rm -f
```

If you run it without the last part, you will see why.

```
find . -name '*.lnk' -print0 | xargs -0 grep -I "C:"
```

The output from 'grep' is not suitable as input to 'xargs'.

---

### Post by john_spiral on 2009-11-19
thanks for the heads up on grep/xargs.

Finally got it to work with the below command:

```
grep -r C: * | sed 's/Binary file//g' | sed 's/ matches//g' | xargs -I '{}' rm "{}"
```

elegant: no
works: yes

---

