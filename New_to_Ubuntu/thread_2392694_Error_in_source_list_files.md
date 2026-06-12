---
title: "Error in source list files"
date: 2018-05-24
forum: New to Ubuntu
---

### Post by aadeazm-forever on 2018-05-24
Guys I am new to lubuntu i have been using debian stretch for the past few years i am having trouble getting new files through the sudo apt-get  command.
Here is what it says
E: Malformed line 61 in source list /etc/apt/sources.list.d/mongodb.list (type)
E: The list of sources could not be read.
E: Malformed line 61 in source list /etc/apt/sources.list.d/mongodb.list (type)
E: The list of sources could not be read.

---

### Post by howefield on 2018-05-24
What version of Lubuntu are you using ?

What is the output of 

```
cat /etc/apt/sources.list.d/mongodb.list
```

---

### Post by andrelima175 on 2018-05-24
Do these commands: 

- sudo rm [COLOR=#000000]/etc/apt/sources.list.d/mongodb.list

- sudo apt update 

- sudo apt upgrade 

Thats it. [/COLOR]

---

