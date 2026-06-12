---
title: "MySQL"
date: 2009-03-28
forum: Programming Talk
---

### Post by miken79 on 2009-03-28
I recently switched from XP to a Ubuntu Desktop. I have a web app in PHP and MySQL that I used on the XP machine. Now when I try to execute it on my Ubuntu desktop I get the no database selected error message. My code is set up that when it creates a connection to the mysql engine, it selects the database to be used by executing "Use <DatabaseName>" but for some reason it is not working. Anytime I run a query on the same connection, it still expects the database to be selected. On my XP machine, it worked fine. Any idea why this would work for XP and not ubuntu?

Thanks,

---

### Post by HotCupOfJava on 2009-03-28
I'm gonna ask a stupid question, but the database IS installed and working on the Ubuntu machine, right?

---

### Post by cerealtx on 2009-03-28
> **HotCupOfJava said:**
> I'm gonna ask a stupid question, but the database IS installed and working on the Ubuntu machine, right?

im assuming also u have the same versions of php and mysql installed, and the database is remote right?

---

### Post by Can+~ on 2009-03-29
> **cerealtx said:**
> im assuming also u have the same versions of php and mysql installed, and the database is remote right?

And also ask if the user you're login in as has been GRANTed access to said database (or schema) @127.0.0.1 @localhost and @<desktop_name>

---

### Post by miken79 on 2009-03-29
> **HotCupOfJava said:**
> I'm gonna ask a stupid question, but the database IS installed and working on the Ubuntu machine, right?

Yes, MySQL is installed and working fine. I can log into it through the terminal and access all my data without any issues.

---

### Post by miken79 on 2009-03-29
> **cerealtx said:**
> im assuming also u have the same versions of php and mysql installed, and the database is remote right?

Yes, I am running php5 and MySQL Server 5. The database is on the machine running locally.

---

### Post by miken79 on 2009-03-29
> **Can+~ said:**
> And also ask if the user you're login in as has been GRANTed access to said database (or schema) @127.0.0.1 @localhost and @<desktop_name>

Yes, the user I am using to log in with has read and write access to the database schema I am try to access.

---

### Post by Tomosaur on 2009-03-29
Sounds like an annoying problem! It would probably be easier to isolate the problem if you posted some code. Did you actually change any of the code when you moved to Ubuntu?

---

### Post by The Cog on 2009-03-30
Can you log in and connect to the database by hand using the mysql console?
Are you using the correct case in the database name? Unlike on Windows, MySQL on Linux is case sensitive about database names.

---

