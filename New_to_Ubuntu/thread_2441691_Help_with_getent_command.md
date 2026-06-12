---
title: "Help with getent command"
date: 2020-04-25
forum: New to Ubuntu
---

### Post by mindfried on 2020-04-25
Can someone please help me understand what each part of the following command means?

getent passwd | cut -d: -f1 | sort

---

### Post by wildmanne39 on 2020-04-25
Hello and welcome to the forum.

*Thread moved to **New to Ubuntu for a more appropriate fit**.*

---

### Post by sisco311 on 2020-04-26
Hi,

Which part of the[ pipeline]("https://www.gnu.org/savannah-checkouts/gnu/bash/manual/bash.html#Pipelines") you don't understand?

Did you read the man pages of the commands?
```

man getent
man cut 
man sort
```

The man page of getent is laconic and uses a lot of jargon. If you don't use LDAP then in short `getent passwd' prints the content of the /etc/passwd file.
```
man 5 passwd
```


Is this home work? Or are you following some kind of tutorial?

---

### Post by TheFu on 2020-04-26
[https://explainshell.com/](https://explainshell.com/) is probably what you need. Just paste the command and press "explain".

---

### Post by mindfried on 2020-04-26
Hello,

I was having problems understanding the combination of all elements but I have a better grasp of it now. This is related to a problem I encountered for school. I appreciate the feedback!

---

