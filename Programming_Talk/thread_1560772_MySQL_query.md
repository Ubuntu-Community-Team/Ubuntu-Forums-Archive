---
title: "MySQL query"
date: 2010-08-25
forum: Programming Talk
---

### Post by nebu on 2010-08-25
Hi,
I wanted to know how can I query a string such that it does not contain a slash at the end?

right now i was trying
```

select string_data from table_of_data where string_data not rlike "/$";

```

but this does not work!:(

what would the right form of the query be?

---

### Post by jobix on 2010-08-25
You might need to escape it, by using a "\", i.e., like this "\/$", otherwise it might be getting interpreted as something else. Haven't tested it, but speaking based on my experience with other scripts/languages.

---

### Post by Some Penguin on 2010-08-25
NOT LIKE '%/' should work.    No need for ^, $ in LIKE syntax; they're implicit; and % is basically '.*'.

---

