---
title: "freetds.conf settings not picked up by PHP"
date: 2010-05-24
forum: Programming Talk
---

### Post by benvogan on 2010-05-24
Hello All,

I am trying to get freetds up and running in PHP 5.3.2 on Apache 2.2.14. I have downloaded the latest freetds snapshot and ./configured it.  Using tsql I am able to connect to my SQL Server instance using the -S option so it appears that freetds is recognizing the server configuration (and that SQL Server is configured properly to accept the connect).  However, when I try to call mssql_connect in PHP with the alias for my server it fails (no error message, it just returns false).  When I specify the DNS name for the server then mssql_connect call works just fine and I am able to run queries without an issue.  

I tried editing the freetds.conf file to turn on logging but no log file appears in the /tmp directory.  I also tried explicity setting the TDSDUMP and TDSDUMPCONFIG environment variables but the log files are not created when I call mssql_connect from my PHP page.  I also tried setting the FREETDS environment variable to point to my freetds.conf file without success.

Getting the PHP info from the webserver shows under a mssql heading:
Active Persisten Links 0
Active Links 0
Library version FreeTDS

Directive Local Value Master Value
mssql.allow_persistent	On	On
mssql.batchsize	0	0
mssql.charset	no value	no value
mssql.compatability_mode	Off	Off
mssql.connect_timeout	5	5
mssql.datetimeconvert	On	On
mssql.max_links	Unlimited	Unlimited
mssql.max_persistent	Unlimited	Unlimited
mssql.max_procs	Unlimited	Unlimited
mssql.min_error_severity	10	10
mssql.min_message_severity	10	10
mssql.secure_connection	Off	Off
mssql.textlimit	Server default	Server default
mssql.textsize	Server default	Server default
mssql.timeout	60	60

Any help would be greatly appreciated.

Thanks,
--Ben

---

