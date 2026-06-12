---
title: "Conversion in MySQL++"
date: 2008-04-10
forum: Programming Talk
---

### Post by 71fnRVVm on 2008-04-10
[I posted this [over on the MySQL forums]("http://forums.mysql.com/read.php?45,204432,204432#msg-204432"), but am wondering how large of a forum community they have...?]

Is there a way to convert a *single* result into a "normal" variable in MySQL++?

I came across .storein() but that doesn't work for this.

After making a query, using ```
mysqlpp::StoreQueryResult users = query.store();
```Then looping through the result... I'd like the ability to store something like ```
users[i]["id"]
``` inside an int, and other types as strings.

I couldn't find anything in the docs. Any suggestions?

Thanks

---

