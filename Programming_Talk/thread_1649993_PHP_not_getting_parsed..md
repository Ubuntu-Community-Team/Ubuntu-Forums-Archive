---
title: "PHP not getting parsed."
date: 2010-12-20
forum: Programming Talk
---

### Post by mizokia on 2010-12-20
Tonight I was following the guide at [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP) for setting up LAMP. I got to the section "Does your browser ask if you want to **download the php** file instead of displaying it?" I followed all their suggestions, even cleared Opera's cache, and still no parsing. I am on Ubuntu 10.04 using PHP5 with Apache2. Any suggestions?

---

### Post by secondstage on 2010-12-29
I'd like to check if you've got the correct packages installed for php.
```
aptitude search '~i php'
```

I tried to follow that guide once and I think I gave up. The quickest and most effective way to get a LAMP server running, for me, is to open Synaptic (System->Administration->Synaptic) and mark packages by the task 'LAMP Server' (Edit->Mark packages by Task...->Lamp Server->Ok) and hit apply. 

Synaptic may ask for a few things along the install process.

---

