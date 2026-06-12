---
title: "Why crontab not work?"
date: 2010-07-01
forum: Programming Talk
---

### Post by huangyingw on 2010-07-01
Hello all,
	I am trying cron at Ubuntu. So I update my /etc/crontab as bellow
	To edit /etc/crontab more conviniently, I run command 
	```

	chmod 777 /etc/crontab
	
```
	first
	```

	# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user	command
17 *	* * *	root    cd / && run-parts --report /etc/cron.hourly
25 6	* * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6	* * 7	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6	1 * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
#
52 22	* * *	root    cd / && run-parts --report /etc/cron.freetime
	
```
	And place a reboot.sh in /etc/cron.freetime/ as bellow
	```

	#!/bin/bash
	reboot
	
```
	So, I wait for 22:52, expecting to see my ubuntu server reboot. But it does not.
	Why?

---

### Post by dwhitney67 on 2010-07-01
I don't know why it didn't work, but I do know your approach is not the easiest way.  In fact, I would have done it this way, using my regular login account.

Step 1:  Create the script...

MyScript
```

#!/bin/bash

echo "Hello World" > /tmp/foo

```
Make sure it is executable...
```

chmod +x MyScript

```

Then setup *your* crontab...
```

crontab -e

```
Insert cron info; for example...
```

# m h  dom mon dow   command
17 * * * * /home/you/MyScript

```
You should not have to modify any of the files in /etc unless you *really* know what you are doing.

---

### Post by ju2wheels on 2010-07-01
Cron does not see your environment variables, thus neither does any script you execute with cron. As a result, every command you execute in cron and any subsequent scripts must be absolutely pathed, otherwise it will not know where to find the executable to run.

Change your /etc/cron.freetime/reboot.sh to this:
```

#!/bin/bash

/sbin/reboot

```

Also make sure that script has the proper execute permissions set and is owned by root.

[edit]
@dwhitney67: You can not add it to your regular user's crontab because the reboot command must be run as root in order to avoid it asking you for the root password.

---

### Post by dwhitney67 on 2010-07-01
> **ju2wheels said:**
> 
@dwhitney67: You can not add it to your regular user's crontab because the reboot command must be run as root in order to avoid it asking you for the root password.

You are correct, but at the same time, you neglected to mention that root can have its own private crontab.  To edit this, this command needs to be used:
```

sudo crontab -e

```

---

### Post by geirha on 2010-07-02
> **huangyingw said:**
> Hello all,
	I am trying cron at Ubuntu. So I update my /etc/crontab as bellow
	To edit /etc/crontab more conviniently, I run command 
	```

	chmod 777 /etc/crontab
	
```

What you are really saying here is that any user, even the least priviledged ones, are welcome to run any command as root. chmod 777 is ALWAYS a bad idea.

I recommend, instead:
```
chgrp admin /etc/crontab
chmod 664 /etc/crontab
```
After that, root and admins can edit the file (without needing to use sudo), but no one else.

> **huangyingw said:**
> 
	And place a reboot.sh in /etc/cron.freetime/ as bellow
	```

	#!/bin/bash
	reboot
	
```
	So, I wait for 22:52, expecting to see my ubuntu server reboot. But it does not.
	Why?
The problem is the extension. run-parts doesn't execute any script that contains a dot (.). One of the reasons for this is to make it easy to disable jobs, by just renaming the script to myscript.disabled for instance.

Also, in general, you shouldn't have extensions on shell scripts.

---

### Post by soltanis on 2010-07-02
+1 for please don't reset the permissions on that file without knowing what you're doing.

Use the command

```

crontab -e

```

To edit your crontab. If you need to have root run some commands, use the root crontab by prepending with a 'sudo'.

Finally, like others have said, but just to make sure this isn't lost on you, cron scripts run in a clean environment, which means they have no path variables set, so you must run all your commands with absolute paths. If a command needs to be run in a certain directory then you should have the cron command switch over to it before running the command (use the &&, Luke):

```

0 * * * * cd /cool/directory && sh cool-script

```

---

### Post by huangyingw on 2010-07-02
> **dwhitney67 said:**
> I don't know why it didn't work, but I do know your approach is not the easiest way.  In fact, I would have done it this way, using my regular login account.

Step 1:  Create the script...

MyScript
```

#!/bin/bash

echo "Hello World" > /tmp/foo

```
Make sure it is executable...
```

chmod +x MyScript

```

Then setup *your* crontab...
```

crontab -e

```
Insert cron info; for example...
```

# m h  dom mon dow   command
17 * * * * /home/you/MyScript

```
You should not have to modify any of the files in /etc unless you *really* know what you are doing.
Yes, thanks for your reminding. I just want to write a system wide "reboot" command at a certain time.

---

### Post by huangyingw on 2010-07-04
> **dwhitney67 said:**
> I don't know why it didn't work, but I do know your approach is not the easiest way.  In fact, I would have done it this way, using my regular login account.

Step 1:  Create the script...

MyScript
```

#!/bin/bash

echo "Hello World" > /tmp/foo

```
Make sure it is executable...
```

chmod +x MyScript

```

Then setup *your* crontab...
```

crontab -e

```
Insert cron info; for example...
```

# m h  dom mon dow   command
17 * * * * /home/you/MyScript

```
You should not have to modify any of the files in /etc unless you *really* know what you are doing.

Hello, I don't know why it still not works, quite frustrated:(

My /etc/cron.freetime/reboot file:
```

root@linux_programming:~# cat /etc/cron.freetime/reboot
#!/bin/bash
/sbin/shutdown -h now

```

Its right:
```

root@linux_programming:~# ls -al /etc/cron.freetime/reboot
-rwxrwxrwx 1 nobody nogroup 50 2010-07-03 10:34 /etc/cron.freetime/reboot

```

Result of my command "sudo crontab -e"
```

# m h  dom mon dow   command
42 12   * * *   root    /etc/cron.freetime/reboot

```
So, I restart the cron wiht command "service cron restart", and wait until 12:44.
And still nothing happen:(

---

### Post by ju2wheels on 2010-07-04
If you have followed some of the steps other people stated in this thread, you may have already broken cron by setting its permissions incorrectly. You should never change the groups or execute permissions on files in /etc or other system folders as it could prevent your system from working altogether if you change the wrong thing.

The first thing is that these files should be owned by root, do these fixes:

```

sudo chown -R root:root /etc/cron.freetime
sudo chown root:root /etc/crontab
sudo chmod 644 /etc/crontab
sudo chmod -R 755 /etc/cron.freetime

```

Also if Im not mistaken, havent looked at the docs, but I think your crontab should be this if you are using crontab for root (sudo crontab -e):
```

42 12   * * * /etc/cron.freetime/reboot

```

OR this if you are editing /etc/crontab (DO NOT do both, not that it will break anything but still choose one method):
```

42 12 * * * root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.freetime )

```

---

