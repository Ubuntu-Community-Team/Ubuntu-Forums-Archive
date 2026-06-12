---
title: "mySQL add auto_increment?"
date: 2012-01-05
forum: Programming Talk
---

### Post by CoffeeRain on 2012-01-05
Is there a way to edit an existing table and add an auto_increment field? I have a table, and I want each row to have it's own "id." I could do this by hashing multiple columns, but I think it would be easier to just have an auto increment field. Will I have to drop my table and create a new one?

---

### Post by KdotJ on 2012-01-05
Hi, you may be able to do it with a rebuild. I'm assuming you have a primary key in the table? Having a quick stab at adding an auto increment attribute gives me this...

```
there can be only one auto column and it must be defined as a key

```


There is a way to add this row, but not be auto incremented (as you will have to mess around with the primary key which could have knock on effects). One way is this:

Add your new column:
```
ALTER TABLE mytable ADD idcol INT NOT NULL;
```

Then create a counter:
```
SET @count = 0;
```

Then update the rows to include the new number ID:
```
UPDATE mytable SET idcol = @count:=@count+1;
```

The problem is, this won't automatically increment for new tuples when they are added unless  you use the count variable when inserting

---

### Post by CoffeeRain on 2012-01-06
Thanks. Would I be able to keep this variable and use it in a PHP page? In other words I guess, is the variable stored in the table or database?

---

### Post by CoffeeRain on 2012-01-06
After looking at my table again, I found that I must not have created a primary key when I created it. Either solution would work.

---

### Post by KdotJ on 2012-01-06
If you haven't defined your primary key on that table, then it makes life easier to add the new field. Assuming you want the new auto increment field to be the primary key...

```
 ALTER TABLE mytable ADD idcol INT NOT NULL AUTO_INCREMENT PRIMARY KEY 
```

That will add your new field, and it should fill in all of your existing rows with a unique number.  Now you dont have to use the count variable I used before, and adding New rows will automatically get a number id. 

After adding the new field, Id do a quick check to make sure all is in order with the existing rows...

 ```
SELECT idcol FROM mytable;
```

should give you a list of numbers

---

### Post by CoffeeRain on 2012-01-06
Wow! Thanks. After Googling for an hour for a solution, you were able to solve it right away.
:D

---

### Post by KdotJ on 2012-01-06
You're very welcome ;)

you may have a follow up question (as I don't know your MySQL experience using auto_increment columns) such as **"How do I insert a row on a table that has an auto_increment field?"**... So I'll explain anyway.

Lets assume you have a simple table with 3 attributes:
```

+------+-------+-------+
| name | color | idcol |
+------+-------+-------+
| Alex | blue  |   1   |
| Tom  | grey  |   2   |
| Jess | red   |   3   |
+------+-------+-------+

```

And you want to add a new person to the table, there are two ways to do it...

1) Specify what columns you are inserting into in your INSERT statement, and not include the idcol. This will automatically insert the next number into the idcol:

```
INSERT INTO mytable(name, color) VALUES ('Anna', 'pink');
```

2) The other option (which is perhaps simpler when you have a table with lots of columns) is to not specify the columns and use NULL for the idcol:

```
INSERT INTO mytable VALUES ('Anna', 'pink', NULL);
```

This will also insert the correct next number into the idcol field. Of course, you may already know this anyway lol.

---

