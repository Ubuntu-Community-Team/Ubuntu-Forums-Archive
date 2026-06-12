---
title: "[SOLVED] grep question"
date: 2007-12-22
forum: Programming Talk
---

### Post by Peter76 on 2007-12-22
Hell, I'm looking for a solution to the following problem: 

I want to parse the output from ```
iwlist scan
``` and print the lines with the essid and encryption info to the screen. I've tried :

```
iwlist scan | grep essid, enc 
```

or another combination like that, but I can't get grep to take two arguments.... ANybody knows a solution to this?
Thanks in advance

---

### Post by Existentialist on 2007-12-22
You should be able to just pipe it in to grep again:

>iwlist scan | grep essid | grep enc

---

### Post by Peter76 on 2007-12-22
@Existentialist: this does not work; you then pipe the output from the first grep to the second grep instead of the whole output....

---

### Post by Existentialist on 2007-12-22
> **Peter76 said:**
> @Existentialist: this does not work; you then pipe the output from the first grep to the second grep instead of the whole output....

Sorry misunderstood what you wanted.  To search a list of patterns you use

>grep -E 'pattern1
>pattern2' file

The patterns need to be separated by a newline character like that.  This should return any line containing one or both of the patterns.

---

### Post by geirha on 2007-12-22
Or you can use ```
iwlist scan | egrep 'ESSID|Encryption'
``` It's case sensitive, so make sure to get that right too, or supply -i to the grep command to make it case insensitive.

---

### Post by Peter76 on 2007-12-23
Thanks a lot for the last two solutions; work like a charm :-)

---

