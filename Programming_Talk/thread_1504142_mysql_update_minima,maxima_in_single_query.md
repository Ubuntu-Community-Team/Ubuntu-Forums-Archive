---
title: "mysql: update minima,maxima in single query"
date: 2010-06-07
forum: Programming Talk
---

### Post by MadCow108 on 2010-06-07
hi,
is there a way to update a minima/maxima value with a single (my)sql statement?
preferably with an ON DUPLICATE KEY UPDATE.
I would need this:
```

INSERT INTO table (col) VALUES (1),(1),(1),(1),...,(1) ON DUPLICATE KEY UPDATE col = MIN(col, VALUES(col));

```

unfortunately that does not work.

Is it possible?
google and documentation are surprisingly unhelpful :(

edit:
never mind figured it out:
INSERT INTO table (col) VALUES (1),(1),(1),(1),...,(1) ON DUPLICATE KEY UPDATE col = IF(col < VALUES(col), col, VALUES(col));

kind of obvious in retrospect... :)

---

