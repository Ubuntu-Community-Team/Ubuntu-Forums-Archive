---
title: "Parse json and execute commands"
date: 2013-05-08
forum: Programming Talk
---

### Post by pedrommone on 2013-05-08
Hi, I've a remote json, and I want fetch it and execute it every 6 hours, its a json with firewall settings (for iptables). Heres an example of the json

```
[COLOR=#000000][
"iptables --flush",
"iptables -P INPUT DROP",
"iptables -P FORWARD DROP",
"iptables -P OUTPUT DROP",
"iptables -A INPUT -i eth0 -p tcp --dport 22 -m state --state NEW,ESTABLISHED -j ACCEPT",
"iptables -A OUTPUT -o eth0 -p tcp --sport 22 -m state --state ESTABLISHED -j ACCEPT",
"iptables -A OUTPUT -o eth0 -p tcp --dport 80 -m state --state NEW,ESTABLISHED -j ACCEPT",
"iptables -A INPUT -i eth0 -p tcp --sport 80 -m state --state ESTABLISHED -j ACCEPT",
"iptables -A OUTPUT -o eth0 -p tcp --dport 7171,7175 -m state --state NEW,ESTABLISHED -j ACCEPT",
"iptables -A INPUT -i eth0 -p tcp --sport 7171,7175 -m state --state ESTABLISHED -j ACCEPT"
][/COLOR]
```

The question is, how I can fetch it and execute with root permission with a bash script? I've searched something to parse the json, but I wasnt been sucessed. Thanks in advance.

---

### Post by epicoder on 2013-05-08
First off, consider the security ramifications behind this sort of action. You're blindly depending on the security of this remote server- if it gets breached, an attacker could replace that file with whatever they want, and then your script would execute their commands with root permissions. So consider finding a way to do this without involving another server. 

For parsing the JSON, it would probably be easier to write your own program. For example, here is a simple python 3 program to do so.
Don't actually use it as it blindly executes whatever it gets and is insecure in every way possible.
```

#!/usr/bin/env python3
import json
import subprocess
import urllib.request
commands = json.loads(urllib.request.urlopen("http://example.com/json/file").read().decode())
for command in commands:
    program, *args = command.split()
    subprocess.call(program, *args)

```

---

### Post by Vaphell on 2013-05-09
agreed, running the commands blindly would be a security nightmare. At the very least you need to whitelist commands eg only iptables is allowed, also you need to watch out for command terminating characters like ; and & (so doing something like *iptables ...; malicious_cmd* is not possible)

---

### Post by pedrommone on 2013-05-09
I dont care about the security stuff right now, Im testing some ideias and I want to see how it works. Anyway, how make it always execute as root?

---

### Post by Vaphell on 2013-05-10
put the job in root's cron
[http://unix.stackexchange.com/questions/3570/how-to-have-cron-run-a-python-script-as-root](http://unix.stackexchange.com/questions/3570/how-to-have-cron-run-a-python-script-as-root)

---

### Post by pedrommone on 2013-05-11
Im trying to add the job with the following command, but is not working!

```
ubuntu@ip-10-252-16-247:~$ sudo crontab /etc/iptables.py 1 * * * * -u root
"/etc/iptables.py":1: bad minute
errors in crontab file, can't install.
ubuntu@ip-10-252-16-247:~$

```

---

### Post by epicoder on 2013-05-11
You are attempting to replace the crontab with /etc/iptables.py. Use
```
sudo crontab -e
```
to edit the crontab.

---

### Post by pedrommone on 2013-05-12
Heres mine crontab

```

# Edit this file to introduce tasks to be run by cron.
#
# Each task to run has to be defined through a single line
# indicating with different fields when the task will be run
# and what command to run for the task
#
# To define the time you can provide concrete values for
# minute (m), hour (h), day of month (dom), month (mon),
# and day of week (dow) or use '*' in these fields (for 'any').#
# Notice that tasks will be started based on the cron's system
# daemon's notion of time and timezones.
#
# Output of the crontab jobs (including errors) is sent through
# email to the user the crontab file belongs to (unless redirected).
#
# For example, you can run a backup of all your user accounts
# at 5 a.m every week with:
# 0 5 * * 1 tar -zcf /var/backups/home.tgz /home/
#
# For more information see the manual pages of crontab(5) and cron(8)
#
# m h  dom mon dow   command


0 * * * * /etc/iptables.py

```

And its not working!

---

### Post by epicoder on 2013-05-12
Make sure that:
[LIST]
[*]You are editing root's crontab and not yours. (make sure crontab -e is run as root)
[*]/etc/iptables.py is hashbanged. That is, this must be its first line: #!/usr/bin/env python
[*]You are using the correct version of python. If this is a python 3 script, use #!/usr/bin/env python3
[*]/etc/iptables.py is owned by root and is executable.
[/LIST]

Also, check root's mail spool (sudo mail) for mail from cron.

---

### Post by pedrommone on 2013-05-12
Is my fault, it was working, but in some boxes is not working, I dont know how!

---

