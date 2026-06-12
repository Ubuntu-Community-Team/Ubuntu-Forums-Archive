---
title: "Using grep with hyphens"
date: 2013-01-31
forum: Programming Talk
---

### Post by woodson2 on 2013-01-31
This is on a RHEL 6 box with bash 4.1.2

I'm trying to to use grep to only find those lines containing matches that form whole words.

The -w option works fantastic unless of course that word has a hyphen.

The problem is I will get a hit on "test-group" which is a good thing, but I will also get a hist on "test" which is bad because the group test doesn't exist. It appears that once grep hits a hyphen it treats the preceding text as a whole word.

Any ideas would be greatly appreciated.

Next time no groups with hyphens..

Thanks

---

### Post by rnerwein on 2013-01-31
> **woodson2 said:**
> This is on a RHEL 6 box with bash 4.1.2

I'm trying to to use grep to only find those lines containing matches that form whole words.

The -w option works fantastic unless of course that word has a hyphen.

The problem is I will get a hit on "test-group" which is a good thing, but I will also get a hist on "test" which is bad because the group test doesn't exist. It appears that once grep hits a hyphen it treats the preceding text as a whole word.

Any ideas would be greatly appreciated.

Next time no groups with hyphens..

Thanks
hi
may be: grep -w test your_file | grep -v \-
or         : grep -w test your_file | grep \-
cheers

---

### Post by ofnuts on 2013-01-31
> **woodson2 said:**
> This is on a RHEL 6 box with bash 4.1.2

I'm trying to to use grep to only find those lines containing matches that form whole words.

The -w option works fantastic unless of course that word has a hyphen.

The problem is I will get a hit on "test-group" which is a good thing, but I will also get a hist on "test" which is bad because the group test doesn't exist. It appears that once grep hits a hyphen it treats the preceding text as a whole word.

Any ideas would be greatly appreciated.

Next time no groups with hyphens..

Thanks
If there are no underscores (or even of there are, in many cases):
```

tr '-' '_' < file  | grep -w (your options) | tr '_' '-' 

```

---

