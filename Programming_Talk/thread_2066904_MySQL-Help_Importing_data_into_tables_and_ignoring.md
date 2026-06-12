---
title: "MySQL-Help Importing data into tables and ignoring existing data"
date: 2012-10-05
forum: Programming Talk
---

### Post by zhogan85 on 2012-10-05
I'm new to MySQL and I have a question about importing data from csv files. I've spent the better part of today googling, trying new solutions, then dropping the table and starting over when a potential solution didn't work.

I have a table, with two columns set as the primary key, and 12 subsequent columns where the data will live for each month. I get a csv file each month and I want to import the data into this table. The csv file has three columns, the two primary keys, and the sales figure for that month. I can import one month without issue, but then when I import the subsequent month, the data from the first month is erased, replaced with NULL.

Any help would be much obliged, as I'm out of ideas.

Thanks!

---

### Post by trent.josephsen on 2012-10-05
You can't change the database design? The table you describe... well, it's just a spreadsheet. What advantage do you hope to get from putting it in a relational database?

That said, the UPDATE statement should do what you want. Assuming you're creating records with something like
```
INSERT INTO ugly_table ( key_1, key_2, january ) VALUES ( 'x', 'y', 200.0 );
```

the following will change ugly_table.february without erasing ugly_table.january:
```
UPDATE ugly_table
SET february=250.0
WHERE key_1='x' AND key_2='y';
```

Last SQL I did was Informix so I could be misrepresenting the syntax.

---

### Post by zhogan85 on 2012-10-05
I realize it is essentially a spreadsheet but it is an extremely  large spreadsheet that has exceeded the capacity of excel.

The code you posted makes sense with individual examples, however I'm running into problems with large imports of data.

---

### Post by trent.josephsen on 2012-10-05
Well, post your process and we'll try to help you figure out what's going wrong.

---

### Post by Some Penguin on 2012-10-05
Adding a separate numerical column for 'month' (and dropping the twelve month-specific columns) would bypass much of the problem.

Then either rebuild the pkey to use it, or use an independent arbitrary pkey and enforce uniqueness via constraints.

---

### Post by Tony Flury on 2012-10-06
> **Some Penguin said:**
> Adding a separate numerical column for 'month' (and dropping the twelve month-specific columns) would bypass much of the problem.

Then either rebuild the pkey to use it, or use an independent arbitrary pkey and enforce uniqueness via constraints.

+1 that is how i would do it

In case it isn't clear

You table is : 

Key_1
Key_2
Month_Number
Sales_for_Month

You might want to include a year coloumn too so you can keep a longer spread of data.

---

### Post by zhogan85 on 2012-10-06
OK, thank you I'll try it that way. Most of the keys are repeated each month though, so should I drop the keys entirely, or use an independent arbitrary pkey, as Some Penguin suggested? Or add the month_num to the key?

---

### Post by Tony Flury on 2012-10-06
Your primary key must uniquely identify the row - so since the two keys you already have don't unqiuely identify the row - so you have 12 rows now per year, then yes - you have to include the month/year.

I don't like the idea of an arbritary key to be honest - it means you have to involve other data (i.e. something that tells you the arbritary key from your original key1, key2, month etc) before you can easily query the data.

Also keeping the keys in the table means you can also build individual indexes later should you find you need them.

---

### Post by zhogan85 on 2012-10-06
> **Tony Flury said:**
> Your primary key must uniquely identify the row - so since the two keys you already have don't unqiuely identify the row - so you have 12 rows now per year, then yes - you have to include the month/year.

I don't like the idea of an arbritary key to be honest - it means you have to involve other data (i.e. something that tells you the arbritary key from your original key1, key2, month etc) before you can easily query the data.

Also keeping the keys in the table means you can also build individual indexes later should you find you need them.

Great, thanks for your help Tony, I'll report back Monday or Tuesday when I'm back at work.

---

### Post by zhogan85 on 2012-10-08
Success! Thanks again for your help, Tony, et all. Going forward, I will use 4 column tables, with 3 columns assigned as the key.

---

