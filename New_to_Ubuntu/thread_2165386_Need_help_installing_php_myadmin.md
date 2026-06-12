---
title: "Need help installing php myadmin"
date: 2013-08-04
forum: New to Ubuntu
---

### Post by eldan2 on 2013-08-04
Hey, 
 
I have just installed Ubuntu using virtual box. When I tried to install phpmyadmin on it, it gave a message on my terminal saying "Command not found"

The command that I was trying to enter is apt-get -y install phpmyadmin 

I had xamp previously installed when installing ubuntu. Can that be the reason why it is giving me that message?

---

### Post by xtremesupremacy3 on 2013-08-09
No it's not due to xampp being installed previously. If this happens during the install phase, it means there is something wrong in the apt-get command.
I just installed phpmyadmin using the command you gave.
Please check to make sure there are no unnecessary spaces and that you use sudo to install it.
If that is the case, can you type the command 'sudo apt-cache search phpmyadmin' and see if that returns the package you are looking for. Not that I suspect it's not in the repo's but if that command doesn't work, then somehow it appears there is something wrong with apt-get.

---

### Post by eldan2 on 2013-08-09
> **xtremesupremacy3 said:**
> No it's not due to xampp being installed previously. If this happens during the install phase, it means there is something wrong in the apt-get command.
I just installed phpmyadmin using the command you gave.
Please check to make sure there are no unnecessary spaces and that you use sudo to install it.
If that is the case, can you type the command 'sudo apt-cache search phpmyadmin' and see if that returns the package you are looking for. Not that I suspect it's not in the repo's but if that command doesn't work, then somehow it appears there is something wrong with apt-get.


xtremesupremacy3, Thank you so much for replying. I have found the issue, and found out that I didn't SSH into the server properly. (It was my first time installing Ubuntu.) But thank you!!

---

