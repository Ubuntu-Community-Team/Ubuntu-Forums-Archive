---
title: "concat in sql"
date: 2012-06-06
forum: Programming Talk
---

### Post by psycho5 on 2012-06-06
Hi I have this sql query 

```
UPDATE SkuAnalysis SET SkuAnalysis.categories = Left([categories],InStr([categories],",")-1);

```

I'd like to modify it so that it counts from the left of string categories up to 10 characters and then looks for the , separator.

at the moment I am thinking

```
UPDATE SkuAnalysis SET SkuAnalysis.categories = concat(Left(([categories] +10),InStr([categories],",")-1);

```

It doesn't seem to work, there is some missing operator or maybe I am just not thinking right here. I'm trying to concat the field categories up to 10 characters and then search in that string for the comma.

---

