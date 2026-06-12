---
title: "[php] don't parse links when inside img tags?"
date: 2009-06-12
forum: Programming Talk
---

### Post by ELD on 2009-06-12
Basically i have this regex to parse links in a post:
```

#(http://){1}((www\.)?[a-z][a-z0-9_.-]*\.[a-z]{2,6}[a-zA-Z0-9/.?&%-]*)(\.com|org|us|uk|nl|de|info|me)([a-zA-Z0-9=\;\_\\/\\.\\?&%-]*)#i

```

How do i adjust it so it won't parse anything wrapped in:
```

[img][/img]

```
Any help would be grand!

---

