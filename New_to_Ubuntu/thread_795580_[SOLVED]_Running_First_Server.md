---
title: "[SOLVED] Running First Server"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by SurrealWraith on 2008-05-15
Hello.  I am currently wanting to make a server similar to that used by police to look up information on drivers using the drivers license number.  Specifically, I would like to construct a server that would be accessible to staff members at my school so they could look up information on students using the student's school ID number or a bar-code on the ID card.  Information about a student would include his or her dean, counselor, schedule, and IEP (learning accommodations) if applicable.  Just being able to display such information is the basic need for my server, though I may come back for more help later.  So, what I need to know is whether this is possible to do using Ubuntu (as my school uses Windows), and how I would go about doing it.  Thank you in advanced for all your help.

---

### Post by christianxxx on 2008-05-15
I would go for a MySQL database containing all the data, and make a quick and dirty PHP to look up in the database and print a webpage with it.
Both MySQL and Apache with PHP is really easy to setup and if you don't allready know PHP, it's quite easy to learn.

It's just as easy to do on a Windows server... :)

---

### Post by SurrealWraith on 2008-05-15
> **christianxxx said:**
> 

It's just as easy to do on a Windows server... :)

Yes, but does it matter what OS I use to make the server?

---

### Post by Oldsoldier2003 on 2008-05-15
> **SurrealWraith said:**
> Yes, but does it matter what OS I use to make the server?

no. the work is done by PHP and mysql which are cross platform.

---

### Post by SurrealWraith on 2008-05-15
> **Oldsoldier2003 said:**
> no. the work is done by PHP and mysql which are cross platform.

Thank you.  That answers my biggest concern.  I'm going to go try out some of this.  I'll report back later.  In the mean time, feel free to post more suggestions!

---

