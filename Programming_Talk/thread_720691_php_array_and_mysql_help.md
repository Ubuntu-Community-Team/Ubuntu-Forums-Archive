---
title: "php array and mysql help"
date: 2008-03-10
forum: Programming Talk
---

### Post by lapubell on 2008-03-10
a bit confused as to how to accomplish this.  any help would be great.

I have a mysql database that is filled with a bunch of tables.  for example:

| id | type | name | ...
| 1 | cat | mittens | ...
| 2 | cat | buttons | ...
| 3 | cat | cougar | ...
| 4 | dog | rover | ...
| 5 | cat | tabby cutie | ...
| 6 | bird | tweety | ...
| 7 | dog | kaninja | ...
...


so I know I need to use a loop to read the database info, but how would I build an array that holds the "type" column, without repeating the info?  I don't want a cell for every row, but (for this example) just an array of ("cat", "dog", "bird").

Any ideas?

---

### Post by LaRoza on 2008-03-10
Look at the DISTINCT option for SELECT statements in SQL. It sounds like it is what you want.

---

### Post by lapubell on 2008-03-10
hmm... working on a not that friendly mysql server without command line access.  any help looking into this through phpmyadmin or the sql command to get that info?

sorry for being a newb at sql... databases make my head spin sometimes...

---

### Post by lapubell on 2008-03-10
google and LaRosa to the rescue!  check this out if you have similiar questions.
[http://www.webdevelopersnotes.com/tutorials/sql/online_mysql_guide_the_distinct_keyword.php3]("http://www.webdevelopersnotes.com/tutorials/sql/online_mysql_guide_the_distinct_keyword.php3")

---

### Post by mssever on 2008-03-10
You can enter any query into phpMyAdmin and see the results. I actually tend to use phpMyAdmin instead of the CLI program, even though I have access to the CLI.

---

