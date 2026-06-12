---
title: "SQL syntax problem"
date: 2009-12-20
forum: Programming Talk
---

### Post by matmatmat on 2009-12-20
I am trying to create a database with a .sql script:
```

drop database if exists cms;
create database cms;

use cms;

create table users( 
	id		int not null primary key auto_increment,
	username	varchar(16) not null,
	passwrd		varchar(30) not null,
	fullname	text
)

create table blogEntries(
	id 		int not null primary key auto_increment,
	writer		varchar(16) not null,
	headline	text,
	content		text,
	created		int,
	modified	int,
	published	int
)

create table tags(
	entry		int not null,
	tag		varchar(16) not null,
	weight		int not null
)

create table pages(
	id 		int not null primary key auto_increment,
	title		text
	content		text
	created		int
	modified	int
	published	int
)

grant select, insert, update, delete
on cms.*
to cms@localhost identified by '###';

```
but when run it says:
```

[matio@myhost cms]$ sudo mysql -u root < create_cms_database.sql
ERROR 1064 (42000) at line 6: You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'create table blogEntries(
        id              int not null primary key auto_increment,
        writer' at line 8

```
I don't know what the problem is -- most of the .sql file is copied from a book.

---

### Post by Arndt on 2009-12-20
> **matmatmat said:**
> I am trying to create a database with a .sql script:
```

drop database if exists cms;
create database cms;

use cms;

create table users( 
	id		int not null primary key auto_increment,
	username	varchar(16) not null,
	passwrd		varchar(30) not null,
	fullname	text
)

create table blogEntries(
	id 		int not null primary key auto_increment,
	writer		varchar(16) not null,
	headline	text,
	content		text,
	created		int,
	modified	int,
	published	int
)

create table tags(
	entry		int not null,
	tag		varchar(16) not null,
	weight		int not null
)

create table pages(
	id 		int not null primary key auto_increment,
	title		text
	content		text
	created		int
	modified	int
	published	int
)

grant select, insert, update, delete
on cms.*
to cms@localhost identified by '###';

```
but when run it says:
```

[matio@myhost cms]$ sudo mysql -u root < create_cms_database.sql
ERROR 1064 (42000) at line 6: You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'create table blogEntries(
        id              int not null primary key auto_increment,
        writer' at line 8

```
I don't know what the problem is -- most of the .sql file is copied from a book.

I don't know offhand what the problem is either, but I wonder why the script you show and the line numbers in the error message don't fit. The blogEntries table starts much later than line 8.

---

### Post by akoskm on 2009-12-20
1. Close the create table blocks with semicolon:
```

create table users( 
	id		int not null primary key auto_increment,
	username	varchar(16) not null,
	passwrd		varchar(30) not null,
	fullname	text
);

```, do this for all create table.
2. Separate the declarations with comma:
```

	title		text,
	content		text,
	created		int,
	modified	int,
	published	int,

```.
So finally your create_cms_database.sql looks like:
```

drop database if exists cms;
create database cms;

use cms;

create table users( 
	id		int not null primary key auto_increment,
	username	varchar(16) not null,
	passwrd		varchar(30) not null,
	fullname	text
);

create table blogEntries(
	id 		int not null primary key auto_increment,
	writer		varchar(16) not null,
	headline	text,
	content		text,
	created		int,
	modified	int,
	published	int
);

create table tags(
	entry		int not null,
	tag		varchar(16) not null,
	weight		int not null
);

create table pages(
	id 		int not null primary key auto_increment,
	title		text,
	content		text,
	created		int,
	modified	int,
	published	int
);

grant select, insert, update, delete
on cms.*
to cms@localhost identified by '###';

```

---

### Post by John Bean on 2009-12-20
I suspect the error is that you haven't used commas to separate the items following the line reported by the error handler. The function create table pages(...) is spread over several lines for clarity but line breaks are ignored of course.

Look at the other functions and spot the difference ;-)

---

### Post by akoskm on 2009-12-20
> **Arndt said:**
> I don't know offhand what the problem is either, but I wonder why the script you show and the line numbers in the error message don't fit. The blogEntries table starts much later than line 8.

The blogEntries table block starts at the line 8. Those create table blocks are read in one row:
```

create table users(id int not null primary key auto_increment, 	usernamevarchar(16) not null, passwrd	varchar(30) not null,fullname text);

```.

---

### Post by matmatmat on 2009-12-20
> **akoskm said:**
> 1. Close the create table blocks with semicolon:
```

create table users( 
	id		int not null primary key auto_increment,
	username	varchar(16) not null,
	passwrd		varchar(30) not null,
	fullname	text
);

```, do this for all create table.
2. Separate the declarations with comma:
```

	title		text,
	content		text,
	created		int,
	modified	int,
	published	int,

```.
So finally your create_cms_database.sql looks like:
```

drop database if exists cms;
create database cms;

use cms;

create table users( 
	id		int not null primary key auto_increment,
	username	varchar(16) not null,
	passwrd		varchar(30) not null,
	fullname	text
);

create table blogEntries(
	id 		int not null primary key auto_increment,
	writer		varchar(16) not null,
	headline	text,
	content		text,
	created		int,
	modified	int,
	published	int
);

create table tags(
	entry		int not null,
	tag		varchar(16) not null,
	weight		int not null
);

create table pages(
	id 		int not null primary key auto_increment,
	title		text,
	content		text,
	created		int,
	modified	int,
	published	int
);

grant select, insert, update, delete
on cms.*
to cms@localhost identified by '###';

```

Thanks everyone -- the above worked

---

### Post by Arndt on 2009-12-20
> **akoskm said:**
> The blogEntries table block starts at the line 8. Those create table blocks are read in one row:
```

create table users(id int not null primary key auto_increment, 	usernamevarchar(16) not null, passwrd	varchar(30) not null,fullname text);

```.

Please explain. Do you and MySql mean a different thing with "line" than the usual?

---

### Post by The Cog on 2009-12-21
Are you just missing the semicolons at the end of each create table statement?

---

