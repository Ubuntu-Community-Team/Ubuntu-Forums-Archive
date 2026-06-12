---
title: "my script isn't running as a cronjob"
date: 2011-08-16
forum: Programming Talk
---

### Post by GrandVizier on 2011-08-16
I wrote myself a little script to give myself an alert when my system is running low on memory. Here is the script:

[PHP]<?php
	$mem_string = exec('cat /proc/meminfo | grep MemFree');
	$mem_string = str_ireplace('MemFree:', '', $mem_string);
	$mem_string = trim(str_ireplace('kb', '', $mem_string));

	$mem_total = exec('cat /proc/meminfo | grep MemTotal');
	$mem_total = str_ireplace('MemTotal:', '', $mem_total);
	$mem_total = trim(str_ireplace('kb', '', $mem_total));
	
	if($mem_total > 0){
		$percentage = ($mem_string / $mem_total) * 100;
		if($percentage < 10){
			exec('notify-send " Memory is LOW"');
		}
	}else{
		return;
	}
?>[/PHP]

it works just fine when I run:
```
/usr/bin/php /home/jeff/memory_script.php
```

but when I add 
22 * * * * root /usr/bin/php /home/jeff/memory_script.php
to /etc/crontab it does nothing - having a look in /var/log/syslog shows:
```
Aug 17 01:22:01 hardcore cron[986]: (*system*) RELOAD (/etc/crontab)
Aug 17 01:22:01 hardcore CRON[29564]: (root) CMD (/usr/bin/php /home/jeff/memory_script.php)
Aug 17 01:22:02 hardcore CRON[29563]: (CRON) info (No MTA installed, discarding output)

```

---

### Post by jmartrican on 2011-08-17
have you tried redirecting the output to a file?

e.g. /usr/bin/php /home/jeff/memory_script.php &> /tmp/file.log

---

### Post by GrandVizier on 2011-08-17
That was a great suggestion - it got rid of the "No MTA installed, discarding output" message in the log - but it didn't work - so I went into my memory_script.php and changed it so that all it did was ```
echo 'STARTING ' . "\n";	
```

when I run the file through the CL, /tmp/file.log fills up with STARTING - but when the cron is set to run, it doesn't output anything to the tmp file (as in if I leave anything in the tmp file, the cron deletes it)

---

### Post by gmargo on 2011-08-17
First of all, if you are going to be messing with **cron**, you should install an [MTA]("http://en.wikipedia.org/wiki/Message_transfer_agent") (aka Message Transfer Agent aka Mail Server) immediately, such as **postfix** or **exim4**.  The cron daemon is trying to send email to you, but can't since there's no mail server.

Second of all, **cron** runs programs in a sanitized environment, which does _not_ include the **$DISPLAY** environment variable that **notify-send** needs.  That's why your script works from the command line but not from cron. (BTW, it is a useful exercise to run the **env** command from cron, just to see how different the environment is.)

Here's a **cron**'able mini hello-world that will send notifications to the main display:
```

<?php
exec('env DISPLAY=:0 notify-send "Hello, World!"');
?>

```

---

