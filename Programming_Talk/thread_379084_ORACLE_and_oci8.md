---
title: "ORACLE and oci8"
date: 2007-03-08
forum: Programming Talk
---

### Post by buFka on 2007-03-08
Hi,
I have a problem with oci8. I installed ORACLE Enterprise with php5 and apache, with this script :

<?php phpinfo(); ?>

I receive information for the set modules. I see that oci8 is enabled however ORACLE_HOME is empty. Additionally, I tried to write a little script which I run as a root. Due to this script, I set variables and start apache:

cmd=`which apache2ctl`
$cmd stop
ORACLE_HOME=/u01/app/oracle/oracle/product/10.2.0/db_1;export ORACLE_HOME
echo ORACLE_HOME: $ORACLE_HOME
ORACLE_SID=orcl; export ORACLE_SID
echo ORACLE_SID: $ORACLE_SID
ORATAB=/etc/oratab; export ORATAB
echo ORATAB: $ORATAB
ORACLE_HOME_LISTNER=$ORACLE_BASE, export ORACLE_HOME_LISTNER
echo ORACLE_HOME_LISTNER: $ORACLE_HOME_LISTNER
ORACLE_BASE=$ORACLE_HOME; export ORACLE_BASE
echo ORACLE_BASE: $ORACLE_BASE
NLS_LANG=AMERICAN_AMERICA.WE8ISO8859P15; export NLS_LANG
echo NLS_LANG: $NLS_LANG
LD_LIBRARY_PATH=$ORACLE_HOME/lib; export LD_LIBRARY_PATH
echo LD_LIBRARY_PATH: $LD_LIBRARY_PATH
LD_PRELOAD=/u01/app/oracle/oracle/product/10.2.0/db_1/lib/libclntsh.so
echo LD_PRELOAD:$LD_PRELOAD
$cmd start

In /etc/php5/apache2/php.ini and /etc/php5/cli/php.ini I set the extension=oci8.s&#1086;, but ORACLE_HOME is still empty (see here [http://www.picvalley.net/u/9/8466_726.PNG](http://www.picvalley.net/u/9/8466_726.PNG))

If someone has an idea how to solve the problem, I will highly appreciate any advices with this regard. I read about an installation of ORACLE Instant client and oci8 but I do not know whether I need this instant client at all, because I use Oracle Enterprise.

PS. i'm sorry for the bad english, i can't explain the problem better.

---

### Post by buFka on 2007-03-08
up!

---

