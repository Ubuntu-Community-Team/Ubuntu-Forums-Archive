---
title: "recovering mysql databases from old system"
date: 2008-02-19
forum: Programming Talk
---

### Post by pedrotuga on 2008-02-19
I red a few similar threads bu none seemed to address exactly this issue.

My laptop borke. As it was kind of old i went and bought a new one.
Now I am transfering whatever sensitive data I had through an external hard drive USB adapter.
It's going ok, until I got reminded that I need my mysql databases too.

What's the simplest way to recover them? User credentials are not important.
I guess just coping the raw database files should result in a lot of errors and permission issues.... right?

---

### Post by LaRoza on 2008-02-19
I have copied the files with no problems before. It is worth a try...

---

### Post by pedrotuga on 2008-02-19
surprisingly it actually worked.
I'll connect my application to it so i check if everything is ok with charsets, etc.

I'll come back to this thread if necessary.
Thank you.

---

### Post by pmasiar on 2008-02-19
Correct thing to do is DUMP tables and then load them, plain moving over binary fines might, or might not, work. MySQL has administration utilities for that.

---

### Post by pedrotuga on 2008-02-20
> **pmasiar said:**
> Correct thing to do is DUMP tables and then load them, plain moving over binary fines might, or might not, work. MySQL has administration utilities for that.

That's not valid in this case. Please rad the opening post carefully.

---

### Post by ebs16 on 2008-04-02
i had the same problem - i needed to recover my mysql database from a non-booting ubuntu installation.  copying the files from /var/lib/mysql seemed to do the trick, although i did lose my permissions.  not a big deal really, i only had about 3 database users set up.

---

### Post by barney_gul on 2008-04-28
Similar problem here.

Copied the tables/directories from a non-booting 7.10 partition to a new 8.04 partition.  Now, phpMyAdmin sees 0 tables in the databases, and a Wine-driven SQLYog gives errors, "Can't read dir of './articles/' (errno:13)".

When I examine the directory structure, everything seems to be there.  Do I need to modify the files in the MySQL directory, *e.g., *ib_logfile1, ibdata1 ib_logfile0?
(Did not copy those files over, just the database directories.)

---

### Post by hyper_ch on 2008-04-29
you should only copy them when mysql server isn't running... otherwise you might bork them.... best way still is to mysqldump them and readd them again.

---

### Post by barney_gul on 2008-04-29
> **hyper_ch said:**
> you should only copy them when mysql server isn't running... otherwise you might bork them.... best way still is to mysqldump them and readd them again.

I quite agree ... however, I'm unable to boot into the partition to make the dump.  I can read it from another partition, but cannot - or don't know how? - boot into it.  And I don't know of any way to use phpMyAdmin to access those files.

It seems that my original statement was erroneous.  The directories copied over, but not the files within them.  When I examine the files, they show ownership by polkit, but I've not been able to change the ownership/permissions from the current distro.

If it matters, the hosed partition is 7.10 (Gutsy) and the working partition is 8.04 (Hardy).

Would it be possible to boot the old partition strictly to command line, then modify the permissions?  I'm thinking yes, but I just don't have enough knowledge, as yet, to accomplish such a task.

---

