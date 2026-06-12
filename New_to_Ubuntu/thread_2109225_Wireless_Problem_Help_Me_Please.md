---
title: "Wireless Problem Help Me Please"
date: 2013-01-26
forum: New to Ubuntu
---

### Post by aerol36 on 2013-01-26
today i installed eeebuntu on my asus x101ch netbook but i cant connect to internet. it doesnt see my wireless card adapter. and i couldnt find .inf file. the driver that i need is on this page under the wireless title:
[http://support.asus.com/Download.aspx?SLanguage=en&m=Eee%20PC%20X101CH&os=29](http://support.asus.com/Download.aspx?SLanguage=en&m=Eee%20PC%20X101CH&os=29)
i need an inf file. what can i do? please help:(

---

### Post by cariboo on 2013-01-27
Those are Windows drivers, they won't work with your Linux distribution. You shouldn't need to install any drivers, as they are included with the kernel. Could you open a terminal and type the following command:

```
sudo lshw -C network > lshw.txt
```

the command will create a text file called lshw.txt, you can use whatever method you want to transfer this file to the system you are using to access the forum, and paste the contents of the text file into your next post.

---

### Post by coldraven on 2013-01-27
I have Xubuntu 12.10 running on my eee pc 900. Everything worked out of the box.
After installing you will need to delete the archived install packages and any old kernel images to free up some disc space.
Use synaptic, there is an option in the preferences to clear the archive and  to delete downloaded packages after installing them.
Using synaptic you can also remove old kernels. Google that.

---

### Post by 3rdalbum on 2013-01-27
Eeebuntu has been abandoned by its developers, so it is not a good idea to use it.

Try Ubuntu 12.10 or Xubuntu 12.10. The latter is a bit more spartan but uses fewer system resources.

---

