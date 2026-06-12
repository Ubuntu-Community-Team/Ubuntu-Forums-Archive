---
title: "Database design - what do you think??"
date: 2008-04-03
forum: Programming Talk
---

### Post by piousp on 2008-04-03
Hi everyone!

I'm looking for some advice in this design.

The "problem" goes like this:

We have Areas. An Area can haev many Faculties. A Faculty can have many schools. And finally, a school have many students.

I know it can be done in my design, but for example, "get all the students from 1 specific area" would be a kinda big select, wouldnt it?

I'm by no means, a db expert, thats why i'm asking here :)

Thanks in advace!

---

### Post by piousp on 2008-04-03
BTW, i used DBDesigner. I would rather use umbrello, but i'm at work right now :P

---

### Post by pedro_orange on 2008-04-03
It wouldn't be that big of a select. 

The idea of normalising your tables is to prevent repeating data. 
You don't want one monolithic table that you query all the time, cause that would be slow and inefficient. 

The main thing is:

Data integrity vs. Performance.

You have to find a balance that is best for your problem. I would tend to go for data integrity, but thats because people would rather wait an extra few seconds for a query to return than data loss/problems in my line of work.

---

### Post by MilkeySUFC on 2008-04-03
pedro_orange is right, it's not that big a query. 

You could add id_area to the School table but that adds in duplication and maintenance issues.

From a requirements point, do you need to cater for students moving school or history of school years?

---

### Post by piousp on 2008-04-03
Thanks for answering!!!

About the requirements:

Nope, once all the data is loaded onto the DB, it WONT change.. except for students. They do have the possibilty to change from one school to another, but again, i dont see much of a problem.

As far as I am concerned, i'm thinking the same as pedro_orange: data integrity.

The perfonce beneffits that i got by adding id_area to student is irrelevant as the end user wont notice 0,5 more seconds or something like that.

But its always better to have others give you some synergy! Long live open source! :)

---

### Post by piousp on 2008-04-03
Just to let you know, this comunnity is awesome

---

### Post by skeeterbug on 2008-04-03
The model looks fine. I wouldn't worry about joining that few of tables. Even with HUGE joins, you still have things like caching to improve performance if needed. Also, most ORM's do the joining for your, so you don't have to worry about the complexity of the join. Either way, stick with the data integrity.

---

### Post by CptPicard on 2008-04-03
> **pedro_orange said:**
> 
The idea of normalising your tables is to prevent repeating data. 
You don't want one monolithic table that you query all the time, cause that would be slow and inefficient. 

I have to take issue with this... it is indeed the normalizing of data that causes you a computational hit because you need to join more. A typical performance enhancement in a database is *not* normalizing, and thus sacrificing some data integrity purity...

That said, I personally always go for purity too because my bases handle money, and hardware is cheap :)


> **skeeterbug said:**
> Also, most ORM's do the joining for your, so you don't have to worry about the complexity of the join.

Yes, you do have to worry about the complexity, because it just doesn't magically go away because of the ORM layer. The ORM still maps it into a possibly big join, which can be slow... but hopefully the database's query optimizer is good!

---

### Post by piousp on 2008-04-03
Thanks for your comments!

---

### Post by skeeterbug on 2008-04-03
> **CptPicard said:**
> 
Yes, you do have to worry about the complexity, because it just doesn't magically go away because of the ORM layer. The ORM still maps it into a possibly big join, which can be slow... but hopefully the database's query optimizer is good!

Sorry, I meant the complexity of writing the huge query by hand, not how the engine processes it.

---

