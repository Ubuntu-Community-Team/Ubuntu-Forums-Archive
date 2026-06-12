---
title: "SQL Question...."
date: 2007-08-30
forum: Programming Talk
---

### Post by 008325 on 2007-08-30
i would like to combine three column into one column

and use comma to separate , 

select ISNULL(u_ar1,'') + ',' + ISNULL(u_ar2,'') + ',' + ISNULL(u_ar3,'') into abc from [@shdt]

however , if the u_ar2 or u_ar3 are null...it still insert a comma

so it will be

XXX,,

how can i delete the comma while the u_ar2 and u_ar3 value are null?

Thanks

Gordon

---

### Post by scooper on 2007-08-30
Sorry if this isn't helpful, but why aren't you doing it in the client side?  Is it important that it happen on the DB server?  Any dynamic language can do that operation easily, e.g. in python:

```
abc = ','.join([a,b,c])
```

I worry about putting too much logic near the database.  To me it should serve data straight, and anything that's not an efficiency issue should happen in the client.  I'd be curious what the motivation is.

For a SQL solution it may be useful to specify which DBMS you're using.  There are likely to be differences in approach.  E.g. postgresql may have something clever that mysql does not have.

---

### Post by cwaldbieser on 2007-08-31
```

select COALESCE(u_ar1, '') + COALESCE(',' + u_ar2, '') + COALESCE(',' + u_ar3, '') into abc from [@shdt]

```

---

