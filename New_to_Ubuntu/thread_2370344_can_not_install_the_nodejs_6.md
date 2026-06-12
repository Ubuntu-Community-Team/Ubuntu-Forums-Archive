---
title: "can not install the nodejs 6"
date: 2017-09-02
forum: New to Ubuntu
---

### Post by johnerin22 on 2017-09-02
At first I installed the node with terminal, with command Update Package Manager


sudo apt-get update
Adding NodeJS PPAs


```
sudo apt-get install python-software-properties
curl -sL https://deb.nodesource.com/setup_6.x | sudo -E bash -
Installing NodeJS and NPM

```

sudo apt-get install nodejs
It works, but when I am looking version node, I see node v 4 Then I used google for search this problem and a found this topic [https://stackoverflow.com/a/43914369](https://stackoverflow.com/a/43914369) There using a ln command for create symbolic link between two files

and used this instruction for manual install, but nothing happens, error appears and not installing [Look at this screenshot]("https://i.stack.imgur.com/mhFyS.png") Maybe I doing anything wrong?

---

### Post by wildmanne39 on 2017-09-02
*Thread moved to **New to Ubuntu**.*

Try:

```
sudo apt install nodejs-legacy
```

---

