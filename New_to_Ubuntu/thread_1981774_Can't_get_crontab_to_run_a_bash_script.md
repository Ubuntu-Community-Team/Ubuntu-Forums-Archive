---
title: "Can't get crontab to run a bash script"
date: 2012-05-17
forum: New to Ubuntu
---

### Post by japhyr on 2012-05-17
I have been trying to get crontab to run a bash script.  I have checked all the common errors, and can't figure it out.  My crontab, which does end in a new line:
```
# m h  dom mon dow   command
* * * * * /home/username/development/cron_test/hello_sh.sh
* * * * * echo "hello from cron `date`" >> /home/username/development/cron_test/hello_sh_log.txt
```
The script I am trying to run, which runs from the command line:
```
#!/bin/bash

echo "hello bash! `date`" >> 'hello_sh_log.txt'
echo "greeted bash."
```
The last entries in syslog:
```
May 17 07:04:01 compname CRON[3750]: (username) CMD (echo "hello from cron `date`" >> /home/username/development/cron_test/hello_sh_log.txt)
May 17 07:04:01 compname CRON[3751]: (username) CMD (/home/username/development/cron_test/hello_sh.sh)
May 17 07:04:01 compname CRON[3749]: (CRON) info (No MTA installed, discarding output)
```

Any suggestions?

---

### Post by matt_symes on 2012-05-17
Hi


Here is how i did mine. I just changed the paths.
```

matthew@matthew-Aspire-7540:~$ pwd
/home/matthew
matthew@matthew-Aspire-7540:~$ ls hello*
ls: cannot access hello*: No such file or directory
matthew@matthew-Aspire-7540:~$ cat <<'EOF' > hello_sh.sh
> #!/bin/bash
> 
> echo "hello bash! `date`" >> 'hello_sh_log.txt'
> echo "greeted bash."
> EOF
matthew@matthew-Aspire-7540:~$ cat hello_sh.sh 
#!/bin/bash

echo "hello bash! `date`" >> 'hello_sh_log.txt'
echo "greeted bash."
matthew@matthew-Aspire-7540:~$ chmod 755 hello_sh.sh 
matthew@matthew-Aspire-7540:~$ ls -l hello_sh.sh 
-rwxr-xr-x 1 matthew matthew 104 May 17 22:17 hello_sh.sh
matthew@matthew-Aspire-7540:~$ crontab -e
```I added this to the cron tab entry
 
```

# m h  dom mon dow   command
* * * * * /home/matthew/hello_sh.sh

```Close crontab and it will update crons configuration.

 ```

matthew-Aspire-7540:~$ crontab -l
# m h  dom mon dow   command
* * * * * /home/matthew/hello_sh.sh
matthew@matthew-Aspire-7540:~$ tail -f /var/log/syslog
...
<snip>
...
May 17 22:29:01 matthew-Aspire-7540 CRON[2732]: (matthew) CMD (/home/matthew/hello_sh.sh)
May 17 22:29:01 matthew-Aspire-7540 CRON[2731]: (CRON) info (No MTA installed, discarding output)
   
matthew@matthew-Aspire-7540:~$ ls hello*
hello_sh_log.txt  hello_sh.sh
matthew@matthew-Aspire-7540:~$ cat hello_sh_log.txt 
hello bash! Thu May 17 22:17:07 UTC 2012
matthew@matthew-Aspire-7540:~$ 

```Kind regards

---

### Post by Lisiano on 2012-05-17
Try prepending bash to it?
```
bash /home/username/development/cron_test/hello_sh.sh
```
Also change the bash echo to point to an absolute path. I don't know 100% how cron works but it might be not setting $PWD or sets one under which you don't have write access.

---

### Post by japhyr on 2012-06-06
Just a quick note to say that I resolved the issue.  I believe it was a path issue, but unfortunately I forget the details now. Thank you both.

---

### Post by santiago g on 2012-08-01
> **japhyr said:**
> I have been trying to get crontab to run a bash script.  I have checked all the common errors, and can't figure it out.  My crontab, which does end in a new line:
```
# m h  dom mon dow   command
* * * * * /home/username/development/cron_test/hello_sh.sh
* * * * * echo "hello from cron `date`" >> /home/username/development/cron_test/hello_sh_log.txt
```
The script I am trying to run, which runs from the command line:
```
#!/bin/bash

echo "hello bash! `date`" >> 'hello_sh_log.txt'
echo "greeted bash."
```
The last entries in syslog:
```
May 17 07:04:01 compname CRON[3750]: (username) CMD (echo "hello from cron `date`" >> /home/username/development/cron_test/hello_sh_log.txt)
May 17 07:04:01 compname CRON[3751]: (username) CMD (/home/username/development/cron_test/hello_sh.sh)
May 17 07:04:01 compname CRON[3749]: (CRON) info (No MTA installed, discarding output)
```

Any suggestions?

When running Cron Tab make sure your bash script starts with a change to directory where you have your script with execution permissions:

#!/bin/bash
cd  /home/pathtomyscript/
my commands....

---

