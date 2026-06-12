---
title: "may be even now i can get a solution  &quot;Resource temporarily unavailable)&quot;"
date: 2011-10-09
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by raja.genupula on 2011-10-09
```
assassin@raju-xubuntu:~$ sudo apt-get install phpmyadmin
[sudo] password for assassin: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
assassin@raju-xubuntu:~$ 

```

I was  interrupted installation process because i had lost my connection.After getting connection again i had tried but its not working and showing like that.I know one solution that restarting my system but i want any better alternative to this.

Thanks in advance.
using xubuntu 11.10.

---

### Post by ronacc on 2011-10-09
looks like dpkg thinks there is already a process running and is waiting for it to finish , try renaming /var/lib/dpkg/lock to something else .

---

### Post by raja.genupula on 2011-10-09
could you please give me step by step process.

---

### Post by tista on 2011-10-09
Hi guys,

Maybe jockey process keeps apt lock?

cheers,
Tista

---

### Post by raja.genupula on 2011-10-09
> **tista said:**
> Hi guys,

Maybe jockey process keeps apt lock?

cheers,
Tista

Hi man , sorry

Jocky process ? I didnt get it.

---

### Post by tista on 2011-10-09
> **raja.genupula said:**
> Hi man , sorry

Jocky process ? I didnt get it.

I mean "jockey-gtk". it sometimes crashes in background and it dies with holding apt lock... if you check the output of "ps aux" and/or "top" out, jockey appeared, kill it. but maybe needs root access.

So "sudo su" and "killall jockey-gtk".

Or something else might lock apt?

cheers.

---

### Post by effenberg0x0 on 2011-10-09
Sometimes I don't even see that update-manager windows is open, behind lots of other windows, telling me to install updates. 

This will kill anything that may be using the lock:

```

sudo fuser -k -KILL /var/lib/dpkg/lock
sudo rm -rf /var/lib/dpkg/lock
sudo apt-get update
sudo apt-get install phpmyadmin

```

Regards,
Effenberg

---

### Post by matt_symes on 2011-10-09
Hi

You should be able to see what is locking it by opening a terminal and typing

```
sudo lsof /var/lib/dpkg/lock
```

Kind regards

---

### Post by raja.genupula on 2011-10-09
My issue got solved.after waiting some time again i have tried to install at that time terminal suggest me to do sudo dpkg --configure -a  and i did that.and then i got installed.

I do remember your suggestions, In future if i got this problem then i will use this.

Thanks to matt_symes,effenberg0x0,tista,ronacc for helping me on this issue.

---

