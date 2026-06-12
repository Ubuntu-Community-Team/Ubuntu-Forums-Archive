---
title: "Run a program on multiple computers"
date: 2008-03-14
forum: Programming Talk
---

### Post by fyplinux on 2008-03-14
I have a school account that could logon many Cent OS computers, I am planning a task that I could run a program on these many computers. 

As it is a hard work to run around in the lab to run the program on every computer,  I am wondering if there could be a method to control the program to run after I have logged into the system.

All the logged in computer share the same account information and the personal data. Any change made on one computer is automatically applied to other computers by the school system. I don't know how these computers are synchronized, but I know that there is a central server to keep the data, and a ssh server for remote login as well.

And I am also hoping that the time when the program should be run is controllable.

---

### Post by pmasiar on 2008-03-14
> **fyplinux said:**
> 1) I am wondering if there could be a method to control the program to run after I have logged into the system.

2) I don't know how these computers are synchronized, but I know that there is a central server to keep the data, and a ssh server for remote login as well.

3) And I am also hoping that the time when the program should be run is controllable.

1: There are many methods. Simplest: login to each computer with 'screen', which will continue to run after you logged out. There are systems to run group of program on the cluster, ask friendly sysadmin if something like that is installed and you have access.

By any chance, is it edubuntu/bunch of X terminals, where only X is running locally?

2: looks like your home directory is on server, not on any of those PC.

3: cron can do such tricks

I am sure that better experts than me add better advice :-)

---

### Post by fyplinux on 2008-03-14
> **pmasiar said:**
> 1: There are many methods. Simplest: login to each computer with 'screen', which will continue to run after you logged out. There are systems to run group of program on the cluster, ask friendly sysadmin if something like that is installed and you have access.

By any chance, is it edubuntu/bunch of X terminals, where only X is running locally?

2: looks like your home directory is on server, not on any of those PC.

thanks, pmasiar:).

From a point of maintenance, I think It 's better to download the home directory to the local machine. as there are thousands of machines in the school, If  everyone works rely on the server, the overload for the server is too heavy. So, it is quite possible that not only X running locally.

Anyhow,  I need to ask the sysadmin.

---

### Post by slavik on 2008-03-15
the best way is if the school has MPI, OpenMP or MOSIX available. :) (They are designed for cluster/grid computing).

---

