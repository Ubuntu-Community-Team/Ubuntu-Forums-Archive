---
title: "MSSQL Connection Problem"
date: 2010-12-20
forum: Programming Talk
---

### Post by ashiq_rahman on 2010-12-20
[IMG]http://ubuntuforums.org/images/icons/icon8.gif[/IMG] 				**MSSQL Connection Problem** 			
 			 			 		   		 		 		I have installed MSSQL Server 2005 in a Windows XP Pro machine.
                  IP                       = 172.17.0.29
                  Username           = sa
                  Password            = dontcry
                  Port                    = 1433
                  Database            = master
                  Table                  = student (id int,name varchar(20)
  Telnet service is up. SQL Client is also installed. I can fetch all data from “student” table from Windows XP Pro.
   
  I have installed Ubuntu Server 10.04 LTS in an AMD-64bit Server machine. 
                  IP     = 172.17.4.254
  I am able to Ping and Telnet to  172.17.0.29 from Ubuntu Server. I  also enabled Telnet service, also install LAMP in Server. I write a PHP  code to fetch MSSQL data from 172.17.0.29 database server. PHP code is
   
  <?php
              $conn = odbc_connect(“myown”,”sa”,”dontcry”);
              $stm = “select * from student”;
  $rs = odbc_exec($conn,$stm);
  $show = odbc_result($rs,1);
  echo $show;
  odbc_close($conn);
  ?>
  Some other settings on Ubuntu Server are,
   
  /etc/freetds.conf
  [myserver]
                  host                    = 172.17.0.29
                  port                    = 1433
                  tds version          = 7.0
   
  /etc/odbc.ini
  myown = myownDSN
  [myown]
  Driver                = FreeTDS
  Description         = myownDSN
  Trace                 = No
  Servername       = myserver
  Database           = master
   
  /etc/odbcinst.ini
  [FreeTDS]
  Description         = TDS driver (Sybase/MS SQL)
  Driver                = /usr/lib/odbc/libtdsodbc.so
  Setup                 = /usr/lib/odbc/libtdsS.so
  CPTimeout          = 
  CPReuse             = 
  Problem is, I am not able to see the data? What should I do next….?

---

### Post by roccivic on 2010-12-20
you are running mysql, so why don't you use mysql functions instead of odbc?

[http://php.net/manual/en/ref.mysql.php](http://php.net/manual/en/ref.mysql.php)

---

### Post by ashiq_rahman on 2010-12-20
MySQL is in Ubuntu Server and MSSQL (Microsoft SQL Server 2005) is in Windows server. Web server (apache2) is in Ubuntu. I intend to connect MSSQL in Windows from Ubuntu to fetch data.  

N.B. I know how to connect MySQL using PHP....:)

---

### Post by roccivic on 2010-12-20
oh, mssql. sorry, lol.

---

### Post by ashiq_rahman on 2010-12-23
No one interested ... giving suggestion...;)

---

### Post by PaulM1985 on 2010-12-23
I'll admit from the off I know a little about MSSQL and nothing about php, but I did find this link: [http://ubuntuforums.org/showthread.php?t=1098688](http://ubuntuforums.org/showthread.php?t=1098688) - useful?

Paul

---

