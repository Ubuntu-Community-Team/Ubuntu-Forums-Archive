---
title: "[SOLVED] Seperate /home partition - Reinstall ubuntu"
date: 2008-08-07
forum: New to Ubuntu
---

### Post by diego898 on 2008-08-07
Hey I recently seperated my /home partition from ubuntu. Now, lets say I wanted to reinstall ubuntu all over again. How exactly would I do this? Is there something special I have to reflect in the installer (Do I have to tell it somehow that I have a seperate /home?)

Thanks

---

### Post by AFarris01 on 2008-08-07
yes, essentially if/whenever you reinstall ubuntu, when you get to the partitioner, only tell it to reformat your system partition, and select your existing home partition and assign it the mount point of "/home"

just make sure that when you do that, you dont accidentally tell the partitioner to reformat that partition too...although i believe it only formats the root partition be default

hope that helps!

Andrew

---

### Post by ibuclaw on 2008-08-07
I just select "manual" partition and assign the partition to /home and **not** format it.

It is nothing that special. But be weary if you tryout a distro other than Ubuntu, because the config files in your home folder may not work to the same extend.

Regards
Iain

---

