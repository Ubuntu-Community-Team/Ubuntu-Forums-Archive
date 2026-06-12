---
title: "defrag anyone? Delte temp files? Clear up some space... some how?"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by 133794m3r on 2008-06-26
ok... is there a way of defrag on Ubuntu.... also is there... some way to delete temp files....
and also I've been using the dua alot... and found a crapload of my memory is wasted in help files... ok... is there anyway to delete these help files that are in dif languages than I need? I'd like to delete them to clear up some space so any help would be great.

---

### Post by iaculallad on 2008-06-26
> **133794m3r said:**
> ok... is there a way of defrag on Ubuntu


-Ubuntu (Linux) doesn't need to.


> **133794m3r said:**
> .... also is there... some way to delete temp files....


-Yes, try to issue the commands in your terminal to free spaces:

```
sudo apt-get clean
sudo apt-get autoremove
sudo deborphan | xargs apt-get -y remove --purge
sudo deborphan | xargs sudo apt-get -y remove --purge

```

---

### Post by 133794m3r on 2008-06-26
yeah when I do that debo... thing... I get this
```
macarthur@macarthur-laptop:~$ deborphan | xargs apt-get -y remove --purge

The program 'deborphan' is currently not installed.  You can install it by typing:
sudo apt-get install deborphan
bash: deborphan: command not found
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
```

---

### Post by billgoldberg on 2008-06-26
[http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html](http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html)

Defrag isn't necessary.

---

### Post by iaculallad on 2008-06-26
> **133794m3r said:**
> yeah when I do that debo... thing... I get this
```
macarthur@macarthur-laptop:~$ deborphan | xargs apt-get -y remove --purge

The program 'deborphan' is currently not installed.  You can install it by typing:
sudo apt-get install deborphan
bash: deborphan: command not found
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
```

That's just another option: If you really want deborphan, install it as the error message says:

```
sudo apt-get install deborphan

```

and if its already installed, insert the sudo command:

```
sudo deborphan | xargs apt-get -y remove --purge
```

---

### Post by billgoldberg on 2008-06-26
> **133794m3r said:**
> yeah when I do that debo... thing... I get this
```
macarthur@macarthur-laptop:~$ deborphan | xargs apt-get -y remove --purge

The program 'deborphan' is currently not installed.  You can install it by typing:
sudo apt-get install deborphan
bash: deborphan: command not found
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
```

That error occurs most likely because you have another package manager open (synaptic, update manager, ...)

---

### Post by 133794m3r on 2008-06-26
I had to do it in root.... 
but yeah is there anyway to just delete the help files that I don't need... ie French Help in Open Office?

---

### Post by billgoldberg on 2008-06-26
Read link again.

---

### Post by 133794m3r on 2008-06-26
yeah... I just skimmed it too lazy... :P

---

### Post by billgoldberg on 2008-06-26
All tricks aside,you can just remove the packages manually using synaptic.

But that could take a while.

---

### Post by 133794m3r on 2008-06-26
yeah... did I metion that I'm lazy?

---

### Post by frt975 on 2010-02-05
I know I'm a little late, but install localepurge

---

