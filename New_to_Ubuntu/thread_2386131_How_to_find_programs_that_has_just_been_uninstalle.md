---
title: "How to find programs that has just been uninstalled"
date: 2018-03-01
forum: New to Ubuntu
---

### Post by fund_raiser on 2018-03-01
Hi,

Sorry for the dumb question, but what is the command in terminal to list packages or programs that I have uninstalled recently? I used *apt-get autoremove* and I have a problem now.

So how to list programs removed by *apt-get autoremove*?

thx

---

### Post by vasa1 on 2018-03-01
Go through */var/log/apt/history.log* or */var/log/apt/history.log.1.gz* (in case the former doesn't have what you want).

---

### Post by ajgreeny on 2018-03-01
Also try running command ```
grep -i " remove " /var/log/dpkg.log.1 /var/log/dpkg.log
``` which will list all packages removed recently in date order.
Note the spaces between the quote marks and the word remove; they are needed for best output as without the space you may get a lot of spurious output, particularly if using the install option (see below).

If you wish you can reinstall all of them, or show us the list and ask for further help.

That command is useful as a quick way to find out what packages have been added as well if you simply replace the word **remove** with **install**.

---

### Post by vasa1 on 2018-03-01
The history log has stuff like```
Start-Date: 2018-02-25  15:38:39
Commandline: apt-get autoremove
Requested-By: vasa1 (1001)
Remove: libboost-locale1.58.0:amd64 (1.58.0+dfsg-5ubuntu3.1), fonts-liberation2:amd64 (2.00.1-5~16.04.1~lo4)
End-Date: 2018-02-25  15:38:41
```where autoremove is explicitly mentioned.

---

