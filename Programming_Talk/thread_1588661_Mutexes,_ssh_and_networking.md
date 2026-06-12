---
title: "Mutexes, ssh and networking"
date: 2010-10-05
forum: Programming Talk
---

### Post by Geek10 on 2010-10-05
Hi all,

I am currently ssh'ing into another computer and want to have two programs running on different computers accessing the same piece of memory on the computer I am ssh'ing to. So I have been writing a program about mutexes, and it's taking a while because it's the first one I have ever written with mutexes, and I would like to know - will I be able to use mutexes across the network by different computers?

Thanks,

---

### Post by MadCow108 on 2010-10-05
generic answer to this generic question:
yes when the the mutex you're using supports this kind of operation.

please describe more detailed what you want to do and which tools you are using.
Are you using a communication framework like MPI? (and no MPI does not have networked mutexes)
How do you expose the memory on the machine to the others?

maybe a simple lockfile on the shared machine is enough for your purpose.

---

