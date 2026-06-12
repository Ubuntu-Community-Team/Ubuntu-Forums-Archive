---
title: "JDBC resultset to int"
date: 2010-03-15
forum: Programming Talk
---

### Post by cdiem on 2010-03-15
I have the following query (sqlite3):

```
SELECT max(id) FROM table WHERE content = "testtest";
```

and the following Java code:

```
prepStat = conn.prepareStatement(<the_above_query>);
ResultSet rs = prepStat.executeQuery();
```

The above query produces a result like: "9" or "8" or some other number. 
How can I read it from the ResultSet (rs) and use the number further in the java code?

---

### Post by cdiem on 2010-03-15
I have just solved it:

```
 	if(rs.next()) {
				id = rs.getInt(1);
	
			}

```

I must have searched google better before posting here; sorry about that. Closing the thread.

---

