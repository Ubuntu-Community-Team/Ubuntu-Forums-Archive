---
title: "[SOLVED] how can i delete my account in evolution?"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by markip on 2008-08-15
i tried to put my yahoo account to evolution but it seems that i put the neccessary information wrong, because i can't send any emails. So how can i delete my present account and create another one? In addition, is there a ''how to'' that can help me install my yahoo account in evolution correctly?
Please answer back soon.

---

### Post by limasierra on 2008-08-15
Open evolution and go to Edit > Preferences. Then in "Mail Accounts" select the account that you want to delete, click the delete button and confirm if you want to delete.

---

### Post by markip on 2008-08-15
thank's i am wondering if someone in the forum knows how can i add a yahoo or an msn account on evolution

---

### Post by peruvianfreak250 on 2008-08-15
do you have the free version of yahoo mail? that version wont work with evolution as it doesn't have pop3. you either need to upgrade your account or get 
[ypops!]("http://www.ypopsemail.com/")

which im trying to do right now :D

---

### Post by t0p on 2008-08-15
There's a command-line utility called **fetchyahoo** which resembles fetchmail and which enabled one to get one's yahoo mail.  Fetchyahoo is in the repos.

Unfortunately, the last time I tried fetchyahoo, it had been broken by yahoo changing their interface.  It might be working again now - I don't know cos I haven't checked.  But I will, now I've been reminded about it.  You could check too - like I said, it's in the repos.

**EDIT:** The version in the repos (2.11.2 I think) does not work. According to [the developer's webpage]("http://fetchyahoo.twizzler.org") the alpha releases (fetchyahoo 2.12) do work with the new interface.  But they are alpha releases, they have bugs, so probably are not for the faint-hearted.

---

### Post by markip on 2008-08-23
thank's for the info!!!!

---

### Post by jzaragoza on 2008-09-04
My Yahoo mail works perfectly with Evolution. Pop server pop.correo.yahoo.es (es means Spain, correo means mail), with SSL, port 995, and smtp server smtp.correo.yahoo.es, with SSL, port 465, use authentication. The same as with the old Outlook Express.

---

