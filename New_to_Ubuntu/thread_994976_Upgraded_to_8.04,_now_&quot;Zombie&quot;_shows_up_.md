---
title: "Upgraded to 8.04, now &quot;Zombie&quot; shows up in System Monitor -- what does it mean?"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by socref on 2008-11-27
Hello, everyone. I just upgraded from Ubuntu 7.10 to 8.04 LTS using the Update Manager feature.

While looking at the System Monitor I notice that I have two instances of "sh" showing in the Process Name column. 

The first shows "Zombie" in the Status column, "0" in the % CPU column, "0" in the Nice column, "6728" in the ID column, and "N/A" in the Memory column.

The second instance shows "Sleeping" in the Status column, "0" in the % CPU column, "0" in the Nice column, "6661" in the ID column, and "64.0KiB" in the Memory column.

Do I have a problem here? To begin with I don't know what "sh" is, and when I see the word "Zombie" I really start worrying.

I searched the term "Zombie" in the help feature of System Monitor but was unsuccessful finding anything useful. I also searched "Zombie" in this Ubuntu forum but did not find a thread that was on this issue (Did I miss one?).

Do I have an issue here? What is "Zombie?"

Thanks!
socref

---

### Post by Peter09 on 2008-11-27
Nothing to worry about. A Zombie is normally the remains of an applications that failed to shutdown properly.

---

### Post by x1a4 on 2008-11-27
Hi, 

A zombie process is a process that has completed execution but still has an entry in the process table. It's nothing to worry about. 

"0" in the % CPU column means it's using 0% of CPU

"0" in the Nice column - This is the amount of system time spent on programs whose priorities have been altered with the Nice command&#8212;Nice time is in addition to system time, so when you have nice time, the percentages may exceed 100 percent

"6728" in the ID column - That's the process ID

"N/A" in the Memory column - not applicable; it's not in memory so it's not even using 0 bytes.

For more info see [the Wikipedia entry on zombie processes]("http://en.wikipedia.org/wiki/Zombie_process")

A sleeping process is a process that's in memory but not doing anything at the moment.  

/bin/sh is a symlink to /bin/dash (Debian Almquist shell).  It is the default command processor used to execute scripts.  Install scripts like those inside packages you installed when you upgraded are run using dash by way of /bin/sh.

---

### Post by Kareeser on 2008-11-27
Careful. Don't let them touch you, lest you also become a zombie.

Better come up with a zombie plan ;)

---

### Post by socref on 2008-11-27
Many thanks for quick reply. 
socref

---

### Post by NewJack on 2008-11-27
If you are really worried:

[http://www.amazon.com/Zombie-Survival-Guide-Complete-Protection/dp/1400049628/ref=pd_bbs_sr_1?ie=UTF8&s=books&qid=1227805488&sr=8-1](http://www.amazon.com/Zombie-Survival-Guide-Complete-Protection/dp/1400049628/ref=pd_bbs_sr_1?ie=UTF8&s=books&qid=1227805488&sr=8-1)

---

