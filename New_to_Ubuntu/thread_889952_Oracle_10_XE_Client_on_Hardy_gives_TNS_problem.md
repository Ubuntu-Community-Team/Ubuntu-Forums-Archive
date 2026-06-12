---
title: "Oracle 10 XE Client on Hardy gives TNS problem"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by PapaGuru on 2008-08-14
Hi,

I've installed Oracle 10 XE Universal on my Ubuntu 8.04.1 LTS Desktop i386, and it's working pretty well, now.
What I've done so far:
Added the following repository to Synaptic Package Manager:
```
deb http://oss.oracle.com/debian unstable main non-free
```
I refreshed the package list, and then selected the following packages 
```
oracle-xe-client
oracle-xe-universal
```
and hit apply.
This gives a few warnings of the type that it's unsigned and potentially malicious, but I ignored that. Later I learned that with
```
wget http://oss.oracle.com/el4/RPM-GPG-KEY-oracle  -O- | sudo apt-key add - 
```
I could have resolved that. Ah well.
Then I configured Oracle via
```
papaguru@ubuntu:~$ /etc/init.d/oracle-xe configure
```
and I could access the console via
```
http://127.0.0.1:8080/apex
```
(same as Applications > Oracle Database 10g Express Edition > Go To Database Home Page)
*[Insert small leap of joy here]*
Connecting to the database via SQL*Plus did not work however. That gave errors like:
```
/usr/lib/oracle/xe/app/oracle/product/10.2.0/server/bin/nls_lang.sh: 114: [[: not found
```
and
```
ORA-12154: TNS:could not resolve service name
```
and
```
ORA-12162 TNS:net service name is incorrectly specified

```
The first error was easily solved, by editing the nls_lang.sh file. Around line 114, that says:
```
if [[ -n "$LC_ALL" ]]; then
locale=$LC_ALL
elif [[ -n "$LANG" ]]; then
```
Simply replace the double square brackets by single ones, and the error wil disappear. (Alternatively, you allegedly can change the first line from ```
#!/bin/sh
``` to ```
#!/bin/bash
```. Whatever.) For good measure I also replaced the double brackets in /usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/nls_lang.sh.

To solve the TNS problems there was a tip to replace the curved single quotes in oracle_env.sh with straight ones, so I did (both in server and client). That changed the color of the text in between the quotes to [COLOR="Magenta"]pink[/COLOR] in gedit, but it did not solve the problem.

So next I tried some tips on setting system variables:
```
export PATH=$PATH:/usr/lib/oracle/xe/app/oracle/product/10.2.0/server/bin/
export ORACLE_HOME=/usr/lib/oracle/xe/app/oracle/product/10.2.0/server

```
and
```
. /usr/lib/oracle/xe/app/oracle/product/10.2.0/server/bin/oracle_env.sh
```
To no avail.
The odd thing is that starting SQL*Plus from a terminal prompt gives a different error that starting SQL*Plus via Applications > Oracle Client 10g Express Edition > Run SQL Command Line.
The first gives:
```
SQL*Plus: Release 10.2.0.1.0 - Production on Thu Aug 14 21:36:34 2008

Copyright (c) 1982, 2005, Oracle.  All rights reserved.

ERROR:
ORA-12705: Cannot access NLS data files or invalid environment specified

```, while the second gives:
```
SQL*Plus: Release 10.2.0.1.0 - Production on Thu Aug 14 21:06:50 2008

Copyright (c) 1982, 2005, Oracle.  All rights reserved.

SQL> connect projects001
Enter password: 
ERROR:
ORA-12162: TNS:net service name is incorrectly specified

```

Naturally, I've checked my TNSNAMES.ORA and LISTENER.ORA, but they seem perfectly in order. Any further help is greatly appreciated.

---

### Post by Rodrigue on 2008-09-13
Hello,

Did you manage to solve this problem after all?  I'm having the same issue with a fresh install of Oracle on a Hardy vm.  When trying to log to Oracle via sql Plus, I get "ORA-12162:  TNS:net service name is incorrectly specified"

Thanks

---

### Post by plopke on 2008-10-20
:( i did everything you did also and still got the error like you. Found somewhere that the oracle user doesnt find the system variables :confused:?

---

### Post by donkeyX on 2008-12-16
I am having the same problem and have been having and cannot resolve it. I can connect to any of the databases in the tnsnames.ora with a full connection string but there seems to be some problem when trying to connect using the alias from sqlplus eg: 

user@hal:/usr/lib/oracle/oracle_client/network/admin$ sqlplus SYSADM@STUDD1

SQL*Plus: Release 10.2.0.1.0 - Production on Wed Dec 17 13:13:27 2008

Copyright (c) 1982, 2005, Oracle.  All rights reserved.

Enter password: 
ERROR:
ORA-12169: TNS:Net service name given as connect identifier is too long


Enter user-name: ^C
user@hal:/usr/lib/oracle/oracle_client/network/admin$ sqlplus STUDD1

SQL*Plus: Release 10.2.0.1.0 - Production on Wed Dec 17 13:13:46 2008

Copyright (c) 1982, 2005, Oracle.  All rights reserved.

Enter password: 
ERROR:
ORA-12162: TNS:net service name is incorrectly specified


Enter user-name: SYSADM
Enter password: 
ERROR:
ORA-12162: TNS:net service name is incorrectly specified


This is attempting a few alternatives but none work and here is the tns for that entry: 

STUDD1,STUDD1.WORLD =

  (DESCRIPTION =

    (ADDRESS = (PROTOCOL = TCP)(HOST = b19e01s01-vip)(PORT = 1521))

    (ADDRESS = (PROTOCOL = TCP)(HOST = b87e01s01-vip)(PORT = 1521))

    (LOAD_BALANCE = yes)

    (CONNECT_DATA =

      (SERVER = DEDICATED)

      (SERVICE_NAME = STUDD1.ntn.org.au)

      (FAILOVER_MODE =

        (TYPE = SELECT)

        (METHOD = BASIC)

        (RETRIES = 180)

        (DELAY = 5)

      )

    )

  )

---

### Post by josir on 2009-02-27
You have to set ORACLE_SID environment variable.
For example, edit /etc/profile

export ORACLE_SID=PROD1

If you guys have the environment set, please reply to tell if this solution works.

---

