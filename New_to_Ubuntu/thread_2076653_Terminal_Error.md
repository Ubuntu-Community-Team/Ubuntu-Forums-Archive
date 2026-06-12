---
title: "Terminal Error"
date: 2012-10-26
forum: New to Ubuntu
---

### Post by timalia on 2012-10-26
sir,
I have upgraded to Ubuntu 12.10. While updating I got following error in Terminal :

tim@tim-MS-AE1111:~$ sudo apt-get update
[sudo] password for tim: 
E: Malformed line 60 in source list /etc/apt/sources.list (URI parse)
E: The list of sources could not be read.
tim@tim-MS-AE1111:~$ 

Please help me how to rectify this error. I am new to Linux/Ubuntu( First time user)

Thanks

---

### Post by Bashing-om on 2012-10-26
timalia; Hi ! Welcome to the forum.

The file sources.list is probably corrupted for some reason. 
I suggest to move it out of the way (keeping it just in case) and generating a new database file thusly:
```
mv /etc/apt/sources.list /etc/apt/sources.list-old
sudo apt-get update
sudo apt-get upgrade
```generates a new database file and then updates all the packages (upgrade).

[INDENT]warm regards <== BDQ

[/INDENT]

---

### Post by COMECON on 2012-10-26
Could you please paste the content of /etc/apt/sources.list here? Try something like that:
```
$ cat /etc/apt/sources.list 
```
Maybe we can see if something has broke! :D

---

### Post by ajgreeny on 2012-10-26
> **Bashing-om said:**
> timalia; Hi ! Welcome to the forum.

The file sources.list is probably corrupted for some reason. 
I suggest to move it out of the way (keeping it just in case) and generating a new database file thusly:
```
mv /etc/apt/sources.list /etc/apt/sources.list-old
sudo apt-get update
sudo apt-get upgrade
```generates a new database file and then updates all the packages (upgrade).
[INDENT]warm regards <== BDQ

[/INDENT]
But if you remove or rename the sources.list those two commands will simply error out.  The commands do not rebuild the sources.list file as far as I'm aware.

You can, however, rebuild the list at [http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/) and replace your current version, but COMECON's suggestion should show us what is wrong and allow a simple edit to put it right.

---

### Post by jerrrys on 2012-10-26
> **ajgreeny said:**
> But if you remove or rename the sources.list those two commands will simply error out.  The commands do not rebuild the sources.list file as far as I'm aware.

It has rebuilt the few times I have use it

---

### Post by Bashing-om on 2012-10-26
@ all ...to set it correct.

 I do stand corrected.
I did attempt my above directions... the /etc/apt/sources.list file is NOT regenerated.
-no errors just nothing to work with -
My notes will so be amended to reflect.

COMECON's course of action  hereby also has my endorsement.

Thank you  ajgreeny for protecting my back (again !)

[INDENT]still learning even after all these years ! ==> BDQ

[/INDENT]

---

