---
title: "sql question"
date: 2010-11-01
forum: Programming Talk
---

### Post by lykwydchykyn on 2010-11-01
I'm working on a database created by our software vendor in Microsoft SQL.  I'm trying to track changes made to values in a database table over time.  The table structure is like this:
```

unitID | change_time | Value

```
In other words, every time users change "Value" in the application, a new entry is recorded in this table with the current time as "change time".  unitID is the object they're changing the value for.  


I want a view that basically does this:
```

unitID | current_Value| previous_Value

```

In other words, I want to take the current value of the object, plus the value of the entry with the next lowest time stamp.

I tried something like this:
```

select unitID , t1.Value as current_value, t_old.Value as previous_value
from 
  mytable t1
join (select unitID, Value from mytable t2 where t2.change_time = 
  (select max(change_time) from mytable t3 where t3.change_time < t1.change_time)) t_old on t1.unitID = t_old.unitID

```
That doesn't work, though, I get an error saying that t1.change_time could not be bound.  Any idea how to do this?

---

### Post by meastwood on 2010-11-03
I'm not really an sql person but have messed around with it a bit - below is a stored procedure that I think does what you are looking for HOWEVER it's in MySql.

Maybe it can help.

The test table and the results of oldnew():
```
mysql> select * from test|
+--------+------------+-------+
| unitid | changetime | value |
+--------+------------+-------+
| p1     | 01:59:45   |    47 | 
| p1     | 02:00:43   |    56 | 
| p1     | 02:01:07   |    43 | 
| p2     | 02:01:22   |    41 | 
| p2     | 02:01:30   |    45 | 
+--------+------------+-------+
5 rows in set (0.00 sec)

mysql> delimiter ;
mysql> call oldnew();
+------+------+------+
| id   | old  | new  |
+------+------+------+
| p1   | 56   | 43   | 
| p2   | 41   | 45   | 
+------+------+------+
2 rows in set (0.01 sec)

Query OK, 0 rows affected, 1 warning (0.01 sec)
```

The stored procedure:
```
create procedure oldnew()
begin
     # Declare some local variables
     declare done int default 0;
     declare id varchar(12);
     declare newval, oldval int(10);

     # Declare a couple of cursors
     # 'getvals' will return two rows corresponding to the 'unitid'.  The first row contains the value for the 
     # most recent 'changetime', the second row will be the value for the next most recent 'changetime'.
     declare getvals cursor for select value from test where unitid=id order by changetime desc limit 2;
     
     # getids will return a number of rows each one containing a uniq 'unitid', one per 'unitid' in the table.
     declare getids cursor for select unitid from test group by unitid;
     
     # Declare a loop handler - a cursor's fetch will set the variable 'done' to 1.
     declare continue handler for not found set done = 1;

     # Create a 'temporary' temporary table to hold the resulting values 
     drop table if exists temptest;
     create table temptest(id varchar(12), old varchar(12), new varchar(12));

     # Open cursor to get 'unitid's
     open getids;

     # Start of loop
     repeat
         # For each id retrieved
         fetch getids into id;
         if not done then 
             # Get the two rows that correspond to the most recent 'changetime' and the one just before it 
             open getvals;                                         # Open the cursor to get the values we want
             fetch getvals into newval;                            # Store the latest value in newval
             fetch getvals into oldval;                            # Store the previous value in oldval
             insert into temptest values (id, oldval, newval);     # Insert both values and unit id
             close getvals;                                        # Close this cursor
         end if;
      until done end repeat;                                       # Repeat the process until there are no more unitids

      close getids;                                                # Close this cursor
      select * from temptest;                                      # Display the results
      drop table temptest;                                         # Tidy up
end;
```

---

