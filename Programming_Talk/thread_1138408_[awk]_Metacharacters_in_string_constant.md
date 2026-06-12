---
title: "[awk] Metacharacters in string constant"
date: 2009-04-26
forum: Programming Talk
---

### Post by Pico1 on 2009-04-26
Hi everyone !
I have a little problem with metacharacters in string constant. I want to set RS variable as block comments characters '\*' or '*\'. 
```
echo '\*comment*\' | awk 'BEGIN {RS="(\\\\\*)|(\\*\\\)"}{print $0}'
awk: warning: escape sequence `\*' treated as plain `*'
awk: warning: escape sequence `\)' treated as plain `)'
awk: fatal: Unmatched ( or \(: /(\\*)|(\*\)/
```but I can't figure out what's wrong :(

---

### Post by Arndt on 2009-04-26
> **Pico1 said:**
> Hi everyone !
I have a little problem with metacharacters in string constant. I want to set RS variable as block comments characters '\*' or '*\'. 
```
echo '\*comment*\' | awk 'BEGIN {RS="(\\\\\*)|(\\*\\\)"}{print $0}'
awk: warning: escape sequence `\*' treated as plain `*'
awk: warning: escape sequence `\)' treated as plain `)'
awk: fatal: Unmatched ( or \(: /(\\*)|(\*\)/
```but I can't figure out what's wrong :(

```
$ echo '\*comment*\' | awk 'BEGIN {RS="\\\\\\*|\\*\\\\"}{print $0}'

comment
```

---

### Post by Pico1 on 2009-04-26
Do you know why there have to be four backshlashes instead of three ? (I don't know and I would be grateful if you could write the reason)

---

### Post by Arndt on 2009-04-27
> **Pico1 said:**
> Do you know why there have to be four backshlashes instead of three ? (I don't know and I would be grateful if you could write the reason)

If 'awk' sees just one backslash, it will have a special meaning in the regexp, so we want it to see two. A backslash in a 'sh' quoted string is used for quoting things, so each of those two needs to be quoted, with one backslash each, that makes four.

---

