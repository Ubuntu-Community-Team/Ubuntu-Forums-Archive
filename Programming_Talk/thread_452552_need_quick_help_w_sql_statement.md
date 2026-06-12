---
title: "need quick help w/ sql statement"
date: 2007-05-23
forum: Programming Talk
---

### Post by jeff00z28 on 2007-05-23
I added a new column to a table, but now i want to add data to the rows in that colums. how would add the data specific rows columns. The table is called Computer_Information, the new column is called Estimated_Age. The first column in the table is called Cubicle_or_office_number and contains number 1 - 50 in rows. thanks

---

### Post by LaRoza on 2007-05-23
INSERT INTO Computer_Information(Estimated_Age) VALUES (WhateverValueYouWant) WHERE ....


I assume this is similar to what you want, if I misunderstood your question or you do not know enough of SQL, please respond.

After the ellipsis, put the statement to control which record(s)gets the data.

---

### Post by jeff00z28 on 2007-05-23
thanks, this is what i tried earlier

INSERT INTO Computer_Information(Estimated_Age) VALUES ('a') WHERE (Cubicle_or_office_number = ' 1')

---

### Post by LaRoza on 2007-05-23
> 
INSERT INTO Computer_Information(Estimated_Age) VALUES ('a') WHERE (Cubicle_or_office_number = ' 1')


No parentheses in the "WHERE" phrase,

WHERE Cubuicle_or_office_number=1

Should work, unless 1 is a string, then you should put parentheses.

I omitted semi-colons, I assume you are using them if they are needed.

---

### Post by kpatz on 2007-05-23
> **jeff00z28 said:**
> thanks, this is what i tried earlier

INSERT INTO Computer_Information(Estimated_Age) VALUES ('a') WHERE (Cubicle_or_office_number = ' 1')You already have rows in the table, and you just need to fill in the Estimated_Age column?

```
UPDATE Computer_Information set Estimated_Age = 'a' WHERE Cubicle_or_office_number = '1';
```

---

