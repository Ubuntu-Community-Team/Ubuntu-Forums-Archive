---
title: "Is normalized data for sissies?"
date: 2005-12-19
forum: Programming Talk
---

### Post by sapo on 2005-12-19
lol..

[http://www.kottke.org/04/10/normalized-data](http://www.kottke.org/04/10/normalized-data)

This is a kinda of interesting text about flickr, and this [PDF](http://www.niallkennedy.com/blog/uploads/flickr_php.pdf) is interesting too... but my problem is at my work, i know that we have a lot of databases gurus here, hope you guys can help me out, so here we go :cool: 

I ve been coding on my own for a long time now, actually i m coding php, using php5 and firebird 1.5 as database.

At my work i m coding a kind of administrative software, in php, this software is meant to control the sellings, cash, stock, and all that stuff, of a small company.

But today i was with a normalization problem, i started to work in the cash stuff right now, but my boss still thinks that every software is like msdos was (dbf database and all that stuff), so we are aways arguing about the database, i ll try to explain.

I had 3 tables:

incoming, bills, and cash (dunno how can i explain this in english, but basically incoming is what they earn, bills is what they spent, and cash is what they have in hand).

So i had the brilliant idea to make the 3 of them become one, cause they seemed redundant for me, something like this:

When the company sells, it creates an incoming, but this incoming can be a future payment, so i have: selling_date, and received_date, and i have the same with the bills table.

So if you think about it, what is positive are the incoming, whats negative are the bills, and when i have the received_date means that i have that in CASH, so i can in just one table know exactly the same that i knew using 3 tables.

But i ve been out of this "database market" for a long time now, and i learned normalization and database years ago and stayed a lot of time without using it.

So guys, could you give me advices in this matter, is what i ve done gonna work? Anyone got a better solution for this "cash" stuff?

thanx in advance, hope you can understand, cause my english vocabulary is kinda rusty you know :D

---

### Post by LordHunter317 on 2005-12-19
Posting schema would be helpful (preferably before and after) as while I think I understand your problem, I'm having troubles visualizing it.  Any reasonable sane SQL would suffice, or an ERD or something.

---

### Post by LordHunter317 on 2005-12-19
I should point out having read that blog post, the guy from flickr has no clue as to why normalization is performed, and should just be ignored.  Normalization is preformed so that there's only one copy of the data.  That's a *good* thing, as it means when you change something, you only have to change it once and you know it's done.  If you have multiple copies, you have to change all of them.  Missing even *one* means your data is **wrong** and that's a very bad thing.  Performance doesn't matter if you give wrong answers.

---

### Post by blastus on 2005-12-20
My personal opinion on this is that all data models should be normalized unless there is a very good reason not too. There are a few cases where a fully normalized (3rd NF) data model may not be the *best* choice. For example, star schemas, are particularly useful in data warehouses where data analysis must be performed on large amounts of data and on multiple levels of aggregation. A star schema consists of a normalized fact table and several denormalized dimensional tables. One company I worked for used DB2 and star schemas to drive a data warehouse containing hundreds of multimillion row tables. The fully normalized alternative to the star schema is the snowflake schema, but generally queries on a star schema are simpler and perform better than queries on a snowflake schema.

Normalization usually involves a compromise between performance and data integrity. Generally all transaction processing systems data models are fully normalized because data integrity would be difficult if not impossible to maintain otherwise. *Absolute* data integrity is often not critical in decision support systems like it is in transaction processing systems, so data models that drive decision support systems may only be partially normalized (i.e. star schemas.)

---

### Post by sapo on 2005-12-20
thanx guys, i ll post the schema as soon as a get to work, thanx for you replies.

I aways try to normalize as much as possible.. but my boss doesnt like that, he wants data all around to be easy to access, just like the flickr guy :(

---

### Post by sapo on 2005-12-20
Here we go:

Before:
[img]http://img530.imageshack.us/img530/4900/before6zn.jpg[/img]

After:
[img]http://img526.imageshack.us/img526/262/after5ac.jpg[/img]

ok, let me explain what is everything about:

Recebimentos are the Earnings, Pagamentos are payments (or bills) and caixa is the cash i have in hand, in the before picture when somebody pay for a product or i pay a bill, i need to insert an new entry on the caixa table.

if you take a close look, all the payments and earnings fields are almost the same.. so i think:

if the value is positive i know that it is an earning, if its negative i know that it is something i have to pay, and when the field cxa_data_rec that is a timestamp is filled with a date, it means that the entry was already paid/received so i have it in hand.

My boss said that this table is gonna have too many entries (almost like what the flickr guy said, that when i need  to search for just one i ll need to search in a very big table for the data i want, but i dont know if the performance will be THAT poor as he is afraid...

what fo you guys think?

thanx :)

---

### Post by LordHunter317 on 2005-12-20
Using one table will be fine here (I think), with one caveat: You must be able to maek the assumption that a NULL  in the cxa_data_rec field means that data hasn't been recieved.  IF you also must care about records where you don't know (it could be recieved, it could not, you just don't know) then you need a second identical table to distinguish unknowns from unrecieved entries.

---

### Post by sapo on 2005-12-20
[QUOTE=LordHunter317]Using one table will be fine here (I think), with one caveat: You must be able to maek the assumption that a NULL  in the cxa_data_rec field means that data hasn't been recieved.  IF you also must care about records where you don't know (it could be recieved, it could not, you just don't know) then you need a second identical table to distinguish unknowns from unrecieved entries.[/QUOTE]
yes, thats how i define what i received and what i do not, i already coded this thing today, everything is working so far, hope i dont have problems in the future :)

thanx :D

---

### Post by squidward on 2005-12-22
Maybe you can get some ideas from XML standards... someone has probably already addressed your problem before. 

Uniform Business Language is toward the bottom of this page: [OASIS]("http://www.oasis-open.org/specs/index.php#avdlv1.0").  It may have some parts applicable to your needs.

If you see a standard you like, you might be able to convince your boss that it is better than 1980's methods.

Just a thought...

---

### Post by sapo on 2005-12-22
I dont convice him, thats impossible, i just lie, i say "I did how you told me to do." 

He doesnt code anything, i just let him think that he is right.. cause its kinda impossible to convince him that he is wrong, i already gave up at that :D

---

### Post by LordHunter317 on 2005-12-22
Best practices for modelling data in XML are generally wrong practices for modeling in a a true normalized relational database.

---

