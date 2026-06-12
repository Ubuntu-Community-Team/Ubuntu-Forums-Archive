---
title: "Need help with ORACLE server"
date: 2012-08-23
forum: Programming Talk
---

### Post by vikkyhacks on 2012-08-23
I have been using mysql for some time and found it good, but i am studying for my exams and the syntax that mysql has is a bit different from my text book because my text book uses Oracle ..
 when it comes to basic queries it is fine by when i see queries like 
**MYSQL >>> ALTER TABLE Persons DROP PRIMARY KEY**
**ORACLE >>> ALTER TABLE Persons DROP CONSTRAINT pk_PersonID **
i am stuck ... I neeeeeeeeeed ORACLE server, instead of downloading Oracle server i downloaded the Oracle Developer Package ... I am confused with all the packages in the oracle website and I also have a slow dail up connection to try out all the packages on their site ... Someone please send me a download link of Oracle server and about oracle ...
1. What is the main difference between oracle server and mysql (apart from SQL syntax which i figured out)
2. Is that as much as an opensource app like mysql.
3. What are the advantages/disadvantages of Oracle over mysql

 ... I am a beginner, don get mad if i am asking something childish ....

---

### Post by Habitual on 2012-08-23
> **vikkyhacks said:**
> ...
1. What is the main difference between oracle server and mysql (apart from SQL syntax which i figured out)
2. Is that as much as an opensource app like mysql.
3. What are the advantages/disadvantages of Oracle over mysql...

1.) Oracle licenses its product and it comes at a Premium.
2. ) "[It is open source but not completely free (as in speech) software]("http://answers.yahoo.com/question/index?qid=20070507065620AAxpyED")."
3. ) is out of my current depth. I'm lucky I had an Oracle DBA job in the first place. I'm a techie, I "install" "stuff".

The difference to me is that MySQL could be thought of as Playing "in the Minors" (American Baseball Metaphor) where Oracle would the "the Pros".

If you must persist... :)
[Install Virtualbox or similar and install CentOS]("http://it.toolbox.com/blogs/database-solutions/oracle-11g-software-installation-on-linuxcentos55-on-oracle-vm-virtualbox-324-40308").
You would then use the "Oracle Developer Package" tools (should include sqlplus?) to connect to the Oracle Instance inside the VM.

Good luck.

---

### Post by SeijiSensei on 2012-08-23
You can download a copy of Oracle 11g [here](http://www.oracle.com/technetwork/database/enterprise-edition/downloads/index.html).  It's a commercial product, but you can download an evaluation copy for free.  Read the [license]("http://www.oracle.com/technetwork/licenses/standard-license-152015.html").

If you want a fully open-source SQL server that is closer syntactically to Oracle than MySQL, I recommend PostgreSQL.  It [conforms]("http://www.postgresql.org/about/") closely to SQL standards including, for instance, the command "ALTER TABLE ... DROP CONSTRAINT" that you cite.  You can install PostgreSQL 9.1 in Ubuntu 12.04 simply by running "sudo apt-get install postgresql-9.1".

MySQL does not conform as well to SQL standards as either PostgreSQL or Oracle.  In the past MySQL was considered to be faster than its competitors, especially for reads, and was thus a common backend for web sites.  I don't think the performance difference is as great today as it once was. I've been building web sites with PostgreSQL back ends for about a decade now and never found my sites to display performance issues.  Of course, some web sites are handling dozens of queries or more each minute; I've never authored those types of sites so I can't comment on performance issues in high-traffic situations.

---

### Post by vikkyhacks on 2012-08-23
> **SeijiSensei said:**
> You can download a copy of Oracle 11g [here](http://www.oracle.com/technetwork/database/enterprise-edition/downloads/index.html)

many thanks for the download link ... I am having a laptop(64bit) and pc(32bit) both running Ubuntu 11.04, so I decided to use this link

[http://www.oracle.com/technetwork/database/enterprise-edition/downloads/112010-linx8664soft-100572.html](http://www.oracle.com/technetwork/database/enterprise-edition/downloads/112010-linx8664soft-100572.html)

but then I have a 
Oracle Database 11g Release 2 Client (11.2.0.1.0) for Linux x86-64 
[http://download.oracle.com/otn/linux/oracle11g/R2/linux.x64_11gR2_client.zip](http://download.oracle.com/otn/linux/oracle11g/R2/linux.x64_11gR2_client.zip)

and two big chunks as
Oracle Database 11g Release 2 (11.2.0.1.0) for Linux x86-64 
[http://download.oracle.com/otn/linux/oracle11g/R2/linux.x64_11gR2_database_1of2.zip](http://download.oracle.com/otn/linux/oracle11g/R2/linux.x64_11gR2_database_1of2.zip)
[http://download.oracle.com/otn/linux/oracle11g/R2/linux.x64_11gR2_database_2of2.zip](http://download.oracle.com/otn/linux/oracle11g/R2/linux.x64_11gR2_database_2of2.zip)

and also a few more packages

... I actually need to install **ONLY THE SERVER** and a **SIMPLE CLIENT** like there is mysql-server and mysql workbench or a simple cli based client in ubuntu repo ... which one do i need to download to get the client and the server .... ?????

---

### Post by lykwydchykyn on 2012-08-23
You probably want to get Oracle Database express edition; it's a lot less of a byzantine monstrosity than the full-on Oracle install.

They have .deb files and an APT repository available for it.

See this:

[http://www.oracle.com/technetwork/topics/linux/xe-on-kubuntu-087822.html](http://www.oracle.com/technetwork/topics/linux/xe-on-kubuntu-087822.html)

The instructions provided will work for any debian-based distro.

---

### Post by vikkyhacks on 2012-08-23
> **lykwydchykyn said:**
> 
[http://www.oracle.com/technetwork/topics/linux/xe-on-kubuntu-087822.html](http://www.oracle.com/technetwork/topics/linux/xe-on-kubuntu-087822.html)

i found that i need express edition but the above link does not seem to work ... The *apt-get update* just gets a lifetime pause ... and even synaptic would not come to rescue .... I tried to get the express edition the other war round but found only rpm based installer .... 
Any links for ubuntu ???

---

### Post by lykwydchykyn on 2012-08-23
Just browse the repository URL and get the deb manually.  It'll be in the non-free folder.

Actually, it may not be worth it.  They've apparently mothballed the repository, it only contains version 10g now that I look closer.

You can convert an rpm to deb using "alien"; I have not tried this for oracle, but IME alien usually works fine.

---

