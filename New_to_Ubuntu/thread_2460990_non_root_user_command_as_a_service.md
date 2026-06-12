---
title: "non root user command as a service"
date: 2021-04-22
forum: New to Ubuntu
---

### Post by bmalik on 2021-04-22
I have a command to create backup file for sql server 
```

sqlcmd -S localhost -U SA -P lhr_lon_tt258 -Q "BACKUP DATABASE [Core] TO DISK = N'/var/opt/mssql/data/corebackup/core.bak' WITH NOFORMAT, NOINIT, NAME = 'Core-full', SKIP, NOREWIND, NOUNLOAD, STATS = 10"
```. It create a back up file. But now i want to run this command as service, when i create a service and start that service it is not getting run successfully. Service code is also given below
```


[Unit]
Description=start sqlbackup service


[Service]
Type=simple
ExecStart=/home/thingtrax/Downloads/DockerCompose_localserver/DockerCompose/Backup_script/sqlbackup.sh
Restart=on-failure
RestartSec=30s
StandardOutput=null


[Install]
WantedBy=multi-user.target
```

---

### Post by TheFu on 2021-04-22
Perhaps running it from the root crontab would be better?  That would be how most people did something like this.
As for running as a different userid, that's been standard Unix stuff since 1970.

[http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) should have an example. 

In these forums, we are sorta not supposed to show the old-school command that is used to switch to other userids, though I think this use would be fine, even necessary.  **su - {other-userid} -c {command}** is the command.  The manpage for su has lots of details and caveats. It is worth a read or re-re-read. 

The main crontab in /etc/crontab even has a field where we can specify the userid to be used when running tasks from that file. A useful template/comments for THAT crontabs:
```
# .---------------- minute (0 - 59)
# |  .------------- hour (0 - 23)
# |  |  .---------- day of month (1 - 31)
# |  |  |  .------- month (1 - 12) OR jan,feb,mar,apr ...
# |  |  |  |  .---- day of week (0 - 6) (Sunday=0 or 7) OR sun,mon,tue,wed,thu,fri,sat
# |  |  |  |  |
# *  *  *  *  * user-name /path/to/command  --arg1 --arg2 file1 file2 > /var/log/log.file 2>&1
```
Other crontabs don't have a userid specified.

First, please make your script better, more exact, and easier to read. 
There are lots of assumptions that just can't be made in this:
```
sqlcmd -S localhost -U SA -P lhr_lon_tt258 -Q "BACKUP DATABASE [Core] TO DISK = N'/var/opt/mssql/data/corebackup/core.bak' WITH NOFORMAT, NOINIT, NAME = 'Core-full', SKIP, NOREWIND, NOUNLOAD, STATS = 10"

```
[https://blog.jdpfu.com/2014/04/01/linux-troubleshooting-101-scripting](https://blog.jdpfu.com/2014/04/01/linux-troubleshooting-101-scripting) lists some things your script is doing.
BTW, almost everyone violates those rules when they are just starting with a new script.  The first 2 of the list are CRITICAL for anything running under different userids and automatically started.

Having you work through the issues will help the learning "stick".
[LIST]
[*]Never trust the PATH. PATH works the same on all platforms. Specify the /full/path/to/any/command used.
[*]Never believe all environment variables have been set outside the current script. If you need any, set them. Period.
[*]The script assumes a specific shell for a userid. It shouldn't.  The first line of all scripts need to speficy the interpreter to be used. 
[/LIST]
Probably want:
```
#!/bin/bash
```
But any scripting language can be used - perl, sh, ksh, python, php, ruby, or 50+ others. Do not assume.

Regardless - using a crontab or starting from a service-unit under systemd - the information above applies.

---

