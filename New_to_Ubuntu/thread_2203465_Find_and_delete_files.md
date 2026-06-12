---
title: "Find and delete files"
date: 2014-02-03
forum: New to Ubuntu
---

### Post by sccjono on 2014-02-03
Hi all,

I imagine this is easy for you experts but it has me stumped. Long story short I have managed to end up with loads of duplicate files in my Documents directory and sub-directories under home and I of course would like to remove them. The duplicates are identified by *(1).*, *(2).* and occasionally *(3).* in the names. I figured that the "find" command would be what I needed as I could use -print until I was happy and then -delete to remove them.

So I came up with the following.

```
find -type f -exec grep -q "(1)" {} \; -print
```

But something must be wrong as I'm getting any filename with a 1 in it. Can anyone tell me where I'm going wrong?

---

### Post by steeldriver on 2014-02-03
Your grep will be looking for string "(1)" *in* the file - not in the file *name* - try

```
find -type f **-name '*(1)*'**
```

or to find numbers other than 1 in the parentheses use a regular expression

```
find -type f **-regex '.*([0-9]+).*'**
```

You can then add a '-exec delete' once you confirm it is finding only the duplicates

---

### Post by sccjono on 2014-02-03
Oh wow thank you. The whole regex thing frightens the life out of me but it worked like a charm. Thank you so much.

---

### Post by steeldriver on 2014-02-03
With hindsight that's actually not a very good regex to use - since find treats regexes as **path** matches (not **file** matches like with the -name predicate) it would matched (*digits*) anywhere in the path e.g. if the folder or subfolder name matched - a safer option would have been

```
find -type f \( -name '*(1)*' -o -name '*(2)*' -o -name '*(3)*' \) -print
```

Cliff notes: *find -regex* is hard to get right...

---

