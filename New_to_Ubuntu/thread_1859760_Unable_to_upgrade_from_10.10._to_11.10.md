---
title: "Unable to upgrade from 10.10. to 11.10"
date: 2011-10-14
forum: New to Ubuntu
---

### Post by jeshrel on 2011-10-14
Hi,

I would like to upgrade from ubuntu 10.10 to 11.04 but when i try to upgrade using update manger or alt-F2, i only get an option to upgrade to ubuntu 11.04, but i would lke to upgrade to ubuntu 11.10. Need help

---

### Post by alphacrucis2 on 2011-10-14
> **jeshrel said:**
> Hi,

I would like to upgrade from ubuntu 10.10 to 11.04 but when i try to upgrade using update manger or alt-F2, i only get an option to upgrade to ubuntu 11.04, but i would lke to upgrade to ubuntu 11.10. Need help

You can only upgrade one release at a time. The only exception is that LTS to LTS upgrades are supported. eg when 12.04 LTS comes out next April, users of 10.04 LTS will be able to upgrade direct. In your case you have to upgrade twice. 10.10 -> 11.04 -> 11.10

---

### Post by carl4926 on 2011-10-14
A clean install is better IMO
Keep your /home (or back it up)
Assuming you have one

dist upgrade are better run out of X if you insist on it
one upgrade at a time
But you need to change your sources
Then run the upgrade with apt
(Always backup)

---

### Post by sadaruwan12 on 2011-10-14
For you we recommend of doing a clean install rather than a upgrade 'cos your system or the Ubuntu version is pretty old better to do a clean install.

Very little margin that you run into errors after a clean install if you upgrade then don't know what will happen.

---

### Post by 23dornot23d on 2011-10-14
Check my list below

I too recommend a clean install ..... 

Maybe in time some of the problems below will get solved and then re-consider the upgrade

---

### Post by jeshrel on 2011-10-15
Thanks for your replies, 
 k after a clean install how do i separate my system files from my data, so tat the next time when i have to re-install all i would have to do is to re-install my system drive. Appreciate all your help.

---

### Post by Lisiano on 2011-10-15
Actually just "Install over" the partition Ubuntu is installed on. The installer will detect that you have a /home folder on it and preserve it.
If you want to go the separate /home and / route then during the install you need to pick Manual partitioning and create 2 partitions, one for /home and one for / . The / one can be as big as 20-30GB depending on how many programs you have installed while /home should be the rest of the disk. In the create partition list there is a white box under the Format checkbox, click on the box and select either /home or / depending on which partition you are adding.

---

