---
title: "How to fragment data into different servers(Master-Slave)?"
date: 2018-07-26
forum: New to Ubuntu
---

### Post by izzati on 2018-07-26
I am new in master-slave replication and horizontal fragmentation technique.
Currently, I am doing my project title "Cluster replication using horizontal fragmentation approach". 


This is my use case:


There are 4 virtual machines. One act as a master server and the others are slave server. I will implement the horizontal fragmentation technique in master server based on campus condition. My database is about student information.


These are the steps for my project:


1. Import data from window to Linux
2. Configure master-slave
3. Implement the horizontal fragmentation techniques.


So, the problem is when I write this coding:


    mysqldump --databases Student --tables Student_info --w"Campus in (select Campus from Student_info WHERE CAMPUS='KGB')" --single-transaction >masterdump1.sql
    
    sudo scp masterdump1.sql slave1@192.168.117.143:


The data from the master server fragmented well. But when I try to add new student name, it is not fragment based on the campus condition.


It should be:


    SLAVE1: student from KGB
    SLAVE2: student from KB
    SLAVE3: student from KK


But when updates, it will copy all the data and not fragment like it should be.


Is there any syntax that I left? Any suggestion to solve this problem? can you please help me?

---

### Post by Tadaen_Sylvermane on 2018-07-27
Not sure what you are trying to achieve. All my googling on fragmentation of mysql is bad things. Certainly not something you would want intentionally.

I think you are misunderstanding the purpose of a master / slave relationship for mysql. That or i'm misunderstanding something.

Aside from the theoretical usage which i cant figure why, there is no benefit to doing this. Slaves are supposed to help with reading tables quicker as well as provide a stable db to dump or work on. Not splitting them among different servers.

Also why sudo for scp?

---

