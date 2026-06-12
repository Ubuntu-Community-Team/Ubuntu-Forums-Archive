---
title: "mysql data tables recovery."
date: 2010-03-03
forum: Programming Talk
---

### Post by hockey97 on 2010-03-03
Hi, my ubuntu system crashed and thank god i backed up my 2 years of website work. The problem was that I forgot to backup my mysql database. 

So now I took out that hard drive and attached it to a windows xp computer to hopefully recover the datatables. I have like 3 tables I made  that I want to recover.

I am using a R-LINUX software to recover the files. I found many.


I just need to know what files I need to succecssfully backup mysql database.

I see alot of .myi files  I would like to know the file types needed to be backedup.

I plan to reinstall ubunmtu but want to recover whatever I can before proceeding.

---

### Post by Hellkeepa on 2010-03-03
HELLo!

There are three files related to each table:
```
<table>.frm
<table>.myd
<table>.myi
```
Also, if you've used InnoDB you'll also want to grab these files:
```
ibdata1
ib_logfile0
ib_logfile1
```
You can find all of the files inside the "/var/lib/mysql" folder, wher the table files are stored within a folder with the same name as the database.

Happy codin'!

---

### Post by hockey97 on 2010-03-04
thanks. I know the files are located in /var/lib/mysql. The problem is my hard drived is messed up filesystem wise. I can't mount it in ubuntu live cd nor windows xp. So I attached it to my windows xp and the comptuers can detect the hard drive but I can't look threw it for files. so I am using R-linux software to recover lost data on that hard drive.

It does show a var/lib/ folders but in lib there is no mysql folders yet I foud in extra files folder that the softer create but not on any hard drive just a reorganization on how it lists stuff. 

I found the mysql folder and inside is is nothing but .myi files.

no table names or database names just numbers folloed by a .myi.

something like 8049304093.myi
I got about 12 of them same amount as the tables I had in mysql database.

on this website: [http://www.crucialp.com/resources/tutorials/server-administration/how-to-restore-repair-a-mysql-database-table-recover.php](http://www.crucialp.com/resources/tutorials/server-administration/how-to-restore-repair-a-mysql-database-table-recover.php)

it claims I only need the .myi files to recover the tables.

thanks for the info. I searched the hd and could only find .myi files. so I am hopoing there is a way to just use the .myi files for the tables. I dont need to recover the data just the table structures. I didn't have any important data in the tables. I just need the same structure because of my website code.

---

