---
title: "sql developer in ubuntu 10.4"
date: 2011-10-10
forum: New to Ubuntu
---

### Post by devika94 on 2011-10-10
i have installed ubuntu 10.4 recently and i need help in installing sql developer in it...
i am a beginner and hardly knows anything in this regard..

ok..
When i tried the step-by step procedure to install sql, i could make till a few steps..
and after that the following message pops out in the terminal..

devika@devika-desktop:~$ sqldeveloper

Oracle SQL Developer
 Copyright (c) 1997, 2011, Oracle and/or its affiliates. All rights reserved. 

/opt/sqldeveloper/sqldeveloper/bin/../../ide/bin/launcher.sh: line 444: [: too many arguments
/opt/sqldeveloper/sqldeveloper/bin/../../ide/bin/launcher.sh: line 464: [: too many arguments
Error: No JDK found on PATH
Please correct the SetJavaHome directive or add the directive
in /opt/sqldeveloper/sqldeveloper/bin/sqldeveloper.conf or
sqldeveloper-Linux.conf
to point to the JDK installation.

what can i do now? plz help..:(

---

### Post by 2F4U on 2011-10-10
Where is Java installed on your machine and is it in the path variable? The error message says it can't find a JDK.

---

### Post by devika94 on 2011-10-10
In 
/usr/lib/jvm
there are 5 folders available.
I tried to correct "SetJavaHome" using each of these..
yet the same error message is coming..:(

---

### Post by Sergio.G on 2011-10-11
Hi, 

Perhaps you need to set the environment variables

export JAVA_HOME=/usr/lib/jvm/java-6-sun-1.6.0.26

I tried to installed the same way you are doing it and I failed, so I searched and found this on the web, it is a procedure step-by-step how to install sql developer in karmic & lucid (the post is from 2010) I tried it a few days ago and it worked for me, here's the web page link:

[http://timony.com/mickzblog/2010/01/09/install-oracle-sql-developer-on-ubuntu-karmic/]("http://timony.com/mickzblog/2010/01/09/install-oracle-sql-developer-on-ubuntu-karmic/")

I also use TOra, which is an open-source multi-platform database management GUI for Oracle, MySQL and Postgres, I use it for Oracle at work. Here is the link if you are interested:

[http://www.pythian.com/news/10857/installing-tora-with-oracle-support-on-ubuntu-10-04-lucid-lynx/]("http://www.pythian.com/news/10857/installing-tora-with-oracle-support-on-ubuntu-10-04-lucid-lynx/")

Hope it helps
Cheers and welcome to Ubuntuforums! :)

---

### Post by devika94 on 2011-10-11
yeh ..
i got it installed..
thnx for ur help friends..

now while opening the oracle sql developer and trying to add a database connection,
the error msg is:

Status: Failure-Test Failed: IO error: The network adapter could not establish the connection.

I gave the connection name as "HR" ,username and password, but test is not successful..:(
what might be the problem?

---

### Post by Sergio.G on 2011-10-11
Hi,

glad you made it work!


When you create the connection, what connection type are you using?
Basic or TNS?

Other thoughts...

Is the database installed on the same machine?

If you have an oracle client on the same machine as SQL Developer, try from the command line

tnsping <service>

Also, check if the database is up and running. Check if the database listener is up or not typing the next command

lsnrctl
lsnrctl> status listener_name

You might also try to 

ping <host>
 
or

telnet <host 1521>


Hope it leads you in the right direction
Cheers!

---

### Post by devika94 on 2011-10-12
no...:(
i dont get it..

when i tried a localhost connection, it shows the 17002 error : network adapter could not establish the connection

when TNS is tried instead of basic , it shows the error "no ocijdbc11 in java.library.path"
unless i get this database connection , i cant open a worksheet in sql..

what might be the problem? 
plz help...:confused:

---

### Post by Sergio.G on 2011-10-12
Hi, 

Did you check if the database listener is up and running?

Where is this database installed?
Locally?
Network?

Cheers.

---

### Post by devika94 on 2011-10-14
thnx.. :)
i got it now!! :)

---

### Post by Sergio.G on 2011-10-14
That is great, thanks for letting us know!

Would you be so kind to share with the rest of the community your findings and how you solved it, 
just as a reference in case there are others with similar issues

And also don't forget to mark the thread as solved  :)

Thank you!

Cheers!

---

