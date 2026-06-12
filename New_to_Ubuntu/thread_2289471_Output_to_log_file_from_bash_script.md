---
title: "Output to log file from bash script"
date: 2015-08-04
forum: New to Ubuntu
---

### Post by CrewDK on 2015-08-04
Hi. I have this simple script: 

```
#!/bin/bash

timestamp=`date "+%Y.%m.%d %H:%M:%S"`

echo -e "\n*******************\n${timestamp}\n*******************\n" >> /home/crew/lftp.log
lftp -e 'mirror / /var/www/nod/www/; bye;' ftp://user:pass@host/ >> /home/crew/lftp.log 2>&1
```

and 

```
/home/crew # ls -l
total 12
-rwxr--r-- 1 crew crew  341 &#1072;&#1074;&#1075;.   4 17:41 lftp_crewdk.sh
-rw-rw-rw- 1 crew crew 1036 &#1072;&#1074;&#1075;.   4 17:54 lftp.log
```

If I running this script manualy - everything I want write to log file. But if I put this script to cron - i cant see output from lftp command, only "echo" with timestamp. 

```
cat /home/crew/lftp.log
*******************
2015.08.04 17:45:48
*******************

cd ok, cwd=/
Total: 1 directory, 12 files, 0 symlinks
To be removed: 3 directories, 0 files, 0 symlinks

*******************
2015.08.04 17:46:01
*******************


*******************
2015.08.04 17:48:01
*******************


*******************
2015.08.04 17:50:01
*******************


*******************
2015.08.04 17:50:53
*******************

cd ok, cwd=/
Total: 1 directory, 12 files, 0 symlinks
To be removed: 3 directories, 0 files, 0 symlinks

*******************
2015.08.04 17:52:01
*******************


*******************
2015.08.04 17:54:01
*******************


*******************
2015.08.04 17:56:01
*******************


```

What i'm doing wrong?

---

### Post by ruzekle on 2015-08-04
Have you looked at your enivornments? I haven't used cron to run tasks yet, but let me know if this helps.

