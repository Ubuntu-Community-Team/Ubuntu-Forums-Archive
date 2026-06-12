---
title: "[SOLVED] Postgres bug??"
date: 2008-09-09
forum: Programming Talk
---

### Post by rax_m on 2008-09-09
Hi all,

I inherited a database with a simple table from a colleague. Instead of manually uploading data, I decided to write a little java app (using netbeans) so we can regularly upload CSV files to it. 

I was having issue with the insert statement and noticed this about the DDL of the table: 
```

CREATE TABLE "Sea_temperature_recorders"
(
  "Location" text,
  "Date" date,
  "Time" time,
  "Temperature" float4,
  "Instrument" text,
  "Analyse" float4,
  id int2 NOT NULL,
  CONSTRAINT "Sea_temperature_recorders_pkey" PRIMARY KEY (id)
) 
WITH OIDS;
ALTER TABLE "Sea_temperature_recorders" OWNER TO rmistry;
GRANT SELECT, UPDATE, INSERT, DELETE, REFERENCES, TRIGGER ON TABLE "Sea_temperature_recorders" TO xxxxx;

```

Notice the quotes around the table and column names. I assume the original person created it like this. 
This causes an issue, as postgres doesn't like inserts unless the column and table names are quoted for every insert. 

```

Internal Exception: org.postgresql.util.PSQLException: ERROR: syntax error at or near "Analyse"
Error Code: 0
Call: INSERT INTO Sea_temperature_recorders (id, Temperature, Location, Instrument, Time, Analyse, Date) VALUES (?, ?, ?, ?, ?, ?, ?)
        bind => [0, 26.465, T1131, I1, 11:00:00, 0.0, 2007-03-27]

```

Is this normal ?? Should this be filed as a bug?

I'm guessing that it would be better to extract all of the data and re-create the tables (without quotes) and work from there. 

Thanks
Rax

---

### Post by kknd on 2008-09-09
Its not a bug, you just can't use keywords as names. Quoting it makes it to be threated as a normal string instead of a keyword.

---

### Post by rax_m on 2008-09-09
Thanks for the reply!
I just figured out the keywords bit. I also noticed that unless you use the quotes, it is not case sensitive. 

so I guess the real issue is, how do I tell netbeans to generate insert code that quotes everything like postgres wants?

---

### Post by themusicwave on 2008-09-09
I have seen this quoting thing happen when using PGAdmin III.

For some reason if you create a table using the Wizard it tends to put quotes around column names whether they are keywords or not.

My solution is always just to grab the SQL out of the wizard, drop the table and recreate it with no quotes.

It is kind of annoying and I wish I understood why they do this.

---

### Post by rax_m on 2008-09-09
I guess they tried to cater for all characters and cases.. 
but it certainly messes things up for other situations 
LOL


Thanks!

---

