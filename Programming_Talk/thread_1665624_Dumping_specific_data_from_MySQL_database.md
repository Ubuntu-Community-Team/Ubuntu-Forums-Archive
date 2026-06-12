---
title: "Dumping specific data from MySQL database"
date: 2011-01-12
forum: Programming Talk
---

### Post by pcman312 on 2011-01-12
I'm looking to be able to dump the data from a specific table in the database, but I also want to have it dump all of the data from any table that it references through foreign keys. So for instance:

```
Table A:
	id bigint(20),
	name varchar(30),
	b_id bigint(20), <-- foreign key, not just a column (same for the others in this example)
	c_id bigint(20)
```

```
Table B:
	id bigint(20),
	value decimal(12,2),
	d_id bigint(20)
```

```
Table C:
	id bigint(20),
	name varchar(30)
```

```
Table D:
	id bigint(20),
	value decimal(12,2)
```

```
Table E:
	id bigint(20),
	value decimal(12,2)
```

From this, dump all of the data from A, which would then dump B and C, and B would dump D. E would not be dumped at all.

Is there a way to do this automatically, or am I going to have to just get all of the foreign keys and then recursively dump each table myself/through a script?

---

