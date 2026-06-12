---
title: "PHP Code Problem...."
date: 2011-02-27
forum: Programming Talk
---

### Post by stamatiou on 2011-02-27
Plz Help,
is ther anything wrong with this code?
```
mysql_query("INSERT INTO usersystem (school,name,ln,ec,gc,username, password, email) VALUES ( '$school',$name','$ln','$ec','$class','$username', '$password', '$email')") or die (mysql_error()); echo "Account created.";) 

```

---

### Post by khauenst on 2011-02-27
I know nothing about PHP but it seems the left hand quote around $name is missing

---

### Post by Joeb454 on 2011-02-27
As well as the above, you appear to have an erroneous ')' at the end of the line

---

### Post by Skidbladnir on 2011-02-27
> **stamatiou said:**
> Plz Help,
is ther anything wrong with this code?
```
mysql_query("INSERT INTO usersystem (school,name,ln,ec,gc,username, password, email) VALUES ( '$school',$name','$ln','$ec','$class','$username', '$password', '$email')") or die (mysql_error()); echo "Account created.";) 

```

Well, there are two things.  Firstly, you should run mysql_real_escape_string on those fields, because they are likely coming from a third party.  Anyway, you do not have a single ' around $name.  Also, the ending parenthesis closes the VALUES function.

---

