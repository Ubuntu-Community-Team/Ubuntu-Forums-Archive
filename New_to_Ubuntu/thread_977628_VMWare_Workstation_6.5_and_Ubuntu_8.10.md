---
title: "VMWare Workstation 6.5 and Ubuntu 8.10"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by enigmacmpr on 2008-11-10
Hi All,

I am running WinXP 64bit. I have installed VMWare Workstation 6.5 and am looking at installing Ubuntu 8.10. I would like to run Ubuntu of my WD 160 USB hdd. I want to run multiple databases (MySql, Oracle) in Ubuntu.

I am looking for recommendations on
1. Partitioning my USB Drive (database sizes will vary from about 3GB to 10GB)
2. My XP will be used mainly to develop the application side of things and I want to be able to access multiple databases concurrently.
3. I have 2GB RAM allocated for the Guesthost(VMWare). Is this going to be sufficient to run all the databases? 

regards,

enigma

---

### Post by JKBurton on 2008-11-10
Hi enigma,

1. Since this sounds like the first time you've done this, I'd give 4GB to "/swap", and everything else into "/". Normally you'd leave a bunch for a separate "/home", which helps when upgrading the OS. However, in your case, the important data is all in the databases, and the different DB apps default to keeping the databases in different places. So keep it simple, and just carefully backup all the databases before changing versions of Ubuntu.

If, on the other hand, you already know how to put the databases/indexes where you want, then make a partition just for that. In that situation, I'd do 10 GB for "/", 4 GB for "/swap", and all the rest for your database partition.

While in large production systems, there are other filesystem-types that will outperform ext3, don't worry about it for development. Just make them ext3.

3. That should be more than enough, if the databases are just supporting a single user for development. 

Best of luck, and hope you have fun,
Keith

---

### Post by enigmacmpr on 2008-11-10
Thanks for the inputs. 

I have been doing it all in a windows environment so far and would like to separate out the backoffice to a more stable environment. The databases seem to utilize more resources in a Windows environment, at least that has been my limited experience looking at Linux vs. Windows for Databases.

regards,

enigma

---

