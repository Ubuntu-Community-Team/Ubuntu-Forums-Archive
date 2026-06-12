---
title: "how to Detect Running Firefox through shell script?"
date: 2008-01-28
forum: Programming Talk
---

### Post by me_himanshu on 2008-01-28
Hi,
I want to Detect Through Shell Script that whether firefox browser is running or not? How can i do this?

Thanks in advance
Himanshu

---

### Post by ghostdog74 on 2008-01-28
check for its process
```

ps -ef |grep firefox

```
or 
```

pgrep firefox

```

---

### Post by SunnyDaze on 2008-01-28
To see all the processes running, just type this in:

**ps -A**

Then you scroll through the list and look for firefox.

Sometimes when you run a program it will start more than one process related to that program.

To stop all the processes related to a program you type **killall** like this (let's use firefox for an example:

**killall firefox**

If you are getting an error message saying firefox is already running, then you either need to delete the .parentlock file in the profile directory, or you no longer have write permission to the profile directory.

---

