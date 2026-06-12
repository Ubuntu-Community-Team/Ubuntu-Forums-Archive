---
title: "Alias in SQL when connecting to MS Access MDB with ODBC"
date: 2008-01-26
forum: Programming Talk
---

### Post by stefanborremans on 2008-01-26
Hello,

I have installed Ubuntu 7.10 on a computer with a working LAMP configuration.
What I'm trying todo is connect a mdb file from Microsoft Access, to a php page.

After installing 

php5-odbc
libmdbodbc
mdbtools
unixodbc-bin

And creating an entry in /etc/odbc.ini

```

Description = TestDatabase
Driver = /usr/lib/libmdbodbc.so.0
Database = /var/www/html/test/test.mdb

```

and creating the following page

[PHP]<?php

$conn = odbc_connect("TestDatabase", "", "");

$query = 'SELECT Achternaam, Voornaam, Geboortedatum From tblPersonen';
$result=odbc_do($conn, $query);

while($myrow=odbc_fetch_array($result)) {
echo  $myrow['Achternaam']
echo  $myrow['Voornaam']
echo  $myrow['Geboortedatum']
?>
[/PHP]

That works just fine.

But if I'm trying to modify my SQL string, to use aliasses, It doesn't work.

I would write it like this:

```
$query = 'SELECT Achternaam, Voornaam, Geboortedatum as Leeftijd From tblPersonen';

```

or

```
$query = 'SELECT Achternaam, Voornaam, Geboortedatum LeeftijdFrom tblPersonen';

```

But that doesn't seem to work.

The error message I get is:

odbc_fetch_array() [function.odbc-fetch-array]: No tuples available at this result index in /var/www/html/test/test.php on line 8

Any suggestions how I can sort this out. I need this alias to sort people on their birthday, so I require day and month extracted to sort this. All suggestions welcome!

Best regards

---

### Post by popch on 2008-01-26
One: You should check any error codes after executing the select statement. You told us the error message after executing fetchrow, which is not the same.

Two: Using an alias (or indeed that SELECT statement) does not extract part of a date. It should return exactly the same result set, but the last column would not be named Geboortedatum but Leeftijd. 

I am speculating, but could it possibly be that Leeftijd is the name of a function supplied by access and thus forbidden to be used as a field name?

---

### Post by stefanborremans on 2008-01-26
> **popch said:**
> One: You should check any error codes after executing the select statement. You told us the error message after executing fetchrow, which is not the same.

Two: Using an alias (or indeed that SELECT statement) does not extract part of a date. It should return exactly the same result set, but the last column would not be named Geboortedatum but Leeftijd. 

I am speculating, but could it possibly be that Leeftijd is the name of a function supplied by access and thus forbidden to be used as a field name?

Thank you for the quick reply popch,

Related to your frist statement, what is the best way to troubleshoot this code and getting the right error code from fetchrow? The error code above is the only one I received so far.

Your second statement, I know Leeftijd (which means age) does not extract a date. I just cut the part out which extracts this in Access, because it looks quite complicated. The SQL statement I'm trying to recreate is:

```
$query = "SELECT Achternaam, Voornaam, Geboortedatum, (year(now())-year(STR_TO_DATE(Geboortedatum, '%d/%m/%Y'))) as Leeftijd, Month(STR_TO_DATE(Geboortedatum, '%d/%m/%Y')) as Maand, Day(STR_TO_DATE(Geboortedatum, '%d/%m/%Y')) AS Dag From tblPersonen where Geboortedatum <> '' ORDER BY Maand, Dag";
```

An example row wold look like this

Achternaam (Last Name)            Jacobs
Voornaam (First Name)              John
Geboortedatum(Date of birth)     23/5/1980
Leeftijd (age)                             27
Maand (month of birth)               5
Dag (day of birth)                       23

PS: In Europe we use dd/mm/yyyy format, and not mm/dd/yyyy, just in case it might confuse :)

---

### Post by popch on 2008-01-26
I have used Access and SQL, and I have read some texts on PHP but never used it, so I can not be very precise in what follows.

Your program contains three functions which interact with the database: connecting, executing SQL statement (the SELECT) and bringing a tuple (or table row) into the program.

Every time you perform a database related function, you should check what it returned as first thing. If the value returned by the function indicates that there was a problem, you should use another PHP function which fetches error codes or messages or such which should help you find the cause.

I feel that this is the moment to tell you to do some reading about the PHP ODBC functions, especially the bits about the handling of errors and results.

---

