---
title: "gconftool-2 and Apache www-data user"
date: 2012-07-06
forum: Programming Talk
---

### Post by ernz on 2012-07-06
Hi all! 

This one has got me stumped. Can't think of a nicer, friendlier place to rage about this problem.

I have a LAMP stack configured on my local machine. I want to be able to fire a URL request at this machine and have it use PHP's exec() function to run the following to enable remote desktop sharing: 

```
gconftool-2 -s -t bool /desktop/gnome/remote_access/enabled true
```

There seems to be some sort of issue with gconftool here that won't allow a user which isn't connected to dbus run the command. A bug perhaps? Another problem is that anything run with exec() will be run as user www-data which won't configure my profile (/home/ernz)

So you say..."But ernz...you can always do this:"

```
echo thepassword | sudo -u ernz -S gconftool-2 -s -t bool /desktop/gnome/remote_access/enabled true 2>&1
```

but then I get this...
```

Array
(
    [0] => [sudo] password for www-data: Sorry, try again.
    [1] => [sudo] password for www-data:
    [2] => [sudo] password for www-data:
    [3] => Sorry, try again.
    [4] => [sudo] password for www-data:
    [5] => [sudo] password for www-data:
    [6] => Sorry, try again.
    [7] => sudo: 3 incorrect password attempts
)

```

Can I figure out www-data's password!? Can I hell! I've even tried with --config-source=xml::/home/ernz/.gconf - no luck.

I've tried all ridiculous combinations of changing the sudoers file which currently has this appended: 

```
www-data ALL=NOPASSWD: /usr/bin/gconftool-2
www-data ALL=NOPASSWD: /usr/bin/sudo
www-data ALL=NOPASSWD: ALL
```

Try it yourself! Here's the full PHP script:

[PHP]<?php

	echo "Turning remote desktop <strong>ON</strong>";
	exec('gconftool-2 -s -t bool /desktop/gnome/remote_access/enabled true 2>&1', $output);
	echo '<pre>';
	print_r($output);
	echo '</pre>';
	
?>[/PHP]

I'd really appreciate some help with this - it's getting silly now an I have no idea how to tackle this without incorporating a very large hammer and a severe ragequit.

---

### Post by ernz on 2012-07-07
Got this one figured out. I was going ***-backward about it. I enabled all my services and then configured ufw (firewall) to close down port 5900 for VNC. I then made a PHP script to edit a local flag file which contains a 1 or a 0:

index.php
[PHP]<?php
	
	error_reporting(0);
	
	function setremotedesktop($status, $fname = '/home/ernz/www/remotedesktop') {
		$fh = fopen($fname, 'w');
		fwrite($fh, $status);
		fclose($fh);
	}
	
	if ($_GET['remotedesktop'] == 'false') {
		setremotedesktop(0);
		echo "Firewall enabled";
	}
	if ($_GET['remotedesktop'] == 'true') {
		setremotedesktop(1);
		echo "Firewall disabled";
	}
	
?>[/PHP]

Then I made this script and had CRON run it every 1 minute:

setremotedesktop.sh
```
# If the remotedesktop is set as 1, enable the firewall blocking 5900
grep "0" /home/ernz/www/remotedesktop -q && echo "hunter2" | sudo -S ufw enable
# If the remotedesktop is set as 1, disable the firewall blocking 5900
grep "1" /home/ernz/www/remotedesktop -q && echo "hunter2" | sudo -S ufw disable
```

So every 1 minute, a CRON job runs a script which checks the content of a flag file which will be either a 1 or a 0 and it will set the ufw as enabled or disabled depending on the content of this file. Calls can be sent to my local web host remotely to configure this firewall too.

---

