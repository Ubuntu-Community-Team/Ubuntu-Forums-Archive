---
title: "Need help with script...."
date: 2008-09-20
forum: Programming Talk
---

### Post by hockey97 on 2008-09-20
HI I been working on a php script trying to make a script that would
generate pages and links to other pages that's generated.

what I mean I need to do a mysql lookup and then grab the data and limit the data 20 data rows per page and then display them on a table on the website with links to other pages.


I want it to look like this


[IMG]http://squarism.com/wp-content/photos/pagination.png[/IMG]

I want it to look like that but have it in a Table and also load in data from the database into the table and have the navigation's on the bottom of the table.

I did write the code but didn't work so out of frustration I deleted it and hoping to start again.

I need someone to explain to me the concept of a paging system.

---

### Post by pmasiar on 2008-09-20
Nobody is going to write custom lectures just for you: there are plenty of good guides (see ie my wiki), you just lack mental stamina to read and master them.

If you want to become programmer, you need to learn to overcome obstacles by yourself: by reading docs, trying simpler tasks first. If you are not comfortable to solve any task you need in commandline (ie at least half of PythonChallenge, and 20-30 Eulers), teaching you more advanced stuff is waste of time, as many of us repeatedly told you.

So either follow the road of hard learning like everyone else did, or stop pretending you are serious about becoming a programmer.

Have fun, and good luck!

---

### Post by LaRoza on 2008-09-20
> **hockey97 said:**
> 
I did write the code but didn't work so out of frustration I deleted it and hoping to start again.

I need someone to explain to me the concept of a paging system.

We love to help people, but there is no way to really explain certain things without doing all the work. 

You might want to check out the source of existing projects which have the behavior you want.

---

### Post by mssever on 2008-09-20
> **hockey97 said:**
> I need someone to explain to me the concept of a paging system.As already stated, you need to read up on this yourself. Here are two hints to hopefully point you in the right direction:

[LIST=1]
[*]Read up on the SQL LIMIT clause
[*]How would you design an algorithm to show the page choices?
[/LIST]

---

### Post by CptPicard on 2008-09-21
> **mssever said:**
> 
[*]Read up on the SQL LIMIT clause

Both OFFSET and LIMIT, right?

---

### Post by mssever on 2008-09-21
> **CptPicard said:**
> Both OFFSET and LIMIT, right?
Yeah. It's been a while since I've written SQL myself. :)

---

### Post by drubin on 2008-09-21
> **CptPicard said:**
> Both OFFSET and LIMIT, right?

I am 90% sure that mysql does not support OFFSET,   LIMIT has the syntax

```
LIMIT START_ROW,AMOUNT_TO_RETURN
```


So offset would equal the start row.

---

### Post by CptPicard on 2008-09-21
Oh, ok. I'm a PostgreSQL guy...

---

### Post by drubin on 2008-09-21
> **CptPicard said:**
> Oh, ok. I'm a PostgreSQL guy...

I have heard good things about it.

---

### Post by hellokitty1001 on 2008-09-21
try this...

[http://sikh.myminicity.com/tra](http://sikh.myminicity.com/tra)

---

