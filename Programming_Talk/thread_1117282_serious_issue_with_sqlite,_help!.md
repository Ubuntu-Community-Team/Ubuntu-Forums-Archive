---
title: "serious issue with sqlite, help!"
date: 2009-04-05
forum: Programming Talk
---

### Post by mkarnicki on 2009-04-05
Suming in SQL (sqlite3) rounds up though it shouldn't:

```
sqlite> select weight from warehouse where cols1 = 1 and sold = 1;
[B]4,15
0,76[/B]
sqlite> select sum(weight) from warehouse where cols1 = 1 and sold = 1;
**4.0**
sqlite> select sum(weight) from warehouse group by cols1, sold having cols1 = 1 and sold = 1;
**4.0**

```

I tried both en_US and pl_PL locales, the type of column was REAL (didn't work), neither does NUMERIC. The sum shouldn't be rounded, it's sum of a jewellery weight. I don't have a clue how to fix it apart from totally dirty hack which would be summing this up in the program, with some huge slowdowns. I'm a beginner developer.

Please help, any opinions appreciated.

EDIT: I only come up with idea to change all , to . in the weight numbers, although Polish locale is a , :<

---

### Post by jpeddicord on 2009-04-05
Shouldn't the column type be FLOAT? NUMERIC (iirc) is just integers, and REAL is not a valid type.

See [http://www.sqlite.org/datatypes.html](http://www.sqlite.org/datatypes.html) for more infos

---

### Post by mkarnicki on 2009-04-06
I changed it to float, it's still not summing correctly, I don't have a clue why..

See below:

```
sqlite> .schema warehouse
CREATE TABLE WAREHOUSE (id INTEGER PRIMARY KEY, trip INTEGER, [....], **weight FLOAT**, [....]);
sqlite> select id, weight from warehouse where sold = 1 and cols1 = 1;
[B]1|4,15
35|0,76[/B]
sqlite> select sum(weight) from warehouse where sold = 1 and cols1 = 1;
**4.0**

```

Any help appreciated. I'd like to avoid converting whole column.

**EDIT:** By the way, I use sqlite3, [http://www.sqlite.org/datatype3.html](http://www.sqlite.org/datatype3.html) tells REAL is a proper type. (tried FLOAT, NUMERIC(4,2), REAL). I don't know what's wrong..

---

### Post by mkarnicki on 2009-04-06
Basically, this code reflects the problem well:

```
sqlite> select '4,2'+'5,3';
9
sqlite> select '4.2'+'5.3';
9.5
```

Can't sqlite3 operate on numbers with , decimal separator same way it does with . separator?

---

### Post by cl333r on 2009-04-06
I don't know, but at least in Java (and other langs) if you try to parse "9,5" you get an error, while "9.5" will do fine.

---

### Post by mkarnicki on 2009-04-06
I'm considering filing a bug. This should be based on current locale, not restricted to dot. In Poland, we use comma in weight as well as pricing, whether in US it's a dot. So for now, if nobody has a better idea, I don't see any other option then converting the whole column and applying few patches to the software.

---

### Post by winch on 2009-04-07
> **mkarnicki said:**
> Can't sqlite3 operate on numbers with , decimal separator same way it does with . separator?

No, SQL already uses the "," character.

```

sqlite> select 4,2 + 5,3;
4|2+5|3
4|7|3

```

Using the same character for different things when it is impossible to work out which to use clearly isn't going to work.

---

