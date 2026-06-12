---
title: "Parse textfile and update MS SQL tables"
date: 2008-06-04
forum: Programming Talk
---

### Post by elj4176 on 2008-06-04
Looking for a language to use to parse a textfile with fixed length fields and update a MS SQL databse. I've done a bit of php and can connect to the db and get data but I have a feeling that is not the most effecient language to use for this and I'd rather it was not a web app.
I have VS.net 2003 but it will not allow me to connect to the MS SQL Server - only the MSDE. 
Python, perl, bash, C++ - stay with php?
any suggestions (other than dumping the MS SQL server for mySQL)?

---

### Post by geirha on 2008-06-04
I don't have any experience with MS SQL, but if php can connect to it, then you might as well use it. Php can be used in the shell as well as on the web server. A google search gave this as the first hit, which shows a simple shell script with php [http://www.phpbuilder.com/columns/darrell20000319.php3](http://www.phpbuilder.com/columns/darrell20000319.php3)

---

### Post by pmasiar on 2008-06-04
pymssql.sourceforge.net/

---

### Post by ghostdog74 on 2008-06-04
if you are experienece in PHP: try [this]("http://www.php.net/mssql")
a web app has the advantage of a central location and don't have to redistribute your programs to users using VB

---

### Post by slavik on 2008-06-04
> **pmasiar said:**
> pymssql.sourceforge.net/
sorry, that is a bad advice.

Use PHP from command line, or if you want, picking up Perl should be really fast.

---

### Post by elj4176 on 2008-06-04
thanks! I will have a look at those links.

This will be a 'quick and dirty' app just to save me some time. Anything i can use an odbc connection with will work too.

---

### Post by ghostdog74 on 2008-06-04
> **elj4176 said:**
> thanks! I will have a look at those links.

This will be a 'quick and dirty' app just to save me some time. Anything i can use an odbc connection with will work too.

yes, PHP can connect through ODBC as well. See [here]("http://www.php.net/odbc"). In fact, google "PHP database" and you may find more info.

---

