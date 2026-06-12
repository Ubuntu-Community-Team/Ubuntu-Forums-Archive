---
title: "clear trash/cache periodically"
date: 2009-07-02
forum: Programming Talk
---

### Post by flylehe on 2009-07-02
Hi,
I am now writing some bash command into cron to clear cache periodically.
Could you let me know what need to be clear?
Here is what I think: trash, ~/.thumbnails, and ~./.mozilla. What else?
Would you tell me what are the directory whose files need to be removed? And the commands?
Thanks and regards!

---

### Post by smartbei on 2009-07-02
I don't think you want to remove .mozilla, since that is also where bookmarks, passwords, etc. are stored. How about:
```

/home/<your username>/.mozilla/firefox/<your profile>/Cache

```
Instead? I believe that is where the Temporary Internet Files are (or equivalent).

---

