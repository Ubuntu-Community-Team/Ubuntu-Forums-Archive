---
title: "what does this mean?"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by childofGod on 2008-06-15
I am having trouble with update manager, synaptic and add/remove applications not running after they open and begin building a dependency tree.  I attempted to use them on the command line and got the following messsage, "E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?"  What does this mean?  What can I do to regain use of these programs?

---

### Post by aysiu on 2008-06-15
It means you're trying to open more than one of the package management processes at once.

Only one can run at a time.

---

### Post by childofGod on 2008-06-15
Thanks Aysiu.  I will definitely watch out for those malicious commands.  On the issue I am having trouble with, however, I don't understand why the OS thinks I am already trying to update.  I have gone so far as to restart my computer several times.  There are no update windows open.  I don't know why my computer responds as if there were.  What can I try?

---

### Post by spiderbatdad on 2008-06-15
```
sudo apt-get install -f
```

---

### Post by perce on 2008-06-15
To see if there is some package manager secretly running on your computer, open System > Administration > System monitor and look at the processes.

---

### Post by tamoneya on 2008-06-15
some process that used synaptic was interupted resulting in the lock file not being removed.  Check this by running:```
ls /var/lib/dpkg/
```Post the output here.

---

### Post by mdpalow on 2008-06-15
> **childofGod said:**
> Thanks Aysiu.  I will definitely watch out for those malicious commands.  On the issue I am having trouble with, however, I don't understand why the OS thinks I am already trying to update.  I have gone so far as to restart my computer several times.  There are no update windows open.  I don't know why my computer responds as if there were.  What can I try?

I think you misunderstood the 'malicious commands' part. That's his signature - not something he was saying specifically to you. It will always appear when he posts something. :)

good luck

---

### Post by childofGod on 2008-06-15
Here's what I get

> **tamoneya said:**
> some process that used synaptic was interupted resulting in the lock file not being removed.  Check this by running:```
ls /var/lib/dpkg/
```Post the output here.
alternatives   cmethopt        info   statoverride      status-old
available      diversions      lock   statoverride-old  triggers
available-old  diversions-old  parts  status            updates

---

### Post by childofGod on 2008-06-15
alternatives, info, parts, triggers and updates are in blue type.  I don't know what that means but I'm sure the color is significant.

---

### Post by perce on 2008-06-15
It means that they I directories, I think

---

### Post by tamoneya on 2008-06-15
well if you confirmed that there are not processes using it by checking with system manager just remove the lock file.
```
sudo rm /var/lib/dpkg/lock
```

---

### Post by childofGod on 2008-06-15
Thanks Tamoneya. That command did the trick.  I just had to restart the machine after running it.

---

### Post by cariboo on 2008-06-15
In your listing you can see **lock** that is why you are getting the message about another update application is running. to remove it in a terminal type the following:

```
sudo rm /var/lib/dpkg/lock
```

After you remove the lock file everything should be OK.

Oops seems some one beat me to it.

Jim

---

