---
title: "MySQL and local-infile"
date: 2012-10-08
forum: New to Ubuntu
---

### Post by rudy1094 on 2012-10-08
I'm trying to load a csv file into mysql using the Load Data Local Infile command in the mysql workbench and I'm getting the errror. 
 
ERROR 1148 (42000): The used command is not allowed with this MySQL version
 
I added the local-infile=1 line to the my.cnf file, but continue to get the error. Do I need to do something else to be able to load a csv file? Is there a better way to load csv files into msql? Thanks.

---

### Post by rudy1094 on 2012-10-08
I was able to load my csv file from the command-line. In addition to changing the server setting in the my.cnf file, I also had to set the client local-infile flag when I connected to the mysql database using the local-infile flag. I don't know how to change the local-infile parameter within the mysql workbench, so I wasn't able to load the csv file within the workbench, but I could do it through the command-line.

---

### Post by kyrenex on 2012-10-09
I am working on a similar problem. Shouldn't it be possible to do this using the MySQL Workbench?
Any ideas?

---

