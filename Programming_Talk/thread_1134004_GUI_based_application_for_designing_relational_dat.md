---
title: "GUI based application for designing relational database"
date: 2009-04-23
forum: Programming Talk
---

### Post by mohtasham1983 on 2009-04-23
Hi,

I'm trying to develop a relatively complex web based application which involves a lot of tables. 

Right now, I'm in the database design process and do everything on a piece of paper. As you can guess, making all your plans on a piece of paper can be very tedious and very hard to understand. I'm pretty sure, eventually everything is going to be dirty as hell.

That's why, I was wondering if there's any application which enables users to create their tables in a visual form, so that all relations can be easily understood. 

I don't really care about automatic code generation, but it would be great, if it creates the corresponding mysql code.

Thanks in advance.

---

### Post by kknd on 2009-04-23
Dia + tedia2sql!

---

### Post by mohtasham1983 on 2009-04-23
Thanks. I actually started making it using Dia. I don't really need the script to generate the sql for me anymore. I'm going to use Django to develop my web application. I have to define my database model using Python classes. Then Django will generate the database automatically.

---

### Post by waffen on 2010-04-17
> **kknd said:**
> Dia + tedia2sql!

I have problem creating relationships using the last dia 0.97 and the las tedia2sql founded both in repos.
You have the same?

Maybe this is the problem: [http://blog.gmane.org/gmane.comp.db.tedia2sql.general](http://blog.gmane.org/gmane.comp.db.tedia2sql.general)

but I dont know is that was fixed in the actual version?

any idea? thanks!
Mario

---

### Post by slavik on 2010-04-17
argouml is another one.

---

### Post by waffen on 2010-04-17
I dont remember if ArgoUML make sql create code for postgres but I can found this:

[http://search.cpan.org/dist/Parse-Dia-SQL/](http://search.cpan.org/dist/Parse-Dia-SQL/)

work perfect!! so the new tools: dia+parsediasql :P

with both I can create my db model and generated the tables and fk

Mario

---

### Post by raffen on 2010-09-28
**[libparse-dia-sql-perl]("https://launchpad.net/ubuntu/maverick/+package/libparse-dia-sql-perl")** will, as of Ubuntu 10.10 "Maverick Meerkat", be available as a .deb package using your favorite package manager.  This will simplify installation of Parse-Dia-SQL.

---

