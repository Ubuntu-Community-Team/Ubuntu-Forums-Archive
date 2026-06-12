---
title: "SQLite weirdness: 'no such column'"
date: 2009-03-20
forum: Programming Talk
---

### Post by DocFox on 2009-03-20
I have this phenomenon which I don't understand:

> 
sqlite> select * from subjects where subjects.id=2;
id|patient_id|family_name|first_name|dob|sex|comments|created_by|record_created
2|123456|Fox|Ben|1972-12-22|m|tryingoutsqlite|ben|2009-03-04 00:19:18

sqlite> delete from subjects where subjects.id=2;
SQL error: no such column: subjects.id

If i can select a record from my subjects table using the id field (an autoincrement integer field for primary key) what am I doing wrong that I can't delete?

---

### Post by ajackson on 2009-03-20
You can, you just need to change your SQL statement to
```
delete from subjects where id=2;
```
Since I don't think you can do multi-table deletes there is no need to dereference the criteria for deleting.

Similarly in your select, since you are only selecting from one table you can get away with
```
select * from subjects where id=2;
```

---

### Post by DocFox on 2009-03-20
hi thanks
yeah i should have mentioned that i tried that first, the subjects.id syntax was me trying different commands out...

curiously when i delete using an id field on an unlinked table i have no problems. could this be an issue with the triggers?

> sqlite> .schema subjects
CREATE TABLE subjects (
id INTEGER PRIMARY KEY, 
patient_id TEXT NOT NULL UNIQUE, 
family_name TEXT NOT NULL, 
first_name TEXT NOT NULL, 
dob TEXT NOT NULL, 
sex TEXT NOT NULL, 
comments TEXT NULL, 
created_by TEXT NULL, 
record_created TEXT DEFAULT CURRENT_TIMESTAMP 
);
CREATE INDEX family ON subjects(family_name ASC);
CREATE UNIQUE INDEX patientid ON subjects(patient_id ASC);
CREATE TRIGGER subject_delete
  BEFORE DELETE ON subjects
  FOR EACH ROW BEGIN
       DELETE from tests WHERE subjects.id = tests.subject_id;
  END;


---

### Post by DocFox on 2009-03-20
It was the trigger that caused the problem, should have been


> 
CREATE TRIGGER subject_delete
  BEFORE DELETE ON subjects
  FOR EACH ROW BEGIN
       DELETE from tests WHERE subject_id = OLD.id;
END;


i should have read [this]("http://www.sqlite.org/cvstrac/wiki?p=ForeignKeyTriggers") more carefully! RTFM and all that...;)

---

