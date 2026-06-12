---
title: "PHP and unix domain sockets"
date: 2018-08-22
forum: Programming Talk
---

### Post by jerome1232 on 2018-08-22
Alright, so I'm making a little robot car on a raspberry pi with a web interface. I'm a beginner programming so a lot of my coding I'm learning as I'm making it.

My biggest hurdle I hit was figuring out how on earth was I going to get keystrokes in a web browser communicated to a python script. I found my answer in unix domain sockets.

So I've successfully gotten two python scripts communicated via unix domain sockets, but I can't get PHP to work. Specifically I'm running into permissions issues.

This is the php portion of my test script.

```
<?php
	echo php_uname();
	echo '<br>';
	echo shell_exec('uptime -p');
	echo '<br>';
	// This is just showing me the current user running the php script
	echo 'Current Script owner: '.get_current_user();
	echo '<br>';
	// Creating a unix domain socket
	$sock = socket_create(AF_UNIX, SOCK_STREAM, 0);
	if ($sock === false) {
		echo "socket_create() failed: reason: "
			.socket_strerror(socket_last_error($sock))."<br>";
	}
	// Setting up my path relative to the virtual servers root
	$path = $_SERVER['DOCUMENT_ROOT'].'/tmp/test';
	// Checking that my path is what I think it's supposed to be
	echo "This is the path to the socket: ".$path."<br>";
	// Binding to the socket
	if(socket_bind($sock, $path) === false) {
		echo "socket_bind() failed: reason:"
			.socket_strerror(socket_last_error($sock))."<br>";
	}
	// checking for errors after having bound to the socket
	echo '<br>';
	// listening on the bound socket
	$isListen = socket_listen($sock);
	while ($isListen) {
		$conn = socket_accept($sock);
		if ($conn == False) {
			usleep(100);
		} else if ($conn > 0) {
			echo socket_read($sock, 1);
			socket_close($sock);
		}
	}
	socket_close($sock) ?>
```

This is what gets outputted to the webpage when that runs.

```
Linux raspberrypi 4.14.62-v7+ #1134 SMP Tue Aug 14 17:10:10 BST 2018 armv7l
up 1 day, 19 hours, 3 minutes 
Current Script owner: pi
This is the path to the socket: /home/pi/Documents/robot_car/webpage/tmp/test
socket_bind() failed: reason: Permission denied
```

I don't understand why php doesn't have permission to create a unix domain socket, even going the other way I was able to create a unix domain socket with python, but php would get denied when trying to connect to it.

---

### Post by spjackson on 2018-08-22
I suspect that the problem is permission in the filesystem. Which user account does the web-server run under? For apache on ubuntu this is usually www-data. Does that account have permission to access and write to the folder /home/pi/Documents/robot_car/webpage/tmp?

---

### Post by jerome1232 on 2018-08-22
Well PHP returns the php script is running under PI.

Is that seperate, can I check what user apache2 runs under?

That particular folder has the permissions below, so if apache2 is indeed running as www-data it wouldn't have permission to write there.

```
drwxr-x-r-x 2 pi pi 4096 Aug 21 00:14 tmp
```

I modified it to the below permissions and...

```
drwxrwxr-x 2 pi www-data 4096 Aug 21 00:14 tmp
```

Hey it worked.

```
Linux raspberrypi 4.14.62-v7+ #1134 SMP Tue Aug 14 17:10:10 BST 2018 armv7l
up 1 day, 20 hours, 7 minutes 
Current Script owner: pi
This is the path to the socket: /home/pi/Documents/robot_car/webpage/tmp/test

Attempting to connect to socket: 'tmp/pySock'
Path to socket: /home/pi/Documents/robot_car/webpagetmp/pySock
Socket connection succeded
```

It's always the simple things isn't?

---

### Post by spjackson on 2018-08-22
> **jerome1232 said:**
> Well PHP returns the php script is running under PI.

Not so. Counter-intuitively, get_current_user() returns the _owner of the current script_ - see docs. It's good that you've managed to solve it.

---

