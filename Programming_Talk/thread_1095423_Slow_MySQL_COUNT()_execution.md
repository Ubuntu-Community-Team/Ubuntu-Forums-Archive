---
title: "Slow MySQL COUNT(*) execution"
date: 2009-03-13
forum: Programming Talk
---

### Post by cl333r on 2009-03-13
Hi folks,
I have a table with 500 rows. I query it twice, first query:
-to fetch the rows by given criteria, fetching only the first 20 ones using LIMIT keyword
and 2nd query:
-to count all existing rows by that criteria using the sql COUNT(*) keyword.

The problem: 1st query executes in 0.6 seconds (OK), second query in like 8 seconds (disaster!).
I can't afford more than like 1.5 seconds for both queries, what do I do (wrong)? Any hints?

Below are the actual queries in case it could help:

```

//GET DATA QUERY, executed in 0.6 seconds:
SELECT * FROM added_cargo_table t JOIN countries_table AS sc ON t.source_country=sc.iso JOIN countries_table AS dc ON t.dest_country=dc.iso , users_table u, vehicle_types_table vehicle_types, vehicles_table vehicles, cargo_types_table ctt WHERE ( t.user_id=u.id AND t.transport_type=vehicle_types.id AND t.transport_detailed_type=vehicles.id AND t.cargo_type=ctt.id  AND t.time_added>1236717964671 )  ORDER BY t.time_added DESC LIMIT 0, 20

//THEN FOLLOWS THE COUNT ALL QUERY, executed in like 8 seconds!!:
SELECT COUNT(*) FROM added_cargo_table t JOIN countries_table AS sc ON t.source_country=sc.iso JOIN countries_table AS dc ON t.dest_country=dc.iso , users_table u, vehicle_types_table vehicle_types, vehicles_table vehicles WHERE ( t.user_id=u.id AND transport_type=vehicle_types.id AND t.transport_detailed_type=vehicles.id  AND t.time_added>1236717964671 ) 

```

---

### Post by Phristen on 2009-03-13
I assume the fields you are joining on are all indexed, right?
Anyway, the where clauses in two of your queries are different...
Second one is missing a "t.cargo_type=ctt.id"

Also, explains of these queries could be useful.

Also, you might wanna read some docs about SQL_CALC_FOUND_ROWS.

---

### Post by cl333r on 2009-03-14
Thanks a lot!
SQL_CALC_FOUND_ROWS was what I needed! I googled on it and found a wonderful short tutorial using it:
[http://www.michiknows.com/2007/08/07/the-secret-of-sql_calc_found_rows/](http://www.michiknows.com/2007/08/07/the-secret-of-sql_calc_found_rows/)

btw, now both queries execute within less than a second, huge improvement!

---

