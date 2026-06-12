---
title: "PHP require"
date: 2012-05-09
forum: Programming Talk
---

### Post by emiller12345 on 2012-05-09
Is there anyway to tell if a file is being called as a require to another file, or if it is being accessed directly?

---

### Post by Bachstelze on 2012-05-09
Not an expert, but looks like you can use $_SERVER['PHP_SELF'].

---

### Post by emiller12345 on 2012-05-10
yes thank you.
[PHP]("MyPHP.class.php" === basename($_SERVER['PHP_SELF']))[/PHP]this appears to work okay to discriminate the required from non required
edit:
I didn't realize that $_SERVER['PHP_SELF'] variable is "user editable", as such it should probably be run through htmlentites to avoid XSS
[PHP]("MyPHP.class.php" === basename(htmlentities($_SERVER['PHP_SELF'])))[/PHP]

---

