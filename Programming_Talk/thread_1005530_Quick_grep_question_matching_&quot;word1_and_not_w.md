---
title: "Quick grep question: matching &quot;word1 and not word2&quot;"
date: 2008-12-08
forum: Programming Talk
---

### Post by khughitt on 2008-12-08
Anyone know how to match a line of text that has one word but not another: 

e.g. "match all lines that have the word red but do not have the word circle."

I can do it with two calls to grep:

```
grep word1 | grep -v word2
```

But I imagine there is a better way to match this sort of expression.

Any ideas? Any advice would be greatly appreciated.

Thanks!

---

### Post by odyniec on 2008-12-08
If by "a better way" you mean just one call instead of two, then it's probably not possible with grep. Grep allows you to use only one regular expression, and you can't express a condition such as "(A) AND NOT (B)" with a single regexp.

So, you need something that can handle two regular expressions -- for example awk:
```
awk '/word1/ && !/word2/' file
```

---

