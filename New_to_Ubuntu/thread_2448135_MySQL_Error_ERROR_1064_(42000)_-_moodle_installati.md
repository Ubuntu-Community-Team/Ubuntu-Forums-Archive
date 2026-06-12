---
title: "MySQL Error ERROR 1064 (42000) - moodle installation"
date: 2020-08-02
forum: New to Ubuntu
---

### Post by ryu0108 on 2020-08-02
GRANT SELECT,INSERT,UPDATE,DELETE,CREATE,CREATE TEMPORARY TABLES,DROP,INDEX,ALTER ON moodle.* TO moodledude@localhost IDENTIFIED BY 'passwordformoodledude';


ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near IDENTIFIED BY 'passwordformoodledude'' at line 1




I'm stuck here... please help.

---

### Post by SeijiSensei on 2020-08-02
GRANT does not use IDENTIFIED as a valid parameter.

[https://dev.mysql.com/doc/refman/8.0/en/grant.html#grant-database-privileges](https://dev.mysql.com/doc/refman/8.0/en/grant.html#grant-database-privileges)

---

### Post by ryu0108 on 2020-08-03
Hi Thank you for the response, sir. Now, I see why. I was following the tutorial in the moodle site.

Thank you!

---

