---
title: "[SOLVED] MySQL Databases"
date: 2008-10-28
forum: Programming Talk
---

### Post by slimx3m on 2008-10-28
so i really don't know if i am posting on the right place or not, but i'll give it a shoot.  well, i have a question about databases, if there is somebody that could enlighten me that would be appreciated.

let me give you a brief summary of my project.  i am currently working with around 350,000 records that are going to be imported to MySQL from Microsoft Access.  YES, Microsoft Access. i know how to create a cvs file using "mdbtools" in order to create my db schema and export my record into a csv. i don't have any problems doing that.

so here were my question comes... i really don't have that much of experience working with databases and i was wondering what would it be the best.

IF having one database with all my tables inside
OR having multiple of databases with different tables

so, that i would like to know which one would be more efficient?

thank you in advance

---

### Post by curvedinfinity on 2008-10-28
From experience, I'd stick to one database containing all the tables. It makes life easier. :)

---

### Post by slimx3m on 2008-10-28
thnx for your quick response. that is what i thought too. is there any difference in the speed of retreiving records, making records, and/or updating records in one db or multiple dbs?!  do you know by any chance?

thanks

---

### Post by drubin on 2008-10-28
> **slimx3m said:**
> thnx for your quick response. that is what i thought too. is there any difference in the speed of retreiving records, making records, and/or updating records in one db or multiple dbs?!  do you know by any chance?

thanks

Yes there would deffinatly be a performance knock by having the data in more then one db. This would be because your application/script would have to make 2 connections to 2 isolated applications/servers.

---

### Post by slimx3m on 2008-10-28
> **drubin said:**
> Yes there would deffinatly be a performance knock by having the data in more then one db. This would be because your application/script would have to make 2 connections to 2 isolated applications/servers.

thanks for this useful information

---

### Post by pp. on 2008-10-28
If the databases really could be used independently of each other, and if your application was written in a way to run queries and updates on several databases at the same time (such as by multithreading), then there would be performance gains by running separate databases.

However, 350k records does not seem such an awful lot of data for a database engine. I'd be more concerned about the number of transactions you expect to perform in a given time.

---

### Post by drubin on 2008-10-28
> **pp. said:**
> If the databases really could be used independently of each other, and if your application was written in a way to run queries and updates on several databases at the same time (such as by multithreading), then there would be performance gains by running separate databases.

However, 350k records does not seem such an awful lot of data for a database engine. I'd be more concerned about the number of transactions you expect to perform in a given time.

How would there be performance gains by making 2  connections to 2 differnt data base servers.  It would be the same as making 2 connections to a *proper* configured data base server. and application

Yes 350k records is not that big for a data base engine. But as pp. pointed out the size is not as important as the number of transactions you expect to be running. If this is a stats reporting info and there is only one query to run but it takes a few seconds then that is ok.

---

### Post by pp. on 2008-10-28
> **drubin said:**
> How would there be performance gains by making 2  connections to 2 differnt data base servers.  It would be the same as making 2 connections to a *proper* configured data base server. and application

Running two distinct (or n) servers in parallel can cut the time needed to run a number of transactions by more than a factor of n. Driving the connections to the server or servers grows primarily linear with the volume of data moved for transmitting the requests and the answers. 

Also, the main workload lies with processing the transaction, not with running the connection.

However, it also depends of the throughput your network is able to sustain. If the network is your bottleneck, the question of the speed of the database servers becomes academical.

---

### Post by slimx3m on 2008-10-28
so far everything is going to be running internally.  but in the future i would want we able to use this web app from a external connection. as it right now no external users will be using this web app, because of my bottle neck connection.  and its capacity is not that fast to hold multiple transactions at the same time.

since i am starting everything from scratch, i am trying to think ahead and try to figure out whether i should go with just one database or multiple of them performing different things.

i mean, the way this web app is going to run is having a members database which is going to contain different tables.  and then the staff will move just sign members to the real members.  and what i was trying to figure out is, if would be better moving sign members from its database to real members database, and keep the members database alone for the users only.

does that make sense? would that still make a big difference of having one or multiple databases?

thank you for you help (all)

---

### Post by drubin on 2008-10-29
I think pp. point is more of a theoretical to save a few milli seconds here and there (Huge improvement on very very high scale appplications) but for your needs  KISS. Keep it simple...

If you are writing a relativly small load application having the data in a single data base and having to keep track of one data base connection is going to be some work. So I say make it as simple for your self as posible. If the need comes that you need to maintain high load scalablity then you can implement solutions to solve this.

@ pp. 
[optimization]("http://en.wikipedia.org/wiki/Optimization_(computer_science)") :)

---

### Post by slimx3m on 2008-10-29
> **drubin said:**
> I think pp. point is more of a theoretical to save a few milli seconds here and there (Huge improvement on very very high scale appplications) but for your needs  KISS. Keep it simple...

If you are writing a relativly small load application having the data in a single data base and having to keep track of one data base connection is going to be some work. So I say make it as simple for your self as posible. If the need comes that you need to maintain high load scalablity then you can implement solutions to solve this.

@ pp. 
[optimization]("http://en.wikipedia.org/wiki/Optimization_(computer_science)") :)

thanks for this information.  i am really up to make myself easier, but i was just wondering if there was a big difference between the two of them.  but, now it make more sense and it is a lot clearer.

thanks everybody for your helpful response

---

