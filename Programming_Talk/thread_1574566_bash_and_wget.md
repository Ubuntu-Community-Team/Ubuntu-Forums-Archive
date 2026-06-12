---
title: "bash and wget"
date: 2010-09-14
forum: Programming Talk
---

### Post by altonbr on 2010-09-14
Is there a way to download multiple links with wget using bash's {a..z} or {0-28} property?

e.g.
```
wget http://domain.com/file{0-28}.htm
```

**EDIT:**
Apparently I didn't catch my own mistake, it needed to be {0..28} and thus,
```
wget http://domain.com/file{0..28}.htm
```

---

