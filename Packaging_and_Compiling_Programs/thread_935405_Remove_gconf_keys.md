---
title: "Remove gconf keys"
date: 2008-10-01
forum: Packaging and Compiling Programs
---

### Post by Nonno Bassotto on 2008-10-01
I want to create a package that removes the gconf keys created by myapp when it is removed. As a user I can remove these keys simply by
```

gconftool-2 --recursive-unset /apps/myapp

```

But since (I think) gconf has different values for each user, I should do that for every user in the system. So I have two problems.

First I should get the list of users. I think I can get it parsing the output of "users".

Second for each user I should execute
```

gconftool-2 --recursive-unset /apps/myapp

```
as that user. This I don't know how to do it, since I think in Ubuntu "su" is disabled.

Is there a simpler way to achieve all this?

---

