---
title: "regex: escape forward slash unless already escaped"
date: 2009-12-19
forum: Programming Talk
---

### Post by altonbr on 2009-12-19
It's pretty easy to escape forward slashes (/), but how do I look in front of the forward slash (/) to see if there is a backslash (\) in front of it so I don't escape it twice?

javascript code:
```
str = '/\/\/';
str.replace(/\//g,'\\/');
```
will become
> \/\\/\\/

how do I make it become:
> \/\/\/

I read about the look behind assertion '?=<' but I'm not sure how to apply it.

---

### Post by Arndt on 2009-12-19
> **altonbr said:**
> It's pretty easy to escape forward slashes (/), but how do I look in front of the forward slash (/) to see if there is a backslash (\) in front of it so I don't escape it twice?

javascript code:
```
str = '/\/\/';
str.replace(/\//g,'\\/');
```
will become


how do I make it become:


I read about the look behind assertion '?=<' but I'm not sure how to apply it.

So your original string contains some slashes which are escaped and some which are not, but you want all to be? In that case, why are some escaped and some not, if they are to mean the same thing?

(I could have misunderstood what you want.)

---

### Post by Some Penguin on 2009-12-19
I am also a bit puzzled about your objective.  It would seem to me that

/\/\/

should be turned into

\/\\\/\\\/

which, when de-scaped ('\\' to '\', '\/' to '\') would become

/\/\/

again.  It's not a question of not generating \\ sequences, but of properly escaping the already-existing \ as well as the / -- because if you have some special characters escaped and some unescaped, how is the recipient to distinguish them?  

*shrug*  Iterate over the string.  If you see \, append \\.  If you see /, append \/.  If you see something else that doesn't need to be escaped, append it as-is.

---

### Post by diesch on 2009-12-19
```
$ echo '/\/\/' | perl -pe 's:(?<!\\)/:\\/:g'
\/\/\/

```

---

