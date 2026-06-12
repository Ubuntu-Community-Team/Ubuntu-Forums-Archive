---
title: "[SOLVED] updating from the command line"
date: 2008-10-16
forum: New to Ubuntu
---

### Post by jdcnosse on 2008-10-16
Hi, I have ubuntu 8.04 LTS server edition, and I was wondering to update from the command line is it just:

```
sudo apt-get update
```

or is there something else to insure I get all the latest updates?

---

### Post by slugboat on 2008-10-16
```
sudo apt-get upgrade
```

is a good follow up to that one - it downloads the packages and installs them.

```
 sudo aptitude 
```

is a great CLI package manager (think synaptic...)

Have fun!:)

---

### Post by Diabolis on 2008-10-16
```
sudo apt-get install update
```

fetches all the available packages in the repositories

```
sudo apt-get upgrade
```

installs the newest version of each package that you have already installed

```
sudo apt-get install *"name of package"*
```

installs a specific package

---

### Post by jdcnosse on 2008-10-16
Alright thank you :)

EDIT: another question.  Is there any way to automatically notify me when new updates are available or will I still have to run a command to do that?

---

### Post by Diabolis on 2008-10-16
That is a service that comes activated by default in Ubuntu. You can activate/deactivate it here: **System / Preferences / Sessions** Its called **Update notifier**

---

### Post by GuitarRocker2562 on 2008-10-16
It will check for update daily, i think. Or, go to System -> Administration -> Update Manager

---

### Post by jdcnosse on 2008-10-17
I think you miss understood me.

I have the server version installed, so I have no GUI...

---

### Post by bodhi.zazen on 2008-10-17
I do not think the server edition will automatically notify you of updates.

With server installs, once they are up, I usually do security only updates.

---

