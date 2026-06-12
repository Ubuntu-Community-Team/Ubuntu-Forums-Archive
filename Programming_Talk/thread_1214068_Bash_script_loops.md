---
title: "Bash script loops"
date: 2009-07-15
forum: Programming Talk
---

### Post by e24ohm on 2009-07-15
folks,
I am trying to write a script that will loop a command a few times over until I close the terminal screen or have key board in put.

#!/bin/sh
ping xxx.xxx.xxx.xxx.
sleep 3000


i want to run ping and hit an ip address and then repeat 5 minutes later. I understand i can do this other ways with cron, but i want to practice loops and calling apps.

Question - how do i format a loop to provide what i need to do..having a hard time with this, and my school study books.

thanks

---

### Post by Martin Witte on 2009-07-15
> **e24ohm said:**
> 
Question - how do i format a loop to provide what i need to do..having a hard time with this, and my school study books.

thanks

Maybe [this]("http://tldp.org/LDP/abs/html/loops1.html") document is more easy to understand than your school books?

---

### Post by unutbu on 2009-07-15
This won't help you learn loops in bash, but it is a convenient:
```
 watch -n 3000 ping -c1 xxx.xxx.xxx.xxx
```
Note the "-c1" flag tells ping to ping once then end. Otherwise it just continues forever until receiving a ctrl-c or other termination signal.

---

### Post by c0mput3r_n3rD on 2009-07-15
```

while [ this is true ]
  do
          expressions...
done

```

---

### Post by e24ohm on 2009-07-16
Thanks for the help folks.


Cheers!!!

---

