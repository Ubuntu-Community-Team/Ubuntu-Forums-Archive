---
title: "Firebird SQL Embedded under mono"
date: 2008-07-07
forum: Programming Talk
---

### Post by Deicist on 2008-07-07
So, I have an application originally developed under Visual Studio / .Net 2.0 on windows that I'm now trying to move over to mono.  My first major problem is that the database I use (Firebird embedded) returns an error whenever I try to create or connect to a database.  This is the error returned:

> 
An exception was thrown by the type initializer for FirebirdSql.Common.Charset in create database



The only solution returned by my Google searches seems to be compiling the .Net data provider for firebird in MonoDevelop rather than visual studio, which I have done.  Still no joy.

Can anyone help?

---

### Post by mariuz on 2008-07-09
> **Deicist said:**
> So, I have an application originally developed under Visual Studio / .Net 2.0 on windows that I'm now trying to move over to mono.  My first major problem is that the database I use (Firebird embedded) returns an error whenever I try to create or connect to a database.  This is the error returned:




The only solution returned by my Google searches seems to be compiling the .Net data provider for firebird in MonoDevelop rather than visual studio, which I have done.  Still no joy.

Can anyone help?

From the first look seems that firebird embeeded is not configured or something might be wrong with the .net driver 

How did you setup the embedded on ubuntu ? and what kit did you used
I will try to write an howto for the embedded and ubuntu 
Also does the application work with the full server install ?
[https://help.ubuntu.com/community/Firebird2.0](https://help.ubuntu.com/community/Firebird2.0)

---

### Post by Deicist on 2008-07-12
I gave up trying to get it working and went for a SQLite backend instead.

Cheers for the response though :)

---

### Post by spector00 on 2008-10-31
So sqLite is capable of running in mono? You made a .net win.forms based program with sqLite and it ran on mono? How?
I have been tring with sql server compact, and vistaDB well no good. I to was about to give up but if sqLite runs great!! i can continue on my work.

---

### Post by mariuz on 2008-11-21
> **Deicist said:**
> I gave up trying to get it working and went for a SQLite backend instead.

Cheers for the response though :)

I solved the issue using the 2.5 provider for firebird, it was in the driver the issue with the charst
[http://mapopa.blogspot.com/2008/09/mono-firebird-example-updated-you-must.html](http://mapopa.blogspot.com/2008/09/mono-firebird-example-updated-you-must.html)

also the issue is fixed in subversion tree for 1.7 (provider included by default in mono)

---

### Post by directhex on 2008-11-21
> **spector00 said:**
> So sqLite is capable of running in mono? You made a .net win.forms based program with sqLite and it ran on mono? How?
I have been tring with sql server compact, and vistaDB well no good. I to was about to give up but if sqLite runs great!! i can continue on my work.

Ubuntu has packages for writing/running CLI apps which can connect to SQLite, FirebirdSQL, PostreSQL, Oracle, MSSQL, and a few more besides.

libmono-sqlite2.0-cil
libmono-firebirdsql1.7-cil
libmono-npgsql2.0-cil
libmono-oracle2.0-cil
libmono-data-tds2.0-cil
libdb4o6.0-cil
libmono-db2-1.0-cil
libmono2.0-cil

---

