---
title: "Java for ubuntu"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by tad214 on 2008-06-09
[B]Hi guys,
I am trying to play a game on pogo.com, and it requires the java plugin. Can someone tell me what i need to download that is the same thing as java for windows? Thanks in advance for the responses in advance.[/B]

---

### Post by tad214 on 2008-06-09
**Anybody?**

---

### Post by PmDematagoda on 2008-06-09
You can install the Sun Java plugin with:-
```
sudo apt-get install sun-java6-plugin
```

---

### Post by tysonh on 2008-06-09
try typing this in a terminal window:

sudo apt-get install sun-java6-jre


post back what happens then.

---

### Post by tad214 on 2008-06-09
Hi,
Thanks a lot guys for the help.

---

### Post by tysonh on 2008-06-09
I should have been a little faster I almost got to solve my first problem.. lol

---

### Post by stchman on 2008-06-09
> **tad214 said:**
> [B]Hi guys,
I am trying to play a game on pogo.com, and it requires the java plugin. Can someone tell me what i need to download that is the same thing as java for windows? Thanks in advance for the responses in advance.[/B]

If you are using 32 bit then do this:

```
sudo apt-get -y install sun-java6-bin sun-java6-fonts sun-java6-jdk sun-java6-jre sun-java6-plugin
```

This will get you going.

---

