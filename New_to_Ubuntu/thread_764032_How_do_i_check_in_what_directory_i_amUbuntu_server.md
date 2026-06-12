---
title: "How do i check in what directory i am/Ubuntu server"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by rgotten on 2008-04-23
How can i check and see on the Ubuntu terminal in what directory I am, and if i need to change directories, how i do this?
rgotten

---

### Post by ace007 on 2008-04-23
```

cd /blah/blah/blah

```

Will change your directory to whatever.

```

pwd

```

for present working directory

---

### Post by TeoBigusGeekus on 2008-04-23
If it is the same with the Desktop edition, type
```
pwd
```

To change directory, type
```
cd /nameofdirectory
```

---

### Post by Oldsoldier2003 on 2008-04-23
as above PWD will give you your gurrent working directory. when you cd if the path starts with a / its a absolute path. if you leave off the / its a relative path.

meaning if you are in /home/chuck and type cd etc you will go to /home/chuck/etc

if you typed cd /etc you would end up in the /etc directory

---

### Post by mlentink on 2008-04-23
Might I respectfully point you to: [http://gd.tuwien.ac.at/linuxcommand.org/](http://gd.tuwien.ac.at/linuxcommand.org/)

---

### Post by rgotten on 2008-04-23
Thanks to everybody

rgotten

---

