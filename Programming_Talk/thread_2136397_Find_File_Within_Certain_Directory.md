---
title: "Find File Within Certain Directory"
date: 2013-04-17
forum: Programming Talk
---

### Post by huangyingw on 2013-04-17
Hi,
   I want to write such a script file, named  AdvanceSearch.sh. It will accept 2 parameters:
   $1: the path to search for;
   $2: the file name with part or all path;
   For example, there is a file: 
/company/forms/renewal/register/form.xml
  My expected command line operation would be ```
AdvanceSearch.sh /company/ "register/form.xml" 
```
  In the above command, /company is the $1.
  "register/form.xml" is the $2.
  Could someone give me some guidance?

---

### Post by aromo on 2013-04-17
find is your friend.  No need to create a shell script
```
man find
```

---

### Post by schragge on 2013-04-17
+1
In your case the suitable find command would be ```
find /company -path \*/register/form.xml
```

---

### Post by huangyingw on 2013-04-17
> **schragge said:**
> +1
In your case the suitable find command would be ```
find /company -path \*/register/form.xml
```
Yes, that's exactly what I want.

---

