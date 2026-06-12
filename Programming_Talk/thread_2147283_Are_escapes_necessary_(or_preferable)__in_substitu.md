---
title: "Are escapes necessary (or preferable)  in substituted regex patterns?"
date: 2013-05-21
forum: Programming Talk
---

### Post by donsy on 2013-05-21
Both of these yield the same result, is one more correct or preferred over the other? I can't seem to find a definite rule for metacharacters in substituted text.
```

echo somedomain.com | perl -pe 's/somedomain\.com/mydomain.net/'
mydomain.net

echo somedomain.com | perl -pe 's/somedomain\.com/mydomain\.net/'
mydomain.net

```

---

### Post by The Cog on 2013-05-21
I suspect that the first one would also find a match with "somedomain.com/mydomainxnet/".

---

### Post by alan9800 on 2013-05-21
> **The Cog said:**
> I suspect that the first one would also find a match with "somedomain.com/mydomainxnet/".you're right.
As explained [here](http://perldoc.perl.org/5.14.2/perlre.html#Regular-Expressions), the backslash quotes the next metacharacter, so the dot is interpreted as a word separator.

---

### Post by shawnhcorey on 2013-05-21
> **donsy said:**
> Both of these yield the same result, is one more correct or preferred over the other? I can't seem to find a definite rule for metacharacters in substituted text.
```

echo somedomain.com | perl -pe 's/somedomain\.com/mydomain.net/'
mydomain.net

echo somedomain.com | perl -pe 's/somedomain\.com/mydomain\.net/'
mydomain.net

```

The first one is preferred because there is less to understand.

> **The Cog said:**
> I suspect that the first one would also find a match with "somedomain.com/mydomainxnet/".

No, the character immediately after the "s" is the separator that separates the pattern from the replacement. The preferred way to do this is:
```

echo somedomain.com | perl -pe 's{ somedomain \. com }{mydomain.net}msx/'
mydomain.net

```

---

### Post by The Cog on 2013-05-21
> **shawnhcorey said:**
> No, the character immediately after the "s" is the separator that separates the pattern from the replacement. 

Doh! I feel silly now.

---

