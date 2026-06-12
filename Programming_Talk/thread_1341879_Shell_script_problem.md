---
title: "Shell script problem"
date: 2009-11-30
forum: Programming Talk
---

### Post by razzer on 2009-11-30
Hello. I am trying to make this shell script bellow work on my server wich should take the names in newacc.cvs and add them to the system. For each user the script should ask me to enter a password for the user im adding and then add them to the system, however my current solution do not work atm as when i run the script it dont stop to let me enter a password at all :/ do someone know how to make this work?

Example from newacc.cvs

maria;jones
andreas;öring

**Script**
```
#!/bin/sh

if [ "$#" == "0" ]
then

cat newacc.cvs | while IFS=';'  read firstname surname;
do

    echo "user $firstname $surname har been added with the password $text"
    useradd $firstname -m
    echo  added $firstname to the system
    passwd $firstname
    cd /home/$firstname/
    maildirmake.courier Maildir
    echo Maildir Created for $firstname


done
  exit 0
```

---

### Post by Barriehie on 2009-11-30
sudo passwd perhaps.

Barrie

---

### Post by razzer on 2009-12-01
> **Barriehie said:**
> sudo passwd perhaps.

Barrie

did not work. it just runs past that point still without asking me to fill in a password :/

---

