---
title: "mysql order question"
date: 2008-11-07
forum: Programming Talk
---

### Post by lapubell on 2008-11-07
looking through my book, and the mysql docs, I couldn't find an answer to a quick question i have.

I'm looking for a way to return my results in a specific way.  I have a table that has item ids stored in a specific order (example items: 24513) and want to return them in this specific order.

When I get that list, i parse it and return items 2, 4, 5, 1, and 3, by mysql reorders them into 12345.  I then have to reorder them back to the way that they should be.  Is there a way that I can query mysql with an ORDER BY or something similar to have the result set returned in the order I request them in?

Thanks a bunch!

---

### Post by Coreigh on 2008-11-07
It looks from your description that you want them in a non-sequential order. This can only mean that the result set needs to be ordered by another column or another part of the return (if using a join or joins).

I do not know the exact answer but I know that if the ids column is numerical you can only order by ascending or descending if you use that column to "ORDER BY".

---

### Post by lapubell on 2008-11-07
i was hoping you weren't going to say that.  my program logic is getting messy.  I was looking for a magic something like...

ORDER (id as 2, 4, 5, 1, 3)

... but i'm thinking that no such thing exists...  dang.

thanks for confirming my doubt though.  anyone know of a different solution?

---

### Post by tomchuk on 2008-11-07
This should do the trick:
```

ORDER BY FIELD(id, 2, 4, 5, 1, 3)

```

---

