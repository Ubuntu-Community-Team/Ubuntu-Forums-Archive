---
title: "Mono, MySQL and ODBC questions"
date: 2006-06-19
forum: Programming Talk
---

### Post by Mickeysofine1972 on 2006-06-19
Hi

I've been trying to connect to an existing database using c#/mono that I have accessed previously through PHP script. 

when I run the script it says:
Description: Error processing request.

Error Message: HTTP 500.

Stack Trace:

System.Data.Odbc.OdbcException: [unixODBC][Driver Manager]Data source name not found, and no default driver specified
in <0x00547> System.Data.Odbc.OdbcConnection:Open ()

HELP!

Mike

---

### Post by LordHunter317 on 2006-06-19
It's because you don't have an ODBC DSN setup for that data source.

But why the hell are you using ODBC in the first place?  Use the MySQL ADO.NET driver unless you have a specific reason to use ODBC.

---

### Post by Mickeysofine1972 on 2006-06-19
[QUOTE=LordHunter317]It's because you don't have an ODBC DSN setup for that data source.

But why the hell are you using ODBC in the first place?  Use the MySQL ADO.NET driver unless you have a specific reason to use ODBC.[/QUOTE]

I forgot to mention that I have just started to get into .NET after a pause of about a year and I didn't know/remember that you can use that namespace :lol:

Just for the record... how might one code that again? :) 

Mike

---

