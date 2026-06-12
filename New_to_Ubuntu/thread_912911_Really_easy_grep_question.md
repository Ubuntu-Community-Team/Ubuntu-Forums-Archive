---
title: "Really easy grep question"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by dhamilton on 2008-09-07
I want to print to screen the names of all the pdfs in my current folder.

I tried the following:

ls | grep *.pdf

However nothing comes up. There are pdfs in the folder I am working

The way I understand it, the standard output of ls is piped into the standard output of grep, and thats the only difference to the running of grep.

So why doesn't grep print to screen here?

P.S before you start, i have read the grep man age and searched for similar solutions already :)

---

### Post by NESFreak on 2008-09-07
```
ls | grep .pdf
```

---

### Post by Yannick Le Saint kyncani on 2008-09-07
How about just "ls *.pdf" ???

---

### Post by TheUbGuy on 2008-09-07
> **dhamilton said:**
> I want to print to screen the names of all the pdfs in my current folder.

I tried the following:

ls | grep *.pdf

However nothing comes up. There are pdfs in the folder I am working

The way I understand it, the standard output of ls is piped into the standard output of grep, and thats the only difference to the running of grep.

So why doesn't grep print to screen here?

P.S before you start, i have read the grep man age and searched for similar solutions already :)

Simple:

```

ls|grep pdf

```

Works fine for me.

---

### Post by dhamilton on 2008-09-07
Thanks for the quick reply, however my question was: 

... why doesn't grep print to screen here?

as opposed to give me something which will get me the desired result.

**Shouldn't the construction *.pdf be equivalent to .pdf in this situation?**

---

### Post by NESFreak on 2008-09-08
> **dhamilton said:**
> Thanks for the quick reply, however my question was: 

... why doesn't grep print to screen here?

as opposed to give me something which will get me the desired result.

**Shouldn't the construction *.pdf be equivalent to .pdf in this situation?**
a quick google:

[http://www.panix.com/~elflord/unix/grep.html#wildcards](http://www.panix.com/~elflord/unix/grep.html#wildcards)
> 
Read the repetion example carefully, and pay careful attention to the fact that the "*" in grep patterns denotes repetition. It does not behave as a wildcard in regular expression syntax (as it is in UNIX or DOS glob patterns). Recall that the pattern ".*" behaves as a wildcard (because .* means "repeat any character any number of times). The pattern "g*" matches the string "", "g", "gg", etc. Likewise, "gg*" matches "g", "gg", "ggg", so "ggg*" matches "gg", "ggg", "gggg", etc.

---

### Post by dhamilton on 2008-09-09
Thanks, thats my question solved

---

