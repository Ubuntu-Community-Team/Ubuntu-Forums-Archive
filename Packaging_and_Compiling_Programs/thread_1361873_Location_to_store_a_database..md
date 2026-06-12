---
title: "Location to store a database."
date: 2009-12-22
forum: Packaging and Compiling Programs
---

### Post by Jordanwb on 2009-12-22
I'm writing a program called "drift" and it will be using an SQLite database. I'm putting the config file in /etc/drift/ but I don't know where to put my database file.

---

### Post by gdonwallace on 2009-12-22
Your first consideration might be what partition has the most space.  If you have /home on a separate partition or any other partitions created, check the used disk space with the disk utility or from terminal type df -h.  The obvious choice is the one with the most space.  If you only have one partition and everything is on it, then I would put it in your /home directory, under a directory with the same name as your program (i.e. /home/drift)

Your second consideration should be how big do you expect the database to get.  If /home is on a small partition, then the first option may be the one for you.  My second recommendation would be /opt/drift/ (making /drift in the /opt directory)  /opt is the directory for third party or user installed applications (generally speaking)  If you have the space you might even consider putting the application and the database in /opt/drift/.  The advantage to doing this are two:
   1.  You have one local location for all the programs and data files 
       for your program.  Making it easier to manage in the long run
   2.  During upgrades to the OS, the /opt directory is ignored.  So
       anything put in this directory is safe and will not get deleted
       accidentally during an upgrade. (putting anything in /etc runs the
       potential risk that it may get erased or moved during and upgrade
       because it is not a file that is generally in the /etc directory)

Hope this helps.

---

### Post by Jordanwb on 2009-12-22
Disk space is not a problem. I got a 500GB drive laying around waiting to be assigned a purpose. I don't expect the database to get too large. Maybe 25 megs, tops. It's mainly a proof of concept software. I'll put everything it the /opt/drift/ folder.

Thanks.

---

