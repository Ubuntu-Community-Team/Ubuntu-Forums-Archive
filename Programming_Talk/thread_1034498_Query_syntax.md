---
title: "Query syntax"
date: 2009-01-08
forum: Programming Talk
---

### Post by Vadi on 2009-01-08
Hi,

Can any db experts point out what is wrong here? I have tested the select subquery alone, it works fine, looked at examples in mysql manual on subqueries, it looks the same too... yet mysql gives a syntax error when I try running it:

> INSERT IGNORE INTO `static_data` (`name`, `maintainer`) VALUES (SELECT `name`, `maintainer` FROM `all_applications`);

---

### Post by pp. on 2009-01-09
Knowing the error message might help in finding the cause of the error.

---

### Post by SupaSonic on 2009-01-09
[http://dev.mysql.com/doc/refman/5.1/en/insert-select.html](http://dev.mysql.com/doc/refman/5.1/en/insert-select.html)

Judging by this page, you need to lose the VALUES keyword and the brackets, like so

```
INSERT IGNORE INTO `static_data` (`name`, `maintainer`) 
SELECT `name`, `maintainer` FROM `all_applications`;
```

---

### Post by pmasiar on 2009-01-09
see [http://www.w3schools.com/SQL/sql_insert.asp](http://www.w3schools.com/SQL/sql_insert.asp)

column names cannot be string literals
```

INSERT IGNORE INTO static_data (name, maintainer)
VALUES (SELECT name, maintainer FROM all_applications); 
```

BTW you should read "how to ask questions" in my sig: provide error message, and use CODE tags, not QUOTE so we can quote you :-)

---

### Post by Vadi on 2009-01-09
Didn't provide the error message 'cause I couldn't copy.

Thanks a bunch, the query works now, but the 'ignore' part does not:

[IMG]http://www.ubuntu-pics.de/bild/8111/screenshot_100_193__P03Ts6.png[/IMG]

Manual just says "Specify IGNORE to ignore rows that would cause duplicate-key violations.". Does that not apply to test fields?

---

