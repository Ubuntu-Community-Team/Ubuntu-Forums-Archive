---
title: "Upgrading a server version, will there be a down time for my site?"
date: 2019-06-08
forum: New to Ubuntu
---

### Post by likewise2 on 2019-06-08
I am new to Linux. So, pardon me if its too basic question.

Say, if I have to upgrade the Ubuntu version from 'x' to 'x+1', then will there be a downtime for my site?

My site runs on LAMP stack.

---

### Post by TheFu on 2019-06-08
Every time there is a kernel update, a reboot should be performed, unless you are paying to have hot-patched kernel patching.
If you need HA, then a single server is not sufficient. You should engage a professional to help architect the best HA solution for your specific needs.

Or live with the 30 sec - 2 min downtime that is a reboot and pray that nothing in the upgrade failed.

Also, x --> x+1 is vague.  What, exactly, do you mean by that?

I patch weekly, on Saturday mornings, early.  I had to reboot about 15 systems this morning because there were kernel updates.  Because the systems are interdependent and the VM host system also got a new kernel, the downtime was a little longer.  I have 4 hrs a week approved for downtime/system maintenance.  Generally, I need less than 10 seconds.  About once a month, I need 5 minutes.  For OS upgrades ... like 16.04.5 --> 16.04.6, I needed 5 minutes.  For 14.04.5 --> 16.04.6 migrations, I needed longer, but took steps to minimize impacts so it was just a few minutes.  That's one of the reasons I have multiple virtual machine hosts and have gateway systems which are really simple, but hide when the main servers are down for a few hours, easily.

I always test major OS upgrades before touching any production systems.  If the test goes well, fine.  If the test doesn't go well, then I keep testing until I get it correct or come up with an alternate plan.

Of course, every server is a little different. There are no guarantees.  Just be certain that you have 100% know-you-can-restore backups before doing any OS modification. That includes weekly patching.  Test the restore so you know how long that will require too.

---

