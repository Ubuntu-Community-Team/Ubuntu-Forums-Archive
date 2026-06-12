---
title: "How to multiboot ubuntu 11.10 with another linux ?"
date: 2012-01-29
forum: New to Ubuntu
---

### Post by kiranmatrixlee on 2012-01-29
I have installed centos on my /dev/sda9.
There is windows 7 on my first partition.
Now i try to install ubuntu on /dev/sad11
While installing,it shows the following error.



migration-assistant needs to mount a partition,but cannot do so because the following mount point could not be mounted:

/dev/sda9

please close any application using this mount points.

would you like migration-assistant to try to unmount these partition again?

---

### Post by wolfen69 on 2012-01-29
Have you tried it without using the migration assistant?

---

### Post by kiranmatrixlee on 2012-01-29
> **wolfen69 said:**
> Have you tried it without using the migration assistant?


i dont know about migration assistant.
How to disable migration assistant while installation?

---

### Post by wolfen69 on 2012-01-29
The migration assistant will transfer certain settings from one install to the next. I assumed you were trying to do that during install.

---

### Post by kiranmatrixlee on 2012-02-01
> **wolfen69 said:**
> The migration assistant will transfer certain settings from one install to the next. I assumed you were trying to do that during install.
now it ok by disable migration-assistant

"sudo ubiquity --no-migration-assistant"


Thank you very much.

---

