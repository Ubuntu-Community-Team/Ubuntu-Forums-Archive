---
title: "mysql auto-increment skipping values"
date: 2012-11-21
forum: Programming Talk
---

### Post by siddharth007 on 2012-11-21
Hi all.I am using a bash script to populate a db table with some data in text file.(Using **Load data infile **command)  Everything is imported nicely from the text file to the db table.However  i have an auto increment column in the table(with auto_increment=1) and  it skips some values every time the script runs.Something like this  happens

[B]# script runs for the first time
ID
1
2
3
4
5
# Second run of script
8
9
10
11
12

[/B]
it is skipping 6 and 7. Multiple records are being inserted into table with each execution of the script.Is  it some kind of bug in mysql which is causing it?? Any solutions for  the problem.I am using mysql-server-5.5.24 and os is Ubuntu-12.04

---

### Post by Bachstelze on 2012-11-21
It's probably a bug not in MySQL but in your script. Post it.

---

### Post by kevinharper on 2012-11-21
+1 what Bachstelze said.

---

### Post by siddharth007 on 2012-11-27
Its not a bug in my script. Its kind of a bug in mysql and i found a workaround for it :guitar:

---

### Post by spjackson on 2012-11-27
> **siddharth007 said:**
> Its not a bug in my script. Its kind of a bug in mysql and i found a workaround for it
Interesting... do you have a bug reference number or link for that?

---

### Post by KdotJ on 2012-11-27
I second that... As I have never encountered this bug before

---

### Post by CptPicard on 2012-11-28
Is auto_increment guaranteed to produce sequential values without gaps in the first place? It might not be.

---

### Post by lisati on 2012-11-28
> **spjackson said:**
> Interesting... do you have a bug reference number or link for that?

> **CptPicard said:**
> Is auto_increment guaranteed to produce sequential values without gaps in the first place? It might not be.

> **Bachstelze said:**
> It's probably a bug not in MySQL but in your script. Post it.

I second all these suggestions. Computers are good at doing what they're told, which might not always be the same as what you want, and even something seemingly as simple as "auto_increment" can sometimes work in unexpected ways.

---

### Post by trent.josephsen on 2012-11-28
> **CptPicard said:**
> Is auto_increment guaranteed to produce sequential values without gaps in the first place? It might not be.

I was thinking the same thing. Especially when you're doing lots of transactional stuff. Autoincrement is for generating *unique* IDs, not *sequential* ones.

---

### Post by siddharth007 on 2012-11-29
Trent i second your opinion on this.The auto_increment guarantees unique values not sequential ones.:) Thanks for your replies everyone.However, i have found out a workaround for this. By resetting the auto_increment to 1 everytime the script runs,i can  obtain a sequential value.Say,first time i ran the script,it inserted 5 records.I now use alter table query to reset auto_increment to 1.However the query resets it to (maxid+1) i.e 5+1=6. So when the script runs the next time it starts from 6 instead of 8 or 9.

---

### Post by KdotJ on 2012-11-29
Glad you found a workaround...

Just out of interest... Why is it so imperative that your ID's are sequential with no gaps? As stated, the idea is that auto_increment produces unique values which is what's needed for primary keys. 

Not saying it's wrong, but I feel it will be possibly troublesome in the future if you're application design *requires* that these be sequential... as you will always have to make sure this is enforced.

---

### Post by tmnuwan12 on 2013-11-05
ALTER TABLE user AUTO_INCREMENT =1;
I tried to use above sql statement to reset the auto_increment value. It will just set the value to 1. Anything you will try to insert will be starting from 1. If you have that record already you will get an error (If that column is a primary key column for example)..

"[COLOR=#000000].However the query resets it to (maxid+1) i.e 5+1=6. So when the script runs the next time it starts from 6 instead of 8 or 9." This doesn't work for me. Am I doing anything wrong?

[/COLOR]

---