[http://stackoverflow.com/questions/18885135/running-bash-script-in-cron](http://stackoverflow.com/questions/18885135/running-bash-script-in-cron)

---

### Post by matt_symes on 2015-08-04
Hi

Try using the full path to lftp in the script.

As suggested, this is almost certainly an evvironment issue and cron will not have your PATH variable.

Kind regards

---

### Post by CrewDK on 2015-08-04
OK. I tried to add  PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin into  my script and cron. But this didn't work. lftp works but without output  to my logfile. :sad: 
Also i tried use full path with lftp so my script now looks like: 

```
#!/bin/bash

PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin

timestamp=`date "+%Y.%m.%d %H:%M:%S"`
echo -e "\n*******************\n${timestamp}\n*******************\n" >> ~/logs/nod.log
/usr/bin/lftp -e 'mirror / /var/www/nod/www/; bye;' ftp://user:pass@host/ >> /root/logs/nod.log 2>&1
```

but still there is no any output to file from lftp. :(

---

### Post by matt_symes on 2015-08-04
Hi

Why is your log file location different between your first and third post ?

Are you running under root or your own cron tab ?

Kind regards

---

### Post by CrewDK on 2015-08-05
Well, I tried different ways to solve this problem - change owners, place, rights  of log and script itself. And even I tried to run this script in cron from other user: 

crontab -e
```
*/1 * * * *     su crew -c /home/crew/nod_crewdk.sh
```

But result is always the same - I can see output from echo, but not from lftp :(
And yes, i added this task to cron from root user with crontab -e command. 
How can this be possible?!

---

### Post by matt_symes on 2015-08-05
Hi

I'm a bit lost as to what you currently have in your script and what is in your crontab at the moment. You may want to repost them.

Anyway, try moving the stdout and stderr redirect to the crontab entry and remove from the script itself. Use the absolute path for the log file.

Do you really want to be running the script every minute ?

Kind regards

---

### Post by CrewDK on 2015-08-06
> **matt_symes said:**
> Hi

I'm a bit lost as to what you currently have in your script and what is in your crontab at the moment. You may want to repost them.



Well, now it looks like this: 

```
# cat /root/sh/nod_crewdk.sh 
#!/bin/sh 

timestamp=`date "+%Y.%m.%d %H:%M:%S"`

echo "\n*******************\n${timestamp}\n*******************\n" >> /root/logs/nod.log
lftp -e 'mirror / /var/www/nod/www/; bye;' ftp://user:pass@host/ >> /root/logs/nod.log
```

```
# cat /var/spool/cron/crontabs/root 
*/2 * * * *     /root/sh/nod_crewdk.sh

```

```
# ls -l /root/logs/
total 16
-rw-rw-rw- 1 root root     0 &#1072;&#1074;&#1075;.   6 00:00 cureit.log
-rw-rw-rw- 1 root root 12260 &#1072;&#1074;&#1075;.   6 20:20 nod.log
```

> **matt_symes said:**
> 

Anyway, try moving the stdout and stderr redirect to the crontab entry  and remove from the script itself. Use the absolute path for the log  file.



Already tried all of this. Result is always the same - if script running by cron - there isn't any output from lftp in my logfile. 

> **matt_symes said:**
> 
Do you really want to be running the script every minute ?


It's only for testing.

---

### Post by matt_symes on 2015-08-06
Hi

Is lftp realising, when starting, that it's not connected to an interactive terminal and so closing fd1 and fd2 ?

Looks to me that what you have should be working so have you looked at the man page and docs for lftp to see if there are any hints in there ? 

Is there a switch to log to a file like wget ?

Can you substitute wget or something else for lftp using some switch to log to a file instead of redirection and try that to see if it will log correctly ?

Kind regards

---

### Post by steeldriver on 2015-08-06
I notice in your latest version you are no longer redirecting standard error, only just standard output - you might want to re-add the [FONT=courier new]2>&1[/FONT] just for the sake of completeness

---

### Post by matt_symes on 2015-08-06
Hi

I think that lftp is itself not logging to stdout and stderr when run from a non interactive terminal. It may even close stdin. It would not be the first program to do this.

An strace of lftp filtered on file commands may be enlightening here when run under and out of cron.

But try substituting something in place of lftp first.

EDIT: I should really be saying a "non interactive shell" and not terminal but I think you know what I mean.


Kind regards

---

### Post by Keith_Helms on 2015-08-08
Try changing your lftp command to use the -c option instead of -e.  The man page says for -e "Execute given commands and don't exit.".  For the -c option it says "Execute the given commands and exit.".

As another post mentioned, it could be that lftp is not closing the standard output and if it is set to "not exit", that could be the case.

---

### Post by matt_symes on 2015-08-08
Hi

> **Keith_Helms said:**
> Try changing your lftp command to use the -c option instead of -e.  The man page says for -e "Execute given commands and don't exit.".  For the -c option it says "Execute the given commands and exit.".

As another post mentioned, it could be that lftp is not closing the standard output and if it is set to "not exit", that could be the case.

This is also an excellent idea and may well be correct.

I thought it may be closing stdout and err but maybe it's keeping them open, just buffering the text and as lftp is never closing due to the -e switch, it's never getting written to the file.

I am convinced it's lftp however having never used it, I cannot give any definitive answers; only suggestions.

@OP do you have many instances of lftp running in top if you run your from cron once a minute for 10 minutes ?


@OP. Any feedback on this. I'm really interested in what is going on :)

Kind regards

---

### Post by CrewDK on 2015-08-09
I'm sorry. I was far from my PC so couldn't reply to you all. 
I'll try everything tomorrow morning :)

---

### Post by CrewDK on 2015-08-11
> **matt_symes said:**
> Hi

I think that lftp is itself not logging to stdout and stderr when run from a non interactive terminal. It may even close stdin. It would not be the first program to do this.

An strace of lftp filtered on file commands may be enlightening here when run under and out of cron.

But try substituting something in place of lftp first.

EDIT: I should really be saying a "non interactive shell" and not terminal but I think you know what I mean.


Looks like that. :( Because i tried run wget in this script and everythig is ok. I got all output and from echo, and from wget. 

> Keith_Helms[INDENT]Try changing your lftp command to use the -c option instead of -e.   The man page says for -e "Execute given commands and don't exit.".  For  the -c option it says "Execute the given commands and exit.".

As another post mentioned, it could be that lftp is not closing the  standard output and if it is set to "not exit", that could be the case.         
[/INDENT]
    


lftp gave me this errorr when i trying to run it with -c options. 

```
Unknown command `mirror /test/ /var/www/nod/www/; bye;'.
```

Allmighty man tells us that: 

```
       -c commands
              Execute  the given commands and exit. Commands can be separated with a semicolon, `&&' or `||'. Remember to quote the commands argument properly in the shell.  **This option must be used alone without other arguments**.
```

As i understand it means that i must set all options in /etc/lftp.conf file and there can be only one set of options. :( 

> @OP do you have many instances of lftp running in top if you run your from cron once a minute for 10 minutes ?

Noop. All instances closed after they done its work. 

Now i have at least working solution: 

```
#!/bin/bash

timestamp=`date "+%Y.%m.%d %H:%M:%S"`
login="user"
pass="pass"
host="host"
remote_dir="/"
local_dir="/var/www/nod/www/nod/"
#log_file="/tmp/lftp-mirror.log"
log_file="/home/crew/logs/nod_${timestamp}.log"


trap "rm -f /tmp/lftp-mirror.lock" SIGINT SIGTERM
if [ -e /tmp/lftp-mirror.lock ]
then
echo "mirror is running already, rm /tmp/lftp-mirror.lock if this is false."
exit 1
else
touch /tmp/mirror
lftp -u $login,$pass ftp://$host << EOF
mirror --delete --continue --parallel=5 --log="$log_file" $remote_dir $local_dir
quit
EOF
rm -f /tmp/lftp-mirror.lock
trap - SIGINT SIGTERM
sed -i 's/%20/ /g' "${log_file}"
exit 0
fi
```

Yeah. I have tooooo many logs in my log dir even if i run it only every 30 mins. But at least i can know now when and what lftp done.

---

