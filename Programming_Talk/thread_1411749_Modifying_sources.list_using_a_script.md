---
title: "Modifying sources.list using a script"
date: 2010-02-20
forum: Programming Talk
---

### Post by Leppie on 2010-02-20
i'm trying to enable repos from a script and am using sed like this:
```
sed '/*'"$REPO"'/,/src/ s/^[ #]*//' /etc/apt/sources.list
```
however, like this it enables both the normal and the src repos. even though i'm trying to stop the replacement when src is found.

any help much appreciated.

---

