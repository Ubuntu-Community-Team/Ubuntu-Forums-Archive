---
title: "E: Type 'n' is not known at line 3 in source list/etc/apt/sources.list.d/yannubuntu-r"
date: 2013-12-29
forum: New to Ubuntu
---

### Post by a.aamukta on 2013-12-29
Hi,
I am completely new to ubuntu.

I am trying to do UBUNTU BOOT Repair ( ubuntu 12.04.3 lts precise)
While I'm doing so I'm facing the below error.



" E: Type 'n' is not known on line 3 in source list /etc/apt/sources.list.d/yannubuntu-boot-repair-precise.list.
  E: The list of sources could not be read " 

I have tried giving  " cat/etc/apt/sources.list.d/yannubuntu-boot-repair-precise.list "
It displayed an error as  "NO such file or directory"

Please suggest me what to do further

---

### Post by Elfy on 2013-12-29
First - you have no space after the cat.

```
cat /etc/apt/sources.list.d/yannubuntu-boot-repair-precise.list
```

Run that and then post the output here.

Then we can see if there's more than one error.

---

