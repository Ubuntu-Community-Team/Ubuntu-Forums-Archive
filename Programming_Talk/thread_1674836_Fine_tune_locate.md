---
title: "Fine tune locate"
date: 2011-01-24
forum: Programming Talk
---

### Post by bcooperizcool on 2011-01-24
How can I have locate only return specific things, and only search in specific folders?
My code:
```

while read names
do locate "$names"
done < $theme_base/.names.txt | sort | uniq > $theme_base/.locationstemp.txt

```
and can I have locate run this with it, so it only returns results containing this?

my other code to run with:
```

grep "^/var/mobile/Applications.*\.app$"

```

and specific folders, to make search quicker would be nice!

Thanks!

---

