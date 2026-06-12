---
title: "HOWTO - FTPStats on Feisty"
date: 2007-10-19
forum: Outdated Tutorials &amp; Tips
---

### Post by Dzs on 2007-10-19
[B][SIZE="5"]FTPSTATS - HOWTO
================[/SIZE][/B]

This howto will help you with installation and configuration ftp web statistics called FtpStats.



My server is running on Ubuntu Feisty, kernel version 2.6.20-9-generic.

Tested software configuration:
FTP server is Pure-ftpd-mysql v1.0.21 with configured MySQL authentication.
PHP is 5.2.1
MySQL is Ver 14.12 Distrib 5.0.38


So, let's start with some work instead of just talking bullsh*** :-D

At first we should install some dependencies for ftpstats:



	```
sudo apt-get install libdbd-mysql-perl libdbi-perl
```




In next step we must install getopt with help of our friend perl:


```

	perl -MCPAN -eshell

	install Getopt::Long

	exit

```

After that we need to edit file : /etc/pure-ftpd/conf/AltLog  where we replace the original row with the this one:

```

	Stats:/var/log/pure-ftpd/transfer.log

```


We should now download ftpstats packages from this web:


	[http://www.edmann.com/tech/ftpstats/](http://www.edmann.com/tech/ftpstats/)

We will need both of listed packages, version 8.8 and version 8.9 and follow instructions in README files included in 

packages.


After that we must edit file /etc/php5/apache2/php.ini to avoid lot of error messages on final site:

In file  we find :
```

	display_errors = on

```
and replace it with:
```

	display_errors = off

```

For automatic update of the web pages we should add to crontab this line:

```


	*/59    * * * * root    /path/where/you/have/ftpStats/MySQL/process-all-logs.sh


```



On some machines when you are populating data from log to ftpstats database, it can appear error similar to this one:

```

Reading /var/log/pure-ftpd/transfer1.log (480 lines).. DBD::mysql::st execute failed: Not unique table/alias: 	

'xfers' at /path/where/you/have/ftpStats/MySQL/ftpstats.pl line 250

MySQL error on:
CREATE TABLE xfers (
  xferID   MEDIUMINT UNSIGNED AUTO_INCREMENT PRIMARY KEY NOT NULL,
  Username CHAR(16) NOT NULL,
  xferTime DATETIME NOT NULL,
  xferDur  MEDIUMINT UNSIGNED NOT NULL,
  xferFile CHAR(255) NOT NULL,
  xferSize INT UNSIGNED NOT NULL,
  xferDirn ENUM('Up','Dn') NOT NULL,
  xferCmpl ENUM('COMP','INCM','ABOR','PERM','NENT','MISC'),
  xferIP   INT UNSIGNED NOT NULL
) ENGINE=MERGE 

UNION=(ftpstats.ftpstats.xfers_d272_2007,ftpstats.xfers_d273_2007,ftpstats.xfers_d279_2007,ftpstats.xfers_d280_2007,ftpstats

.xfers_d285_2007,ftpstats.xfers_d287_2007)
Returned:
You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to 

use near '.xfers_d272_2007,ftpstats.xfers_d273_2007,ftpstats.xfers_d279_2007,ftpstats.xfer' at line 11 (#1)
Added 0 transfers

```




So don't worry about that, this is very usual error, when you are using newer MySQL. This problem we will solve by editing 

file ftpstats.pl where we should need to find this:
```

	TYPE=MERGE

```
and replace it by:
```

	ENGINE=MERGE

```

in same file we find:

```

	# get a list of tables so we know what to create later
	$existing_tables = join ' ', $db_conn->tables;

```


and below this we add some new lines:

```

	# Fix for newer mysql versions removing
	$existing_tables =~ s/\`//g;

```

It should work now, in case of some problems first at all ask our very well known uncle google. :-)

I' hope that this HowTo is usefull at least for few of you.

---

