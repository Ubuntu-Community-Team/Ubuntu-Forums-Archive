---
title: "what ubuntu version do i have"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by Troca on 2008-04-24
Iam asking alot now but i have 1 more question for today. How do i know what ubuntu verssion i have iam trying to install some applets for avant and it asks me be4 i can download what ubuntu version i have 

i can select from hardy and some outhers. i just donwloaded the regular ubuntu from the main page.

---

### Post by kk0sse54 on 2008-04-24
Go to System and select About Ubuntu.

---

### Post by neurostu on 2008-04-24
open a terminal and run 
```

uname

```

---

### Post by elmer_42 on 2008-04-24
There should be a section in *System -> About Ubuntu* that says what version you have. It is highlighted below.
[img]http://arch.kimag.es/share/33234588.png[/img]

---

### Post by philinux on 2008-04-24
Use 

uname -a 

in a terminal

[edit] go system> admin > system monitor > click the system tab

---

### Post by neurostu on 2008-04-24
AHHH! I forgot the -a.

Thanks!

```

uname -a

```

---

### Post by Oldsoldier2003 on 2008-04-24
another neat shell trick is 
```
cat /etc/lsb-release
```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04"

---

### Post by grannyw on 2008-04-24
use

```
sudo lshw -C cpu
```

it will get you all the info

---

### Post by Oldsoldier2003 on 2008-04-24
> **grannyw said:**
> use

```
sudo lshw -C cpu
```

it will get you all the info

the OP was looking for Ubuntu Version.

---

