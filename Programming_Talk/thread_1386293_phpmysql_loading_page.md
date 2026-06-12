---
title: "php/mysql loading page"
date: 2010-01-20
forum: Programming Talk
---

### Post by sprouty on 2010-01-20
Hi,

I have a query that takes a while to run (currently taking 10 seconds but i believe the time will only increase.)

Currently when the query runs it holds the page from loading. Is there a way to contine to load the page and where that data should be just have text say loading?

I'm unsure the best way to go about doing this :-S and would be grateful for any help or direction.

Many Thanks,

Sprouty.

---

### Post by hessiess on 2010-01-20
Eather display a `loading' message before running the query, or use a second thread or process for running the query. Though I would also be inclined to work out why the query is so slow. If you havent already moving the database onto a separate server would be a good idea.

---

### Post by korvirlol on 2010-01-20
depends on your specific situation.

may want to look into AJAX: [http://en.wikipedia.org/wiki/Ajax_%28programming%29](http://en.wikipedia.org/wiki/Ajax_%28programming%29)

---

### Post by Hellkeepa on 2010-01-20
HELLo!

Post the query here, along with the table structure, and we can fix that slow loading for you.

Happy codin'!

---

### Post by sprouty on 2010-01-21
Hi Hellkeepa,

Just to give you a bit more of a insight:
```

Date - External login attempts - Uniq Uname - Uniq Pass - Uniq IP
2010-01-21 - 149259 - 130 - 522 - 2 Query loaded in 1.41497 seconds.

2010-01-20 - 375867 - 1415 - 1925 - 6 Query loaded in 3.08025 seconds.

2010-01-19 - 409313 - 3533 - 4623 - 6 Query loaded in 4.8073 seconds.

2010-01-18 - 380592 - 1561 - 2798 - 4 Query loaded in 6.45326 seconds.

2010-01-17 - 247982 - 1783 - 1302 - 2 Query loaded in 8.01801 seconds.

2010-01-16 - 89181 - 1013 - 1564 - 1 Query loaded in 9.41363 seconds.

2010-01-15 - 5321 - 89 - 208 - 3 Query loaded in 10.7382 seconds.

2010-01-14 - 16371 - 411 - 756 - 4 --Query loaded in 12.07046 seconds.
```
I know it slowed done because it works out the time but it about 2 seconds for each query to run.

The database is set up into four tables
1. Username
2. password
3. IP
4 Attacks (this import the primary key of the above tables.

the php code is:[PHP]$query = "SELECT count(id) from Attempts where Date LIKE '$start%'";
        $result = mysql_query($query) or die ("Could retrieve data at this time");
        $row = mysql_fetch_array( $result );
        $attacks = $row[0];

        //get number of users
        $query = "SELECT count(distinct Username) from Attempts where Date LIKE '$start%'";
        $result = mysql_query($query) or die ("Could retrieve data at this time");
        $row = mysql_fetch_array( $result );
        $user = $row[0];


        //Get number of passwords
        $query = "SELECT count(distinct Password) from Attempts where Date LIKE '$start%'";
        $result = mysql_query($query) or die ("Could retrieve data at this time");
        $row = mysql_fetch_array( $result );
        $pass = $row[0];

        //get number of ips
        $query = "SELECT count(distinct IP) from Attempts where Date LIKE '$start%'";
        $result = mysql_query($query) or die ("Could retrieve data at this time");
        $row = mysql_fetch_array( $result );
        $IP = $row[0];

        print "$start - $attacks - $user - $pass - $IP";[/PHP]
I know i could spped it up by archive the past days data out. Once the query it cached it take less than a second.

Although i would still like to have a loading or while the query runs allow the page to load.

Many Thanks,

Sprouty

---

### Post by Finalfantasykid on 2010-01-21
Could you show the table structures though, like show what keys there are and whatnot.

My guess is you are doing a search by using a column that is not an index(therefore would have to do a linear search).

---

### Post by sprouty on 2010-01-21
is this what you are after:

Attempts
Field 	Type 	Null 	Default 	Comments
ID 	int(100) 	No 		[pk,Auto increment]
Date 	datetime 	No 		
Username 	int(100) 	No 		
Password 	int(100) 	No 		
IP 	int(100) 	No 		

IPS
Field 	Type 	Null 	Default 	Comments
ID 	int(11) 	No 		[pk,Auto increment]
IP 	varchar(100) 	No 		


Passwords
Field 	Type 	Null 	Default 	Comments
ID 	int(11) 	No 		[pk,Auto increment]
Password 	varchar(100) 	No 		


Username
Field 	Type 	Null 	Default 	Comments
ID 	int(11) 	No 		[pk,Auto increment]
Username 	varchar(100) 	No

---

### Post by Finalfantasykid on 2010-01-21
Hmm, so ya whenever you are doing the LIKE '$start%', you are doing a search on that column, which is not sorted.  I bet if you changed around the schema a bit, you could have some massive performance improvements.

For example, if you had another table called Dates or something, you could store all of the dates in there, with references to the attempts id.  This would allow for log(n) performance.  I think you would need to change many of the SQL queries though to make it display the proper data.  There may be an easier way to create the secondary index, but I am not a database expert :P

---

### Post by Hellkeepa on 2010-01-21
HELLo!

No need to create a new table, just for the dates. They are normalized data by default, especially if you use timestamps. All that's needed is to create an index on the "date" columns, and you should witness quite a noticable speedup. Also, use the "datetime" functions of MySQL to do the comparisons, instead of treating it like text. Should give you some performance benefits as well, which could be quite noticable. Especially as the tables grow.
Another thing you might try is to join those four queries into one, either by using UNION or JOIN.

Also, if the code above is in a loop, then I highly recommend using the datetime functions and group the results in the wanted resolution. That will give you a huge speed benefit, as you go from 4*<number of days> queries, to 4.
The general tips is: If you have a query inside a loop, especially a SELECT-query, then you're most likely doing something wrong/*very* inefficient.

Happy codin'!

---

