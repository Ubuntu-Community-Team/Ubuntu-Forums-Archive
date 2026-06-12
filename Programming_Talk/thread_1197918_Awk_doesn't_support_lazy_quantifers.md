---
title: "Awk doesn't support lazy quantifers?"
date: 2009-06-26
forum: Programming Talk
---

### Post by Arctic_Fox on 2009-06-26
Hi guys, I tried to write an awk script which used the "*?" quantifier and found that it didn't work.
```

echo "ababbba" | awk '{ match($0,/a.*?a/); print RLENGTH}'
```

Should output 3 but outputs 7 instead. egrep behaves in the same way. Are there any linux utilities that do support lazy quantifiers?

---

### Post by ghostdog74 on 2009-06-26
> **Arctic_Fox said:**
> Hi guys, I tried to write an awk script which used the "*?" quantifier and found that it didn't work.
```

echo "ababbba" | awk '{ match($0,/a.*?a/); print RLENGTH}'
```

Should output 3 but outputs 7 instead. egrep behaves in the same way. Are there any linux utilities that do support lazy quantifiers?

not everything have to solved with regular expression.
```

# echo "dsfsfabxsadfabbba" | awk  -F"a" '{print length($2)+2}'
5

```

---

### Post by MadCow108 on 2009-06-26
perl regexp hast non greedy(lazy) quantifiers:
[http://docstore.mik.ua/orelly/perl/cookbook/ch06_16.htm](http://docstore.mik.ua/orelly/perl/cookbook/ch06_16.htm)

---

