---
title: "About KMail"
date: 2016-10-23
forum: New to Ubuntu
---

### Post by usuha on 2016-10-23
Hello.
I'm using Lubuntu 16.10.
When I start the KMail, I get the following error message.
Will there is a method to improve.
Thank you.

```
Akonadi Server Self-Test Report
===============================
 
Test 1:  SUCCESS
--------
 
Database driver found.
Details: The QtSQL driver 'QMYSQL' is required by your current Akonadi server configuration and was found on your system.
 
File content of '/home/pure/.config/akonadi/akonadiserverrc':
[%General]
Driver=QMYSQL
 
[QMYSQL]
Host=
Name=akonadi
Options="UNIX_SOCKET=/tmp/akonadi-pure.3GdUKd/mysql.socket"
ServerPath=/usr/sbin/mysqld-akonadi
StartServer=true
 
 
Test 2:  SUCCESS
--------
 
Akonadi is not running as root
Details: Akonadi is not running as a root/administrator user, which is the recommended setup for a secure system.
 
Test 3:  SUCCESS
--------
 
MySQL server found.
Details: You have currently configured Akonadi to use the MySQL server '/usr/sbin/mysqld-akonadi'.
Make sure you have the MySQL server installed, set the correct path and ensure you have the necessary read and execution rights on the server executable. The server executable is typically called 'mysqld'; its location varies depending on the distribution.
 
Test 4:  SUCCESS
--------
 
MySQL server is executable.
Details: MySQL server found: /usr/sbin/mysqld  Ver 5.7.15-0ubuntu2 for Linux on x86_64 ((Ubuntu))
 
 
Test 5:  SUCCESS
--------
 
No current MySQL error log found.
Details: The MySQL server did not report any errors during this startup. The log can be found in '/home/pure/.local/share/akonadi/db_data/mysql.err'.
 
Test 6:  SUCCESS
--------
 
MySQL server default configuration found.
Details: The default configuration for the MySQL server was found and is readable at <a href="/etc/xdg/akonadi/mysql-global.conf">/etc/xdg/akonadi/mysql-global.conf</a>.
 
File content of '/etc/xdg/akonadi/mysql-global.conf':
#
# Global Akonadi MySQL server settings,
# These settings can be adjusted using $HOME/.config/akonadi/mysql-local.conf
#
# Based on advice by Kris Köhntopp <kris@mysql.com>
#
[mysqld]
 
# strict query parsing/interpretation
# TODO: make Akonadi work with those settings enabled
# sql_mode=strict_trans_tables,strict_all_tables,strict_error_for_division_by_zero,no_auto_create_user,no_auto_value_on_zero,no_engine_substitution,no_zero_date,no_zero_in_date,only_full_group_by,pipes_as_concat
# sql_mode=strict_trans_tables
 
# DEBUGGING:
# log all queries, useful for debugging but generates an enormous amount of data
# log=mysql.full
# log queries slower than n seconds, log file name relative to datadir (for debugging only)
# log_slow_queries=mysql.slow
# long_query_time=1
# log queries not using indices, debug only, disable for production use
# log_queries_not_using_indexes=1
#
# mesure database size and adjust innodb_buffer_pool_size
# SELECT sum(data_length) as bla, sum(index_length) as blub FROM information_schema.tables WHERE table_schema not in ("mysql", "information_schema");
 
# NOTES:
# Keep Innob_log_waits and keep Innodb_buffer_pool_wait_free small (see show global status like "inno%", show global variables)
 
#expire_logs_days=3
 
#sync_bin_log=0
 
# Use UTF-8 encoding for tables
character_set_server=utf8
collation_server=utf8_general_ci
 
# use InnoDB for transactions and better crash recovery
default_storage_engine=innodb
 
# memory pool InnoDB uses to store data dictionary information and other internal data structures (default:8M)
# Deprecated in MySQL >= 5.6.3, removed in 5.7 (works in MariaDB)
# innodb_additional_mem_pool_size=8M
 
# memory buffer InnoDB uses to cache data and indexes of its tables (default:128M)
# Larger values means less I/O
innodb_buffer_pool_size=80M
 
# Create a .ibd file for each table (default:0)
innodb_file_per_table=1
 
# Write out the log buffer to the log file at each commit (default:1)
innodb_flush_log_at_trx_commit=2
 
# Buffer size used to write to the log files on disk (default:1M for builtin, 8M for plugin)
# larger values means less I/O
innodb_log_buffer_size=1M
 
# Size of each log file in a log group (default:5M) larger means less I/O but more time for recovery.
innodb_log_file_size=64M
 
# # error log file name, relative to datadir (default:hostname.err)
log_error=mysql.err
 
# print warnings and connection errors (default:1)
log_warnings=2
 
# Convert table named to lowercase
lower_case_table_names=1
 
# Maximum size of one packet or any generated/intermediate string. (default:1M)
max_allowed_packet=32M
 
# Maximum simultaneous connections allowed (default:100)
max_connections=256
 
# The two options below make no sense with prepared statements and/or transactions
# (make sense when having the same query multiple times)
 
# Memory allocated for caching query results (default:0 (disabled))
query_cache_size=0
 
# Do not cache results (default:1)
query_cache_type=0
 
# Do not use the privileges mechanisms
skip_grant_tables
 
# Do not listen for TCP/IP connections at all
skip_networking
 
# The number of open tables for all threads. (default:64)
table_open_cache=200
 
# How many threads the server should cache for reuse (default:0)
thread_cache_size=3
 
# wait 365d before dropping the DB connection (default:8h)
wait_timeout=31536000
 
# We use InnoDB, so don't let MyISAM eat up memory
key_buffer_size=16K
 
[client]
default-character-set=utf8
 
 
Test 7:  SKIP
--------
 
MySQL server custom configuration not available.
Details: The custom configuration for the MySQL server was not found but is optional.
 
Test 8:  SUCCESS
--------
 
MySQL server configuration is usable.
Details: The MySQL server configuration was found at <a href="/home/pure/.local/share/akonadi/mysql.conf">/home/pure/.local/share/akonadi/mysql.conf</a> and is readable.
 
File content of '/home/pure/.local/share/akonadi/mysql.conf':
#
# Global Akonadi MySQL server settings,
# These settings can be adjusted using $HOME/.config/akonadi/mysql-local.conf
#
# Based on advice by Kris Köhntopp <kris@mysql.com>
#
[mysqld]
 
# strict query parsing/interpretation
# TODO: make Akonadi work with those settings enabled
# sql_mode=strict_trans_tables,strict_all_tables,strict_error_for_division_by_zero,no_auto_create_user,no_auto_value_on_zero,no_engine_substitution,no_zero_date,no_zero_in_date,only_full_group_by,pipes_as_concat
# sql_mode=strict_trans_tables
 
# DEBUGGING:
# log all queries, useful for debugging but generates an enormous amount of data
# log=mysql.full
# log queries slower than n seconds, log file name relative to datadir (for debugging only)
# log_slow_queries=mysql.slow
# long_query_time=1
# log queries not using indices, debug only, disable for production use
# log_queries_not_using_indexes=1
#
# mesure database size and adjust innodb_buffer_pool_size
# SELECT sum(data_length) as bla, sum(index_length) as blub FROM information_schema.tables WHERE table_schema not in ("mysql", "information_schema");
 
# NOTES:
# Keep Innob_log_waits and keep Innodb_buffer_pool_wait_free small (see show global status like "inno%", show global variables)
 
#expire_logs_days=3
 
#sync_bin_log=0
 
# Use UTF-8 encoding for tables
character_set_server=utf8
collation_server=utf8_general_ci
 
# use InnoDB for transactions and better crash recovery
default_storage_engine=innodb
 
# memory pool InnoDB uses to store data dictionary information and other internal data structures (default:8M)
# Deprecated in MySQL >= 5.6.3, removed in 5.7 (works in MariaDB)
# innodb_additional_mem_pool_size=8M
 
# memory buffer InnoDB uses to cache data and indexes of its tables (default:128M)
# Larger values means less I/O
innodb_buffer_pool_size=80M
 
# Create a .ibd file for each table (default:0)
innodb_file_per_table=1
 
# Write out the log buffer to the log file at each commit (default:1)
innodb_flush_log_at_trx_commit=2
 
# Buffer size used to write to the log files on disk (default:1M for builtin, 8M for plugin)
# larger values means less I/O
innodb_log_buffer_size=1M
 
# Size of each log file in a log group (default:5M) larger means less I/O but more time for recovery.
innodb_log_file_size=64M
 
# # error log file name, relative to datadir (default:hostname.err)
log_error=mysql.err
 
# print warnings and connection errors (default:1)
log_warnings=2
 
# Convert table named to lowercase
lower_case_table_names=1
 
# Maximum size of one packet or any generated/intermediate string. (default:1M)
max_allowed_packet=32M
 
# Maximum simultaneous connections allowed (default:100)
max_connections=256
 
# The two options below make no sense with prepared statements and/or transactions
# (make sense when having the same query multiple times)
 
# Memory allocated for caching query results (default:0 (disabled))
query_cache_size=0
 
# Do not cache results (default:1)
query_cache_type=0
 
# Do not use the privileges mechanisms
skip_grant_tables
 
# Do not listen for TCP/IP connections at all
skip_networking
 
# The number of open tables for all threads. (default:64)
table_open_cache=200
 
# How many threads the server should cache for reuse (default:0)
thread_cache_size=3
 
# wait 365d before dropping the DB connection (default:8h)
wait_timeout=31536000
 
# We use InnoDB, so don't let MyISAM eat up memory
key_buffer_size=16K
 
[client]
default-character-set=utf8
 
 
Test 9:  SUCCESS
--------
 
akonadictl found and usable
Details: The program '/usr/bin/akonadictl' to control the Akonadi server was found and could be executed successfully.
Result:
Akonadi 5.2.2
 
 
Test 10:  ERROR
--------
 
Akonadi control process not registered at D-Bus.
Details: The Akonadi control process is not registered at D-Bus which typically means it was not started or encountered a fatal error during startup.
 
Test 11:  ERROR
--------
 
Akonadi server process not registered at D-Bus.
Details: The Akonadi server process is not registered at D-Bus which typically means it was not started or encountered a fatal error during startup.
 
Test 12:  SKIP
--------
 
Protocol version check not possible.
Details: Without a connection to the server it is not possible to check if the protocol version meets the requirements.
 
Test 13:  ERROR
--------
 
No resource agents found.
Details: No resource agents have been found, Akonadi is not usable without at least one. This usually means that no resource agents are installed or that there is a setup problem. The following paths have been searched: '/usr/share/akonadi/agents'. The XDG_DATA_DIRS environment variable is set to '/etc/xdg/lubuntu:/usr/local/share:/usr/share:/usr/share/gdm:/var/lib/menu-xdg:/usr/share/Lubuntu:/usr/local/share/:/usr/share/:/var/lib/snapd/desktop'; make sure this includes all paths where Akonadi agents are installed.
 
Directory listing of '/usr/share/akonadi/agents':
akonotesresource.desktop
archivemailagent.desktop
birthdaysresource.desktop
contactsresource.desktop
davgroupwareresource.desktop
followupreminder.desktop
googlecalendarresource.desktop
googlecontactsresource.desktop
icaldirresource.desktop
icalresource.desktop
imapresource.desktop
invitationsagent.desktop
kalarmdirresource.desktop
kalarmresource.desktop
kolabresource.desktop
maildirresource.desktop
maildispatcheragent.desktop
mailfilteragent.desktop
mboxresource.desktop
migrationagent.desktop
mixedmaildirresource.desktop
newmailnotifieragent.desktop
notesresource.desktop
openxchangeresource.desktop
pop3resource.desktop
sendlateragent.desktop
vcarddirresource.desktop
vcardresource.desktop
 
Environment variable XDG_DATA_DIRS is set to '/etc/xdg/lubuntu:/usr/local/share:/usr/share:/usr/share/gdm:/var/lib/menu-xdg:/usr/share/Lubuntu:/usr/local/share/:/usr/share/:/var/lib/snapd/desktop'
 
Test 14:  ERROR
--------
 
Current Akonadi server error log found.
Details: The Akonadi server reported errors during its current startup. The log can be found in <a href="/home/pure/.local/share/akonadi/akonadiserver.error">/home/pure/.local/share/akonadi/akonadiserver.error</a>.
 
File content of '/home/pure/.local/share/akonadi/akonadiserver.error':
Database process exited unexpectedly during initial connection! 
executable: "/usr/sbin/mysqld-akonadi" 
arguments: ("--defaults-file=/home/pure/.local/share/akonadi/mysql.conf", "--datadir=/home/pure/.local/share/akonadi/db_data/", "--socket=/tmp/akonadi-pure.3GdUKd/mysql.socket") 
stdout: "" 
stderr: "mysqld: Error on realpath() on '/var/lib/mysql-files' (Error 2 - No such file or directory)\n2016-10-23T08:04:33.261279Z 0 [Warning] The syntax '--log_warnings/-W' is deprecated and will be removed in a future release. Please use '--log_error_verbosity' instead.\n2016-10-23T08:04:33.261359Z 0 [Warning] TIMESTAMP with implicit DEFAULT value is deprecated. Please use --explicit_defaults_for_timestamp server option (see documentation for more details).\n2016-10-23T08:04:33.261484Z 0 [ERROR] Failed to access directory for --secure-file-priv. Please make sure that directory exists and is accessible by MySQL Server. Supplied value : /var/lib/mysql-files\n2016-10-23T08:04:33.261495Z 0 [ERROR] Aborting\n\n2016-10-23T08:04:33.261511Z 0 [Note] Binlog end\n" 
exit code: 1 
process error: "Unknown error" 
Failed to remove Unix socket 
Failed to remove runtime connection config file 
 
 
Test 15:  ERROR
--------
 
Previous Akonadi server error log found.
Details: The Akonadi server reported errors during its previous startup. The log can be found in <a href="/home/pure/.local/share/akonadi/akonadiserver.error.old">/home/pure/.local/share/akonadi/akonadiserver.error.old</a>.
 
File content of '/home/pure/.local/share/akonadi/akonadiserver.error.old':
Database process exited unexpectedly during initial connection! 
executable: "/usr/sbin/mysqld-akonadi" 
arguments: ("--defaults-file=/home/pure/.local/share/akonadi/mysql.conf", "--datadir=/home/pure/.local/share/akonadi/db_data/", "--socket=/tmp/akonadi-pure.3GdUKd/mysql.socket") 
stdout: "" 
stderr: "mysqld: Error on realpath() on '/var/lib/mysql-files' (Error 2 - No such file or directory)\n2016-10-23T07:48:15.637359Z 0 [Warning] The syntax '--log_warnings/-W' is deprecated and will be removed in a future release. Please use '--log_error_verbosity' instead.\n2016-10-23T07:48:15.637439Z 0 [Warning] TIMESTAMP with implicit DEFAULT value is deprecated. Please use --explicit_defaults_for_timestamp server option (see documentation for more details).\n2016-10-23T07:48:15.637527Z 0 [ERROR] Failed to access directory for --secure-file-priv. Please make sure that directory exists and is accessible by MySQL Server. Supplied value : /var/lib/mysql-files\n2016-10-23T07:48:15.637536Z 0 [ERROR] Aborting\n\n2016-10-23T07:48:15.637596Z 0 [Note] Binlog end\n" 
exit code: 1 
process error: "Unknown error" 
Failed to remove Unix socket 
Failed to remove runtime connection config file 
 
 
Test 16:  SUCCESS
--------
 
No current Akonadi control error log found.
Details: The Akonadi control process did not report any errors during its current startup.
 
Test 17:  SUCCESS
--------
 
No previous Akonadi control error log found.
Details: The Akonadi control process did not report any errors during its previous startup.

```

---

### Post by adampdistefano on 2016-11-09
I had the exact problem today. I was able to resolve it by installing mysql-server

```
sudo apt-get install mysql-server
```

cheers

---

