---
title: "MySQL Insert Issue (JAVA)"
date: 2012-12-07
forum: Programming Talk
---

### Post by kevinharper on 2012-12-07
I am having issues inserting into my MySQL DB.

I have successfully executed SELECT queries, but keep getting syntax errors. I even got one after inserting a row manually via PHPMyAdmin, copying the query it returned for the insert, and then pasting it into the SQL textarea.

The DB isn't used for anything except this project. But I'm not sure if I should just share the un/pwd on an open forum. :S

Here is the code that query construct that is passed via executeUpdate():
```
query = "INSERT INTO " +  USERS + " ('id','user_name','password','full_name','active')" +
					" VALUES(NULL,'" + userName + "','" + password + "','" + fullName + "',1)";
```

Here's what it looks like when I print it to the console:
INSERT INTO cis279JAVA.users ('id','user_name','password','full_name','active') VALUES(NULL,'testUN','testPWD','testName',1)

I have also tried the above string with single quotes (') around the 1, no difference.

---

### Post by spjackson on 2012-12-08
You cannot use single quotes to quote column names. You have 3 options: don't quote the columns, use the MySQL default of backtick, or use the ANSI standard double quote.

You don't need to quote column names, unless there is something special about them, such as containing a space.
```

(id,user_name,password,full_name,active)

```

The MySQL default is to use backticks, but this is not portable to other DBMS.
```

(`id`,`user_name`,`password`,`full_name`,`active`)

```

You can use ANSI standard double quote, but you need to explicitly enable it in MySQL.
```

set session sql_mode = 'ansi';
("id","user_name","password","full_name","active")

```

---

### Post by kevinharper on 2012-12-08
Worked like a charm! Awesome! Thank you for the reply. I spent hrs looking into this in the past few days. I must have overlooked that minor detail when reading through the dozens of tutorials.

---

