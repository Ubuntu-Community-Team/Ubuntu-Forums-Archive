---
title: "Java acting weird with dates"
date: 2011-11-12
forum: Programming Talk
---

### Post by raac on 2011-11-12
There is a MS SQL database that java talks to. For some strange reason, every time it reads a date, java thinks it is two days behind.

For instance if the database has 2011-12-01

After I do

```

Date date = resultSet.getDate("theDate");

```

date value is "2011-11-29".

I could never figure out why it is doing that, anyway I decided to add two days to whatever I have. so I did the following.

```

Calendar cal = Calendar.getInstance();
cal.set(date .getYear(), date.getMonth(), date.getDay());
cal.add(cal.DAY_OF_YEAR, 2);

```

I tried cal.DAY_OF_YEAR and cal.DAY_OF_MONTH in the add method

In both ways the result is "2011-11-31". Obviously, November does not have 31 days. What can I do?
Does anybody know what is happening?


Thanks.

---

### Post by t1497f35 on 2011-11-12
Try getting the value of the date as a string: resultSet.getString(colName), if the string value is different from "2011-11-29" then draw conclusions. Otherwise I don't know what's wrong.

---

### Post by raac on 2011-11-12
It does the same thing if I retrieve it as a String

---

### Post by t1497f35 on 2011-11-12
> **t1497f35 said:**
> Try getting the value of the date as a string: resultSet.getString(colName), if the string value is different from "2011-11-29" then draw conclusions. Otherwise I don't know what's wrong.
Sorry, typo, I obviously mean "2011-12-01", not "2011-11-29".

Edit: Also, I usually use java.util.GregorianCalendar, it might make a difference to your test which adds 2 days to November.

---

### Post by raac on 2011-11-12
> 
Sorry, typo, I obviously mean "2011-12-01", not "2011-11-29".

Edit: Also, I usually use java.util.GregorianCalendar, it might make a difference to your test which adds 2 days to November. 	


I figured you meant "2011-12-01"

I tried with GregorianCalendar and it didn't work either. I don't know why it is doing that, it does not make any sense.

---

### Post by jwbrase on 2011-11-12
Well, there's this link: [http://stackoverflow.com/questions/7724258/date-columns-in-sql-server-mssql-jdbc-3-0-running-under-java-1-7-0-retrieved-a](http://stackoverflow.com/questions/7724258/date-columns-in-sql-server-mssql-jdbc-3-0-running-under-java-1-7-0-retrieved-a)

And this one: [http://blogs.msdn.com/b/jdbcteam/archive/2011/11/07/supported-java-versions-november-2011.aspx](http://blogs.msdn.com/b/jdbcteam/archive/2011/11/07/supported-java-versions-november-2011.aspx)

The first link mentions the JDBC driver as a potential problem, and the second says that the JDBC driver currently only supports Java 1.5.0 and 1.6.0.

So if you're using Java 1.7.0, that's probably your problem, as the MS JDBC driver doesn't yet support it.

---

### Post by ofnuts on 2011-11-12
The spelled out date is a figment of your imagination...especially with Java. Never use spelled out dates, use timestamps (java.util.Date or java.sql.Date), that are absolute. 

For instance, imagine that at the same time (they are on the phone with each other and say "go") a guy in Paris (UTC+1) and a guy in London (UTC) do something that is logged in your database. Assume it's 23:30 on November 12th in London, which means it's 00:30 on November 13th in Paris. What spelled out date do you log? The local date for these guys? The server date? While if you use the java.util.Date, you'll be logging exactly the same thing for the event in London and the one in Paris. And if later the french guy looks up the update by the english, he will find that it happened at 00:30 on the 13th, exactly like his own.[SIZE=3][SIZE=2]And the english will find they both happened at 23:30 on the 12th[/SIZE].[B] 

The spelled out date is nothing more than the result of formatting a timestamp for a given time zone[/B][/SIZE]. 

For your actual problem, find the answers to:

1) if the date is stored spelled out in the base as a string or as a timestamp?
2) if a timestamp, is it a real one (with time) or is arbitrary (forcing time to 00:00:00.000 usually)?
3) what is the TZ used by the DB server?
4) what is the TZ used by your Java code?
5) what is the TZ used by any tool you use to lookup the DB data directly (TOAD or else)?

---

### Post by Arndt on 2011-11-12
> **raac said:**
> There is a MS SQL database that java talks to. For some strange reason, every time it reads a date, java thinks it is two days behind.

For instance if the database has 2011-12-01

After I do

```

Date date = resultSet.getDate("theDate");

```

date value is "2011-11-29".

I could never figure out why it is doing that, anyway I decided to add two days to whatever I have. so I did the following.

```

Calendar cal = Calendar.getInstance();
cal.set(date .getYear(), date.getMonth(), date.getDay());
cal.add(cal.DAY_OF_YEAR, 2);

```

I tried cal.DAY_OF_YEAR and cal.DAY_OF_MONTH in the add method

In both ways the result is "2011-11-31". Obviously, November does not have 31 days. What can I do?
Does anybody know what is happening?


Thanks.

With dates, you always have to check when programming whether months go from 1 to 12, or from 0 to 11. And the same for the other entities. Could the problem be a discrepancy in what interpretation the different objects use?

---

### Post by raac on 2011-11-12
> 
Well, there's this link: [http://stackoverflow.com/questions/7...-0-retrieved-a]("http://stackoverflow.com/questions/7724258/date-columns-in-sql-server-mssql-jdbc-3-0-running-under-java-1-7-0-retrieved-a")

And this one: [http://blogs.msdn.com/b/jdbcteam/arc...mber-2011.aspx]("http://blogs.msdn.com/b/jdbcteam/archive/2011/11/07/supported-java-versions-november-2011.aspx")

The first link mentions the JDBC driver as a potential problem, and the  second says that the JDBC driver currently only supports Java 1.5.0 and  1.6.0.

So if you're using Java 1.7.0, that's probably your problem, as the MS JDBC driver doesn't yet support it. 	


You were right, Java 7 does not support the driver. I installed Java 6 and it worked just fine. I hope they update the driver sooner.

Thanks a lot

---

