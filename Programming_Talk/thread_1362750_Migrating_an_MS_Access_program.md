---
title: "Migrating an MS Access program"
date: 2009-12-23
forum: Programming Talk
---

### Post by cariboo on 2009-12-23
I had a client that wrote a program for the logging industry, he has since retired and no longer wants to support the program. I've had requests from some of his customers to maintain and maybe update the program. I really don't want to do that using Access. How hard is it to migrate the program including the logic and databases to mysql, and convert the logic to php.

---

### Post by cybergalvez on 2009-12-23
without seeing what the program does, it should be really simple to do

---

### Post by thornmastr on 2009-12-23
Consider using Python and SqlLite.

---

### Post by cariboo on 2009-12-23
> **thornmastr said:**
> Consider using Python and SqlLite.

Why would I want to use SqLite? 

I have more experience with mysql. I should add, that the application was really to big for Access, it should have used MSSQL.

---

### Post by Can+~ on 2009-12-23
> **cariboo907 said:**
> Why would I want to use SqLite? 

I have more experience with mysql. I should add, that the application was really to big for Access, it should have used MSSQL.

Indeed, if you have access to MSSQL and .NET C#, then you could build client applications easily.

(Everyone else: And don't give me the weird look because I'm suggesting MS tools, these are actually quite good)

---

### Post by WitchCraft on 2009-12-23
You can keep the access database.
Just write a GUI and connect with JET.
JET works on Linux, too...

---

### Post by cariboo on 2009-12-24
Here's an explanation of what the program does:

When a logging truck driver brings a load of logs to the saw mill, the truck is weighed and the driver is given a load slip, with the weight of the load and the mileage, off-road and on-road. The driver turns the load slips in to the bookkeeper at the end of the day, and he/she enters the info. The program then calculates how much the load was worth, how much fuel was used, and how many kilometers the trips involved. At the end of the pay period the program calculates the drivers wages. Most companies pay commission on the the total loads, instead of an hourly wage. One of the year end functions, is that it calculates the amount of fuel used by a particular truck, and then calculates how much of a tax rebate each truck receives. There are other functions included, such as truck and trailer inventory and payroll. 

Just before the original author retired, He was working to integrate the program with Quickbooks, but life got in the way, he found himself a new wife and retired to Yuma Arizona in the winter, and Point Roberts WA. in the summer.

---

### Post by CptPicard on 2009-12-24
About the MySQL vs. SQLite issue... if this is not a client/server application, running a whole database server process for something like this is probably very much overkill. If it's your regular desktop app, you just want a file for the application to use as a data store, and SQLite allows you to do this using an SQL interface.

If this were me writing the application, I would probably use a combination of Python, SQLite and SQLAlchemy for an object-relational mapper layer that would allow for transparent object storage into the db file, but... it's not me writing the application ;)

---

