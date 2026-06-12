---
title: "Dynamic MMap ran out of room (an error when update)"
date: 2012-08-10
forum: New to Ubuntu
---

### Post by gsmser on 2012-08-10
when I update my Ubuntu system with update manager, I encounter 
an error, and now the update manager is stuck. The error message 
is as following:

An unresolvable problem occurred while initializing the package 
information.

Please report this bug against the 'update-manager' package and include the following error message:

'E: Dynamic MMap ran out of room. Please increase the size of 
APT::Cache-Limit. Current value: 25165824. (man 5 apt.conf),
E: Error occurred while processing moonlight-tools (NewVersion1),
 E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_lucid-
proposed_universe_binary-i386_Packages, E:The package lists or 
status file could not be parsed or opened.'


I google the way how to increase the cache-limit, and input this code
```
APT::Cache-Limit "100000000"
```
into ```
/etc/apt/apt.conf.d/70debconf
```, 
but this solution doesn't work. The problem can not be fixed.

What should I do to fix this problem?

Thanks every much for your help.

---

### Post by Bashing-om on 2012-08-11
gsmser;
  This one is beyond my experience level ,,, but ....
do this and advise of the results
```

sudo apt-get update
```
```

sudo apt-get autoremove
```
```
   
sudo apt-get upgrade  
```

hth BDQ

---

### Post by scvpaul on 2013-02-10
I'm a Linux newbie, but this worked for me (caveat emptor);  

1)  Edit /etc/apt/sources.list, commenting out some of the sources that may be outdated.  Working on 10.04 (due to old HW platform) I commented out us.archive.ubuntu and lenny references.  

2)  sudo apt-get autoclean

3)  sudo apt-get update

4)  sudo apt-get install <whatever you were trying to install>

This reduces the number of sources that the mmap must handle.  Your mileage may vary.

---

