---
title: "Make one user a subordinate of another"
date: 2011-09-15
forum: New to Ubuntu
---

### Post by pteri498 on 2011-09-15
I have an interesting setup where one person has two user accounts. I want his main account to be able to change the password of and otherwise administer his subordinate account, without root access.

Is there a way to do this?

---

### Post by Daveth on 2011-09-15
to what end, may I inquire?

---

### Post by grahammechanical on 2011-09-15
Is this with Ubuntu?

Surely you do it through Users and Groups. The main account has administrator privileges. When you log into the main account, set up a second user but set him as a desktop user and not administrator. There should be a page in Users and Groups (called Advance settings?) that lets you limit still further what the desktop user can do

If you do not mark the network connections (wired and wireless) as Available To All Users, then the second account will not have Internet access.

If you already know about this, then you need to explain in more detail what you want to achieve.

Regards.

---

### Post by Wim Sturkenboom on 2011-09-15
It seems quite clear what OP wants to achieve. Have a user that can change the password of one (and only one) other user without using root powers.

Answer
The system user A can su (see man su) to the system user B and change the password.

---

