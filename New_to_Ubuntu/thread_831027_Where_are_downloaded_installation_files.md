---
title: "Where are downloaded installation files??"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by talisfang on 2008-06-16
Where can i find the files that ubuntu downloaded from repos??

---

### Post by rpw on 2008-06-16
In /var/cache/apt/archives/

---

### Post by rraj.be on 2008-06-16
I think you are trying to make a backup of all downloaded installation files as you did in windows.

You can make a local repositories of that so you can install every thing from that cd/DVD without any need of internet connection.

Just an easy application called apton cd will help you.

to install that type this in terminal

```
sudo apt-get install aptoncd

```

After creating this you can easily install each applications that you have already downloaded just by inserting the cd and opening synaptic.
there is no need to download already downloaded application's.


This will reduce your download charges.

---

### Post by ibuclaw on 2008-06-16
All packages are stored in:
**/var/cache/apt/archives/**

Unless you regularly run the command
```
sudo apt-get clean
```
or have synaptic set to delete packages on the odd occasion. Then that folder should be pretty much empty.

Regards
Iain

---

