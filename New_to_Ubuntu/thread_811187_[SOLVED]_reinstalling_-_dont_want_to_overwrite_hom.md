---
title: "[SOLVED] reinstalling - dont want to overwrite /home"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by tropdoug on 2008-05-28
Hi guys

I have done it again, been trying to enable my nvidia drivers correctly, and in the process lost a few things. My fault I did not think through removing some files. 

Cut a long story short, I have decided to reinstall gutsy from the cd. I have a separate /home partition, but what do I have to do to ensure that partition is not only not written too, but that the sym links to it and my /home directory are correctly set up during the install

oooh just found a thread that suggests that all the settings I now have, will be preserved by my having a separate /home partition. Sooo if I have lost my wireless network (which I have) then presumably a reinstall won't fix that?

---

### Post by Oldsoldier2003 on 2008-05-28
> **tropdoug said:**
> Hi guys

I have done it again, been trying to enable my nvidia drivers correctly, and in the process lost a few things. My fault I did not think through removing some files. 

Cut a long story short, I have decided to reinstall gutsy from the cd. I have a separate /home partition, but what do I have to do to ensure that partition is not only not written too, but that the sym links to it and my /home directory are correctly set up during the install

oooh just found a thread that suggests that all the settings I now have, will be preserved by my having a separate /home partition. Sooo if I have lost my wireless network (which I have) then presumably a reinstall won't fix that?

use the option to manually patition when you install.mount your /home partition as /home when you select the partition you want to install gutsy. make sure you do not mark the box to format it or you'll lose all the data in the /home dir

---

### Post by tropdoug on 2008-05-28
Thanks that explains that, just need to slip over to wireless forum and see what I can do about my 'unclaimed' wireless card, then maybe I wont need to do a reinstall :)

---

