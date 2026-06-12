---
title: "CEWE Photoworld - Failed to execute child process."
date: 2012-09-16
forum: New to Ubuntu
---

### Post by Mrricheyrich on 2012-09-16
Hi,
I stumbled on this post when searching for answers to why my CEWE Photoworld program will not execute, and gives me "failed to execute child process" errors when I click on the desktop icon.

I've gone through the usual permissions testing (//programs/photoworld$ chmod 777 *) and the permissions for the program are -rwxrwxrwx.

I've tried clicking on the desktop icon, plus the following in the terminal window:

$ ./PHOTOWORLD
$ sudo ./PHOTOWORLD
$ sudo PHOTOWORLD

$ su root
then
$ ./PHOTOWORLD

also
$ gksu nautillus
then double clicking the icon in the super user document browser

Nothing works. Am I missing the point? What on earth will make this program run?! My os is Ubuntu 12.1.

Cheers,
Rich

---

### Post by Mrricheyrich on 2012-09-16
P.S. Following advice from another forum, I also had a go at creating a link in my /bin folder, as I thought this would add it to the global path list:

/bin$ sudo ls -s /programs/photoworld/PHOTOWORLD PHOTOWORLD

This also did nothing to help executing the program from terminal or icon.

---

### Post by coffeecat on 2012-09-16
@Mrricheyrich, I've moved your posts into their own thread from the old thread that you posted to, and amended the title. It is usually better to start your own threads.

---

