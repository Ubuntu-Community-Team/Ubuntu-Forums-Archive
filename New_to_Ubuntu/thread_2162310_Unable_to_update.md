---
title: "Unable to update"
date: 2013-07-14
forum: New to Ubuntu
---

### Post by Crossbow on 2013-07-14
I don't understand what's going on here. 

```

anna@anna-desktop:~$ sudo apt-get update
[sudo] password for anna: 
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

---

### Post by claracc on 2013-07-14
Do you have any other update software running at the same time you run the 
```
sudo apt-get update
``` command?

Synaptic manager can be opened ( so close it)
software center can be opened (so close it)
And try again to do the update

---

### Post by bmullan on 2013-07-14
> **Crossbow said:**
> I don't understand what's going on here. 

```

anna@anna-desktop:~$ sudo apt-get update
[sudo] password for anna: 
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

As Claracc says:
[LIST=1]
[*]Synaptic manager can be opened ( so close it)
[*]software center can be opened (so close it)
[/LIST]


BUT... it is possible that the "lock" file has been left on the system if NEITHER of the above are true.

In that case you can delete the "lock" file to remove it:
$ sudo rm /var/lib/apt/lists/lock

But don't do that until you've verified that synaptic or the software center are not running.

Once the lock file is gone you will be able to update again.

---

### Post by newb85 on 2013-07-14
In addition to the Software Center and Synaptic Package Manager, the Software Updater/Update Manager (depending on your release) could also be the reason for the lock.  Make sure it isn't open.

---

