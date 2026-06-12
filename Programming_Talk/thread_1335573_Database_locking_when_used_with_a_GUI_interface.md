---
title: "Database locking when used with a GUI interface"
date: 2009-11-23
forum: Programming Talk
---

### Post by bluedalmatian on 2009-11-23
Imagine the following situation:

A remote central database server such as MySQL or PostgreSQL and multiple client apps accessing it simultaneously. The clients are GUI based such as a Java or Gnome app.

The system is object based and one of the classes involved is called Person. Each row in the DB is an object instance.

One of the GUI clients brings up a Person's details on screen for editing - the row in the DB is locked but the user then leaves their desk for 5 mins holding up all other access. Imagine it was a bank customer, and no transactions could take place involving the account until the clerk had finished editing their details

Id be interested to see what the concensus here is on the best solution.

---

### Post by Can+~ on 2009-11-23
The gui should not be locking the database/table in the first place. The gui should establish what is the procedure to be done on the database (either direct sql command or interface), and only execute it once the user agrees (submit).

If you absolutely must hold the database/table for a particular client, you can establish a maximum time of inactivity, in which the client loses connection.

---

### Post by bluedalmatian on 2009-11-24
i dont quite follow....if the gui doesnt lock the row in the DB then theres a risk of inconsistency between what it writes back

imagine  gui A reads users phone no as 123 from DB and displays it in gui but doesnt hold the row locked.  another user (gui B) alters phone no to 345 and commits.  gui A writes changes back and sets it back to 123.

or are you saying the gui code should be smart enough to detect that phone number field hasnt been edited by gui and therefore omit it.

currently the orm framework im working with writes the entire objects state back to the DB including those fields which havent been altered.

---

### Post by Can+~ on 2009-11-24
Ok, now I understood you, I think I got a bit off-topic before.

You can either:

[LIST=1]
[*]Keep the row unlocked (normal read/writing concurrency problems are already covered by databases). Always make sure that the submitted information matches the last modification timestamp/counter (SVN does it with a counter (revision number)). This can be expensive if there's a high volatility rate. Maybe add a trigger, or the specific database provides a tool for this. (MSSQL has "[rowversion]("http://msdn.microsoft.com/en-us/library/ms182776.aspx")")
[*]Have the row locked while the GUI is working (like you're doing now), but add a timeout that will close the connection and unlock the row if the user becomes idle (1 minute?). This could lead to starvation though, if a user gets kicked, another one is chosen, and they keep doing this one after another.
[/LIST]

I think I would chose #1. It may be more expensive, but you would be saving from having to write multiple things that haven't changed, just by checking the revision number, maybe have a separate table with the revision numbers so you can keep it in main memory.

---

