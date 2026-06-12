---
title: "to perform admin tasks from script"
date: 2012-03-15
forum: New to Ubuntu
---

### Post by dinesh17 on 2012-03-15
[SIZE=3]i need to execute the command[/SIZE] [SIZE=4]**ifconfig eth0 x.x.x.x**[/SIZE][SIZE=3]  from a shell script !!  but it needs admin privileges i don't know how to solve this problem please help me ! [/SIZE]

---

### Post by sudodus on 2012-03-15
Welcome to the Ubuntu Forums!

You get administration privileges by running ***sudo*** 'superuser do' and the command.

So in your case
```
sudo ifconfig eth0 x.x.x.x
```
Good luck :-)

---

### Post by codemaniac on 2012-03-15
if you want sudo in a script without prompting for password,
edit /etc/sudoers
and add:

```
username ALL=(ALL) NOPASSWD: ALL
```

save and that's it.
the username is the user you want to give doing sudo without password.
But as yu can see the above process has security issues .

---

