---
title: "Problem installing Limewire"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by parkinrg on 2008-06-05
I have just tried to install Limwire , on the first attempt the package manager locked up . The only way I could get rid of it was to restart Ubuntu. Now when I try to install it the package managers says that there is another software management package running, but there definitley is not!
Any ideas ?  
Is there an equivalent of windows "control,alt,delete"

---

### Post by neurostu on 2008-06-05
run:
```

sudo dpkg --configure -a

```

---

### Post by kamitsukai on 2008-06-05
why limewire? why not frostwire?

---

### Post by neurostu on 2008-06-05
It says that the package manager is running but it isn't. 

The package managers create a "Lock" or a file that says "Hey I'm running" and then it deletes the file when it closes. This prevents another package manager from running at the same time.


The command I wrote above will delete the lock and allow you to run another package manager.

---

### Post by neurostu on 2008-06-05
> **parkinrg said:**
> 
Is there an equivalent of windows "control,alt,delete"

Yes, open a terminal and type: 
```

ps -A

```
that will list ALL running processes.
if you want to search for a specific process use grep to search for it:

```

ps -A | grep firefox

```
then you can kill a process with killall or kill, but again this won't help as you don't have a package manager running.

---

### Post by parkinrg on 2008-06-05
Thanks Neurostu , that worked perfectly

---

### Post by neurostu on 2008-06-05
For the record, You can publically thank people by clicking the little gold star on the bottom right of a post.

---

### Post by daberger on 2008-06-05
parkinrg, as i was told when i asked pretty much the same questions, this forum is not for any filesharing(which is considered illegal, even though most filesharing is clean)

but im not an administrator so im not goin to tell u not to go head =)

and ironically xubuntu comes with a torrenter

---

### Post by daberger on 2008-06-05
my bad, accidentally dual posted

---

### Post by lisati on 2008-06-05
> **kamitsukai said:**
> why limewire? why not frostwire?

Why not? As near as I can make out, they are both derivatives of the same package. At least the Windows versions I've used are.

And watch out for "Windows nasties" in the search results.....

---

