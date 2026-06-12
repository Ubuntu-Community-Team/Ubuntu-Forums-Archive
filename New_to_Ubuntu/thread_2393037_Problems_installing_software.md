---
title: "Problems installing software"
date: 2018-05-28
forum: New to Ubuntu
---

### Post by pardeek on 2018-05-28
Hi there,

I am desperate for some help with installing the Scaffold 4 software. I have been trying to install if for 2 hours and just don't know what I'm doing wrong.

I downloaded the .zip file, unzipped it, and changed the permissions to allow it to be executable. Then, in the terminal i entered "**bash Install_Scaffold_4.8.6_Linux_x64.sh" **which opened the installer. It asks where to store shared application data such as license keys (default is /var/lib/Scaffold4) and says this folder's permissions will be set to be readable and writable by all users. I kept all the settings at default, but it won't finish the installation. It pops up with "Can't make data folder accessible to all users" and then quits. Any ideas? 

Thanks!

---

### Post by #&amp;thj^% on 2018-05-28
I think or at the least you don't mention if you first ran: (Run from the proper path)
```
./Install_Scaffold_4.8.6_Linux_x64.sh
```
And if that fails again I would get help from the folks than can help you here: [http://www.proteomesoftware.com/support/](http://www.proteomesoftware.com/support/)

---

### Post by #&amp;thj^% on 2018-05-28
Ok I got it installed by this method:
The same way you did extract and make the change file permissions for script execution.
Then i was met with the same error as you seen "Can't make data folder accessible to all users"
So I helped it with:
```
sudo mkdir /var/lib/Scaffold4
```
So then I changed the command to:
```
sudo bash Install_Scaffold_4.8.6_Linux_x64.sh

```
And bob's your uncle installed. Sorry it took a bit of time to download for me to try to help

---

### Post by pardeek on 2018-05-28
You are my hero. Thank you so much! Now I can put off being the dumb person who thought she could handle Linux for at least one more class day.

---

