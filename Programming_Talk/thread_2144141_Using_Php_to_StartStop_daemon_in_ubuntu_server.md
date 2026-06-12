---
title: "Using Php to Start/Stop daemon in ubuntu server"
date: 2013-05-11
forum: Programming Talk
---

### Post by termvrl on 2013-05-11
Hi All,

i am install a apache, mysql server in ubuntu 12.04.
what i try to do, using a php code to start/stop mysql daemon.

here my code,

<html>
<body>

<?php
exec("sudo /etc/init.d/mysql start > /dev/null 2>&1 &");
?>
</body>
</html> 

when i do ps aux, mysql not running... when i try to use phpadmin console also cannot login.

thanks 				

p/s: this is repost. i have post this on Absolute beginner but no one answer.

---

### Post by hakermania on 2013-05-11
Hi there! I guess it doesn't run due to the fact that **sudo **will expect your password after the command executes.

A **completely unsafe **(but quick) way to achieve this is to do:
```
echo your_password_here | sudo -S your_command_here
```
Another way would be to edit the sudoers file and allow the user which attempts to run mysql (I don't know which user is being used from apache to run stuff like this) without password.

More info for the latter way here:
[http://askubuntu.com/questions/159007/how-do-i-run-specific-sudo-commands-without-a-password](http://askubuntu.com/questions/159007/how-do-i-run-specific-sudo-commands-without-a-password)

---

### Post by termvrl on 2013-05-11
Hi ,
thanks for your help.
when i try put apache user, www-data, to sudoers, the mysql daemon still not start.

root    ALL=(ALL:ALL) ALL
www-data ALL=(ALL:ALL) ALL

same also when i do,

<?php

echo (your_password_here | sudo -S sudo /etc/init.d/mysql start);

?>




i'm new to php, sorry if i get it wrong

---

### Post by epicoder on 2013-05-11
One thing you could do is allow www-data to run /etc/init.d/mysql as root without a password. Before you do that, please consider the following security hole that would then be opened:
If someone sneaks a malicious script onto your system (the php and apache combo are notorious for blind execution holes), they could stop your mysql service with no effort. If you are handling sensitive data like personally identifying info, or important transactions such as money transfers, this could potentially be catastrophic. Basically, don't do this in production. ;)

To do this, remove the previous www-data line in sudoers and add this one in its place: 
```
www-data ALL=NOPASSWD:/etc/init.d/mysql
```
This will allow the user www-data to execute /etc/init.d/mysql as root without a password.

You should then be able to use your original method [exec("sudo...");] as you intended.

Make sure to use visudo, which uses a temporary file and checks it before replacing the actual file,
```
EDITOR=nano sudo visudo
```
 to avoid screwing yourself over with a syntax error. If there is one, sudo won't work. Once you're done, reload sudo with 
```
sudo service sudo reload
```
to put your changes in effect.

---

### Post by SeijiSensei on 2013-05-12
The only safe way to do this is via "semaphores."  Have the PHP application write a file to a known location that includes the command you want to execute, say "stop" or "start".  Then have a cron job running as root that checks for that file, carries out the command, and deletes the file when it is finished.  You can tell cron to check for the file once per minute.  That should be quickly enough if all you're doing is taking down the MySQL server.

If you need confirmation, have the cron script send you an email when it is finished.

Do not give the www-data any root privileges whatsoever unless this is a server that will never be exposed to the world outside your firewall.

Here's a simple example for the cron script assuming the file is called /tmp/mysql-controller and contains "start" or "stop".

```

#!/bin/bash
ADMIN=you@example.com
CHKFILE=/tmp/mysql-controller

# quit if the file isn't there or has zero length 
[ -s "$CHKFILE" ] && exit 0

# extract the command from the file and run it
CMD=$(cat $CHKFILE)
service mysql $CMD >> /dev/null
rm -f $CHKFILE

# send an email notice to ADMIN
mail -s 'MySQL restarted' $ADMIN < /dev/null

```

To have the server send you mail, you need to have an SMTP server like Postfix installed and also the **mailutils** package that includes the "mail" command-line program.  If you use "sudo apt-get install mailutils" it will install Postfix as a dependency if you do not already have it.

---

### Post by termvrl on 2013-05-12
Hi,

thanks for help.
its work.. mysql deamon started.
if you dont mind, is there any other way (best practice) that we can stop/start daemon using php.

thanks again.

---

### Post by termvrl on 2013-05-12
hi SeijiSensei,

thanks i will try it later.

---

### Post by termvrl on 2013-05-12
Hi,

i use 'crontab -e' to edit my cron job.
i add your script with additional "*/5 * * * * CHKFILE=/tmp/mysql-controller" in order to check the file for every 5 minute. 
but it show me error, "/tmp/crontab.xb4M7S/crontab":27: bad minute.

---

### Post by SeijiSensei on 2013-05-12
You have to write a script with contents similar to what I posted, mark the script executable, then run it from cron.  Everything needs to be done with root privileges.

Use nano or some other editor with sudo to create a root-owned file called "/usr/local/sbin/mysql-check" and copy the contents of the code block above into that file.  Save the file and mark it executable with "sudo chmod u+x /usr/local/sbin/mysql-check".  Now use your editor, again as root, to create the file /etc/cron.d/mysql-check that contains just this line:

```

* * * * * root /usr/local/sbin/mysql-check

```

That will run the script once each minute.  If you want to try this approach, you should [read this guide first]("https://help.ubuntu.com/community/CronHowto").

---

